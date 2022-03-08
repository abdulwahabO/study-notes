## REST APIs Overview

REST (Representational State Transfer) is an architectural style that defines a set of constraints for building applications on the web. 

_Web services_ are purpose-built _web servers_ that support an application. Clients communicate to web services using a Application Programming Interface(API), i.e., a set of functions and data formats used to exchange information. 

 A _web API_ is the point of contact between a client and a web service. A web API that uses the REST architectural style is called a _REST API_. A web service is said to be _RESTful_ if it exposes a REST API.

The constraints defined by REST are:

1. **Client-Server**: This constraints calls for separation of concerns between client and server. This allows client and server to evolve independently. Client and server can be developed and deployed using different tech stacks as long as they conform to a uniform interface.

2. **Uniform Interface**: 

3. **Cacheable**: This constraint requires the server to explicitly state if a response is cacheable and for how long.

4. **Stateless**: This constraint dictates that a server should not store the state of any of it's clients. 

5. **Layered**:

6 **Code Transfer(optional)**: 


_TODO: Read REST API Design Rulebook_ 

## HTTP Headers

`Content-Type`: Tells client/server the format of the response/request body. The value of this header is known as media type. It's format is `type/subtype; [paramKey=paramValue]`E.g., `application/json`, `text/html; charset=utf8`. Vendor-specific media types convey a message to programs that understand them. Theyhave their subtypes beginning with `vnd.`. E.g. `application/vnd.ms-excel`

`Content-Length`: Tells client/server the size(in bytes) of the response/request boy. This is important in responses because the client can compare this to the actual size of the data in the body to determine that the correct number of bytes were downloaded.

`Last-Modified`: This is used in responses to tell clients the last time a resource was modified. 

`Cache-Control`: This is used in responses to encourage or discourage caching. It can include a TTL value(in seconds) or a `no-cache` instruction.