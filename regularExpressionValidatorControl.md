<!-- RegularExpresionValidator Control in ASP.NET -->

<!-- This is a very powerful valiation control. This control is used to check if the value of an asociated input control matches the pattern specified by a regular expression. The only property that is specific to the RegularExpressionValidator is ValidationExpression. -->

<!-- Ex.

<asp:RegularExpressionValidator
    ID="Regular_Expression_Validator_Email"
    runat="server"
    ErrorMessage="Sorry, you've entered an invalid email."
    ControlToValidate="Text_Email"
    ValidateExpression="\w+([-+.']\w+([-.]\w+)*\.\w+([-.]\w+)*"
>
</asp:RegularExpressionValidator>

-->

<!-- By default client-side validation is turned on. To disable client-side validation set EnableClientScript to false. This property is supported by all validation controls. -->

<!-- While to disable the validation control you need to set Enabled to false. -->