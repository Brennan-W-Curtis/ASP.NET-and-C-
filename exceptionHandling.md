<!-- Exception Handling in ASP.NET -->

<!-- Exceptions are unforeseen errors that happen within the logic of an application. For example, when reading a file, a number of exception conditions may occur. -->
<!-- 1. The file might not exist. -->
<!-- 2. You may not have permissions to access the file. -->

<!-- When an exception occurs and if it is not handled, then, that exception is called an, unhandled exception. An unhandled exception is displayed to the user using a "yellow screen of death". Displaying the screen of death is bad for 2 reasons. -->
<!-- 1. Error messages are cryptic and may not make any sense to the ender user. -->
<!-- 2. The exception information may be useful for a malicious user, to hack into your application. -->

<!-- To handle exceptions use Try & Catch Keywords -->

<!-- try -->
<!-- Wrap the code in a try block that could possible cause an exception. If a statement in the try block causes an exception the control will be immediately transferred to the catch block. -->

<!-- catch -->
<!-- Catches the exception and tries to correct the error and/or handles the exception. -->

<!-- finally -->
<!-- Used to free resources. The finally block is guaranteed to execute irrespectice of whether an exception has occurred or not. -->

<!-- throw -->
<!-- Used to raise an exception. -->

<!-- Ex.

protected void Page_Load(object sender, EventArgs e)
{
    Response.Write(System.Security.Principal.WindowsIdentity.GetCurrent().Name);
    try 
    {
        DataSet = DS = new DataSet();
        DS.ReadXml(Server.MapPath("~/Countires.xml"));
        GridView1.DataSource = DS;
        GridView1.DataBind(); 
    }
    catch (System.IO.FileNotFoundException exception) 
    {
        // Log the exception
        Label_Result.Text = "Sorry, file is missing.";
    }
    catch (System.UnauthorizedAccessException exception)
    {
        //Log the exception
        Label_Result.Text = "Access denied.";
    }
    catch (Exception exception)
    {
        // Log the exception
        Label_Result.Text = "There is an unknown problem.";
    }
    finally 
    {
        // Clean-up code     
    }
}

-->

<!-- The base class for all exceptions is the Exception class. Specific exceptions should be caught, before catching the general parent exception. -->