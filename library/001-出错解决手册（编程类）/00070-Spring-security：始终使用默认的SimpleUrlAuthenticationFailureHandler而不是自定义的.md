# Spring-security ：始终使用默认的SimpleUrlAuthenticationFailureHandler而不是自定义的
`【系统环境】windows 10`  
`【操作内容】SpringMVC4 /  Hibernate5.2 / Redis 3.2 / IntelliJ IDEA 2018.1 / Java1.8`  
`【解决方案验证次数】1次`  
## <i class="fa fa-question-circle"></i> 出现问题
Spring security想要使用自定义的出错处理类CustomAuthenticationFailureHandler，但是却没有被使用，而是用的默认的SimpleUrlAuthenticationFailureHandler。
## <i class="fa fa-bullseye"></i> 根本原因
配置没有配置好。
## <i class="fa fa-check-circle"></i> 解决方法
修改SecurityConfig.java中的：
```
CustomAuthenticationFilter customAuthenticationFilter() throws Exception {
        CustomAuthenticationFilter filter = new CustomAuthenticationFilter();
        filter.setAuthenticationManager(authenticationManagerBean());
        return filter;
    }
```
为：
```
@Resource
private CustomAuthenticationSuccessHandler customAuthenticationSuccessHandler;
@Resource
private CustomAuthenticationFailureHandler customAuthenticationFailureHandler;


CustomAuthenticationFilter customAuthenticationFilter() throws Exception {
        CustomAuthenticationFilter filter = new CustomAuthenticationFilter();
        filter.setAuthenticationSuccessHandler(customAuthenticationSuccessHandler);
        filter.setAuthenticationFailureHandler(customAuthenticationFailureHandler);
        filter.setFilterProcessesUrl("/login");
        filter.setAuthenticationManager(authenticationManagerBean());
        return filter;
    }
```
