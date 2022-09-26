<!-- Locking User Accounts -->

<!-- For example, if a user enters the wrong password, they will be given 3 more chances to enter the correct password. After the 3 chances have elapsed the account will be locked. After the account is locked the user will not be able to log in, even, if they provide the correct password. -->

<!-- 

protected void ButtonLogin_Click(object sender, EventArgs e)
{
    AuthenticateUser(Text_Username.Text, Text_Password.Text);
}

private void Authenticate_User(string username, string password)
{
    // Creating connection string.
    string ConnectionString = ConfigurationManager.ConnectionString["DBCS"].ConnectionString;

    // Creating SQL connection object.
    using (SqlConnection connection = new SqlConnection(CS))
    {
        // Creating an instance of SQL Command and invoking the stored procedure.
        SqlCommand command = new SqlCommand("spAuthenticateUser", connection);
        // Specifying the command type as stored procedure because of line above.
        command.CommandType = CommandType.StoredProcedure;

        // Must encrypt password first since the password within the database in encrypted.
        string Encrypted_Password = FormsAuthentication.HashPasswordForStoringInConfigFile(password, "SHA1");

        // Since the stored procedure expects two parameters we create them.
        SqlParameter paramUsername = new SqlParameter("@Username", username);
        SqlParameter paramPassword = new SqlParameter("@Password", Encrypted_Password);

        // Associate each parameter object with the command object.
        command.Parameters.Add(paramUsername);
        command.Parameters.Add(paramPassword);

        // Open connection.
        connection.Open();
        // Invoke ExecuteReader method because a row of data is returned by stored procedure.
        SqlDataReader Return_Data_Reader = (int)command.ExecuteReader();
        while (Return_Data_Reader.Read())
        {
            // Store retry attempts from the reader object.
            int Retry_Attempts = Convert.ToInt32(Return_Data_Reader["RetryAttempts"]);
            // If account is locked display message to user.
            if (Convert.ToBoolean(Return_Data_Reader["AccountLocked"]))
            {
                Label_Message.Text = "Account Locked. Please contact administrator.";
            }  
            else if (Retry_Attempts > 0)
            {
                int Attempts_Left = (4 - Retry_Attempts);
                Label_Message.Text = "Invalid username and/or password. " + Attempts_Left.ToString() + " attempt(s) left.";
            }
            else if (Convert.ToBoolean(Return_Data_Reader["Authenticated"]));
            {
                FormsAuthentication.RedirectFromLoginPage(Text_Username.Text, Checkbox_Remember_Me.Checked);
            }
        }
    }
} 

-->