<!-- Literal Control in ASP.NET -->

<!-- 1. In many ways a Literal control is similar to a Label control. Both of these controls are used to display Text on a webform. The Text property can be set in the HTML or in the code-behind. -->

<!-- 2. Label control wraps the text in a span tag when rendered. Any style that is applied to the label control, will be rendered using the style property of the span tag. A Literal control, doesn't output any surrounding tags. The Text is displayed as is. -->

<!-- 3. To apply any styles to a Literal control, include them in the Text of the Literal control. -->

<!-- 4. If you just want the text to be displayed without any styles, the use a Literal control otherwise use a Label control. -->

<!-- 5. By default, both the Label and Literal controls do not encode the text they display. -->
<!-- Ex.

<asp:Label ID="Label" runat="server" Font-Bold="true" ForeColor="Red" Text="<script>alert('Label Text')</script>">
</asp:Label>

<asp:Literal ID="Literal" runat=server Text="<script>alert('Literal Text')</script>"></asp:Literal>

-->

<!-- 6. To HTML encode Label text, use the Server.HTMLEncode() method. For the Literal control, use the Mode property. -->
<!-- Ex.

<asp:Label ID="Label" runat="server" Font-Bold="true" ForeColor="Red">
    <%=Server.HtmlEncode("<script>alert('Label Text')</script>") %>
</asp:Label>

<asp:Literal ID="Literal" runat=server Mode="Encode" Text="<script>alert('Literal Text')</script>"></asp:Literal>

-->

<!-- 7. The Literal control is a light wieght control, when compared with the Label control. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    Label.Text = "Label Text";
    Literal.Text = "<em><font color=\"Red\">Literal Text</font></em>"

}

Design Time:
<asp:Label ID="Label" runat="server" Font-Bold="true" ForeColor="Red"></asp:Label>
<asp:Literal ID="Literal" runat=server></asp:Literal>

Run Time:
<span id="Label" style="color:Red;font-weight:bold;">Label Text</span>
<em><font color="Red">Literal Text</font></em>

-->