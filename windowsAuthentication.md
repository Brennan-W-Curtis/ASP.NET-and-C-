<!-- Windows Authentication -->

<!-- Anonymous authentication is fine for web sites that contain public information, that everyone can see. -->

<!-- However, if the web site contains private information or performs tasks such as booking tickets, placing orders, etc, then the users need to be authenticated and authorized. -->

<!-- Windows authentication, identifies and authorizes users based on the server's user list. Access to resources on the server is then granted or denied based on the user account's privileges. -->

<!-- Windows authentication is best suited for Intranet Web pplications. -->

<!-- The advantage of Windows authentication is that, the Web application can use the exact same security scheme that applies to your corporate network. User names, passwords, and permissions are the same for network resources and Web applications. -->

<!-- Security for an ASP.NET Web application can be configured in 2 places. In IIS and in the application itself. -->

<!-- If both, anonymous and windows authentication are enabled in IIS and if we don't have a deny entry for anonymous users in the web.config file, then the resources on the web server are accessed using anonymous authentication. -->

<!-- Anonymous authentication can be disabled in IIS or in the web.config file. -->

<!-- Ex.

<authorization>
    <deny users="?" />
</authorization>

-->

<!-- If you want to have the application code executed using the logged in user identity, then enable impersonation. Impersonation can be enabled through IIS or by adding the following element to the web.config file. -->

<!-- Ex. <identity impersonate="true"> -->

<!-- If impersonation is enabled, the application executes using the permissions found in your user account. So, if the logged in user has access, to a specific network resource, only then will they be able to access that resource through the web application. -->

<!-- Summary -->

<!-- ? and * have special meaning when us4ed in the authorization element in the web.config -->

<!-- ? (Question Mark) -->
<!-- Indicates anonymous users. -->

<!-- * (Star) -->
<!-- Indicates all users. -->

<!-- Allowing or denying access to specific users: -->

<!-- Ex.

<authorization>
    <allow users="Example-User\User" />
    <deny users="*" />
</authorization>

-->

<!-- Using windows roles to control access: -->

<!-- Ex.

<authorization>
    <allow roles="Administrators" />
    <deny users="*" />
</authorization>

-->

<!-- How to programmatically check if the user belongs to a specific role: -->

<!-- Ex.

if (User.IsInRole("Administrators"))
{
    // Admin statements
}
else 
{
    // Non-admin statements
}

-->

<!-- Folder Level Authorization -->

<!-- A very common ASP.NET interview question: -->
<!-- Is it possible to have more than one web.config file? -->

<!-- If you want to execute the application code, using the looged in Administrator account, then enable impersonation in the web.config file of the Admin folder. With this setting in place all the pages in the Admin folder are executed using the logged in user account. Where as the pages outside of the folder are executed using the identity of the application pool. -->

<!-- Ex.

<system.web>
    <authorization>
        <allow roles="Administrators" />
        <deny users="*" />
    </authorization>
    <identity impersonate="true" />
</system.web>

-->

<!-- It's also possible to impersonate with a specific user name and password. With this setting, whenever any user belonging to the "Administrators" group requests a page from the Admin folder the code with be executed using the "Example" account. -->

<!-- Ex.

<system.web>
    <authorization>
        <allow roles="Administrators" />
        <deny users="*" />
    </authorization>
    <identity impersonate="true" userName="Example" password"Example" />
</system.web>

-->