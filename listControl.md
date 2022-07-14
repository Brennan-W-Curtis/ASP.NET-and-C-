<!-- List Control in ASP.NET -->

<!-- In ASP.NET there are several list controls, such as:  -->
<!-- 1. DropDownList -->
<!-- 2. CheckBoxList -->
<!-- 5. RadioButtonList -->
<!-- 4. ListBox -->
<!-- 3. BulletedList -->

<!-- All these controls inherit from the ListControl class. -->
<!-- 1. It's a collection of ListItem objects. -->
<!-- 2. ListItems can be added in the HTML source or in the code behind file. -->
<!-- 3. Supports databinding. -->

<!-- Since all the list controls inherit from the ListControl class, the AddListItems() method can be used to add ListItems to any list control. A parent class reference varaible can point to a derived class object. This fact allows us to pass any list control into the AddListItems() method as a paramenter. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack) 
    {
        Add_List_Items(DropDownList);
        Add_List_Items(CheckBoxList);
        Add_List_Items(RadioButtonList);
        Add_List_Items(ListBox);
        Add_List_Items(BulletedList);
    }
}

private void Add_List_Items(ListControl listControl)
{
    ListItem li1 = new ListItem("Item1", "1");
    ListItem li2 = new ListItem("Item2", "2");
    ListItem li3 = new ListItem("Item3", "3");
}

-->

<!-- ListBox (If SelectionMode = Multiple) and CheckBoxList allows users to select multiple items. So, to retrieve each of the selected ListItem's Text, Value, and Index use a foreach loop. A reusable method that can be used with any control that derives from the ListControl class, but works best with controls that allows multiple selections. -->

<!-- Ex.

private void Retrieve_Multiple_Selections(ListControl listControl)
{
    foreach (ListItem li in listControl.Items)
    {
        if (li.Selected)
        {
            Response.Write("Text = " + li.Text + ", Value = " + li.Value + ", Index = " + listControl.Items.IndexOf(li).ToString() + "<br />");
        }
    }
}

-->

<!-- ListBox (If SelectionMode = Single), the RadioButtonList and DropDownList allow users to select only one item. So, use the SelectedIndex and SelectedItem properties to retrieve the Text, Value, and Index of the selected ListItem. A reusable that can be used with any control that derivces from the ListControl class, but works best with controls that allows for a single selection. -->

<!-- Ex.

private void Retrieve_Selected_Item_Text_Value_and_Index(ListControl listControl)
{
    if (listControl.SelectedIndex != - 1)
    {
        Response.Write("Text = " + listControl.SelectedItem.Text + "<br />");
        Response.Write("Value = " + listControl.SelectedItem.Value + "<br />");
        Response.Write("Index = " + listControl.SelectedIndex.ToString());
    }
}

-->