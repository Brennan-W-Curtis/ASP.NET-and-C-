<!-- Sending Emails in ASP.NET -->

<!-- How to send an email to the development team or administrator along with logging exceptions. -->

<!-- To compose the email message, use MailMessage calls. To send the email use, the SmtpClient class. Both of these classes are present in the System.Net.Mail namespace. -->

<!-- SMTP, stands for  Simple Mail Transfer Protocol. -->

<!-- Configuring the capability of sending emails can occur in the web.config file. -->

<!-- Ex.

<appSettings>
    <add key="SendEmail" value="true" />
</appSettings>

-->

<!-- Organizations typically have their own SMPT server. If you want to send emails using your own SMTP server, use the respective SMTP server address and credentials. -->

<!-- Ex.

public static void Send_Email(string Email_Body)
{
    MailMessage Mail_Message = new MailMessage("your_email@gmail.com", "your_email@gmail.com");
    Mail_Message.Subject = "Exception";
    Mail_Message.Body = Email_Body;

    // 587 is the port number Google's SMTP server uses
    SmtpClient Smtp_Client = new SmtpClient("smtp.gmail.com", 587);
    Smtp_Client.credentials = System.Net.NetworkCredential()
    {
        UserName = "your_email@gmail.com", 
        Password = "your_password"
    };
    Smtp_Client.EnableSsl = true;
    Smtp_Client.Send(Mail_Message);

}

-->

<!-- Web.config settings for SMTP server -->
<!-- 

<system.net>
    <mailSettings>
        <smtp deliveryMethod="Network">
            <network host="smtp.gmail.com" enableSsl="true" port="587" userName="your_email@gmail.com" password="your_password">
        </smtp>
    </mailSettings>
</system.net>

-->

<!-- Since the SMTP server settings are now configured in the web.config file with the code you must: -->

<!-- 1. Create an instance of the MailMessage class. Specify the FROM & TO email addresses, the subject, and body. -->
<!-- 2. Create an instance of the SmtpClient class and send the email using the Send() method. The SMTP settings will be automatically picked up from the web.config file when sending the email. -->

<!-- If the SMTP settings are assigned as properties within the web.config file specifying the server, port number, and credentials is no longer required. -->

<!-- Ex.

    SmtpClient Smtp_Client = new SmtpClient();
    Smtp_Client.Send(Mail_Message);

}

-->