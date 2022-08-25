<!-- State Server Session State Mode -->

<!-- 3. StateServer -->
<!-- The Session State variables are stored in a process called ASP.NET state service. This process is different from the ASP.NET worker process. -->

<!-- The ASP.NET state service can be present on a web server or a dedicated machine. -->

<!-- Configure ASP.NET web application to use StateServer: -->
<!-- A) Start the ASP.NET State Service. -->
<!-- I. Click Start > Type Run > Press Enter -->
<!-- II. In the run window, type "services.msc" and click OK. -->
<!-- III. Set stateConnectionString="tcpip=StateServer:42424" -->

<!-- Advantages of using StateServer session state mode: -->
<!-- A) Is ASP.NET worker process indepedent. Thus, it survives the worker process restart. -->
<!-- B) It can be used with both web farms and web gardens. -->
<!-- C) State server offers more scalability than InProc. -->

<!-- Disadvantages of using StateServer session state mode: -->
<!-- A) StateService is slower than InProc. -->
<!-- B) Complex objects need to be serialized and deserialized. -->
<!-- C) If the StateServer is on a dedicated machine and the server goes down all the sessions are lost. -->