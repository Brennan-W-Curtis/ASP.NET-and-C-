<!-- HiddenField Control in ASP.NET -->

<!-- HiddenField: The HiddenField control is used to store a value that needs to be persisted across posts to the server, but you don't want the control or it's value to be visible to the user. For example, when editing and updating an employee record, we don't want the user to see the EmployeeId. So, we will store the EmployeeId in a HiddenField, so that it can then be used on the server to update the correct employee's record. -->

<!-- 1. Value property of the HiddenField is used to get or set the value. -->
<!-- 2. The value is stored as a string. -->
<!-- 3. ViewState uses the HiddenField control to main state across postback. -->
<!-- 4. The HiddenField is rendered as an <input type="hidden" /> element. -->

<!-- Alternatives to use instead of the HiddenField -->
<!-- ViewState, QueryStrings, Session State, and Cookies can be used as an alternative for the HiddenField. Session state and cookies will be accessible from other pages as well, and will be available until their timeout has been reached. Where as, ViewState and HiddenField data is available only on that page and the data is lost when you navigate away from the page. -->

<!-- Advantages to using the HiddenField -->
<!-- The HiddenField data is lost when you navigate away from the page and doesn't require an explicit cleanup task. -->

<!-- The HiddenField is accessible to client-side scripts -->
<!-- Ex.

<script type="text/javascript">
    const Get_Hidden_Field_Value = () => {
        alert(document.getElementById("HiddenField).value);
    };
</script>

-->

<!-- Disadvantages to using the Hidden Field -->
<!-- The HiddenField can be seen by viewing the page source. Never, use a HiddenField control to store confidential data. -->