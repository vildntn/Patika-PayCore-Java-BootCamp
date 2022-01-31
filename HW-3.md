
# HOMEWORK- 3
### 1 – SOAP vs Restful ?
**SOAP (Simple Object Access Protocol)** is a communication protocol used in distributed applications and communication of various web services.
**REST (Representational State Transfer)** is an architecture that enables fast and easy communication between client and server, thanks to the HTTP protocol. In Rest architecture, instead of communicating via methods such as GetProduct, GetCategory in SOAP, all information is presented over URIs.
**Restful web services**, on the other hand, are lightweight, extensible and simple services developed based on the REST architecture. The purpose of Restful services is to be able to perform the data flow between the client and the server independently of the platform.
**The differences between them:**
*	While Restful services can work in many formats such as JSON, HTML, XML as a response type, SOAP obliges XML-based use.
*	Soap has to use a W3C standard WSDL language to generate its requests. In Rest this is not needed, requests can be created via the URI.
*	It uses REST simple HTTP method for caching request. SOAP makes complicated XML requests for this process.
*	HTTP is required in REST to ensure communication between server and client, while SOAP can also support protocols such as TCP/IP STMP.
### 2 - Difference between acceptance test and functional test ?
**Test**; It is checking whether a piece of software or software coded to achieve a goal achieves the intended goal. Test types are examined under 4 headings such as Unit Test, Integration Test, Functional Test, Acceptance Test.

 **Here are the differences between them:**
*	Functional testing aims to make result-oriented inferences while testing the operation of a feature. The goal is to test whether the function works.
*	Acceptance testing is considered end-user testing. The end user knows nothing about the project and tries to use the project for certain purposes by himself. It is tested whether the system meets the desired needs.
*	While Acceptance testing is last and final step perform, Functional testing is performed before acceptance testing.
### 3 - What is Mocking ?
Mocking is the creation of fake versions of the objects we depend on while testing the code we write. The reason we do this is to actually do the testing at the unit level when doing unit testing. For example, the scenario that we are going to test may depend on an external service or depend on a database operation. We need to test our test case without using these dependencies. This is where mock objects come into play. Here are the some mock libraries available in java: Mockito,JMock,PowerMock.
**The advantages of mocking:**
*	Since unit test tests a unit, it ensures that the dependencies connected to this flow do not break the test flow while testing the flow there.
*	While performing unit testing, it allows us to direct the test in the scenario we want.
*	It allows us to get rid of the slowness of complex objects. For example, a database operation can take a very long time.
### 4 - What is a reasonable code coverage % for unit tests (and why) ?
Code coverage  shows which lines of the code were  being executed by the tests.Code coverage of 70-80% is a reasonable goal for unit test of most projects with most coverage metrics.The higher the code coverage, the more robust and reliable our project is, and how quickly it can adapt to changes.
### 5 – HTTP/POST vs HTTP/PUT ?
HTTP is a protocol that allows us to communicate between the browser and the server, and it has some methods.
POST and PUT are both HTTP methods used to send data to the server. POST is only used to send data to a specific resource and what to do with the data is up to the server. In PUT, the same resource is accessed with the same address and if there is content, it is replaced with the incoming data, if there is no content, new content is created.
### 6 - What are the Safe and Unsafe methods of HTTP ?
**Safe method** means that if a method is logically read-only and the requests we make with this method do not cause any damage or change to the server. While all safe methods are also idempotent, not all idempotent methods are safe. For example, PUT and DELETE are both idempotent but unsafe.
**Likewise Unsafe method** means that if the requests we make with some method cause any changes on the server.We are adding information to or removing information from our database with unsafe methods.
*	A few http methods such as Get, Head or Options are safe methods.
*	Put,Delete, Post, Patch methods are unsafe methods.
### 7 - How does HTTP Basic Authentication work ?
Among the HTTP Authentication methods, the most popular ones are Basic, Digest, Bearer and NTLM authentication mechanisms. It is used for server-to-server authentication.It is a method for the client to provide a username and password when making a request.
**Basic Authentication Stages:**
1.	Browser (Client) sends HTTP Get request to page using Basic Authentication.
2.	The server responds with "401 Unauthorized WWW-Authenticate : Basic .This actually means send me your user + password.
3.	When the client browser encounters this header, it creates the window with an input field for username and password.
4.	The client sends a Get request again, but this time it encodes as Authorization: Basic Base64, and sends the user: password information. The browser will encode it like this.
```
	Coding: Base64Encode(‘admin:12345678’)
	Result: YWRtaW46MTIzNDU=
```
5.	The client browser then sends it by adding this Base64 value inside the Authorization header. Like:  **Authorization : Basic YWRtaW46MTIzNDU=**
6.  The server sends HTTP status code 200 with the requested data, or it sends 401 status code.
### 8 - Define RestTemplate in Spring ?
RestTemplate is the default class in Spring library to handle synchronous HTTP requests on client side. RestTemplate is thread-safe. RestTemplate is built on the servlet structure. So it follows thread-per-request approach. Performance problems arise as the application will consume the thread-pool. It went into maintenance mode with Spring 5. It will probably not be supported in future versions.
### 9 – What is idempotant and which HTTP methods are idempotant ?
If a method is called once and the result is the same when it is called more than once, it is called an idempotent method. In other words, an idempotent method should not have any side-effects. 
*	The http methods Get, Delete, Put, Options, Head are idempotent methods. But Post method is not.
*	All safe methods are also idempotent.
**Exemplarily:**
```
/customer/1
{"id":1, name":"Henry", "surname":"Cavil"}
```
**GET**
```
 http://localhost/api/getById/1
 Response: {"id":1, name":"Henry", "surname":"Cavil"}
```
*	It is idempotent because the result will not change no matter how many requests we send for a result with the GET method.

