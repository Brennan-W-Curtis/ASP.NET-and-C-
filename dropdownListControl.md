<!-- DropDownList Controls in ASP.NET -->

<!-- 1. The DropDownList is a collection of ListItem objects. -->
<!-- 2. The ListItems can be added to the DropDownList at design time or at runtime. -->
<!-- 3. If you want a specific ListItem to be selected in the DropDownList set the Selected property of the ListItem object to true. -->
<!-- 4. To hide a ListItem in the DropDownList, set the Enabled property to False. -->
<!-- 5. If you are adding ListItem objects to the DropDownList in the Page_load event, make sure you do only when the page is loaded for the first time. Otherwise, everytime you post the page back, by clicking a button, the listem items will be added again causing duplication. -->

<!-- A DropDownList is a collection of ListItem objects. Along the same lines, the CheckBoxList, RadioButtonList, BulletedList, and ListBox are also a collection of ListItem objects. So, adding items to these controls is also very similar to DropDownList. -->

<!-- Select or Deselect all List Items -->

<!-- Ex.

protected void ButtonSelectAll_Click(object sender, EventArgs e)
{
    foreach (ListItem li in CheckBoxList.Items)
    {
        li.Selected = true;
    }
}

protected void ButtonDeselectAll_Click(object sender, EventArgs e)
{
    foreach (ListItem li in CheckBoxList.Items)
    {
        li.Selected = false;
    }
}

-->