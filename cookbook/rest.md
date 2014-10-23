## Exposing A REST API

Note:  I haven't gone through and tried this yet, but it's on my to-do list.  Here's a bunch of research on how to do REST APIs with Meteor.  Best of luck!  


#### Server Side REST APIs

https://github.com/EventedMind/iron-router/blob/master/lib/server/router.js   
https://github.com/nooitaf/meteor-cfs-public-folder/blob/master/cfs-public-folder.js   


````js
// serve up a virtual library
Router.map(function () {
  this.route("test-page", {path: "test.js", where: "server", action: testAction});
});

var testAction = function() {
  console.log(this.params);
  console.log(this.request);

  this.response.statusCode = 200;
  this.response.setHeader("Content-Type", "application/javascript");
  this.response.end("console.log('hi!');");
};
````

````js
// serve up a single page
Router.map(function () {
  this.route("test-page", {path: "/post", where: "server", action: getPost});
});

var getPost = function() {
  console.log(this.params);
  console.log(this.request);
  var responseBody = "";
  responseBody = JSON.stringify(Posts.find().fetch());

  this.response.statusCode = 200;
  this.response.setHeader("Content-Type", "application/javascript");
  this.response.body(responseBody);
  this.response.end("console.log('hi!');");
};
````



#### References  

**Meteorpedia on six ways to provide REST APIs**  
http://www.meteorpedia.com/read/REST_API

**Meteor REST Collection**  
http://stackoverflow.com/questions/13699126/meteor-rest-collection-api-and-auth  



#### Light Weight REST Api

**RestStop 2**  
https://github.com/BeDifferential/reststop2  

**Meteor - Collection API**    
https://github.com/crazytoad/meteor-collectionapi  


#### REST APIs using GridFS

**HTTP Publish**  
https://github.com/CollectionFS/Meteor-http-publish  

**HTTP Methods**  
https://github.com/CollectionFS/Meteor-http-methods  
