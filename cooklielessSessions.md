<!-- Cookieless Sessions in ASP.NET -->

<!-- By default sessions use cookies. The session-id is stored as a cookie on the client computer. This session-id, is then, used by the web-server too identify if the request is coming from the same user or a different user. -->

<!-- Some users do not like websites writing information to their computers. So it is very common for users to disable cookies. If that is the case, then websites using cookies to manage sessions may not work as expected. However, to overcome this problem, cookieless sessions can be enabled. To enable cookieless session, set cookieless="true" in the web.config file. -->

<!-- Ex. <sessionState mode="InProc" cookieless="true"></sessionState> -->

<!-- When cookieless sessions are enabled, the session-id is part of the URL and is sent back and forth between the client and the web server, with every request and response. -->

<!-- The web server uses the session-id from the URL to identify if the request has come from the same user or a different user. -->

<!-- For cookieless sessions to work correctly, relative URLs must be used in application, when redirecting users to different webforms. -->

<!-- For example, if you are on http://index.com/WebForm1.aspx and if you want to navigate to WebForm2.aspx then use, -->
<!-- Ex.

//Relative URL
response.Redirect("~/WebForm2.aspx");

//INSTEAD OF

//Absolute URL (or Complete Path)
Response.Redirect("http://index.com/WebForm2.aspx");

-->