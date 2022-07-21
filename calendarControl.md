<!-- Calendar Control in ASP.NET -->

<!-- Response.Write("ToString() = " + DateTime.Now.ToString() + "<br />"); -->
<!-- Produces: ToString() - 20/06/22 5:00:00 -->

<!-- Response.Write("ToLongDateString() - " + DateTime.Now.ToLongDateString() + "<br />"); -->
<!-- Produces: ToLongDateString() - 20 June 2022 -->

<!-- Response.Write("ToShortDateString() - " + DateTime.Now.ToShortDateString() + "<br />"); -->
<!-- Produces: ToShortDateString() - 20/06/2022 -->

<!-- Response.Write("ToLongTimeString() - " + DateTime.Now.ToLongTimeString() + "<br />"); -->
<!-- Produces: ToLongTimeString() - 05:00:00 -->

<!-- Response.Write("ToShortTimeString() - " + DateTime.Now.ToShortTimeString() + "<br />"); -->
<!-- Produces: ToShortTimeString() - 05:00 -->

<!-- Response.Write("d - " + DateTime.Now.ToString("d") + "<br />") -->
<!-- Produces: d - 20/06/2022 -->

<!-- Response.Write("D - " + DateTime.Now.ToString("D") + "<br />") -->
<!-- Produces: D - 20 June 2022 -->

<!-- Response.Write("dd/MM/yyyy - " + DateTime.Now.ToString("dd/MM/yyyy") + "<br />"); -->
<!-- Produces: dd/MM/yyyy - 20/06/2022 -->

<!-- Response.Write("dd/MMMM/yyyy - " + DateTime.Now.ToString("dd/MMMM/yyyy") + "<br />"); -->
<!-- Produces: dd/MMMM/yyyy - 20/June/2022 -->

<!-- Response.Write("dd/MMMM/yy - " + DateTime.Now.ToString("dd/MMMM/yy") + "<br />"); -->
<!-- Produces: dd/MMMM/yy - 20/June/22 -->

<!-- Response.Write("MM/dd/yy - " + DateTime.Now.ToString("MM/dd/yy") + "<br />"); -->
<!-- Produces: MM/dd/yy - 06/20/22 -->

<!-- Useful Properties -->

<!-- 1. Caption -->
<!-- This is a string read/write property. -->

<!-- 2. CaptionAlign -->
<!-- Used to align the caption. -->

<!-- 3. DayHeaderStyle -->
<!-- Style properties that can be used to customize the look and feel of the day header in the calendar. -->

<!-- 4. DayNameFormat -->
<!-- Can be set to Full, Short, FirstLetter, FirstTwoLetters, and Shortest -->

<!-- 5. DayStyle -->
<!-- Style properties that can be used to customize the look and feel of the day in the calendar. -->

<!-- 6. FirstDayOfWeek -->
<!-- Which day of the week is displayed first. -->

<!-- 7. NextPrevFormat -->
<!-- Can be set to ShortMonth, FullMonth, and CustomText. -->

<!-- 8. NextMonthText -->
<!-- The text to use for the next month button. -->

<!-- 9. PrevMonthText -->
<!-- The text to use for the previous month button. -->

<!-- 10. SelectionMode -->
<!-- Can be set to Day, DayWeek, and DayWeekMonth. Determines if Days, Weeks, and Months are selectable. -->