<!-- Error Events in ASP.NET -->

<!-- Handling exceptions using try/catch blocks is commonly termed as structured exception handling. ASP.NET provides 2 error events. -->

<!-- 1 Page_Error -->
<!-- This event is raised at the page level, when there is an unhandled exception on the page. The event handler resides on the page. -->

<!-- 2. Application_Error -->
<!-- This event is raised at the application level, when there is an unhandled exception at an application level. The event handler resides in the Global.asax file. -->

<!-- These error events can be used as a substitute or supplemental to structured exception handling. -->

<!-- Please note that: -->
<!-- 1. If the exception is not cleared in the Page-Error event, it gets propagated to the application level and the Application_Error event handler gets executed. If we are not clearing the exception at the application level the application crashes with the "Yellow Screen of Death". -->
<!-- 2. If the exception is cleared and redirection to Errors.aspx is not done then a blank page is displayed. This is because web form processing is immediately stopped when an exception occurs. -->

<!-- Ex.

protected void Page_Error(object sender, EventArgs e)
{
    Exception ex = Server.GetLastError();
    Server.ClearError();
    Response.Redirect("~/Errors.aspx");

}

-->

<!-- If an exception is not handled at the page level using the Page_Error event, it gets propagated to the application level and can be handled using the Application_Error event handler in Global.asax and can be used as a single, centralized location for error handling. -->