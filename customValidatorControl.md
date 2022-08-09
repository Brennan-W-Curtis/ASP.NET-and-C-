<!-- CustomValidator Control in ASP.NET -->

<!-- The CustomeValidator control allows us to write a method with a custom logic to handle the validation of the value entered. If none of the other validation controls, serve our purpose, then the CustomValidator can be used. -->

<!-- Just like any other validation control, the CustomValidator can be used for both client and server side validation. Client-side and server-side validation functions need to be written by the developer and associate thme to the CustomValidator control. -->

<!-- Properties specific to the CustomValidator control -->

<!-- 1. OnServerValidate -->
<!-- Specifies the name of the server-side validation method. -->

<!-- 2. ClientValidationFunction -->
<!-- Specifies the name of the client-side validation method. -->

<!-- 3. ValidateEmptyText -->
<!-- Specifies whether the validator control validates when the text of the associated input control is empty. By default this property is false and both the client side and server side validation functions will not be invoked if the associated input control is empty. -->

<!-- Ex.

<asp:TextBox ID="Text_Even_Number" runat="server"></asp:TextBox>
<asp:CustomValidator
    ID="Cusom_Validator_Even"
    runat="server"
    ErrorMessage="Sorry, the number entered is not even."
    ControlToValidate="Text_Even_Number"
    onservervalidate="CustomeValidatorEven_ServerValidate"
    ClientValidationFunction="Is_Even"
    ValidateEmptyText="True"
></asp:CustomValidator>

// Server-side Validation

protected void CustomValidatorEven_ServerValidate(object source, ServerValidateEventArgs e)
{
    if (e.Value == "")
    {
        e.IsValid = false;
    }
    else
    {
        int Number;
        bool isNumber = Int.TryParse(e.Value, out Number);
        if (isNumber && Number >= 0 && Number % 2 == 0)
        {
            e.IsValid = true;
        } 
        else 
        {
            e.IsValid = false;
        }
    }
}

// Client-side Validation

const Is_Even = (source, args) => {

    if (args.Value === "") {
        args.Value = false;
    } else {
        if (args.Value % 2 === 0) {
            args.IsValid = true;
        } else {
            args.IsValid = false;
        }
    }

}

-->