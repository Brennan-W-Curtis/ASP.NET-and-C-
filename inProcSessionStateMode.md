<!-- InProc Session State Mode -->

<!-- The ASP.NET Session State mode can have any of the following 4 values and is set in the web.config file. -->

<!-- 1. Off -->
<!-- Disables Session State for the entire application. -->

<!-- 2. InProc -->
<!-- The Session State variables are stored on the web-server memory inside the ASP.NET worker process. This is the default Session State mode. -->

<!-- Advantages of InProc Session State mode: -->
<!-- A) Very easy to implement. All that is required is, to set the Session State mode="InProc" in the web.config file. -->
<!-- B) It will perform best because the Session Stat memory is kept on the webserver, within the ASP.NET worker process (w3wp.exe). -->
<!-- C) Suitable for web paplications hosted on a single server. -->
<!-- D) Objects can be added without serialization -->

<!-- Disadvantages of InProc Session State mode: -->
<!-- A) Session State data is lost, when the worker process or application pool is recycled. -->
<!-- B) It's not suitable for webfarms and webgardens. -->
<!-- C) Scalability could be a potential is use. -->

<!-- 3. StateServer -->
<!-- 4. SQL SErver -->
<!-- 5. Custom -->

<!-- Note: -->

<!-- Web Garden -->
<!-- A Web application deployed on a server with multiple processors. -->

<!-- Web Farm -->
<!-- A Web application deployed on mutiple servers. -->