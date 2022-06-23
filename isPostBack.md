<!-- IsPostBack in ASP.NET -->

<!-- IsPostBack is a Page level property, that can be used to determine whether the page is being loaded in response to a client postback, or if it is being loaded and accessed for the first time. -->

<!-- Ex. 

protected void Page_Load(object sender, EventArgs e)
{
    Load_City_DropDownList();
} 

public void Load_City_DropDownList()
{
    ListItem li1 = new ListItem("London");
    dropdownlistCity.Items.Add(li1);
    ListItem li2 = new ListItem("Sydney");
    dropdownlistCity.Items.Add(li2);
    ListItem li2 = new ListItem("Mumbai");
    dropdownlistCity.Items.Add(li3);
}

protected void Button_Click(object sender, EventArgs e) 
{
}

-->

<!-- Now run the application. Look at the city DropDownList. The cities are correctly shown as expected. Just clikc the button once. Notice, that the city names in the DropDownList are duplicated. So, every time you click the button, the city names are again added to the DropDownList. -->

<!-- What causes the duplication -->

<!-- We know that all ASP.NET server controls retain their state across postback. These controls make use of ViewState. So, for the first time, when the webform loads the cities get correctly added to the DropDownList and sent back to the client. -->

<!-- Now, when the client clicks the button control, and the webform is posted back to the server for processing. During the Page initialization, ViewState restoration happens. During this stage, the city names are retrieved from the viewstate and added to the DropDownList. -->

<!-- The PageLoad event happens later in the life cycle of the webform. During page load we are again adding another set of cities. Hence, the duplication. -->

<!-- Solving the DropDownList Item Duplication -->

<!-- There are several ways to solve this. One of the best ways to do this, is to use the IsPostBack property. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        Load_City_Dropdownlist();
    }
}

-->

<!-- Another way to solve this problem is to simply disable the ViewState of the DropDownList control. Issues with this approach include, -->
<!-- 1. DropDownList will not remember your selection across postback. -->
<!-- 2. DropDownList events may not work correctly as expected. -->

<!-- Another way to solve this is to clear all the DropDownList items before calling the Load_City_Dropdownlist() method. But this is not efficient from a performance perspective. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    dropdownlistCity.Items.Clear();
    Load_City_Dropdownlist();
}

-->