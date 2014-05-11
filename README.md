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

//GET EVERY SERVICE
dreamfactory.buildAll();
//GET A FEW
dreamfactory.build(['user', 'db', 'system']);
//GET ONE
dreamfactory.build('user');
//LISTEN FOR THE LAST RESOURCE YOU CALLED:
//LISTEN FOR THE RESOURCE YOU WANT TO USE IF YOU DID NOT BUILD ALL

//USE if you included system or are using buildAll


$(document).on("api:system:ready", function () {
//your code here
};

    var body ={email : $("#email").val(), password : $("#password").val()};
        dreamfactory.user.login(body)
            .then(function (response) {
            //set session token for upcoming calls
               window.dreamfactory.SESSION_TOKEN = response.session_id;
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
<br/>
Check out your SDK Docs on your DSP for all methods and required fields.
