<!-- RequiredField Validator Control in ASP.NET -->

<!-- Validation controls are used to ensure if the data entered by the user is valid. Microsoft ASP.NET framework, provides 6 built-in validation controls, the RequiredFieldValidator, RangeValidator, RegularExpressionValidator, CompareValidator, CustomValidator, and ValidationSummary controls. -->

<!-- These validation controls can be used to perform both client side and server side validation. -->

<!-- The Browser only understands client-side scripts and HTML. In the past to perform client side validation, developers had to write themselves the required JavaScript code. With validation controls, we don't have to write JavaScript, we can use the built-in validation controls, which will generate the required JavaScript for us. -->

<!-- Client-side scripts can spread viruses and cause security concerns. Consequently, users may disable JavaScript on their browser. If this happens, client-side validation is skipped. That is why it is always good practice to have server side validation as well. -->

<!-- Ex.

// Validation for a TextBox

<asp:TextBox ID="Text_Name" runat="server"></asp:TextBox>
<asp:RequiredFieldValidator ID="RequiredFieldValidatorName" runat="server" ErrorMessage="Sorry, a name is required" ControlToValidate="Text_Name"></asp:RequiredFieldValidator>

// Validation for a DropDownList

<asp:DropDownList ID="DropDownList_Gender" runat="server">
    <asp:ListItem Text="Select Gender" Value="-1"></asp:ListItem>
    <asp:ListItem Text="Male" Value="Male"></asp:ListItem>
    <asp:ListItem Text="Female" Value="Female"></asp:ListItem>
    <asp:ListItem Text="Other" Value="Other"></asp:ListItem>
</asp:DropDownList>
<asp:RequiredFieldValidator ID="RequiredFieldValidatorName" runat="server" ErrorMessage="Sorry, a gender is required" InitialValue="-1" ControlToValidate="Text_Name"></asp:RequiredFieldValidator>

protected void SaveButton_Click(object sender, EventArgs e)
{
    if (Page.IsValid)
    {
        Label_Status.Text = "Data Saved Successfully.";
    }
}

-->