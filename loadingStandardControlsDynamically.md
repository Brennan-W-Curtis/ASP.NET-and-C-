<!-- Loading ASP.NET Controls Dynamically -->

<!-- To maintain the state of controls across postback -->
<!-- 1. Add the controls in the page load event, and set their visibility to false. -->
<!-- 2. Based on the DropDownList selection, show/hide the dynamically added controls. -->

<!-- Ex.

// Front End

<body>
    <form id="Form" runat="server">
        <div>
            <asp:DropDownList ID="Drop_Down_List runat="sever" AutoPostBack="True">
                <asp:ListItem Text="Please Select" Value="-1"></asp:ListItem>            
                <asp:ListItem Text="Select City" Value="DropdownList"></asp:ListItem>
                <asp:ListItem Text="Enter Postal Code" Value="Textbox"></asp:ListItem>            
            </asp:DropDownList>
            <asp:PlaceHolder ID="Place_Holder" runat="server"></asp:PlaceHolder>
        </div>
    </form>
</body>

// Code Behind

protected void DropDownList_SelectedIndexChanged(object sender, EventArgs e)
{
    if (Drop_Down_List.SelectedValue == "DropdownList")
    {
        DropDownList City_Dropdown_List = new DropDownList();
        City_Dropdown_List.ID = "Dropdown_List_1;
        City_Dropdown_List.Items.Add("Toronto");
        City_Dropdown_List.Items.Add("Vancouver");
        City_Dropdown_List.Items.Add("Montreal");
        Place_Holder.Controls.Add(City_Dropdown_List);
    }
    else if (Drop_Down_List.SelectedValue == "Textbox")
    {
        Textbox Textbox = new TextBox();
        Textbox.ID = "Text_Box_1";
        Place_Holder.Controls.Add(Textbox);
    }
}

-->

<!-- There's a problem with the webform as it stands. Upon postback all dynamically created controls will be erased. They are created upon the SelectedIndexChanged event being raised and nothing happening in the Page_Load event. They do not persist across postback because webforms operate on a stateless protocol. Every request is kind of like a new request to the web server, it will then create a new instance of the webform. -->

<!-- We can address this by first moving the code block to the Page_Load event handler and removing the conditional statements to generate them every time. Next set the visibility of both controls to false. Then when the user makes a selection change the targeted element's visibility to true. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    DropDownList City_Dropdown_List = new DropDownList();
    City_Dropdown_List.ID = "Dropdown_List_1;
    City_Dropdown_List.Items.Add("Toronto");
    City_Dropdown_List.Items.Add("Vancouver");
    City_Dropdown_List.Items.Add("Montreal");
    Place_Holder.Controls.Add(City_Dropdown_List);
    City_Dropdown_List.Visible = false;

    Textbox Textbox = new TextBox();
    Textbox.ID = "Text_Box_1";
    Place_Holder.Controls.Add(Textbox);
    Textbox.Visible = false;

    If (Drop_Down_LIst.SelectedValue == "City_Dropdown_List")
    {
        City_Dropdown_List.Visible = true;
    }
    else if (Drop_Down_List.SelectedValue == "Textbox")
    {
        Textbox.Visible = true;
    }
}

protected void Button_Click(object sender, EventArgs e)
{
    If (Drop_Down_LIst.SelectedValue == "City_Dropdown_List")
    {
        Response.Write(((DropDownList)Plade_Holder.FindControl("Dropdown_List_1")).SelectedItem.Text);
    }
    else if (Drop_Down_List.SelectedValue == "Textbox")
    {
        Response.Write(((TextBox)Plade_Holder.FindControl("Text_Box_1")).Text);
    }
}

-->