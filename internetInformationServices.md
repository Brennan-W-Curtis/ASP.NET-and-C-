<!-- IIS and ASP.NET -->

<!-- What is a web server? -->
<!-- In simple terms, a web server is software, that is used to deliver web pages to clients using the Hypertext Transfer Protocol (HTTP). For example, IIS is a web server that can be used to run ASP.NET web applications. -->

<!-- Do you need IIS to develop and test ASP.NET web applications. -->
<!-- No, Visual Studio ships with a built-in web server. If you want to just build and test web applications on your machine, you don't need an IIS. However, a built-in web server will not serve requests to another computer. By default, Visual Studio uses the built-in web server. -->

<!-- How to check if IIS is installed -->
<!-- 1. Click on the windows Start button. -->
<!-- 2. Type INETMGR in the run window. -->
<!-- 3. Click OK. -->
<!-- 4. If you get the IIS manager window, it is installed, otherwise it's not installed. -->

<!-- How to install IIS -->
<!-- 1. Click on the start button and select ControlPanel and click on Programs and Features. -->
<!-- 2. Click on Turn windows feature on or off, under the Programs and Features option. -->
<!-- 3. In the windows features, select Internet Information Services and related services. -->

<!-- To configure a virtual directory in IIS to run ASP.NET web applications -->
<!-- 1. In the IIS Manager window, double click on the IIS server name in the connections section. -->
<!-- 2. Expand sites. -->
<!-- 3. Right click on Default Web Site and Select Add Application. -->
<!-- 4. Give an alias name. This is the name you will use in the URL when connecting to your web application. -->
<!-- 5. Click the button next to the textbox under the physical path. Selec the physical web application folder. -->

<!-- You can also create the virtual directory from Visual Studio, on the project properties window. -->
<!-- 1. Select Use Local IIS Web Server. -->
<!-- 2. Project URL will be populated automatically. You can change the name of the virtual directory if you wish to do so. -->
<!-- 3. Click the Create Virtual Directory button. -->
<!-- 4. After a few seconds the virtual directory will be successfully reated and a message will appear. -->
<!-- 5. Click OK. -->