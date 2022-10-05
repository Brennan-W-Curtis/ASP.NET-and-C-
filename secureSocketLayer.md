<!-- Secure Socket Layer (SSL) in ASP.NET -->

<!-- Advantages of Using HTTPS -->
<!-- HTTP stands for Hyper Text Transfer Protocol while HTTPS stands for Hyper Text Transfer Protocol Secure. As the name suggests, HTTPS is more secure than HTTP. When the web server and the client communicate, using HTTP, the messages that are exchanged over the internet are not encrypted. Any one can secretly listen and see the messages that are exchanged between the client and web server. That's why, any sensitive information like passwords or financial transactions should never be done over HTTP protocol. -->

<!-- Most banking applications use HTTPS. Messages exchanged between the client and web server using HTTPS are encrypted and are very secure. HTTP uses port 80 where as HTTPS uses port 443. -->

<!-- How to identify if the web application you are currently accessing uses HTTPS -->

<!-- 1. The browser displays a lock symbol either in the address or status bar. Click on the lock icon for more information such as the certificate issuing authority, encryption key length, etc. -->

<!-- 2. In the address bar look for HTTPS instead of HTTP. -->

<!-- How to configure HTTPS instead of HTTP for ASP.NET web applications -->
<!-- IIS is the web server for ASP.NET web applications. So, the configuration to use HTTPS, is usually done in IIS. The encryption and decryption of messages exchanged between the client and server is done by server certificates. These server certificates need to be installed on the IIS server. -->

<!-- What is Secure Socket Layer and how is it different from HTTPS -->
<!-- HTTPS is HTTP plus SSL. SSL is a standard security technology for establishing an encrypted link between a web server and a browser, so that the data sent over the internet can't be ready by others. -->

<!-- When a user requests a secure Web page, the server generates an encryption key for the user's session and then encrypts the page's data before sending a response. On the client side, the browser uses the same encryption key to decrypt the requested web page to encrypt new requests sent from the page. A SSL uses server certificates for both encryption and decryption. -->

<!-- An SSL certificate contains a public key and certificate issuer. Not only can clients use the certificate to communicate with a server, clients can verify that the certificate was cryptographically signed by an official Certificate Authority. -->

<!-- For example, if your browser trusts the VeriSign Certificate Authority, and VeriSign signs the SSL certificate, your browser will inherently trust the SSL Certificate. -->

<!-- Who issues server certificates  -->

<!-- Server certificates are issued by an entity called a certificate authority. There are several trusted certificate authorities like VeriSign, Thawte, Geotrust, Comodo, and GoDaddy. -->

<!-- The certificate authority acts as a clearinghouse to verify the server's identity over the Internet. When a browser requests a page over HTTPS, the browser also requests the server certificate and checks it against a list of trusted sites provided by the certificate authority. If the server certificate does not match one of the sites already authorized by the user, or if the server certificate does not match the web address for which it was registered, or if there are any other problems with the server certificate, a warning message is displayed. -->

<!-- Besides providing encryption and decryption for secure data transmission, certificate authorities also provide assurance to users that a website is authentic. -->

<!-- It is also possible to generate our own server certificates, using a tool called makecert.exe. This tool comes with visual studio and can be used from visual studio's command prompt. -->

<!-- The certificates that are generated using this tool, can only be used for testing purposes and not for production use. -->

<!-- What are the performance differences when using HTTPS over HTTP -->
<!-- Extra processing time is required for HTTPS, for key negiotiation. Key negotiation is also referred to as a SSL handshake. The handshake allows the server to authenticate itself to the client. -->