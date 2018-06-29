# PHP输出HTML纯文本而不让浏览器解析

## HTML转文本：
```bash
echo htmlentities($htmlstr,ENT_QUOTES,"UTF-8");
```

## 获取翻译用表：
```bash
get_html_translation_table()
```

### 文本转HTML：
```bash
html_entity_decode()
```
