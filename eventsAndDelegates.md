<!-- Events and Delegates in C# -->

<!-- To raise DateSelected custom event, whenever, the user selects a "Date" from the "CalendarUserControl". -->

<!-- Step 1: Create "DateSelectedEventArgs" class that will contain the event data. -->

<!-- Ex.

public class DateSelectedEventArgs : EventArgs
{
    private DateTime _selectedDate;

    public DateTime SelectedDate
    {
        get 
        {
            return this._selectedDate;
        }
    }

    public DateSelectedEventArgs(DateTime selectedDate)
    {
        this._selectedDate = selectedDate;
    }
}

-->

<!-- Step 2: Create DateSelectedEventHandler delegate. -->

<!-- Ex.

public delegate void DateSelectedEventHandler(object sender, DateSelectedEventArgs e);

-->

<!-- Step 3: Create DateSelected event. -->

<!-- 

public partial class CalendarUserControl : System.Web.UI.UserControl
{
    public event DateSelectedEventHandler DateSelected;
}

-->

<!-- Step 4: Create a protected virtual method "OnDateSelection" to raise the event. -->

<!-- Ex.

protected virtual void OnDateSelection(DateSelectedEventArgs e)
{
    if (DateSelected != null)
    {
        DateSelected(this, e);
    }
}

-->

<!-- Step 5: Finally raise the event, whenever a date is selected. -->

<!-- We raised the event whenever we select a date from the calendar. -->

<!-- 

protected void Calendar_SelectionChanged(object sender, EventArgs e)
{
    DateSelectedEventArgs dateSelectedEventData = new DateSelectedEventArgs(Calendar.SelectedDate);
    OnDateSelection(DateSelectedEventData);
}

-->

<!-- Drag and drop the user control on a web form. Associate the DateSelected event with an event handler method, either in the -->
<!-- 1. HTML -->
<!-- 2. Code -->