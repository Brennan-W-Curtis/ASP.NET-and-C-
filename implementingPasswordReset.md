<!-- Implementing Password Reset Link -->

<!-- Step 1: -->
<!-- Design a page, that allows the user to enter their username for requesting a password reset. -->

<!-- Step 2: -->
<!-- Create a table "TableResetPasswordRequests" in SQL server. This table is going to store a unique GUID (Globally Unique Identifier) along with the user id, each time a user requests a password recovery. This GUID will then be passed as part of the querystring in the link to the password reset page. This link will then be emailed to the email that is associated with the user id. When a user clicks on the link the page will look up the GUID in "TableResetPasswordRequests" table and get the user id from there allowing the user to change their password. You should consider not using, UserId, as the querystring parameter because it may be open to abuse. -->

<!-- Step 3: -->
<!-- Create a stored procedure to check if the username exists and to insert a row into "TableResetPasswordRequests" table. -->

<!-- Step 4: -->
<!-- Invoke the stored procedure and email the link to the email address that is registered against the username. -->

<!-- Ex.

private void ButtonReset_Click(object sender, EventArgs e)
{
    String Connection_String = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
    using (SqlConnection connection = new SqlConnection(Connection_String))
    {
        SqlCommand command = new SqlCommand("spResetPassword", connection);
        command.CommandType = CommandType.StoredProcedure;

        SqlParameter paramUsername = new SqlParameter("@Username", Text_Username.Text);
        
        command.Parameters.Add(ParamUsername);

        connection.Open();
        SqlDataReader reader = command.ExecuteReader();
        While (reader.Read())
        {
            if (Convert.ToBoolean(reader["ReturnCode"]))
            {
                Send_Password_Reset_Email(reader["Email"].ToString(), Text_Username.Text, reader["UniqueId"].ToString());
                Label_Message.Text = "An email with instructions to reset your password has been sent to your registered email.";
            }
            else 
            {
                Label_Message.Text = "Sorry, username not found.";
            }
        }
    }
}

private void Send_Password_Reset_Email(string Recipient_Email, string Target_Username, string Unique_Id)
{
    MailMessage Mail_Message = new MailMessage("Your_Email@gmail.com", Recipient_Email);

    StringBuilder String_Builder_Email_Body = new StringBuilder();
    String_Builder_Email_Body.Append("Dear " + Target_Username + ",<br /><br />");
    String_Builder_Email_Body.Append("Please click on the following link to reset your password.");    
    String_Builder_Email_Body.Append("<br />");
    String_Builder_Email_Body.Append("http://password_reset_link.aspx" + Unique_Id);
    String_Builder_Email_Body.Append("<br /><br />");
    String_Builder_Email_Body.Append("<em>Your Email Signature</em");

    Mail_Message.IsBodyHTML = true;

    Mail_Message.Body = String_Builder_Email_Body.ToString();
    Mail_Message.Subject = "Reset Your Password";
    SmtpClient SMTP_Client = new SmtpClient("smtp.gmail.com", 587);

    SMTP_Client.Credentials = new System.Net.NetworkCredentials()
    {
        Username = "Your_Email@gmail.com";
        Password = "Your_Password";
    }

    SMTP_Client.EnableSsl = true;
    SMTP_Client.Send(Mail_Message);

}

-->

<!-- Notice that, the Change_Password.aspx page has a query string "UID". This GUID, is used to loo up the UserID for whom the password needs to be changed. -->

<!-- After updating the password, delete the row from "TabelResetPasswordRequests", so the link becomes invalid after the user has changed his/her password. -->

<!-- Since, user ids are integers, they may be open for abuse as it is very easy to use random integers as query string values, to change another user's password. -->

<!-- Ex.

public partial class ChangePassword : System.Web.UI.Page 
{

    protected void Page_Load(object sender, EventArgs e)
    {
        if (!IsPostBack)
        {
            If (!Is_Password_Reset_Link_Valid())
            {
                Label_Message.Text = "Password reset link has expired or is invalid.";
            }
        }
    }

