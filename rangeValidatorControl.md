<!-- RangeValidator Control in ASP.NET -->

<!-- RangeValidator is used to check if the value is within a specified range of values. For exmaple, to check if the age falls between 1 and 100. -->

<!-- Properties specific to RangeValidator control: -->

<!-- 1. Type -->
<!-- Data type of the value to check. This includes Currency, Date, Double, Integer, and String. -->

<!-- 2. MinimumValue -->
<!-- The minimum value allowed. -->

<!-- 3. MaximumValue -->
<!-- The maximum value allowed. -->

<!-- Ex.

// Validation for an integer

<asp:TextBox ID="Text_Age" runat="server"></asp:TextBox>
<asp:RangeValidator 
    ID="Range_Validator_Age" 
    runat="server" 
    ErrorMessage="Age must be between 1 & 100." 
    ControlToValidate="Text_Age"
    MinimumValue="1"
    MaximumValue="100"
    Type="Integer"
    Display="Dynamic"
></asp:RangeValidator>

// Validation for a date

<asp:TextBox ID="Text_Date" runat="server"></asp:TextBox>
<asp:RangeValidator 
    ID="Range_Validator_Date" 
    runat="server" 
    ErrorMessage="Date must be between 01/01/2022 & 31/12/2022." 
    ControlToValidate="Text_Age"
    MinimumValue="01/01/2022"
    MaximumValue="31/12/2022"
    Type="Date"
    Display="Dynamic"
></asp:RangeValidator>

-->

<!-- Display property is supported by all validation controls. -->

<!-- 1. None -->
<!-- The error message is not rendered and displayed next to the control. It's used to show the error message only in the ValidationSummary control. -->

<!-- 2. Static -->
<!-- The error message is displayed next to the control if validation fails. Space is reservered on the page for the message even if validation succeeds. The span tag is rendered with style visibility: hidden. -->

<!-- 3. Dynamic -->
<!-- The error message is displayed next to the control if validation fails. Space is not reserved on the page for the message if the validation succeeds. The span tag is rendered with style display: nomne. -->