**DELETE**
```
 http://localhost/api/deleteById/1
 Response: "customer has been deleted successfully"
```
*	When we send a request to the server to delete the record with id 1 using the DELETE method, record 1 will be deleted. When we call the relevant request again, no action will be taken because there is no record with an id of 1.
	
### 10 – What is DNS Spoofing ? How to prevent ?
DNS spoofing is cyber attacks in which hackers redirect web traffic to fake web servers and phishing websites. Domain Name System (DNS) is used to translate a domain name to a specific IP address. The DNS cache is a temporary database containing all records of visits to other domains, and each computer has a DNS cache that stores the most recent DNS requests. By gaining access to this DNS cache, attackers replace the real IP address with the IP address of a fake website, allowing users to reach the fake website designed for fraud instead of the real website.
**To prevent:**
*	Set up DNSSEC
*	The data contained in DNS requests and responses should always be encrypted.
*	Perform thorough DNS traffic-filtering
*	DNS cache should be flushed periodically
### 11 – What is content negotiation?
Content Negotiation is a content agreement between client and server. Its purpose is to be able to serve content in different document types with the same URI. In other words, the form of reference is determined by the users. Browsers forward their requests to the server as HTTP Accept Header information.
**Exemplarily:**
```
GET http://localhost:8080/employee
Accept: application/json
```
Here, the client makes a request to the address /employee and JSON is requested as the response format.
### 12 – What is statelessness in RESTful Web Services?
Rest services have advantages such as platform independent, language independent, working over HTTP as well as some limitations like statelessness. The fact that REST is stateless means that the server does not keep information about the client, such as session. Every request made by the client carries the necessary information for the server to give a response, that is, all kinds of state are kept by the client, and if needed, it is reported to the server in the request.
**The advantages of statelessness:**
*	Scalibility: Statelessness between requests simplifies resource management.
*	Visibility: With a single request, understand the purpose of the request.
### 13 - What is CSRF attack? How to prevent ?
CSRF (Cross-site Request Forgery) it is the execution of transactions against the requests of the users using the web application. This forgery occurs in uncontrolled systems from which source and how the requests to the application are sent.
**To prevent:**
*	Token information is included in the POST data.
*	Cookies and site data should be cleared regularly.

### 14 - What are the core components of the HTTP request and HTTP response ?
**Http request core components are:**
*	HTTP Version 
*	Request Body 
*	Request Header 
*	URI 
*	Verb 

**Likewise Http response core components are:**
*	HTTP Version 
*	Response Body
*	Response Header 
*	Status/Response Code 
