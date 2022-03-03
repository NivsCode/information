Introduction
Identifier design with URLs

# Why APIs?
- service oriented architecture principles
- Future-proof, ensuring lesser rewrite
- Multiple front-end support
- Can be used internally and externally
- Set up cost + configuration are extra steps to the process but DRF removes the painpoints

# How it works
Step1: The browser needs to find the desired server on the internet
Step2: It converts the domain name (google.com) into [IP address]() with DNS (Domain name service)
Step3: It sets up a consistent connection with the desired server with TCP (Transmission Control Protocol) with 3 way handshake
	Step3.1: The client sends a [SYN]() asking to establish a connection
	Step3.2: The server responds with a [SYN-ACK]() and passes a connection param
	Step3.3: The clients and [ACK]() to confirm the connection.
**The connection is set up.**

# RESTful API
- is stateless like HTTP
- supports common HTTP verbs (GET, POST, etc.)
- returns data in either JSON or XML format

Format: `URL = scheme "://" authority "/" path [ "?" query ] [ "#" fragment ]`

# URL terminology
- **Scheme**: Communicates how to access resources at the location. (http, https, ftp,  smtp)
- **Host name / Authority**: The name of the site
- **Path(Optional)**:
- **Query:**
- **Fragment:**

# URL Format
- A trailing forward slash should not be included in URLs
- Hypens are preferred and makes url more readable. Underscores are bad news.
- Lowercase letters should be preferred in URL patterns.
- File extensions are not to be included in the URL, it needs to be sent via `content-type` header.

# URL Authority
- Consistent subdomain names should be used for APIs
- Consistent subdomain names should be used for your client developer portal
`api.soccer.restapi.org`  or `developer.soccer.restapi.org` (for dev portal)

# Resource modeling
- The URL path shoild convey a rest API's resource model, with each '/' separated path segment corresponding to a unique resource within a the model's hierarchy. eg: `phones/moto/year/2010/model/exp`

# Resource Archetypes
- The RA helps us consistently communicate the structures and behaviours that are commonly found in REST API designs. A REST API is composed of four distinct resource archetypes: **document, collection, store, and the controller.**
- **Document Archetype (GET + CREATE)**:  A document state rep. includes both fields with values and links to other related resources. With it's fundamental fiels and linked based structure, The document type is conceptiual **base archetype** of the other resource archetypes. They have a root resource, called **docroot** often the entry point, `api.soccer.restapi.org`.
- **Collection Archetype(INDEX)**: A collection resource is a server managed directory of resources. This handles the creation and urls of each contained archetype. The url is a plural form of the resource name.
- **Store Archetype(PUT + PATCH)**: A store is a client-managed resource repo. A store resource lets an API client put resources in, get them back out and decide when to delete them. On their own, stores do not create new resource. Each stored resource has a URL that was chosen by a client when it was initially put into the store. eg: PUT and PATCH requests.
- **Controller archetype(POST)**: A controller resource models a procedural concept. REST API relies on this to persom application specific actions that cannot be logically mapped to one of the standard methods. This doesn't fit into any of CRUD activities.

 # URL Path design
 

Interaction design with HTTP
Metadata design
Representational design
Client design


# Tags
#incomplete 