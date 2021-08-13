<h1> Spring's Reactive Restful Web Application </h1>

Base of Spring tutorial.

<h2> Architecture </h2>

* Client : Receive the message.
	User -> Client

* Router : Receive the URI request and transmit it to the Handler who returns an Object.
	User <- Router <- Handler.

