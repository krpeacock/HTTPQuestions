## HTTP Questions

__URLs__

* Name all of the parts of the url that you can remember.  In your own words describe what they do. 

```
There's the protocol, domain, path, port, queries, and anchors. 
    The protocol specifies what kind of document the browser is looking for.
    The domain is the "name" we use to look up ip addresses. 
    The path directs us to the specific content we're looking for. 
    The port allows servers to potentially listen to multiple types of requests.
    Queries are useful for providing the server with more specific information that you want it to display.
    Anchors allow the page to scroll to a certain element or piece of content.  
```
 
* Name the pieces of the following urls:
	* `https://www.google.com/`
	
	```
	Protocol and Domain
	```
	* `https://workbook.galvanize.com/cohorts/41/learning_experiences/367`
	
	```
	Protocol, Domain, Path
	```
	* `http://locahost:5000/animals/puppies?onlycute=1&size=medium#firstpuppy`
	
	```
	Protocol, Domain, Port, Path, Query(onlycute - medium), anchor
	```
	* `https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_Client_Error`
	
	```
	protocol, domain, path, anchor
	```
* Can a server use more than 1 port?

```
Totally. For example, a server can handle both http and https on different ports.	
```

* Why is https different than http?

```
Https is a secure protocol that encrypts data while it is en route between the client and the server. Very important for any site that handles post requests.
```

* How does a server interpret the following url's query paramter.  What data structure does it create on the server?

```
http://locahost:5000/animals?puppies=fido&puppies=max&puppies=moxie
```

```
The server takes the query parameter as a series of key-value pairs. It can create several types of data structures, commonly as a JSON string.
```

__HTTP Request/Response__

* Name at least 4 http verbs

```
Post, Get, Put, Delete
```

* What is each verb useful for in your own words

```
Post sends new information for the server to process in existing resource. Get retrieves information to be used by the client's browser. Put is useful to update existing resources with new information, and is idempotent. Delete is the simplest way to remove an object once you know its id.
```

* What does idempotent mean?

```
An idempotent function is one that can be called repeatedly and will always produce the same result without generating problems.  Idempotetent operations are called "safe".
```

* Name the 5 http status code ranges.  What are they used for in general?
* If a server returns a http status code of 301 and a location of `https://www.google.com/`, what does the browser do?

```
100's -- Everything is okay
    200's -- Some form of success
    300's -- You're in the wrong place for what you're looking for.
    400's -- Resource wasn't found
    500's -- There was a server error
```

* For the following HTTP headers, decide if the following header is used for requests, responses or both:
	* Accept
	* Content-type
	* User-agent
	* Set-cookies
	* Cache-control
	* Cookie
	
```
	Accept: Req && Res
    Content-Type: Req && Res
    User-Agent: Req only
    Set-cookies: Res only
    Cache-control: Res only
    Cookie: Req && Res
```
* Is the following a http request or response?  How do you know for each?

```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Vary: Accept
Content-Type: text/html; charset=utf-8
Content-Length: 722
ETag: W/"2d2-Wu0We9N5g35FXWY+gOATLA"
Date: Tue, 08 Mar 2016 20:37:11 GMT
Connection: keep-alive

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="/style.css">
    <title>Student Roster</title>
  </head>
  <body>
    <main>
      <h1>Student Roster</h1>
      
        <section>
          <h3>Daenerys Targaryen</h3>
          <span>Student Id: nys8fbohl</span>
          <h4>Hobby: Motherhood</h4>
          <img src="https://i.imgur.com/KlycRG5.jpg" alt="Daenerys Targaryen" />
        </section>
      
        <section>
          <h3>Tyrion Lannister</h3>
          <span>Student Id: njehukbohe</span>
          <h4>Hobby: Traveling</h4>
          <img src="https://i.imgur.com/fFMusdC.png" alt="Tyrion Lannister" />
        </section>
      
    </main>
  </body>
</html>
```
```
This is a response. I can tell because it returned an html page in its body.

```

```
DELETE /students/n1vmyrw3x HTTP/1.1
Host: g22-students.herokuapp.com
Accept: application/json
Cache-Control: no-cache
Postman-Token: 0041e3c3-efdb-f0c3-b2f4-2d79f6d0f44b
```

```
The second is a delete request. Delete is an http verb used to communicate from the client toward the server, and as far as I know it always is used in requests.
```

__JSON__

* Describe what JSON is.  What is it used for.

```
JSON is a storage protocol designed to communicate between servers and browsers, and is a particularly friendly format for javascript. It's used to store information to create more dynamic web content than simple static html pages.
```

* Convert the following map into a javascript object then console log the age.

```
{ "company" : "Github", "age": 7, "categories" : "Services,Internet,Software"}
```

```
var json = { "company" : "Github", "age": 7, "categories" : "Services,Internet,Software"};

console.log(json.age);
```
* Convert the following to a javascript object.  Console log each company name.

```
{ "Companies":[ { "company": "Github", "age": 7, "categories": "Services,Internet,Software"},
              { "company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},
              { "company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},
              { "company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web Hosting"}
            ]
}
```

```
parsed = JSON.parse('{ "Companies":[ { "company": "Github", "age": 7, "categories": "Services,Internet,Software"},{ "company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},{ "company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},{ "company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web Hosting"}]}');

parsed.Companies.forEach(function(company){
  console.log(company.age)
});
```
* The following is javascript.  Convert the object to a string and console log it.

```
var myObj = {
  company: "Galvanize",
  age: 3,
  categories: "Education"
};
```

```
console.log(JSON.stringify(myObj))
```
__MISC__

* Describe what DNS is.

```
The Domain Name System is a large resource dedicated to converting url addresses into data, directing browsers to the correct ip address where the website is hosted.
```
* In the terminal, type `man curl`.  Look at the man page for curl.  What do the following flags do? `-v`, `-X`.  (Hint: to search for a string, type `/` then the text you want, then enter.  To quit the man page, type `q`).

```
-v tells the curl protocol to be more verbose, while -X specifies a custom request method to use instead of GET, HEAD, POST, or so on.
```
* What is TCP/IP?  How does it interact with HTTP?

```
TCP/IP is the lower-level transfer comminications protocol that http uses to send packets of information safely over the internet and to stitch them back together on the other end.
```

* Does HTTP break the data that is being sent into small packets?  If not, what protocol is responsible for it?


```
I guess I jumped the gun there. No, HTTP isn't responsible for breaking the data up, that's what TCP does. HTTP is there for all the fancy stuff that happens to structure requests and interpret responses  that TCP/IP transmits. 
```

