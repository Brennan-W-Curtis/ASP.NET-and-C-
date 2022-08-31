<!-- ApplicationState in ASP.NET -->

<!-- Points to Remember when using Application State Variables -->
<!-- 1. Application State variables are available across all pages and sessions. They are like multi-user global data. -->
<!-- 2. Application State variables are stored on the web-server. -->
<!-- 3. Application State variables are cleared only when the process hosting the application is restarted, that is when the application ends. -->
<!-- 4. Application State variables are not shared across a Web Farm or a Web Garden. -->

<!-- Ex. 

public partial class WebForm1 : System.Web.UI.Page
{
    protected void ButtonSendData_Click(object sender, EventArgs e)
    {
        Application["Name"] = Text_Name.Text;
        Application["Email"] = Text_Email.Text;

        Response.Redirect("~/WebForm2.aspx");
    }
}

public partial class WebForm2 : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (Application["Name"] != null)
        {
            Label_Name.Text =  Application["Name"].ToString();
        }
        if (Application["Email"] != null)
        {
            Label_Email.Text =  Application["Email"].ToString();
        }
    }
}

-->

<!-- 5. Application State variables are not thread safe. lock and Unlock methods of the application class must be used to protect against race conditions, deadlocks, and access violations. -->

<!-- Ex.

Application.Lock();
Application["GlobalVariable"] = (int)Application["GlobalVariable"] + 1;
Application.UnLock();

-->

<!-- Please Note: In this example, we are using application state variables to send data from one web form to another. If the requiement is just to send data from webform to another you should consider other alternatives. -->

<!-- 6. Use Application State variables only when the variables need to have global access and when you need them for the entire time, during the life time of an application. The cache object can be used as an alternative, if you need to have global access for a certain duration. -->

<!-- Application state variables are global and all sessions have access to them. So, these variables can be used to track the number of users online. -->

<!-- Every time a new user connects to your application, we want to increase the number of users online by 1. Along these same lines, when ever a user session ends then we need to decrease the number of users online by 1. -->

<!-- But how do we know when a new user connects to our application. Session_Start() event is fired when ever a new session is established. When the session ends, Session_End() event is fired. The event handlers are in the global.asax file. -->

<!-- By default, the browser instances share the session cookie. To have a new session id assigned when a new browser instance requests the webform, set cookieless="true" for the sessionState element in the web.config. -->

<!-- Ex.

protected void Application_Start(object sender, EventArgs e)
{
    Application["UsersOnline"] = 0;
}

protected void Session_Start(object sender, EventArgs e)
{
    Application.Lock();
    Application["UsersOnline"] = (int)Application["UsersOnline"]++;
    Application.UnLock();
}

protected void Session_End(object sender, EventArgs e)
{
    Application.Lock();
    Application["UsersOnline"] = (int)Application["UsersOnline"]--;
    Application.UnLock();
}

public partial class WebForm1 : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        Response.Write("Number of Users online: " + Application["UsersOnline"].ToString());
    }
}

-->