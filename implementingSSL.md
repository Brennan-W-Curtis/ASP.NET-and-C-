<!-- Implementing SSL -->

<!-- What are self signed certificates -->
<!-- A self-signed certificate is an identity certificate that is signed by its own creator. Certificates are signed by by a certificate authority. In general, self signed certificates are fine for testing purposes but not for production. -->

<!-- Creating self signed certificates -->

<!-- There are several ways to create self signed test certificates. -->
<!-- 1. Using IIS -->
<!-- 2. Using MakeCert.exe -->

<!-- Associating an ASP.NET web application with a specific certificate -->

<!-- Add HTTPS site binding, if it is not already present. -->

<!-- At this point, you will be able to access your application using both HTTP and HTTPS protocol. When the site is accessed over HTTPS, you may receive a browser warning about the authenticity of the website. -->

<!-- If you want to dis-allow, access over HTTP protocol there are 2 options -->

<!-- 1. Remove the HTTP binding at the IIS Server level. This option will ensure all the web applications running on that server use only the HTTPS binding. -->
<!-- 2. Let both the bindings be available at the server level and configure SSL settings at an application or web site levle. -->

<!-- Note: Use the Import and Export features of IIS to import and export certificates. -->