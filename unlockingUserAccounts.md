<!-- Unlocking User Accounts -->

<!-- Previously locking a user account was disccused, if a user repeatedly enters the wrong password. Accounts are locked to prevent malicious users from guessing passwords and dictionary attacks. -->

<!-- There are several ways to unlock a user account -->

<!-- Approach 1: -->
<!-- The end user calls the technical helpdesk. The authorized person can issue a simple update query to remove the lock. However, running UPDATE queries manually against a production database is not recommended, as it is error prone and may result in unintentionally modifying other rows that were not intended to update. -->

<!-- Approach 2: -->
<!-- Provide a web page that lists all the locked user accounts. From this page, the helpdesk agent, can unlock the account by clicking a button. This is not as dangerous as running a manual update query, but still a manual process and may be inefficient. If you know how to write basic ADO.NET code, this appraoch should not be difficult to achieve. -->

<!-- Ex.

// Front End

<asp:Button ID="Button" Enabled='<%# Convert.ToInt32(Eval("Hours_Elapsed")) > 24 %>' CommandArgument='<%# Convert.ToInt32(Eval("Username")) > 24 %>' runat="server" Text="Enable">

// Code Behind

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        if (User.Identity.Name.ToLower() == "admin")
        {
            Get_Data();
        }
        else 
        {
            Response.Redirect("Access_Denied.aspx");
        }
    }
}

private void Get_Data()
{
    string Connection_String = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
    using (SqlConnection connection = new SqlConnection(Connection_String))
    {
        SqlCommand command = new SqlCommand("spGetAllLockedUserAccounts", connection);
        command.CommandType = CommandType.StoredProcedure;

        connection.Open();
        Grid_View_Locked_Accounts.DataSource = command.ExecuteReader();
        Grid_View_Locked_Accounts.DataBind();
    }
} 

private void Enable_User_Accounts(string username)
{
    string Connection_String = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
    using (SqlConnection connection = new SqlConnection(Connection_String))
    {
        SqlCommand command = new SqlCommand("spEnableUserAccount", connection);
        command.CommandType = CommandType.StoredProcedure;

        SqlParameter paramUsername = new SqlParameter()
        {
            ParameterName = "@Username",
            Value = username
        };

        command.Parameter.add(paramUsername);

        connection.Open();
        command.ExecuteNonQuery();
    }
} 

protected void GridViewLockedAccounts_RawCommand(object sender, GridViewCommandEventArgs e)
{
    Enable_User_accounts(e.CommandArgument.ToString());
    Get_Data();
}

-->

<!-- Approach 3: -->
<!-- Create a SQL Server job. This job checks the table_Users table for locked accounts periodically and then unlocks them. The frequency at which the job should run is configurable. -->