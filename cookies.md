<!-- Cookies in ASP.NET -->

<!-- Cookies store small amounts of information on the client's machine. In general, web sites use cookies to store user preferences or other information that is client-specific. -->

<!-- Cookies can be broadly classified into 2 types -->

<!-- 1. Persistent Cookies -->
<!-- They remain on the client computer, even after the browser is closed. You can configure how long the cookies remain using the Expires property of the HttpCookie object. -->

<!-- 2. Non-Persistent Cookies -->
<!-- If you don't set the Expires property, the the cookie is called a Non-Persistent cookie. Non-Persistent cookies only remain in memory until the browser is closed. -->

<!-- Ex.

public partial class WebForm1 : System.Web.UI.Page 
{
    protected void ButtonSendData_Click(object sender, EventArgs e)
    {
        HttpCookie cookie = new HttpCookie("UserInfo");
        cookie["Name"] = Text_Name.Text;
        cookie["Email"] = Text_Email.Text;
        Response.Cookies.Expires = DateTime.Now.AddDays(30);

        Response.Cookies.Add(cookie);

        Response.Redirect("WebForm2.aspx");
    }
}

public partial class WebForm2 : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        HttpCookie cookie = Response.Cookies["USerInfo"];
        if (cookie != null)
        {
            Label_Name.Text = cookie["Name"];
            label_Email.Text = cookie["Email"];
        }
    }
}

-->

<!-- How to check if cookies are enabled or disabled -->

<!-- Most of the articles on the internet states that we can use the Request.Browser.Cookies property to check, if cookies are enabled or disabled. However, this is incorrect. -->

<!-- The Request.Browser.Cookies property is used to check if the browser supports cookies. Most modern browsers support the use of cookies. Irrespective of whether, the cookies are enabled or disabled, if the browser supports cookies Request.Browser.Cookies always returns true. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        if (Request.Browser.Cookies)
        {
            if (Request.QueryString["CheckCookie"] == null)
            {
                HttpCookie cookie = new HttpCookie("TestCookie", "1");
                Response.Cookies.Add(cookie);
                Response.Redirect("WebForm1.aspx?CheckCookie=1");
            }
            else 
            {
                HttpCookie cookie = Request.Cookies["TestCookie"];
                if (cookie == null)
                {
                    Label_Message.Text = "We have detected that you have disabled cookies on your browser. Please enable cookies.";
                }
            }
        }
        else 
        {
            Label_Message.Text = "Your browser doesn't support cookies. Please install a modern browser.";
        }
    }
}

-->

<!-- How we check if cookies are enabled or disabled -->
<!-- 1. Write a test cookie. -->
<!-- 2. Redirect to the same page. -->
<!-- 3. Read the test cookie. -->
<!-- 4. If the cookie exists, cookies are enabled. -->
<!-- 5. Otherwise, cookies are disabled. -->

<!-- If you are testing code on your local machine, and want to disable cookies for the localhost -->
<!-- 1. Run the application. -->
<!-- 2. Press F12, to open developer tools. -->
<!-- 3. Press Select, then Cache, and Disable Cookies. -->