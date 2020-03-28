# No installed provider supports this key SecretKeySpec
`【系统环境】Linux`  
`【操作内容】java AES加密`  
`【解决方案验证次数】2次`  
## <i class="fa fa-question-circle"></i> 出现问题
Linux运行24位AES加密程序报错：
```
No installed provider supports this key: javax.crypto.spec.SecretKeySpec
error=Illegal key size or default parameters
Exception in thread "main" java.lang.NullPointerException
	at java.lang.String.<init>(String.java:566)
	at Jce.main(Jce.java:23)
```

## <i class="fa fa-bullseye"></i> 根本原因
Java的政策文件限制了密钥长度。  
JCE（Java Cryptography Extension）是Java的加密扩展包，由于美国对某些国家有进出口限制，因此低版本Java默认限制了密钥长度，比如AES加密只能使用16位AES-128，超过16位就会报这个错。  

[JDK8文档描述](https://www.oracle.com/java/technologies/jdk-8-readme.html)
```
Unlimited Strength Java Cryptography Extension
Due to import control restrictions for some countries, the Java Cryptography Extension (JCE) policy files shipped with the JDK and the JRE allow strong but limited cryptography to be used. These files are located at: <java-home>/lib/security/local_policy.jar <java-home>/lib/security/US_export_policy.jar where <java-home> is the jre directory of the JDK or the top-level directory of the JRE.

An unlimited strength version of these files indicating no restrictions on cryptographic strengths is available on the JDK web site for those living in eligible countries. Those living in eligible countries may download the unlimited strength version and replace the strong cryptography jar files with the unlimited strength files.
```

## <i class="fa fa-check-circle"></i> 解决方法
### 1、Java版本<Java8u151
（1）去Oracle官网找到对应的政策解封jar包local_policy.jar和US_export_policy.jar
* [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 6](https://www.oracle.com/java/technologies/jce-6-download.html)
* [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 7](https://www.oracle.com/java/technologies/javase-jce7-downloads.html)
* [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8](https://www.oracle.com/java/technologies/javase-jce8-downloads.html)
* [百度网盘全部下载](https://pan.baidu.com/s/16SEchr3S3IZ4BKvTpgVIFg)（密码pmhg）  

（2）覆盖$JAVA_HOME/jre/lib/security路径下对应的文件  
（3）重启Java应用程序

### 2、Java版本>=8u151且<8u161
（1）找到对应的安全描述文件
* JDK：<java_home>/jre/lib/security/java.security
* JRE：<java_home>/lib/security/java.security

（2）取消注释这一行，并保存
```
crypto.policy=unlimited
```
（3）重启JVM
### 3、Java版本>=8u161
例如Java8u161、Java9等，默认已经放开了这个JCE密钥长度限制。如果仍然发生报错，请检查java.security这个文件是否是最新的。
