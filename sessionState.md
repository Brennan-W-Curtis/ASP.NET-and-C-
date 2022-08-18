<!-- Session State in ASP.NET -->

<!-- Just like query strings, Session State variables can also be used to send data from one webform to another. -->

<!-- Points to remember about Session State variables -->
<!-- 1. Session State variables are stored on the web server by default and kep for the life time of a session. -->
<!-- 2. The default session state mode is InProc. -->

<!-- Ex.

public partial class WebForm1 : System.Web.UI.Page 
{
    protected void ButtonSendData_Click(object sender, EventArgs e)
    {
        Session["Name"] = Text_Name.Text;
        Session["Email"] = Text_Email.Text;

        Response.Redirect("~/WebForm2.aspx");
    }
}

public partial class WebForm2 : System.Web.UI.Page 
{
    protected void Page_load(object sender, EventArgs e)
    {
        Label_Name.Text = Session["Name"].ToString();
        Label_Email.Text = Session["Email"].ToString();
    }
}

-->

<!-- 3. The lifetime of a session is determined by the time-out value in the web.config file. The default is 20 minutes. The time-out value can be adjusted according to your application requirements. -->

<!-- Ex. <sessionState mode="InProc" timeout="20"></sessionState> -->

<!-- 4. Session State variables are available across all pages, but only for a given single session. Session variables are like the single-user global data. -->
<!-- 5. It is always good practice to check if a Session State variable is null before calling any of its methods, such as ToString(). Otherwise, it may result in a NullReferenceException at runtime. -->

<!-- Ex.

if (Session["Name"] != null)
{
    Label_Name.Text = Session["Name"].ToString();
}

-->

<!-- 6. Application performance can be improved by disabling Session State, if it's not required. Session state can be turned off at the page or application level. To turn off the Session State at the page level, set EnableSessionState="False" in the page directive. To turn off the Session State at the application level, set the SessionStateMode="False" in the web.config file. -->

<!-- Ex. <%@ Page Language=c"C#" EnableSessionState="False"> -->