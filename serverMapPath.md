<!-- Server.MapPath() Method -->

<!-- Server.MapPath() returns the physical path for a given virtual path. This method can be used in several different ways, depending on the characters that we use in the virtual path. -->

<!-- Server.MapPath(".") - Current physical directory of the page that you are running -->
<!-- Server.MapPath("..") - Parent physical directory of the page that you are running -->
<!-- Server.MapPath("~") - The physical path of the root directory of the application -->

<!-- Server.MapPath() Method Application -->

<!-- The Tilde(~) symbol resolves to the root application directory, no matter how deep you are in the folder hierarchy. This is the advantage of using the former (~) over the other (..). The following code works from any folder in our application.  -->
<!-- Ex. ds.ReadXml(Server.MapPath("~/Data/Countries/Countries.xml")); -->

<!-- Whereas, the following code will only work from folders that are 2 levels deeper relative to the root directory of the application. -->
<!-- Ex. ds.ReadXxl(Server.MapPath("../../Data/Countries/Countries.xml")); -->

<!-- DropDownList Selected Item -->

<!-- To retrieve, -->
<!-- the selected item's text: DropDownList.SelectedItem.Text -->
<!-- the selected item's value: DropDownList.SelectedItem.Value -->
<!-- the selected item's value: DropDownList.SelectedValue -->
<!-- the selected item's index: DropDownList.SelectedIndex -->

<!-- The SelectedIndex and SelectedValue properties of the DropDownList can also be used to have a list item selecte in the dropdown list. -->