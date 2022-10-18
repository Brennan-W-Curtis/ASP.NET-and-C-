<!-- Redirect from HTTP to HTTPS -->

<!-- To redirect users from HTTP to HTTPS automatically, there are several ways. -->

<!-- URL ReWrite Module -->

<!-- Step 1: -->
<!-- Download and install "URL ReWrite" module from the following link. -->
<!-- http://www.iis.net/downloads/microsoft/url-rewrite -->

<!-- Step 2: -->
<!-- Uncheck "Require SSL" option from "SSL Settings" for the web application in IIS. -->

<!-- Step 3: -->
<!-- Add ReWrite rules in the web.config file. These rules can also be created in IIS directly using the "URL ReWrite" module. -->

<!-- Ex.

<system.webServer>
    <httpRedirect enabled="false" destination="" httpResponseStatus="Found" />
    <rewrite>
        <rules>
            <rule name="HTTP to HTTPS Redirect" stopProcessing="true" >
                <match url="(.*)" />
                <conditions>
                    <add input="{HTTPS}" pattern="off" />
                </conditions>
                <action type="Redirect" url="https://{HTTP_HOST}{REQUEST_URI}" redirectType="Found" />
            </rule>
        </rules>
    </rewrite>
</system.webServer>

-->

<!-- Custom Errors -->

<!-- Custom error pages can be set at the server level or at a specific application level in IIS. -->

<!-- Step 1: -->
<!-- Make sure the "Require SSL" option from "SSL Settings" is checked for your web application in IIS. -->

<!-- Step 2: -->
<!-- Create an HTML file, that does the redirection. -->

<!-- Step 3: -->
<!-- In IIS, set the error page -->

<!-- Access the application using HTTP. You will be automatically redirected to HTTPS. -->

<!-- Ex.

<script type="text/javascript" language="JavaScript">

    function Redirect_HTTP_To_HTTPS() {
        const HTTP_URL - window.location.hostname + window.location.pathname;
        const HTTPS_URL = "https://" + HTTP_URL;
        window.location = HTTPS_URL;
    }
    Redirect_HTTP_To_HTTPS();
    
</script>

-->