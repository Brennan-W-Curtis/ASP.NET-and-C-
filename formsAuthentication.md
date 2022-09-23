<!-- Forms Authenication -->

<!-- Anonymous authenication is fine for web sites that contain public information that everyone can see. -->

<!-- Windows authenication is used for intranet Web applications, where the users are part of a windows domain-based network. -->

<!-- When to use Forms Authentication -->
<!-- Forms authenication is used for internet Web applications. The advantage of Forms authentication is that users do not have to be a member of a domain-based network to have access to your application. Many internet web sites like Gmail.com, Amazon.com, Facebook.com, etc use forms authentication. To access these applications you do not have to be a member of their domain-based network. -->

<!-- Notes: FormsAuthentication classes are present in the System.Web.Security namespace. -->

<!-- Ex.

// Web.config

<system.web>
    <authenication mode="Forms" >
        <forms loginUrl="Login.aspx" defaultUrl="Welcome.aspx" protection="" timeout="" />
            <credentials passwordFormat="clear" />
                <user name="Example" password="Example" />
            </credentials>
        </forms>
    </authentication>
    <authorization>
        <deny users="?" />
    </authorization>
</system.web>

// Code Behind

protected void ButtonLogin_Click(object sender, EventArgs e)
{
    if (FormsAuthenication.Authenticate(Text_Username.Text, Text_Password.Text))
    {
        FormsAuthentication.RedirectFromLoginPage(Text_Username.Text, Checkbox_Remember_Me.Checked);
    }
    else
    {
        Label_Message.Text = "Sorry, invalid user name and/or password";
    }
}

-->

<!-- It is good practice, when validation fails, do not tell the user which value is entered incorrectly because if they are a malicious user receives confirmation that they entered correct information that narrows the scope of their next attack. As far as security is concerned only provide the minimum amount of details required to the end user. -->

<!-- There are 2 problems with this application at the moment. -->

<!-- 1. It is not good practice to store usernames and passwords in the web.config file. If you want to create the usernames and passwords dynamically you need to change the web.config file. -->

<!-- 2. At the moment, users are not able to access the Register.aspx page, if they are not logged in. If a user does not have a username and password, they should be able to register themselves using the Register.aspx page. -->

<!-- To solve this issue, add another web.config file to the "Registration" folder and specify the authorization element to allow all users. -->

<!-- Ex.

<system.web>
    <authorization>
        <allow users="*" />
    </authorization>
</system.web>

-->

<!-- This is because with the previous authorization setting in place to deny anonymous users (Line 25) the end-users now will only be able to access the login page. Since we have specified the loginUrl without logging in they can only access Login.aspx. If they attempt to navigate to any other page they will be denied access and redirected back to Login.aspx. -->

<!-- So far, authenticating users against a list stored in a web.config file and registering users if they do not have a username and password to login have been discussed. Next is discussing how to authenticate users against a list stored in a database table. -->

<!-- The FormsAuthentication class exposes a static method Authenticate(), which does all the hardwork of authenticating users. -->

<!-- If you want to authenticate user against a list stored in a database table, writing a stored procedure and a method in the application to authenticate users is required. -->

<!-- Ex.

protected void ButtonLogin_Click(object sender, EventArgs e)
{
    if (AuthenticateUser(Text_Username.Text, Text_Password.Text))
    {
        FormsAuthentication.RedirectFromLoginPage(Text_Username.Text, Checkbox_Remember_Me.Checked);
    }
    else 
    {
        Label_Message.Text = "Invalid username and/or password.";
    }
}

private bool Authenticate_User(string username, string password)
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
        // Invoke ExecuteScalar method because a single value is returned by stored procedure and type cast return object as integer.
        int ReturnCode = (int)command.ExecuteScalar();
        return ReturnCode == 1;
    }
}

-->