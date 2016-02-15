#Robust REST Architectures

In this era of digital technology, we find ourselves developing software that is required to be shared and utilized as far as possible in a manner that is as concise as possible. This is not a new concept, however, the need to refine and better these integrations have become more and more prevalent due to high demand for interoperability between different pieces of software.

An emerging trend is the use of RESTful APIs for both exposing data resources as well as consuming data resources from other sources. Within the development community, there exists some misunderstandings around what REST, and RESTful actually is. It is important to understand that REST is not a protocol, and it’s not a standard. REST is simply an architectural style achieved by combining a number of different well-known architectures.

##Architectures
There exist commonly used architectures in most distributed web-based software. It is important to understand the purpose of these patterns and where it is applicable.

###Client-Server
The client-server architecture is a fairly well-known and widely used architecture. Most network based applications work in this manner. The architecture consists of a server that acts as a central point that one or many clients may interact with. The idea behind a client-server architecture is that that the server does the heavy lifting and orchestration required, whilst the client consumes the rich data and functionality by interacting with the server. When these computers communicate with each other, there’s a clear need for a common protocol that is understood and supported by both computers. The commonality required is the message format. Imagine the protocol being a channel of communication between two people such as speech which is common between the two, and the message format being the language that is understood between them.

###Layered
The layered architecture is utilized for a number of different factors. A layered approach allows developers to separate concerns and loosely couple components that interact with each other. The advantage of this approach when implemented optimally is that layers may change independently without impacting the rest of the application. There are also cases where a layered architecture may consist of a layer that is shared across multiple other layers. An example of this is a shared domain that is utilized throughout the application. The layered architecture implies that the various layers reside within the same application container.

###Tiered
The tiered architecture is very similar to the layered architecture. It consists of the same pattern and characteristics. The terminology “tier” is mapped to the terminology “layer”. The key difference between a layered architecture and a tiered architecture is that each tier resides on a different physical or virtual environment. This implies that tiers that interact with each other consist of different deployments and environments.

###Stateless
A vast majority of web applications make use of server-side managed session to keep track of a specific client, these sessions are often used for auth, keeping track of context, and storing meta data in memory that may be useful for managing the user’s activity. This make scaling difficult as additional technologies and development is required to create session management servers in a clustered environment. The stateless architecture removes the need for the server to create and hold sessions. In a stateless architecture, the state is managed by the client via some mechanism such as tokens, header data, etc. that are passed back and forth.

###Cacheable
The cacheable architecture is the concept of cleverly caching data that is used often, and changed infrequently. Caching may occur in places like the client browser, and a caching server. Caching mechanisms are expected to be smart enough to server cached data or resources until that piece of data or resource changes for the client requesting it. One of the advantage of caching is a reduced load on the network, this translates to reduction of unnecessary requests, lower data usage, and a more optimal application.

###Uniform Interface
The concept of a uniform interface includes creating a standard method of interacting with a system. The uniform interface architecture also promotes abstraction of the implementation from the interface definition. This allows for clients to interact with all services in the same way, using a standard protocol and message format with a well defined set of operations.

##Overview of HTTP
HTTP (Hypertext Transfer Protocol) is an application protocol for distributed hypermedia information systems. This section describes the basic concepts of the protocol.

###URLs (Universal Resource Locators)
HTTP URLs consist of several components including:
* Protocol
* Domain
* Port
* Resource
* Query

###Verbs
HTTP provides several well known, widely used verbs for operations on resources, including:
* GET
* POST
* PUT
* DELETE

HTTP provides operations that are less known, but still useful:
* PATCH
* HEAD
* TRACE
* OPTIONS

###Status Codes
* 1xx: Information. The request was received by the server, continue processing.
* 2xx: Successful. The request was received, understood, accepted, and processed by the server. 
* 3xx: Redirection. Additional action is required to complete request.
* 4xx: Client Error. There was a problem with the request received by the server.
* 5xx: Server Error. The request was received, understood, and accepted by the server, however, a server error occurred in processing it.
