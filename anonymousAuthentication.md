<!-- Anonymous Authentication -->

<!-- Authenication is the process of identifying users. Authorization is the process of granting access to users based on their identity. Together, authentication and authorization secure our Web Applications. -->

<!-- Questions Posed by Each -->

<!-- Authentication -->
<!-- Who is the User? -->

<!-- Authorization -->
<!-- What rights does the user have? -->
<!-- What resources can the user access? -->

<!-- Most public web sites, do not ask the user to enter any user name and password. But still, they are able to access the content of said web sites. -->

<!-- ASP.NET Web Applications provide anonymous access to resources on the server. -->

<!-- Anonymous authentication allows users to access the public areas of the web site without prompting the user for their user name or password. -->

<!-- In IIS 6.0 -->
<!-- IUSR_ComputerName is used for providing anonymous access. -->

<!-- In IIS 7.0 -->
<!-- IUSR account is used for providing anonymous access. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    Response.Write("Application code executed using: ");
    Response.Write(System.Security.Principal.WindowsIdentity.GetCurrent().Name = "<br />");
    
    Response.Write("Is User Authenticated: ");
    Response.Write(User.Identity.IsAuthenticated.ToString() + "<br />");
    
    Response.Write("Authentication Type, if Authenticated: ");
    Response.Write(User.Identity.AuthenticationType + "<br />");

    Response.Write("User Name, if Authenticated: ");
    Response.Write(User.Identity.Name + "<br />");
}

-->

<!-- By default anonymous authentication is enabled in IIS. -->

<!-- By default, the application pool identity is used to execute the application code. -->

<!-- To disable anonymous authentication: -->
<!-- Click the "Disable" link under actions in the right hand side panel in IIS or add the following to the web.config file. -->

<!-- Ex.

<authorization>
    <deny users="?">
    <allow users="*">
</authorization>

-->

<!-- To change the account that is associated with anonymous access, click the "Edit" link under actions in the right hand side panel in IIS. Notice that the default account is IUSR. This can be changed to a custom windows account or application pool identity. -->

 