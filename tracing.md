<!-- Tracing in ASP.NET -->

<!-- Tracing enables us to view diagnostic information about a request and is very useful when debugging problems with an application. -->

<!-- Tracing can either be turned enabled or disabled at the: -->
<!-- 1. Application Level -->
<!-- 2. Page Level -->

<!-- To enable tracing at the application level set a "trace" element's "enabled" attribute to "true" in the web.config file. This enables tracing for all pages in the application. -->

<!-- To disable tracing for specific pages, set Trace="false" in the webform's "Page" directive. -->

<!-- If tracing is enabled at the application level, the trace messages are written to a file called trace.axd. The trace.axd file can be accessed locally. To make it available to remote users set localOnly="false". Tracing displays sensitive information, that could be useful to a hacker to hack into the server. So, set this attribute to "false" only when it is required. -->

<!-- To append trace messages at the end of the page set pageOutput="true". -->

<!-- Use RequestLimit attribute to control the number of trace requests that are stored on the server. The default is 10. After this limit is reached, the server will stop writing to the trace file. -->

<!-- If you want to log trace messages, even after the requestLimit has been reached set the mostRecent attribute to true. When this attribute is set to true, the old entries in the trace log are discarded and the new entries get added. -->

<!-- Ex.

<configuration>
    <system.web>
        <compilation debug="true" targetFramework"" />
        <trace enabled="true" requestLimit="" />
    </system.web>
</configuration>

-->

<!-- Writing Custom Tracing Messages -->

<!-- To write custom ASP.NET trace messages Trace.Write() and Trace.Warn() methods can be used. -->

<!-- The only difference, between these 2 methods is that, the messages written using Trace.Warn() are displayed in red colour. Where as the messages written using Trace.Write() are displayed in black colour. -->

<!-- In fact, what is the difference between Trace.Write() and Trace.Warn() is a very common ASP.NET interview question. -->

<!-- The Trace.IsEnabled property can be used to check if tracing is enabled. In the following code Trace.Warn() method is invoked only if tracing is enabled. If you don't check, the Trace.IsEnabled prior to writing out trace messages, you don't get an exception. But if you are going to do any sort of significant work to build the trace message, the you can avoid that work by checking the isEnabled property first. -->

<!-- 

if (Trace.IsEnabled)
{
    Trace.Warn(divideByZeroException.Message);
}

-->

<!-- With classic ASP, the only option for printing debugging information was Response.Write(). There are 2 problems with this. -->

<!-- 1. Actual end users can also see the debugging information that you have written using Response.Write(). But with tracing, if the pageOutput attribute is set to false, then the trace messages are written to the trace.axd file. End users cannot see the trace information. -->

<!-- 2. All the Response.Write() statements must be removed before the application is deployed to productions. But with tracing, all you have to do is diable tracing in web.config. -->

<!-- If an ASP.NET Page is very slow. What could you do to make it run faster. -->

<!-- This is a very common interview question. There are several reasons for the page being slow. So, we need to identify the cause. -->

<!-- We cannot debug an application on the production server, as we will usually, not have visual studio installed and as the code is optimized for release builds. -->

<!-- Step 1: -->
<!-- Find out which source is slow, is it the application or the database. If the page is executing SQL queries or stored procedures run those on the database and check how long they take to run. Alternatively, SQL profiler can be used to inspect the queries and the time they take. If the queries are taking most of the time, then you know you have to refine the queries for better performance. To refine the queries, there are severals way. -->

<!-- A) Check if there are indexes to help the query -->
<!-- B) Select only the required columns (Avoid Select *) -->
<!-- C) Check if there is a possibility to reduce the number of joins -->
<!-- D) If possible use NO LOCK on your select statements -->
<!-- E) Check if there are cursors and if you can replace them with joins -->

<!-- Step 2: -->
<!-- If the queries are running fast, then we know it is the application code that is causing the slowness. Isolate the page event or method that is causing the issue by turning tracing on. -->

<!-- To turn tracing on, set Trace="true" in the page directive. Once you have tracing turned on you should see trace information at the bottom of the page or in the trace.axd file. From the trace infomration, it should be clear to identify the piece of code that is taking the most time to execute. -->