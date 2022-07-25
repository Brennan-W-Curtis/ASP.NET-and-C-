<!-- MultiView Control in ASP.NET -->

<!-- As the name states, a MultiView is made up of multiple view controls, and each view control in turn can have controls within it. -->

<!-- Ex.

<asp:MultiView ID="MultiView" runat="server">
    <asp:View ID="View1" runat="server"></asp:View>
    <asp:View ID="View2" runat="server"></asp:View>
    <asp:View ID="View3" runat="server"></asp:View>
</asp:MultiView>

-->

<!-- To create a simple example, where we want to capture employee information. -->
<!-- 1. First capture Employee Personal details. -->
<!-- 2. Next capture Employee Contact details -->
<!-- 3. Show summary for confirmation. Upon confirmation, save the data to a database table. -->

<!-- The ActiveViewIndex property of the MultiView control is used to determine, the view that is visible or active. -->

<!-- This can also be acheived by using the WIZARD control or by creating multiple webforms and passing data between webforms using Cookies, QUery Strings, or Session variables. -->

<!-- Ex. Step 1

<asp:MultiView ID="Multi_View" runat="server">
    <asp:View ID="View_Personal_Details" runat="server">
        // Several fields and a button to progress
    </asp:View>
    <asp:View ID="View_Contact_Details" runat="server">
        // Several fields and a button to progress 
    </asp:View>
    <asp:View ID="View_Summary" runat="server">
        // A summary of the information entered
    </asp:View>
</asp:MultiView>

-->

<!-- Ex. Step 2

public partial class WebForm : System.Web.Ui.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            Multi_View.ActiveViewIndex = 0;
        }
    }

    protected void ButtonProgressToStep2_Click(object sender, EventArgs e)
    {
        Multi_View.ActiveViewIndex = 1;
    }

    protected void ButtonProgressToStep3_Click(object sender, EventArgs e)
    {
        Multi_View.ActiveViewIndex = 2;

        Label_First_Name.Text = Text_First_Name.Text;
        Label_Last_Name.Text = Text_Last_Name.Text;
        Label_Gender_Options.Text = DropDownList_Gender.SelectedValue;
        Label_Email_Address.Text = Text_Email_Address.Text;
        Label_Mobile_Number.Text = Text_Mobile_Number.Text;
    }

    protected void ButtonRegressToStep1_Click(object sender, EventArgs e)
    {
        Multi_View.ActiveViewIndex = 0;
    }

    protected void ButtonReogressToStep2_Click(object sender, EventArgs e)
    {
        Multi_View.ActiveViewIndex = 1;
    }

    protected void ButtonSubmit_Click(object sender, EventArgs e)
    {
        Response.Redirect("~/Confirmation.aspx");
    }
}

-->