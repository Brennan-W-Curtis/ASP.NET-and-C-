<!-- Windows Event Viewer -->

<!-- Exceptions in an ASP.NET web application can be logged to the event viewer. -->

<!-- Under windows log there is -->

<!-- 1. Application -->
<!-- Logs information from applications like Microsoft Office, SQL Server, Visual Studio, etc. -->

<!-- 2. Security -->
<!-- Logs information related to security like user sign-ons, access checks, etc. -->

<!-- 3. System -->
<!-- Logs information related to driver, system service failures, etc. -->

<!-- The Event Source is the name of the application that logged the event. -->

<!-- Ex.

private void CreateEventLogButton_Click(object sender, EventArgs e)
{
    if (Event_Log_Name_TextBox.Text != string.Empty && Event_Log_Source_TextBox.Text != string.Empty) 
    {
        System.Diagnostics.EventLog.CreateEventSource("Event_Log_Source_TextBox.Text", "Event_Log_Name_TextBox.Text");
        MessageBox.Show("Event Log and Source created.");
    } else {
        MessageBox.Show("Event Log and Source required.");
    }
}

-->

<!-- How to log an exception in the event viewer -->

<!-- Ex.

// Method from Event_Viewer_Log Class

public static void Log_Exception(Exception exception)
{
    StringBuilder Stringbuilder_Exception_Message = new StringBuilder();
    Stringbuilder_Exception_Message.Append("Exception Type" + Environment.NewLine);
    Stringbuilder_Exception_Message.Append(exception.GetType().Name);
    Stringbuilder_Exception_Message.Append(Environment.NewLine + Environment.NewLine);
    Stringbuilder_Exception_Message.Append("Message" + Environment.NewLine);
    Stringbuilder_Exception_Message.Append(exception.Message + Environment.NewLine + Environment.NewLine);
    Stringbuilder_Exception_Message.Append("Stack Trace" + Environment.NewLine);
    Stringbuilder_Exception_Message.Append(exception.StackTrace + Environment.NewLine + Environment/NewLine);

    Exception Inner_Exception = exception.InnerException;

    while (Inner_Exception != null)
    {
        Stringbuilder_Exception_Message.Append("Exception Type" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(Inner_Exception.GetType().Name);
        Stringbuilder_Exception_Message.Append(Environment.NewLine + Environment.NewLine);
        Stringbuilder_Exception_Message.Append("Message" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(Inner_Exception.Message + Environment.NewLine + Environment.NewLine);
        Stringbuilder_Exception_Message.Append("Stack Trace" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(Inner_Exception.StackTrace + Environment.NewLine + Environment/NewLine);

        Inner_Exception = Inner_Exception.InnerException;
    }

    if (EventLog.SourceExcists("WebForm1.aspx"))
    {
        EventLog Event_Log = new EventLog("WebForm1");
        Event_Log = "WebForm1.aspx";
        Event_Log.WriteEntry(Stringbuilder_Exception_Message.ToString(), EventLogEntryType.Error);
    }
}

// Global.asax.cs

protected void Application_Error(object sender, EventArgs e)
{
    Exception exception = Server.GetLastError();

    if (exception != null)
    {
        Event_Viewer_Log.Log_Exception(exception);
        Server.ClearError();
        Server.Transfer("~/Errors.aspx");
    }
}

// How to log exceptions of a different type

public static void Log_Exception(Exception exception)
{
    Log_Exception(exception, EventLogEntryType.Error);
}

public static void Log_Exception(Exception exception, EventLogEntryType Event_Log_Entry_Type)
{
    StringBuilder Stringbuilder_Exception_Message = new StringBuilder();

    do
    {
        Stringbuilder_Exception_Message.Append("Exception Type" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(exception.GetType().Name);
        Stringbuilder_Exception_Message.Append(Environment.NewLine + Environment.NewLine);
        Stringbuilder_Exception_Message.Append("Message" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(exception.Message + Environment.NewLine + Environment.NewLine);
        Stringbuilder_Exception_Message.Append("Stack Trace" + Environment.NewLine);
        Stringbuilder_Exception_Message.Append(exception.StackTrace + Environment.NewLine + Environment/NewLine);

        exception = exception.InnerException;

    } while (exception != null)

    if (EventLog.SourceExcists("WebForm1.aspx"))
    {
        EventLog Event_Log = new EventLog("WebForm1");
        Event_Log = "WebForm1.aspx";
        Event_Log.WriteEntry(Stringbuilder_Exception_Message.ToString(), Event_Log_Entry_Type);
    }
}

-->