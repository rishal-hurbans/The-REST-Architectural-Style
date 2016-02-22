#Robust REST Architectures

In this era of digital technology, we find ourselves developing software that is required to be shared and utilized as far as possible in a manner that is as concise as possible. This is not a new concept, however, the need to refine and better these integrations have become more and more prevalent due to high demand for interoperability between different pieces of software.

An emerging trend is the use of RESTful APIs for both exposing data resources as well as consuming data resources from other sources. Within the development community, there exists some misunderstandings around what REST, and RESTful actually is. It is important to understand that REST is not a protocol, and it’s not a standard. REST is simply an architectural style achieved by combining a number of different well-known architectures.

##Architectures
There exist commonly used architectures in most distributed web-based software. It is important to understand the purpose of these patterns and where it is applicable.

###Client-Server

![Architectures - Client-Server](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-client_server.jpg)

The client-server architecture is a fairly well-known and widely used architecture. Most network based applications work in this manner. The architecture consists of a server that acts as a central point that one or many clients may interact with. The idea behind a client-server architecture is that that the server does the heavy lifting and orchestration required, whilst the client consumes the rich data and functionality by interacting with the server. When these computers communicate with each other, there’s a clear need for a common protocol that is understood and supported by both computers. The commonality required is the message format. Imagine the protocol being a channel of communication between two people such as speech which is common between the two, and the message format being the language that is understood between them.

###Layered

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-layered.jpg)

The layered architecture is utilized for a number of different factors. A layered approach allows developers to separate concerns and loosely couple components that interact with each other. The advantage of this approach when implemented optimally is that layers may change independently without impacting the rest of the application. There are also cases where a layered architecture may consist of a layer that is shared across multiple other layers. An example of this is a shared domain that is utilized throughout the application. The layered architecture implies that the various layers reside within the same application container.

###Tiered

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-tiered.jpg)

The tiered architecture is very similar to the layered architecture. It consists of the same pattern and characteristics. The terminology “tier” is mapped to the terminology “layer”. The key difference between a layered architecture and a tiered architecture is that each tier resides on a different physical or virtual environment. This implies that tiers that interact with each other consist of different deployments and environments.

###Stateless

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-stateless.jpg)

A vast majority of web applications make use of server-side managed session to keep track of a specific client, these sessions are often used for auth, keeping track of context, and storing meta data in memory that may be useful for managing the user’s activity. This make scaling difficult as additional technologies and development is required to create session management servers in a clustered environment. The stateless architecture removes the need for the server to create and hold sessions. In a stateless architecture, the state is managed by the client via some mechanism such as tokens, header data, etc. that are passed back and forth.

###Cacheable

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-cacheable.jpg)

The cacheable architecture is the concept of cleverly caching data that is used often, and changed infrequently. Caching may occur in places like the client browser, and a caching server. Caching mechanisms are expected to be smart enough to server cached data or resources until that piece of data or resource changes for the client requesting it. One of the advantage of caching is a reduced load on the network, this translates to reduction of unnecessary requests, lower data usage, and a more optimal application.

###Uniform Interface

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/architecture-uniform_interface.jpg)

The concept of a uniform interface includes creating a standard method of interacting with a system. The uniform interface architecture also promotes abstraction of the implementation from the interface definition. This allows for clients to interact with all services in the same way, using a standard protocol and message format with a well defined set of operations.

##Overview of HTTP
HTTP (Hypertext Transfer Protocol) is an application protocol for distributed hypermedia information systems. HTTP is widely used in networked computing, it is hugely prevalent in how the internet works. This section describes the basic concepts of the protocol.

###URLs (Universal Resource Locators)

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/http-urls.jpg)

HTTP URLs consist of several components including:
* Protocol: The protocol that the request is being made on. Typically HTTP or HTTPS. HTTPS is a secured version of HTTP. It requires a certificate to validate the authenticity of the server in relation to the domain.
* Domain: The domain includes the address of the server. Typically this is represented by a sub-domain, a domain name, and a top level domain. In the example www.prolificidea.com, www is the sub-domain, this is the default sub-domain for the world wide web. prolificidea.com is the registered domain name.
* Port: Different applications can communicate via different ports on a computer. Typically, port 80 is the default port for HTTP web application servers. 
* Resource: The resource being requested by the client. This could be any media including virtual objects. An example is the /user resource gives the client data about users.
* Query: Queries are used to provide parameters for the resource being requested. An example is the /user?name=bob specifies that the client wants a user with the name "bob".

###Verbs
HTTP provides several well known, widely used verbs for operations on resources, including:
* GET: Read data or resources. This verb should never be used to modify data.
* POST: Create data or resource. This verb should be used to create new data.
* PUT: Update data or resources. This verb should work on existing resources. The same PUT request should be able to be repeated with the same end result.
* DELETE: Delete data or resources. Similarly to PUT, a DELETE request should be able to be repeated with the same end result.

HTTP provides operations that are less known, but still useful:
* PATCH: Patch is used to update data or resources similarly to PUT. The difference is that PATCH requests should be used to update parts of a resource instead of updating a resource in its entirety. PATCH reduces the need to update complete objects by updating only the properties that require an update.
* HEAD: Head is similar to GET requests, however, the request should not contain a body. This request is useful to validate data or resources.
* TRACE: Trace invokes a remote, application-layer, loop-back. The TRACE request reflects the message that the final recipient server receives. This is useful to determine the final message after a request is proxied along a chain of servers. The TRACE request is useful for diagnostics on applications.

###Status Codes
* 1xx: Information. The request was received by the server, continue processing.
* 2xx: Successful. The request was received, understood, accepted, and processed by the server. 
* 3xx: Redirection. Additional action is required to complete the request.
* 4xx: Client Error. There was a problem with the request received by the server.
* 5xx: Server Error. The request was received, understood, and accepted by the server, however, a server error occurred in processing the request.

Many applications tend to use the 200 OK status code for all responses to the client. In the case of errors or additional information, additional information is stored in the response message body. This should be avoided. The HTTP status codes should be leveraged and used correctly in the given context. An example being, a POST request should yield a 201 Created status code in the response rather than just a 200 OK.

###HTTP/2

![Architectures - Layered](https://raw.githubusercontent.com/rishal-hurbans/Robust-REST-Architectures/master/images/http-http2.jpg)

HTTP/2 is a new faster version of HTTP. The aim of HTTP/2 is to make applications quicker and more robust. HTTP/2 was spawned from Google's SPDY protocol (SPDY is not an acronym, Google just thought is sounded cool). The biggest change is the method of transporting data. Data is being transported using binary rather than using text as HTTP/1 does. Binary data is smaller than text and therefore makes it more efficiently transported over a network. Nothing changes in terms of the semantics of the protocol. The same operations and standards exist when using it. This change shouldn't affect the average web application developer. Developers that build browsers, application servers, or applications that work directly with the network layer will be impacted by the changes of HTTP/2.
