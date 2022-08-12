<!-- Page Navigation Techniques -->

<!-- What are the different page navigation techniques in ASP.NET? -->
<!-- How do you link pages in an application? -->
<!-- How do you move from one webform to another webform in ASP.NET? -->
<!-- These are very common interview questions in ASP.NET. There are several techniques to navigate between webforms in ASP.NET. -->\

<!-- 1. Hyperlink Control -->
<!-- Is used to navigate to another page. The page you want to navigate to is specified by the NavigateURL property. Using hyperlink, you can navigate to another page within the same application or to an external web site. The Hyperlink control is rendered as an HTML anchor <a> tag. -->

<!-- Ex.

<asp:HyperLink ID="Hyper_Link" NavigateUrl="~/WebForm2.aspx" Text="Go to WebForm." runat="server"></asp:HyperLink>

-->

<!-- 2. Response.Redirect -->
<!-- Response.Redirect is similar to clicking on a hyperlink. The Hyperlink control does not expose any server-side events. So, when the user clicks on a hyperlink, there is no server-side event to intercept the click. -->

<!-- So, if you want to intercept a click event in code, use the Button, LinkButton, or the ImageButton server controls. In the button click event, call the Response.Redirect() method. When the user clicks the button, the web server receives a request for redirection. The server then sends a response header to the client. The client then automatically issues a new GET request to the web server. The web server will then serve the new page. So, in short, Response.Redirect causes 2 request/response cycles.-->

<!-- Also, note that when Response.Redirect() is used the URL in the address bar changes and the browser history is maintained. Response.Redirect() can be used to navigate pages/websites on the same web server or on a different web server. -->

<!-- Ex.

protected void Button_Click(object sender, EventArgs e)
{
    Response.Redirect("~/WebForm2.aspx");
}

-->

<!-- 3. Server.Transfer -->
<!-- Differences between Server.Transfer and Response.Redirect -->

<!-- A) Just like a hyperlink and Response.Redirect(), Server.Transfer() is used to navigate to other pages/websites running on the same web server. -->
<!-- B) Server.Transfer() cannot be used to navigate to pages/websites on a different web server. -->
<!-- C) Server.Transfer() does not change the URL in the address bar. -->
<!-- D) Server.Transfer() is faster than Response.Redirect as the redirection happens on the server in one Request/Response cycle. Where as Response.Redirect() involves 2 Request/Response cycles. -->
<!-- E) With Server.Transfer() the Form Variables from the original request are preserved. -->
<!-- F) Server.Transfer() has a second boolean parameter that determines whether the form values are preserved, Server.Transfer("~/WebForm2.aspx, false) -->

<!-- Ex.

// Initial Page Code-Behind

public partial class WebForm1 : System.Web.UI.Page
{
    protected void ButtonTransfer_Click(object sender, EventArgs e)
    {
        Server.Transfer("~/WebForm2.aspx");
    }
}

// Redirect Page
<asp:Label ID="Label_Name" runat="server"></asp:Label>
<asp:Label ID="Label_Email" runat="server"></asp:Label>

// Redirect Page Code-Behind

public partial class WebForm2 : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        System.Collections.Specialized.NameValueCollection previousFormCollection = Request.Form;
        Label_Name.Text = previousFormCollection["Text_Name"];
        Label_Email.Text = previousFormCollection["Text_Email"];
    }
}

-->

<!-- 4. Server.Execute -->
<!-- Server.Transfer() and Server.Execute() are similar in many ways. -->
<!-- A) The URL in the browser remains the same as the first page URL. -->
<!-- B) Server.Transfer() and Server.Execute() can only be used to navigate to pages/websites on the same web server. Trying to navigate to pages/websites on a different web server causes a runtime exception to be thrown. -->
<!-- C) Server.Transfer() and Server.Execute() preserve the Form Variables from the original request. -->

<!-- The major difference between Server.Transfer() and Server.Execute() -->
<!-- Server.Transfer() terminates the execution of the current page and starts the execution of the new page, where as Sever.Execute() processes the second Web form without leaving the first Web form. After completing the execution of the first webform, the control returns to the second webform. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    Page previousPage = this.Page.PreviousPage;
    if (previousPage != null && previousPage.IsCrossPagePostBack)
    {
        //Access the name and email public properties
        Label_Name.Text = ((TextBox)previousPage.FindControl("Text_Name")).Text;
        Label_Email.Text = ((TextBox)previousPage.FindControl("Text_Email")).Text;
    }
}

-->

<!-- 5. Cross-Page postback -->
<!-- Cross page posting allows one to post one page to another page. By default, when you click a button, the webform posts to itself. If you want to post to another webform on a button click, set the PostBackUrl of the button to the page that you want to post to instead. -->

<!-- The Page.IsCrossPagePostBack property is used to indicate whether the page is involed in a cross-page postback. -->

<!-- The problem with the FindControl() method is that, if you mis-spell the ControlID, a runtime NullReferenceException could be thrown. This can be avoided by obtaining a strongly typed reference to the previous page. -->

<!-- To obtain a strongly type reference -->
<!-- First, create Public Properties, as read-only fields are insufficient. -->
<!-- Second, obtain a strongly typed reference by TypeCasting or using the PreviousPageType directive. -->

<!-- Ex.

// Initial Page Code-Behind

public string Name {
    get {
        return Text_Name.Text;
    }
}

public string Email {
    get {
        return Text_Email.Text;
    }
}


// Redirect Page

<%@ PreviousPageType VirtualPath="~/WebForm1.aspx" %>

<asp:Button 
    ID="Button_Cross_Page_Postback
    runat="server"
    Text="Cross Page Postback to WebForm2"
    PostBackUrl="~/WebForm2.aspx"
>

// Redirect Page Code-Behind

protected void Page_Load(object sender, EventArgs e)
{
    WebForm1 previousPage = this.PreviousPage;
    if (previousPage != null && previousPage.IsCrossPagePostBack)
    {
        //Access the name and email public properties
        Label_Name.Text = previousPage.Name;
        Label_Email.Text = previousPage.Email;
    }
}

-->

<!-- 6. Window.Open -->
<!-- Syntax: window.open(URL, name, features, replace); -->

<!-- Ex.

const Open_New_Window = () => {

    const name = document.getElementById("Text_Name").value;
    const email = document.getElementById("Text_Email").value;

    window.open("WebForm2.aspx?Name=" + Name + "&Email=" + Email, "_blank", "toolbar=no, directories=yes, location=no, resizable=yes", true);

};

// Accessing the query strings

protected void Page_Load(object sender, EventArgs e)
{
    Label_Name.Text = Request.QueryString["Name"];
    Label_Email.Text = Request.QueryString["Emai"];
}

-->