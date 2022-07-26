<!-- Wizard Control in ASP.NET -->

<!-- The Wizard Control enables creation of a multi-step user interface. It provides this with it's built-in previous/next functionality. -->

<!-- A wizard is a collection of WizardSteps. The StepType property of a WizardStep element determines the correct previous/next buttons to show -->

<!-- Ex. Step 1

<asp:Wizard ID="Wizard" runat="server">
    <asp:WizardSteps>
        <asp:WizardStep ID="Wizard_Step_1" StepType="" runat="server" Title="Step 1 - Personal Details">
        </asp:WizardStep>
        <asp:WizardStep ID="Wizard_Step_2" runat="server" Title="Step 2 - Contact Details">
        </asp:WizardStep>
        <asp:WizardStep ID="Wizard_Step_2" runat="server" Title="Step 2 - Detail Summary">
        </asp:WizardStep>
    </asp:WizardSteps>
</asp:Wizard>

-->

<!-- Ex. Step 2

protected void Page_Load(object sender, EventArgs e)
{

}

protected void Wizard1Next_ButtonClick(object sender, WizardNavigationEventArgs e)
{
    if (e.NextStepIndex == 2)
    {
        Label_First_Name.Text = Text_First_Name.Text;
        Label_Last_Name.Text = Text_Last_Name.Text;
        Label_Gender_Options.Text = Text_Gender_Options.Text;
        Label_Mobile_Number.Text = Text_Mobile_Number.Text;
        Label_Email_Address.Text = Text_Email_Address.Text;
    }
}

protected void Wizard1Finish_ButtonClick(object sender, WizardNavigationEventArgs e)
{
    if (e.NextStepIndex == 2)
    {
        Response.Redirect("~/Confirmation.aspx");
    }
}

-->