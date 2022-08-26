<!-- SQL Server Session State Mode -->

<!-- 4. SQL Server -->
<!-- The Session State variables are stored in a SQLServer database. -->

<!-- Steps to configure Session State Mode to SQLServer -->
<!-- A) Create the ASPState database using aspnet_regsql.exe tool. -->
<!-- B) Set the Session State mode to SQLServer and sqlConnectionString. -->

<!-- Ex. <sessionState mode="SQLServer" sqlConnectionString="data source=.; integrated security=SSPI" timeout="20"></sessionState> -->

<!-- Advantages of using SQLServer Session State mode: -->
<!-- A) SQLServer is the most reliable option. It survives worker process recycling and SQL Server restarts. -->
<!-- B) Can be used with both web farms and web gardens. -->
<!-- C) It's more scalable than State server and InProc session state modes. -->

<!-- Disadvantages of using StateServer Session State mode: -->
<!-- A) Slower than StateServer and InProc Session State modes. -->
<!-- B) Complex objects need to be serialized and deserialized. -->

<!-- 5. Custom -->