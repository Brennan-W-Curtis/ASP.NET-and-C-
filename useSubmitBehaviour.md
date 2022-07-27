<!-- UseSubmitBehavior Property -->

<!-- The UseSubmitBehaviour property specifies if the Button control uses the browser's built-in submit function or the ASP.NET postback mechanism. -->

<!-- This property is set to TRUE by default. When set to FALSE, ASP.NET adds a client-side script to post the form. -->

<!-- To view the client side script added by ASP.NET, right click on the browser and view source. -->

<!-- Ex.

Design Time:
<asp:Button ID="Clear_Button" runat="server" onclick="Clear_Button_Click" Text="Clear" UseSubmitBehavior="False" />
<asp:Button ID="Submit_Button" runat="server" onclick="Submit_Button_Click" Text="Submit" />

Run Time:
<asp:Button ID="Clear_Button" runat="server" onclick="javascript:__doPostBack(&#39;Clear_Button&#39;,&#;39&#39;)" Text="Clear" UseSubmitBehavior="False" />
<asp:Button ID="Submit_Button" runat="server" onclick="Submit_Button_Click" Text="Submit" />

-->