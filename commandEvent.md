<!-- Command Event -->

<!-- The ASP.NET button control exposes 2 events - Click and Command events. When the Button is clicked, both the events are raised. The Click event occurs before the Command event -->

<!-- Note: Eventhandlers can be associated with the events of a control in 2 ways. -->
<!-- 1. Declaratively at design time in the HTML. -->
<!-- 2. Programmatically using delegates. -->

<!-- If you have multiple button controls on a webform, and if you want to programmatically determine which Button control is clicked, we can make use of the Command event, along with the CommandName and CommandArgument properties. -->

<!-- The Command event, makes it possible to have a single event handler method responding to the Click event of multiple buttons. The Command event, along with CommandName and CommandArgument properties are extremely useful when working with data-bound controls like Repeater, GridView, and DataList. All 3 button controls expose the Command event, in addition to CommandName and CommandArgument properties. -->