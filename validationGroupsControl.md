<!-- ValidationGroups Control in ASP.NET -->

<!-- First Problem -->
<!-- When the Clear button is clicked form validation still happens. Ideally upon clicking it would clear the textboxes in the registration section. Validations don't make sense here. So, I can prevent validation from occuring by setting the CausesValidation property to false. -->

<!-- Second Problem -->
<!-- When the Login button is clicked only the fields in the login section need to be validated. Along the same lines when I click the Registor button only fields in the registration section need to be validated. If we don't use validation groups, then by default, whenever any button is clicked all the validation controls on the page get validated. -->

<!-- So, when you click the login button, and if you only want, the fields in the login section to be validated, then set the ValidationGroup property of the validation controls and the login button control to the same group name. Use a different group name for the validation controls and register button, in the registration section. -->

<!-- Ex.

protected void ButtonClear_Click(object sender, EventArgs e)
{
    Text_Email_Address.Text = "";
    Text_User_Name.Text = "";
    Text_Initial_Password.Text = "";
    Text_Confirm_Password.Text = "";

}

-->