    protected void ButtonSave_Click(object sender, EventArgs e)
    {
        if (Change_User_Password())
        {
            Label_Message.Text = "Password Changed Successfully.";
        }
        else 
        {
            Label_Message.Text = "Password reset link has expired or is invalid."; 
        }
    }

    private bool Change_User_Password()
    {
        List<SqlParameter> Parameter_List = new List<SqlParameter>()
        {
            new SqlParameter()
            {
                ParameterName = "@GUID",
                Value = Request.QueryString["uid"]
            },
            new SqlParameter()
            {
                ParameterName - "@Password",
                Value - FormsAuthentication.HashPasswordForStroingInConfigFile(Text_New_Password.Text, "SHA1")
            }
        };
        return Execute_Stored_Procedure("spChangePassword", Parameter_List);
    }

    private bool Is_Password_Reset_Link_Valid()
    {
        List<SqlParameter> Parameter_List = new List<SqlParameter>()
        {
            new SqlParameter()
            {
                ParameterName = "@GUID",
                Value = Request.QueryString["uid"]
            }
        };
        return Execute_Stored_Procedure("spIsPasswordResetLinkValid", Parameter_List);
    }

    private bool Execute_Stored_Procedure(string Stored_Procedure_Name, List<SqlParameter> Stored_Procedure_Parameters)
    {
        string Connection_String = ConfigurationManager.ConnectionStrings["DBCS"].ConnectionString;
        using (SqlConnection connection = new SqlConnection(Connection_String))
        {
            SqlCommand command = new SqlCommand(Stored_Procedure_Name, connection);
            command.CommandType = CommandType.StoredProcedure;

            foreach (SqlParameter parameter in Stored_Procedure_Parameters)
            {
                command.Parameters.Add(parameter);
            }

            connection.Open();
            return Convert.ToBoolean(command.ExecuteScalar());
        }
    }
}


-->

<!-- To change the user's password by providing the current password include the following changes to previous methods and update the page load. -->

<!-- Ex.

private bool Change_User_Password_Using_Current_Password()
{
    List<SqlParameter> Parameter_List = new List<SqlParameter>()
    {
        new SqlParameter()
        {
            ParameterName = "@Username",
            Value = User.Identity.Name
        },
        new SqlParameter()
        {
            Parameter = "@CurrentPassword",
            Value = FormsAuthentication.HashPasswordForStoringInConfigFile(Text_Current_Password.Text, "SHA1")
        },
        new SqlParameter()
        {
            ParameterName = "@NewPassword",
            Value = FOrmsAuthentication.HashPasswordForStoringInConfigFile(Text_New_Password.Text, "SHA1")
        }
    };
    return Execute_Stored_Procedure("spChangePasswordUsingCurrentPassword", Parameter_List);
}

protected void Page_Load(object sender, EventArgs e)
{
    if (Request.QueryString["uid"] == null && User.Identity.Name == "")
    {
        Response.Redirect("~/Login.aspx");
    }
    if (!IsPagePostback)
    {
        if (Request.QueryString["uid"] != null)
        {
            if (!Is_Password_Reset_Link_Valid())
            {
                Label_Message.Text = "Password reset link has expired or is invalid.";
            }
            Input_Current_Password.Visible = false;
        }
        else if (User.Identity.Name != "")
        {
            Input_Current_Password.Visible = true;
        }
    }
}

protected void ButtonSave_Click(object sender, EventArgs e)
{
    if ((Request.QueryString["uid"] != null && Change_User_Password())) || (User.Identity.Name != "" && Change_User_Password_Using_Current_Password()))
    {
        Label_Message.Text = "Password changed successfully.";
    }
    else 
    {
        if (Input_Current_Password.Visible)
        {
            Label_Message.Text = "Sorry, invalid current password.";
        }
        else
        {
            Label_Message.Text = "Password reset link has expired or is invalid.";
        }
    }
}

-->