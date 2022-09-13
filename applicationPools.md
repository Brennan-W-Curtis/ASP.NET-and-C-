<!-- What Are Application Pools in Internet Information Services (IIS) -->

<!-- An Application Pool can contain one or more web applications. In IIS it is possible to create one or more application pools. -->

<!-- Applications in different application pools run in their own worker process (w3wp.exe). Errors in one application pool will not affect the applications running in other application pools. -->

<!-- For example, if an application pool is recycled only the applications in that pool are affected (may lose state information if stored inside the worker process), and applications in other application pools are unaffected. -->

<!-- Deploying applications to different application pools enables us to achieve the degree of application isolation that we need, in terms of availability and security. -->

<!-- For example, applications that require high security can be present in one application pool, and the other applications can be in a different application pool. -->

<!-- Another example, hosting providers can place competing business applications pools, so that they do not accidentally access the data belonging to their competitor. -->

<!-- Application Pool Identities -->

<!-- ASP.NET applications execute inside the ASP.NET worker process called w3wp.exe. The applications are executed by the worker process, using a windows identity. The windows identity that is used, is dependent on the application pool identity. The application pool identity can be any of the following built-in accounts. -->

<!-- 1. LocalService -->
<!-- Completely trusted account that has very high privileges and can also access network resources. -->

<!-- 2. LocalSystem -->
<!-- Restricted or limited service account that is generally used to run, standard least-privileged services. This account has less privileges than LocalSystem account. This account can access network resources. -->

<!-- 3. NetworkService -->
<!-- Restricted or limited service account that is very similar to NetworkService and meant to run standard least-privileged services. This account cannot access network resources. -->

<!-- 4. ApplicationPoolIdentity -->
<!-- When a new Application Pool is created, IIS creates a virtual account with the name of the new Application Pool and runs the Application Pool's worker processes under this account. This is also a least privileged account. -->

<!-- In addition to these built-in accounts, we can also use a custom account by specifying the username and password. -->

<!-- By default, when a new applciation pool is created, it uses ApplicationPoolIdentity. -->

<!-- Running an application using a low-privileged account is a good security practice because if there is a bug it cannot be used by a malicious user to hack into your application or your system. -->

