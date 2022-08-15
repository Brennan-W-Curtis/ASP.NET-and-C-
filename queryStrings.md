<!-- QueryStrings in ASP.NET -->

<!-- Points to Remember About Query Strings -->
<!-- 1. Query strings are name/value collection paris. -->
<!-- 2. Using query strings is a very common way to send data from one webform to another. -->
<!-- 3. Query strings are appended to the page URL. -->
<!-- 4. The ? (question mark) symbol indicates the beginning of a query string and it's value. -->
<!-- 5. It is possible to use more than one query string. The first query string is specified using the question mark. Subsequent query strings can be appended to the URL using the & symbol (ampersand). -->
<!-- 6. There is a limit on the Query string length. Hence, Query strings cannot be used to send very long data. -->

<!-- Ex.

public partial class WebForm1 : System.Web.UI.Page
{
    protected void ButtonSendData_Click(object sender, EventArgs e)
    {
        Response.Redirect("~/WebForm2.aspx?UserName=" + Text_Name.Text + "&UserEmail=" + Text_Email.Text);
    }
}

public partial class WebForm2 : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        Label_Name.Text = Request.QueryString["UserName"];
        Label_Email.Text = Request.QueryString["UserEmail"];
    }
}

-->


<!-- 7. Querystrings are visible to the user, hence should not be used to send sensitive information, unless encrypted. -->
<!-- 8. To read the query string value, use the Request object's QueryString property. -->
<!-- 9. The & symbol is used to concatenate query strings, so if you want to send & as a value for the query string there are 2 options you have. -->

<!-- Ex.

protected void ButtonSendData_Click(object sender, EventArgs e)
{
    // Using Server.UrlEncode() to encode the & symbol 
    Response.Redirect("WebForm2.aspx?UserName=" + Server.UrlEncode(Text_Name.Text) + "&UserEmail=" + Server.UrlEncode(Text_Email.Text));

    // Using String.Replace() to replace the & symbol with %26
    Response.Redirect("WebForm2.aspx?UserName=" + Text_Name.Text.Replace("&", "%26") + "&UserEmail=" Text_Email.Text.Replace("&", "%26")); 
}

-->