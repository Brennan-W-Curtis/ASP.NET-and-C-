<!-- Loading User Controls Dynamically -->

<!-- Normally, we drag and drop user controls on the webform at design time. However, there could be several reasons in real time, for loading user controls dynmically. -->

<!-- For example, depending on the preferences of the currently logged in user like age, gender, location, etc, we many want to load different user controls. -->

<!-- Along the same lines, based on ADmin and Non-Admin users, different user controls should be loaded. -->

<!-- Most internet articles, state that, for dynamically created controls, to maintain viewstate across postback, the controls should be loaded in the Page_Init() event of the webform. -->

<!-- However, the Page_Load() event can be used, but the controls are still able to retain their state across postback. -->

<!-- Use either PlaceHolder or Panel controls at the location of the webform where you want the controls to be loaded. -->

<!-- Ex.

// Front End

<body>
    <form id="Form" runat="server">
        <div>
            <asp:PlaceHolder ID="PlaceHolder" runat="server"></asp:PlaceHolder>
            <asp:Button ID="Button" runat="server" Text="Button" onclick="Button_Click" />
        </div>
    </form>
</body>

// Code Behind

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        CalendarUserCtonrol Calender_User_Control = (CalendarUserControl)LoadControl("~/UserControls/CalendarUserControl.ascx);
        Calendar_User_Control.ID = "Calendar_User_Control";
        PlaceHolder.Controls.ADD(Calendar_User_Control);
    }

    protected void Button_Click(object sender, EventArgs e)
    {
        Response.Write(((CalendarUserControl)PlaceHolder.FindControl("Calender_User_Control")).SelectedDate);
    }
}

-->