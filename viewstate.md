<!-- ViewState -->

<!-- Web Applications work on HTTP protocol. HTTP protocol is a stateless protocol, meaning it does not retain state between user requests. -->

<!-- Ex.

public partial class WebForm : System.Web.UI.Page
{
    int Clicks_Counted = 0;
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            TextBox.Text = "0";
        }
    }

    protected void Button_Click(object sender, EventArgs e)
    {
        Clicks_Counted = Clicks_Counted + 1;
        TextBox.Text = Clicks_Counted.ToString();
    }
}

-->

<!-- When a request is received web forms live for barely a moment. -->
<!-- 1. An instance of the requested webform is created. -->
<!-- 2. Events are processed. -->
<!-- 3. It generates the HTML and is posted to the client. -->
<!-- 4. The webform is immediately destroyed. -->

<!-- Ex.

public partial class WebForm : System.Web.UI.Page
{
    int Clicks_Counted = 1;
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            TextBox.Text = "0";
        }
    }

    protected void Button_Click(object sender, EventArgs e)
    {
        if (ViewState["Clicks] != null)
        {
            Clicks_Counted = (int)ViewState["Clicks"] + 1;
        }
        TextBox.Text = Clicks_Counted.ToString();
        ViewState["Clicks"] = Clicks_Counted;
    }
}

-->

<!-- Ex.

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            TextBox.Text = "0";
        }
    }

    protected void Button_Click(object sender, EventArgs e)
    {
        int Clicks_Counted = Convert.ToInt32(TextBox.Text) + 1;
        TextBox.Text = Clicks_Counted.ToString();
    }
}

-->

<!-- Click the button now, and the value gets incremented every time we click whereas before it did not. -->
<!-- It's possible because, we are using the ViewState variable Clicks to preserve the data between requests. The ViewState data, travels with every request and response between the client and the web server. -->

<!-- ASP.NET Server Controls & ViewState -->

<!-- Upon clicking the Button, the value gets incremented correctly as expected. This is possible because, TextBox is an asp.net server control, that uses viewstate internally, to preserve data across postbacks. -->

<!-- Because Web forms have very short lifetimes, ASP.NET takes special steps to preserve the data entered in the controls on a Web form. -->
<!-- Data entered in controls is sent with each request and restored to controls in Page_Init. The data in these controls is then available in the Page_Load(), Button_Click(), and many more events, that occur after the Page_Init() event. -->

<!-- ASP.NET Server Controls & HTML Controls -->

<!-- ASP.NET server controls retain state. HTML controls, do not retain state across post backs. -->

<!-- An HTML control can be converted into an ASP.NET server control, by adding the runat="server" attribute in the HTML source as shown below. -->
<!-- <input id="Text" runat="server" type="text"> -->

<!-- ViewState data is serialized into base64-encoded strings, and is stored in a Hidden input field. -->
<!-- <input type="hidden" name="__EVENTVALIDATION" id="__EVENTVALIDATION" value="${ENCODEDSTRING}" /> -->
