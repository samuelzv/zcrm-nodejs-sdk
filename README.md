**Node JS SDK for Zoho CRM**

**Abstract**

Node SDK is a wrapper for Zoho CRM APIs. Hence invoking a Zoho CRM API from your Node application is just a function call which provide the most appropriate response.

This SDK supports both single user as well as multi user authentication.

**Installation of Node CRM SDK**

Node JS SDK will be installed and a package named 'zcrmsdk' will be created in the installation directory.

>npm install zcrmsdk

Once installed it can be used in the code as below,

>var ZCRMRestClient = require('zcrmsdk')

**API Usage**

**Initialize**

Below snippet has to be called before starting the app

```
var ZCRMRestClient = require('zcrmsdk');

ZCRMRestClient.initialize().then(function(){

    ...

});

```

**Generating access and refresh token from granttoken**

```

ZCRMRestClient.generateAuthTokens(user_identifier,grant_token).then(function(auth_response){

    console.log("access token :"+auth_response.access_token);
    console.log("refresh token :"+auth_response.refresh_token);
    console.log("expires in :"+auth_response.expires_in);

});

```

**Generating access token from refresh token**

This will be handled by sdk itself if the access and refresh token is generated by sdk.Developer need not call this explicitly.

```
ZCRMRestClient.generateAuthTokenfromRefreshToken(user_identifier,grant_token).then(function(auth_response){

    console.log("access token :"+auth_response.access_token);
    console.log("refresh token :"+auth_response.refresh_token);
    console.log("expires in :"+auth_response.expires_in);

});

```

**Sample API Calls** 

```
var input ={};
input.module = "Leads";

var params = {};
params.page = 0;
params.per_page = 5;
input.params = params;

crmclient.API.MODULES.get(input).then(function(response){

    var result = "<html><body><b> Top 5 Leads</b>";
    var data = response.body;
    data = JSON.parse(data);
    data = data.data;
    for (i in data){

        var record = data[i];
        var name = record.Full_Name;
        
        result+="<br><span>"+name+"</span>";

    }

    result+="</body></html>";

})
```

For generating grant token and for detailed description please refer this [link](https://zcms.zohocorp.com/crm/help/developer/server-side-sdks/node-js.html)




