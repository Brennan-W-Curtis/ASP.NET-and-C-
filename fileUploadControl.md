<!-- FileUpload Control in ASP.NET -->

<!-- Ex.

protected void ButtonUpload_Click(object sender, EventArgs e)
{
    if (FileUpload.HasFile)
    {
        string fileExtension = System.IO.Path.GetExtension(FileUpload.FileName);
        if (fileExtension.ToLower() != ".doc" && fileExtension.ToLower() != ".docx")
        {
            labelMessage.Text = "Only files with the .doc or .docx extensions are allowed.";
        }
        else
        {
            int fileSize = FileUpload.PostedFile.ContentLength;
            if (fileSize > 2097152)
            {
                labelMessage.Text = "Maximum file size (2MB) exceeded";
            }
            else
            {
                FileUpload.SaveAs(Server.MapPath("~/Uploads/" + FileUpload.FileName));
                labelMessage.Text = "File Uploaded";
            }
        }
    }
    else
    {
        labelMessage.Text = "Please select a file to upload.";
    }
}

-->