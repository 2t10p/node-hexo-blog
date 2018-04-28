---
title: Postman - validate your api response array data use chai js
date: 2018-04-27 23:30:00
updated: 2018-04-27 23:30:00
tags: [postman]
---

Chai is a BDD / TDD assertion library ,
that let you can write readable js test,
like this :

```
expect(2).to.equal(2); 
expect('foo').to.have.lengthOf(3); /
expect(resJson.total_count).to.be.an('number');
expect(resJson.data.length).to.be.above(0);
```
and postman support this library,
so here is a sample test script,
that will validate :
1. important column not null
2. iterator array check have data 

<!--more-->

{% asset_img 1.png "api test demo image" %}

here is the code

```

pm.test("response data not null", function () {
    var jsonData = pm.response.json();

    pm.expect(jsonData.page).to.be.an('number');
    pm.expect(jsonData.per_page).to.be.an('number');
    pm.expect(jsonData.total_count).to.be.an('number');
    pm.expect(jsonData.data.length).to.be.above(0);

});

pm.test("response data have id", function () {
    var jsonData = pm.response.json();

    jsonData.data.forEach(function(element) {
        pm.expect(element.id).to.be.an('string');
    });

    if (jsonData.data.length > 0) {
        pm.environment.set("video_id", jsonData.data[0].id);
    }
});
```
