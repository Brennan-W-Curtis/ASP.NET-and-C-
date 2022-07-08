<!-- ASP.NET CheckBoxList Controls in ASP.NET -->

<!-- Just like the DropDownList -->
<!-- 1. A CheckBoxList is a collection of ListItem objects. -->
<!-- 2. Items can be added to the CheckBoxList in the HTML source or in the code behind file. -->
<!-- 3. CheckBoxList can be bound to a database table or an xml file. -->

<!-- DropDownList is generally used, when you want to present the user with multiple choices from which you want them to select only a single option. Where as if you want the user to select more than one option, then a CheckBoxList control can be used. -->

<!-- Useful Properties -->
<!-- RepeatDirection -->
<!-- RepeatColumns -->
<!-- Enabled -->
<!-- SelectedIndex -->
<!-- SelectedValue -->
<!-- SelectedItem -->

<!-- Check for null when using the SelectedItem property of a CheckBoxList control. -->
<!-- Ex.

if (checkboxListExample.SelectedItem != null)
{
    Response.Write(checkboxListExample.SelectedItem.Text);
}

-->