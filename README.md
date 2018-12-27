# IIS_Rewrite
IIS Rewrite Rules

```xml
<code>
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <defaultDocument enabled="true">
            <files>
                <clear />
                <add value="route.php" />
                <add value="index.asp" />
                <add value="Default.htm" />
                <add value="Default.asp" />
                <add value="index.htm" />
                <add value="index.html" />
                <add value="iisstart.htm" />
                <add value="default.aspx" />
                <add value="" />
            </files>
        </defaultDocument>
<!--
Block potentially dangerous querystrings.
Requires the IIS7 URL Rewrite Module, available from: http://www.iis.net/download/urlrewrite
-->            	
        <rewrite>
            <rules>
                <rule name="rule 1x" stopProcessing="true">
                    <match url="^(.*)$"  ignoreCase="true" />
                    <action type="Rewrite" url="route.php?uri={R:1}"  appendQueryString="true" />
                </rule>
            </rules>
        </rewrite>

    </system.webServer>
</configuration>

</code>
```
