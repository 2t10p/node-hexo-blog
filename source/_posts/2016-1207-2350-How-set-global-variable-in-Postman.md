---
title: How set global variable in Postman
date: 2016-12-07 23:48:47
tags: [Postman]
---

when you useing postman to cook your api,
some time you need a variable to keep for next api.


example :
api create a new data and return id,
you wanna keep this id for update,
delete api to use.


add this code at postman's tab

    //take response data
    var jsonData = JSON.parse(responseBody);
    //set variable
    postman.setEnvironmentVariable("acy_guid", jsonData.data.acy_guid);



{% asset_img 1.png "after send add request, set guid to variable " %}


{% asset_img 1.png "use this variable in update body" %}


