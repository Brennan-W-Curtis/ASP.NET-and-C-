<!-- Events -->

<!-- In a web application, events can occur at 3 levels -->
<!-- 1. At the Application Level (Example: Application Start || Session_Start event in global.asax) -->
<!-- 2. At the Page or web form Level (Example: Page Load || Page_load) -->
<!-- 3. At the Control Level (Example: Button Click || Selected index changed event on a dropdownlist) -->

<!-- ViewState variables are used to preserve data across page post back. By default, ViewState of one webform is not available in another webform. -->

<!-- Techniques to send data from one webform to another. -->
<!-- 1. Query Strings -->
<!-- 2. Cookies -->
<!-- 3. Session State -->
<!-- 4. Application State -->

<!-- Session state variables are available across all pages, but only for a given single session. -->
<!-- Session variables are like single-user global data. Only the current session has access to its Session state. -->

<!-- Application state variables are available across all pages and across all sessions. -->
<!-- Application state variables are like multi-user global data. All sessions can read and write Application State variables. -->

<!-- Application Level Events -->

<!-- In an ASP.NET web application, the Global.asax file contains the application level events. In general, Application events are used to initialize data that needs to be available to all the current session of the application. Where as Session events are used to initialize data that needs to be available for a given individual session, but not between multiple sessions. -->

<!-- Ex.

void Application_Start(object sender, EventArgs e)
{
    // Code that runs on application startup.
}

void Application_End(object sender, EventArgs e)
{
    // Code that runs on application shutdown.
}

void Application_Error(object sender, EventArgs e)
{
    // Code that runs when an unhandled error occurs.
}

void Session_Start(object sender, EventArgs e)
{
    // Code that runs when a new session is started.
}

void Session_End(object sender, EventArgs e)
{
    // Code that runs when a session ends.

    // Note: the Session_End event is raised only when the sessionstate mode is set to InProc in the Web.config file. If session mode is set to StateServer or SQLServer, the event is not raised.
}

-->

<!-- Ex. Global.asax

void Application_Start(object sender, EventArgs e)
{
    // Create Application state variables
    Application["TotalApplications"] = 0;
    Application["TotalUserSessions"] = 0;
    // Increment TotalApplications by 1
    Application["TotalApplications"] = (int)Application["TotalApplications"] + 1;
}

void Session_Start(object sender, EventArgs e)
{
    // Increment TotalUserSessions by 1
    Application["TotaluserSessions"] = (int)Application["TotalUserSessions"] + 1;
}

void Session_End(object sender, EventArgs e)
{
    // Decrement TotalUserSessions by 1
    Application["TotaluserSessions"] = (int)Application["TotalUserSessions"] - 1;
}
 
-->

<!-- Ex. Webform.aspx

protected void Page_load(object sender, EventArgs e)
{
    Response.Write("Number of Applications: " + Application["TotalApplications"]);
    Response.Write("Number of Users Online: " + Application["TotalUserSessions"]);
}
 
-->

<!-- What is a Session -->

<!-- A session is a unique instance of the browser. A single user can have multiple sessions, by visiting your application, with multiple instances of the browser running with a different session-id on their machine. -->

<!-- How to get a new session-id and force the Session_Start() event to execute -->
<!-- 1. Close the existing borwser window and then open a new instance of the browser. -->
<!-- 2. Open a new instance of a different browser. -->
<!-- 3. Use Cookie-less Sessions -->

<!-- Ex. <sessionState mode="InProc" cookieless="true"></sessionState> -->
