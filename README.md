new-javascript-sdk
==================



New Features:
<ol>
<li>Promises df.resource.methodName().then() ...etc
<li>Build All, Some, or One of the Resource SDKs
<li>Error Handling
</ol>
<br/>
Useage:
<br/>
Requires Jquery<br/>
Download dreamfactory.js and link to it in your html

```html
<script src='path_to_your/jquery.js' type='text/javascript'></script>
<script src='path_to_your/dreamfactory.js' type='text/javascript'></script>
```

```javascript
//login and get data records on success

    var body ={email : $("#email").val(), password : $("#password").val()};
        dreamfactory.user.login(body)
            .then(function (response) {
               window.dreamfactory.SESSION_TOKEN = response.session_id;
                $("#login-form").hide();
                $("#logout-button").show();
                $("#password").val("");
                dreamfactory.db.getRecords({table_name: "todo"});
            }, function (error) {
               //console.log(error);
               console.log(dreamfactory.processErrors(error));
            });


//logout
 dreamfactory.user.logout().then(function(){
           //user logged out
        });

```
