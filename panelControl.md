<!-- Panel Control in ASP.NET -->

<!-- The Panel control is used as a container for other controls. -->

<!-- A Panel control is very handy, when you want to group controls, and then show or hide, all the controls in the group. -->

<!-- The Panel control is also very useful, when adding controls to the webform dynamically. You can also use the Panel control to group controls and then toggle their visibility, using the Panel control's Visible property. -->

<!-- Ex.

<asp:Panel ID="Admin_Panel" runat="server">
</asp:Panel>

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        Admin_Panel.visible = false;
    }
}

protected void DropDownList_SelectedIndexChanged(object sender, EventArgs e)
{
    if (DropDownList.SelectedValue == "-1")
    {
        Admin_Panel.Visible = false;
    } 
    else if (DropDownList.SelectedValue == "Admin")
    {
        Admin_Panel.visible = true;
    }
}

-->

<!-- Creating Controls Dynamically -->

<!-- Ex.

protected void ButtonGenerateControls_Click(object sender, EventArgs e)
{
    int Count = Convert.ToInt32(Text_Controls_Count.Text);
    foreach (ListItem li in CheckBox_List_Control_Type.Items)
    {
        if (li.Selected)
        {
            if (li.Value == "Label")
            {
                for (int i = 1; i <= Count; i++)
                {
                    Label label = new Label();
                    label.Text = "Label - " + i.ToString();
                    Container_Labels.Controls.Add(label);
                    //this.Page.Controls.Add(label);
                    //Panel_Labels.Controls.Add(label);
                }
            }
            else if (li.Value == "TextBox")
            {
                for (int i = 1; i <= Count; i++)
                {
                    TextBox textBox = new TextBox();
                    textBox.Text = "TextBox - " + i.ToString();
                    Container_TextBoxes.Controls.Add(textBox);
                    //this.Page.Controls.Add(textBox);
                    //Panel_TextBoxes.Controls.Add(textBox);
                }
            }
            else {
                for (int i = 1; i <= Count; i++)
                {
                    Button button = new Button();
                    button.Text = "Button - " + i.ToString();
                    Container_Buttons.Controls.Add(button);
                    //this.Page.Controls.Add(button);
                    //Panel_Buttons.Controls.Add(button);
                }
            }
        }
    }
}

-->