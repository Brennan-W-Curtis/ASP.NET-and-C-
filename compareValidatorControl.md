<!-- CompareValidator Control in ASP.NET -->

<!-- The CompareValidator control is used to compare the value of one control with the value of another control or a constant value. The comparison operation cvan be any of the following, Equal, GreaterThan, GreaterThanEqual, LessThan, LessThanEqual, NotEqual, and DataTypeCheck. -->

<!-- It can also be used for DataType checking. -->

<!-- Ex.

// Validation for confirming a password

<asp:TextBox ID="Text_Password" runat="server">

<asp:TextBox ID="Text_Retype_Password" runat="server"></asp:TextBox>
<asp:CompareValidator 
    ID="Compare_Validator_Passwords" 
    runat="server" 
    ErrorMessage="Sorry, Password and RetType Password must match." 
    ControlToValidate="Text_Retype_Password"
    ValueToCompare="Text_Password"
    Operator="Equal"
    Type="String"
    Display="Dynamic"
></asp:CompareValidator>

// Validation for comparing a date

<asp:TextBox ID="Text_Date" runat="server"></asp:TextBox>
<asp:CompareValidator 
    ID="Compare_Validator_Date" 
    runat="server" 
    ErrorMessage="Sorry, the date must be greater than 01/01/2022." 
    ControlToValidate="Text_Date"
    ValueToCompare="01/01/2022"
    Operator="GreaterThan"
    Type="Date"
    Display="Dynamic"
></asp:CompareValidator>

// Validation for checking whether an integer

<asp:TextBox ID="Text_Age" runat="server"></asp:TextBox>
<asp:CompareValidator 
    ID="Compare_Validator_Age" 
    runat="server" 
    ErrorMessage="Sorry, age must be a number." 
    ControlToValidate="Text_Age"
    Operator="DataTypeCheck"
    Type="Integer"
    Display="Dynamic"
></asp:CompareValidator>

-->

<!-- The following are the properties that are specific to the compare validator. -->

<!-- 1. ControlToCompare -->
<!-- The control with which to compare. -->

<!-- 2. Type -->
<!-- The DataType of the value to compare. Such as a string or an integer. -->

<!-- 3. Operator -->
<!-- The comparison operator. Such as equal or not equal. -->

<!-- 4. ValueToCompare -->
<!-- The constant value to compare with. -->

<!-- SetFocusOnError property is supported by all validation controls. If this property is set to true, then the control will automatically receive focus, when the validation fails. -->