
# Homework 5
### 1 – What are Authentication and Authorization ?
Authentication is the process of authenticating a user to access any resource.Authentication technology provides access control for systems by checking that a user's credentials match those in the database.
Authorization, on the other hand, defines the powers of the authenticated user on the resource they want to access. For example, customers cannot enter places where only personnel can enter.
### 2 - What is Hashing in Spring Security ?
Hashing is the process of producing a fixed size output with the help of a hash function from different sizes of inputs.Hashing is a one way encryption method and hash algorithms are deterministic. That is, as long as the input does not change, the same hash output is always taken.Hashing is the method used to securely store our passwords in the database. Because it is one-sided, even if the database is attacked, the passwords cannot be recovered. But passwords can be found by comparing the hash values of possible passwords with our hash values.Dictionary attack and Brute force attack can be given as an example.Among the two most used algorithms for hashing, the SHA-256 hashing algorithm can produce 256-bit outputs, while MD5 produces 128-bit outputs.
### 3 - What is Salting and why do we use the process of Salting ?
Hashing is the method used to securely store our passwords in the database, and because they are one-sided, they are irreversible. But since users choose simple, memorable passwords, there are some attacks like Dictionary, Brute Force that make hash comparisons by trying the probabilities of these hashed passwords.Salting is the hashing of passwords by adding a random text called salt to the beginning or end of the password before hashing it.In this way, the hashes of the passwords of users who have chosen the same password are converted to a completely different text each time.
### 4 -  What is “intercept-url” pattern ?
The intercept-url element defines a pattern which is matched against the URLs of incoming requests using an ant path style syntax.The access attribute defines the access requirements for requests matching the given pattern.
```
<http>
    <intercept-url pattern="/admin/*" access="ROLE_ADMIN"/>
</http>
```
### 5 - What do you mean by session management in Spring Security ?
Session is a state management where server-based users information is kept and is used for data storage.The data stored in Sessions can be accessed from all pages in the site.Session management manages sessions between the web application and the users. 
Spring security use two options to control the HTTP session functionalities which are *SessionManagementFilter* and *SessionAuthneticationStrategy*.
These helps spring security to manage these:
1. Session Timeout detection and handling.
2. Concurrent sessions (how many sessions an authenticated user may have open concurrently).
3. Session-fixation – handle the session
### 6 – Why we need Exception Handling ?
Exception runtime, that is, the errors that occur while the application is running. Some of these errors can be tolerated, while others cause the application to stop completely.Thanks to Exception handling, we ensure that the normal, desired flow of the program is preserved even when unexpected events occur.If Java exceptions are not handled, programs may crash or requests may fail.
### 7 - Explain what is AuthenticationManager in Spring security ?
Authentication is the process of authenticating a user to access any resource and Authentication Manager is the core for the Spring security authentication process.It is an interface with one method inside.
It is an interface with a method inside. And this method can do one of 3 things which are :
1. Return an Authentication (normally with authenticated=true) if it can verify its a valid input.
2. Throw an AuthenticationException if it understand it is not a valid input.(Runtime exception)
3. Return null if it cannot decide.
### 8 - What is Spring Security Filter Chain ?
In web applications, Spring security is managed through servlet filters. Servlet filters passes through the filters the incoming request before it reaches the actual resource. (e.g. Spring controller) and filters are executing in a specific order .Authentication and authorization process in Spring Security project are handled with filters technology.Spring Security maintains a filter chain internally where each of the filters has a particular responsibility and filters are added or removed from the configuration depending on which services are required.
The order that filters are defined in the chain is very important.For example, the order of the first four filters is as follows:
1. *ChannelProcessingFilter:* It might need to redirect to a different protocol
2. *SecurityContextPersistenceFilter:* Populates the SecurityContextHolder with information got from the configured.
3. *ConcurrentSessionFilter:* Filter for handling concurrent session
4. *UsernamePasswordAuthenticationFilter:* Looks for the username and password in the request and tries to authenticate if found these parameters in the request.
### 9 – What are the differences between OAuth2 and  JWT ?
The main differences between them are: 
* While JWT is just a token format, OAuth 2.0 is a protocol.
* OAuth can use either JWT as a token format or access token which is a bearer token.
### 10 - What is method security and why do we need it ?
The method level Spring security allows us to add security to individual methods within our service layer.Spring method security allows us to support / add authorization supports at the method level.So we can define which roles can access which methods.There are different options to apply spring method security like @Secured annotaion, @PreAuthorize and @PostAuthorize Annotations. 
### 11 – What Proxy means and how and where can be used ?
A proxy is an intermediate server used while accessing the Internet.When we visit a website directly, we send a web request containing information about us, such as our location, browser fingerprints, IP address. In response to this sent data, the web resource provides us with the content we request.Proxies can hide or modify our web request data and filter website content preventing we from receiving unwanted information.As a result of the requests we make using a proxy server, our IP address is stored.Therefore, it is possible to get rid of online monitoring thanks to the proxy known as the proxy server.From time to time, governments, companies and institutions we work with prohibit access to some websites. By using a proxy server, we can continue to access them at any time with our IP address hidden.As there are websites where we can get paid or free Proxy Server service, we can also use proxy by adjusting the proxy settings of our browsers.
### 12 – What is Wrapper Class and where can be used ?
Wrapper classes provide a way to use primitive data types like int,boolean as objects and they are of reference type.We can't always do everything using only primitive types. There are situations where we need objects.
* If we want to use primitive data types as an object, we should use wrapper classes.
* Data structures in the Collection framework such as ArrayList, LinkedList,Stack store only the objects and not the primitive types.
* In java.util package we can only implement with classes and we can use wrapper classes that way.
* We can use it to create a necessary object for multithreading synchronization.
### 13 – What is SSL ? What is TLS ? What is the difference ? How can we use them ?
*SSL (Secure Sockets Layer)* is a security layer that uses port 443 by default, enabling data exchange between the client and the server in an encrypted / secure manner.
*TLS (Transport Layer Security)* is a security layer that was developed after SSL and made more advanced and secure than SSL, providing data privacy just like SSL.
*The differences between them:*
* At the security point, both SSL and TLS offer almost equal security.However, while SSL starts the process with security and switches directly to secure data communication, TLS sends an insecure boot message to the server and if the handshake does not occur, the connection is not established.
* TLS transmits the certificate authentication message in handshake, while SSL transmits the authentication message in a more complex process.
* If the client does not have an SSL certificate, the TLS protocol may pass a "No Certificate" message. In SSL, there is no need for a separate notification.
### 14 - Why do you need the intercept-url ?
With the intercept-url, we define the URLs that we want to manage, restrict and authorize access to. We create a more secure environment as we define which roles can access which urls. Thus, for example, we prevent a customer from accessing the admin page.
```
<http>
    <intercept-url pattern="/admin/*" access="ROLE_ADMIN"/>
</http>
```