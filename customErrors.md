<!-- Custom Errors in ASP.NET -->

<!-- If there is an unhandled exception, by default, the generic yellow screen of death is displayed. Instead, custom error pages can be displayed. Custom error pages can be defined at 2 levels. -->

<!-- 1. Application Level -->
<!-- In the web.config file using the customErrors element. -->

<!-- 2. Page Level -->
<!-- In the Page directive, using the ErrorPage attribute. -->

<!-- Page level custom error pages take precedence over application level custom error pages. -->

<!-- Custom error pages provide the flexibility of displaying a specific page in response to one or more of the available HTTP status codes. -->

<!-- To specify the custom error pages at an application level, use the customErrors element in web.config. -->
<!-- Ex.

<customErrors mode="On" defaultRedirect="DefaultErrorPage.aspx">
    <error statusCode="401" redirect="UnauthorizedErrorPage.aspx" />
    <error statusCode="404" redirect="PageNotFoundErrorPage.aspx" />
    <error statusCode="500" redirect="InternalServerErrorPage.aspx" />
</customErrors>

-->

<!-- The mode attribute determines when a custom error page is displayed over the yellow screen of death exception page. Mode attribute can have On, Off, or RemoteOnly. RemoteOnly is set by default. -->

<!-- 1. On -->
<!-- Custom error pages are displayed both on local and remote machines. -->

<!-- 2. Off -->
<!-- Custom error pages are not displayed anywhere. -->

<!-- 3. Custom error pages are displayed on remote machines and the exception page on a local machine. -->

<!-- If the redirect is done in Application_Error() event handler in Global.asax, the custom error page will have no effect. -->

<!-- In your application, if you have to display specific custom error pages for specific http status codes, then use custom errors. If you just have one generic error page, then Global.asax can be used. -->

<!-- Please note that, the exception object needs to be retrieved before the user is redirected to a custom error page. Because a custom error page is displayed through redirection, the context for the error is lost and Server.GetLastError() returns nothing from the target custom error page. -->
