<!-- ASP.NET Page Life Cycle Events -->

<!-- Events can occur at 3 levels in an ASP.NET web application. -->

<!-- Web applications work on a stateless protocol. Every time a request is made for a webform, the following sequence of events occur. -->
<!-- 1. Web Application creates an instance of the requested webform. -->
<!-- 2. It processes the events of the webform. -->
<!-- 3. Generated the HTML, and sends the HTML back to the requested client. -->
<!-- 4. The webform gets destroyed and removed from the memory. -->

<!-- The following are some of the commonly used events in the life cycle of an ASP.NET webform. These events are shown in order of occurrence, except for, Error event, which occurs only if there is an unhandled exception. -->

<!-- PreInit -->
<!-- As the name suggests, this event happens just before the page initialization event starts. IsPostBack, IsCallback, and IsCrossPagePostBack properties are set at this stage. This event allows us to set the master page and theme of a web application dynmically. PreInit is used extensively when working with dynamic controls. -->
<!-- Ex. 

protected void Page_PreInit(object sender, EventArgs e) 
{ Response.Write("Page_PreInit" + "<br/>"); }

-->

<!-- Init -->
<!-- Page Init, event occurs after the Init event, of all the individual controls on the webform. Use this event to read or initialize control properties. The server controls are loaded and initialized from the Web form's view state. -->
<!-- Ex. 

protected void Page_Init(object sender, EventArgs e) 
{ Response.Write("Page_Init" + "<br/>"); }

-->

<!-- InitComplete -->
<!-- As the name says, this event gets raised immediately after page initialization. -->
<!-- Ex. 

protected void Page_InitComplete(object sender, EventArgs e) 
{ Response.Write("Page_InitComplete" + "<br/>"); }

-->

<!-- PreLoad -->
<!-- Pre Load event occurs just before the Page Load event. -->
<!-- Ex. 

protected void Page_PreLoad(object sender, EventArgs e) 
{ Response.Write("Page_PreLoad" + "<br/>"); }

-->

<!-- Load -->
<!-- Page Load event occurs before the load event of all the individual controls on that webform. -->

<!-- Control Events -->
<!-- After the Page Load event, the control events like a button's click or dropdownlist's selected index change events are raised. -->

<!-- Load Complete -->
<!-- This event is raised after the control events are handled. -->
<!-- Ex. 

protected void Page_LoadComplete(object sender, EventArgs e) 
{ Response.Write("Page_LoadComplete" + "<br/>"); }

-->

<!-- PreRender -->
<!-- This event is raised just before the rendering stage of the page. -->
<!-- Ex. 

protected void Page_PreRender(object sender, EventArgs e) 
{ Response.Write("Page_PreRender" + "<br/>"); }

-->

<!-- PreRenderComplete -->
<!-- Raised immediately after the PreRender event. -->
<!-- Ex. 

protected void Page_PreRenderComplete(object sender, EventArgs e) 
{ Response.Write("Page_PreRenderComplete" + "<br/>"); }

-->

<!-- Unload -->
<!-- Raised for each control and then for the page. At this stage the page is unloaded from memory. -->
<!-- Ex. 

protected void Page_Unload(object sender, EventArgs e) 
//{ Response.Write("Page_Unload" + "<br/>"); }
Note: Uncommenting Response.Write in Page_Unload Event, causes a runtime exception.

-->

<!-- Error -->
<!-- This event occurs only if there is an unhandled exception. -->