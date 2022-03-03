1. Basic authentication
		Process:
			- Client makes an HTTP request
			- Server responds with an HTTP response containing 401 status and WWW-Authenticate HTTP header with details on how to authorize
			- Vlient sends creds back via authorization HTTP header
			- Server checks creds and responds with either 200 or 403 status
		Adv/Dis-adv:
			- Simplicity
			- Needs to verify every request. An easier approach would be to verify once and pass a token to announce the user is approved
			- Insecure, hence should be used only over HTTPS
2. Session
	Process:
		- A user enters their log in creds
		- The server verifies the creds are correct and generates a session object that is then stored in DB.
		- The server sends the client a session ID - not the session object itseld - which is stored as a cookie on the browser
		- On all future requests, the session ID is included as an HTTP header and if verified by the db, the request proceeds.
		- Once a user logs out of an application, the session ID is destroyed by both the client and server
		- If the user later logged in again, a new session ID is generated and stored as a cookie on the client.
	Adv/Dis-adv:
		- Stateful approach
		- Challenge to support multiple servers/frond-ends.
		- Cookie sent out for every request, not efficient.
		- Doesn't work accross multiple domains
		- Not adviced to use a session based auth for an API that have multiple front-ends
3. Token
	Process:
		- The client sends a initial user credentials to the server
		- A unique token is generated and then stored by the client as either a cookie or in local storage
		- This token is then passed in the header of each incoming HTTP request and the server uses it to verify whether the user is authenticated (The server doesnt keep a record of the user, only whether a token is valid or not)
	Adv/Dis-adv:
		- Stateless
		- Cookie vs localstorage: Cookies are used for reading server-side information. They are smaller (4kb) in size and automatically sent with each HTTP request. LocalStorage is designed for client-side information. It is much larger (5120 kb) and its contents are not sent by default with each HTTP request.
		- Scalable, token is sharable between multiple frontends
		- Tokens can grow large since it contains session id, user info. Managing size can become a performance issue
		- Django's inbuilt token auth does not support setting tokens to expire, it needs to be added
5. JWT
	Process:
		- An improvement on the token authentication which generates unique client tokens and token expiration.
		- They can either be generated on the server or with a third-party service like Auth0
		- Safer since they are encrypted to send over unsecured HTTP connections
	Adv/Dis-adv:

