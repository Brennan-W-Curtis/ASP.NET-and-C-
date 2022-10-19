<!-- User Controls in ASP.NET -->

<!-- Web user controls combine one or more server or HTML controls on a web user control page, which can in turn, be used on a web form as a single control. -->

<!-- For example, to capture dates from the end user on a webform, we need a TextBox, ImageButton, and Calendar control. To achieve this functionality, considerable amount of code needs to be written in the webform. -->

<!-- If you are capturing dates, on multiple web forms, rather than repeating the same HTML markup and code, on each webform, you can encapsulate all of them into a single web user control, which can then be used on multiple web forms. This way you are reusing the same code, which save time in terms of development and testing. -->

<!-- So in short, user controls, increase reusability of code, implement encapsulation, and reduce development and maintenance cost. -->

<!-- Ex.

public partial class CalendarUserControl : System.Web.UI.UserControl
{
    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            Calendar.Visible = false;
        }
    }

    protected void ImageButton_Click(object sender, ImageClickEventArgs e)
    {
        if (Calendar.Visible)
        {
            Calendar.Visible = false;
        }
        else 
        {
            Calendar.Visible = true;
        }
    }

    protected void Calendar_SelectionChanged(object sender, EventArgs e)
    {
        Text_Date.Text = Calendar.SelectedDate.ToShortDateString();
        Calendar.Visible = false;

    }
}

-->

<!-- Designing User Controls -->

<!-- Designing and implementing web user controls is very similar to web forms. -->

<!-- Web forms have the extension .aspx, where as web user controls have the extension of .ascx. -->

<!-- Web forms begin with a @Page directive and can have <html>, <head>, and <body> elements, where as a web user control begins with a @Control directive and cannot have <html>, <head>, and <body> elements. -->

<!-- Just like web forms, user controls also have code behind files. --> 

<!-- Adding User Controls to a Webform -->

<!-- Adding user controls to a web page is very straight forward. Simply drag the user control from the solution explorer and drop it on the web page. Make sure, the "Design" view of the webform is selected before dragging and dropping the user control on the webform. -->

<!-- This will automatically, -->

<!-- 1. Add a "Register" directive for the user control and -->
<!-- Ex. <%@ Register src="CalendarUserControl.ascx: tagname="CalendarUserControl" tagprefix="uc1" %> -->

<!-- 2. The control declaration -->
<!-- <uc1:CalendarUserControl ID="CalendarUserControl1" runat="server" /> -->

<!-- If you intend to add the user control on mutiple web forms, rather than including the "Register" directive on each and every web form, every time, the control can be registered once in the web.config file and can be used on any number of web forms, without the "Register" directive. -->

<!-- Ex.

<system.web>
    <pages>
        <controls>
            <add src="~/CalenderUserControl.ascx" tagName="CalendarUserControl" tagPrefix="uc1" />
        </controls>
    </pages>
</system.web>

-->

<!-- Will all of the compositional elements now encapsulated within the user control to retrieve date we have to expose it as a property. -->

<!-- Ex. 

public string Selected_Date 
{ 
    get 
    {
        return Text_Date.Text;
    } 
    set
    {
        Text_Date.Text = value; 
    } 
} 

-->

<!-- Adding Properties to the User Control -->

<!-- A user control can also have it's own properties and methods. At the moment, CalendarUserControl does not expose any property that returns the selected date. -->

<!-- The user control properties can also be set declaratively in the HTML at design time, either in HTML "source" mode or "design" mode. -->

<!-- But one limitation here with the user control, is that the design time value is not shown in the control at design time. -->

<!-- This is by design, and there are 2 ways to solve this issue. -->
<!-- 1. Create a custome control instead of a user control. -->
<!-- 2. Compile the user control into a DLL. -->

<!-- Very important points to keep in mind -->
<!-- 1. Delegates are function pointers, and their syntax is similar to that of a function. -->
<!-- 2. Events are variables of type delegates with an event keyword. -->

<!-- At the moment, the CalenderUserControl does not have any custom events. -->

<!-- 5 Steps to raise CalendarVisibilityChanged event -->
<!-- Step 1: Create CalendarVisibilityChangedEventArgs class that will contain the event data. -->
<!-- Step 2: Create CalendarVisibilityChangedEventHandler delegate -->
<!-- Step 3: Create CalendarVisibilityChanged event -->
<!-- Step 4: Create a protected virtual method to raise the event -->
<!-- Step 5: Finally raise the event, whenever the visibility of the Calendar is changed -->

<!-- Ex.

// Webform Code Behind

protected void Page_Load(object sender, EventArgs e)
{
    Button.Click += new EventHandler(Button_Click);
}

// User Control Code Behind

public void CalendarVisibilityChangedEventHandler(object sender, CalendarVisibilityChangedEventArgs e);

// Custom Event Class (Added to previous example)

public partial class CalendarUserControl : System.Web.UI.UserControl
{
    public event CalendarVisibilityChangedEventHandler CalendarVisibilityChanged;

    protected void ImageButton_Click(object sender, ImageClickEventArgs e)
    {
        if (Calendar.Visible)
        {
            Calendar.Visible = false;
            CalendarVisibilityChangedEventArgs Visibility_Changed_Event_Data = new CalendarVisibilityChangedEventArgs(false);
            OnCalendarVisibilityChanged(Visibility_Changed_Event_Data);
        }
        else 
        {
            Calendar.Visible = true;
            CalendarVisibilityChangedEventArgs Visibility_Changed_Event_Data = new CalendarVisibilityChangedEventArgs(true);
            OnCalendarVisibilityChanged(Visibility_Changed_Event_Data);
        }
    }

    protected virtual void CalendarVisibilityChanged(CalendarVisibilityChangedEventArgs e)
    {
        if (CalendarVisibilityChange != null)
        {
            CalendarVisibilityChanged(this, e);
        }
    }
}

public class CalendarVisibilityChangedEventArgs : EventArgs
{
    private bool _isCalendarVisible;

    public bool IsCalendarVisible
    {
        get 
        {
            return this._isCalendarVisible;
        }
    }

    public CalendarVisibilityChangedEventArgs(bool IsCalendarVisible)
    {
        this._isCalendarVisible = isCalendarVisble;
    }
}

public delegate void CalendarVisibilityChangedEventHandler(object sender, CalendarVisibilityChangedEventArgs e);

-->

<!-- Consuming Custom Events -->

<!-- To consume the event, there are 2 simple steps. -->

<!-- Step 1: Create an event handler method, The method signature must match the signature of the "CalendarVisibilityChangedEventHandler" delegate. -->
<!-- Step 2: Register the event handler method "CalendarUserControl_CalendarVisibilityChanged()" with "CalendarVisibilityChanged" event of the "CalendarUserControl" using the "+=" operator. -->

<!-- Please Note: EventHandler methdos must be registered before the event is raised. -->

<!-- Importance of, checking if the event is null, before raising the event -->
<!-- If there are no subscribers for the event, that is, if there are no event handler methods registered with the CalendarVisibilityChanged event, and if you try to raise the event, you'll receive the exception. To avoid this it's always better to check for null before raising the event. -->

<!-- Delegates are type safe function pointers because the signature of the delegate matches the signature of the function to which it's pointing to. -->