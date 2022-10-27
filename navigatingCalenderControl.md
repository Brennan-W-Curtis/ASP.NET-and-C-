<!-- Skipping Months and Years in a Calendar -->

<!-- There are several reasons and situations where you may need to navigate to a specific month and year in an ASP.NET calendar control. -->

<!-- For example, if the date of birth of a person is in the year 1960, we may have to click on the calendar control several times to navigate to that year. -->

<!-- The code on this page can be easily encapsulated into an user control and reused anywhere in the entire project. -->

<!-- Ex.
 
public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        Load_Years();
        Load_Months();
    }
    
    private void Load_Months()
    {
        DataSet Data_Set_Months = new DataSet();
        Data_Set_Months.ReadXML(Server.MapPath("~/Data/Months.xml"));

        Months_DropDownList.DataTextField = "Number";
        Months_DropDownList.DataValueField = "Number";

        Months_DropDownList.DataSrouce = Data_Set_Months;
        Months_DropDownList.DataBind();
    }

    private void Load_Years()
    {
        DataSet Data_Set_Years = new DataSet();
        Data_Set_Years.ReadXML(Server.MapPath("~/Data/Years.xml"));

        Years_DropDownList.DataTextField = "Number";
        Years_DropDownList.DataValueField = "Number";

        Years_DropDownList.DataSrouce = Data_Set_Years;
        Years_DropdownList.DataBind();
    }

    protected void YearsDropDownList_SelectedIndexChange(object sender, EventArgs e)
    {
        int year = Convert.ToInt16(Years_DropDownList.SelectedValue);
        int month = Convert.ToInt16(Months_DropDownList.SelectedValue);
        Calendar.VisibleDate = new DateTime(year, month, 1);
        Calendar.SelectedDate = new DateTime(year, month, 1); 
    }

    protected void MonthsDropDownList_SelectedIndexChange(object sender, EventArgs e)
    {
        int year = Convert.ToInt16(Years_DropDownList.SelectedValue);
        int month = Convert.ToInt16(Months_DropDownList.SelectedValue);
        Calendar.VisibleDate = new DateTime(year, month, 1);
        Calendar.SelectedDate = new DateTime(year, month, 1); 
    }

    Button_Click(object sender, EventArgs e)
    {
        Response.Write(Calendar.SelectedDate.ToShortDateString());
    }
} 
 
-->