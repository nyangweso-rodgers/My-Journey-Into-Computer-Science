# WebHooks

## Table Of Contents
- [Introduction to WebHooks](#Introduction-to-WebHooks)
- [Webhooks vs APIs](#Webhooks-vs-APIs)
- [How Webhooks Work](#How-Webhooks-Work)
- [When to use Webhhoks](#When-to-use-Webhhoks)
- [Cons Of WebHooks](#Cons-Of-WebHooks)
- [How Can We Secure Webhooks?](#How-Can-We-Secure-Webhooks?)

- [Further Reading]()
    - [Webhooks Explained](https://www.baeldung.com/cs/webhooks-polling-real-time-information)


# Introduction to WebHooks
* __Webhooks__ allow third-party services to send data to an application in real-time. __Webhooks__ are another way apps communicate and exchange data, just like __APIs__, but a little different. i.e., there is no __request__ and __response__ system ,just an __event__ and __automatic response__.

* To set up a __webhook__, you register with a __webhook provider__ and provide a destination URL where the requests will be sent. 

# Webhooks vs APIs
* __APIs__ and __Webhooks__ facilitate data transfer between two applications, but in different ways, giving them slightly different purposes.

* __APIs__ are intermediary software that enables two programs to communicate with each other. __APIs__ use __HTTP__ to transfer data between _client_ and _server_ bi-directionally in a request and response cycle. __Webhooks__ only allow one-way communication between client and server, and a specified event triggers this communication. 

* Using __Webhooks__ involves setting up an __HTTP POST Request__ on the sending end and registering a URL on the receiving end to accept the data. The main difference is that __APIs__ need a request to return a response, but __Webhooks__ do not. _This makes Webhooks less resource-intensive because, unlike APIs, they do not need to poll for new data constantly._

* A client can use an __API__ to _create_, _read_, _update_ and _delete_ (CRUD) data on a website. __Webhooks__, however, are set up to listen for specific events that initiate a planned response. They do not allow a user to perform CRUD operations.

# How Webhooks Work
When a specified event occurs, a __webhook__ makes an __HTTP request__ to a designated __URL__. This allows you to push data to your application the moment a particular event happens. i.e.,
1. A set event or action triggers webhooks
2. Once triggered, the server sends and HTTP POST response

# When to use Webhhoks
* __Webhooks__ are commonly used when real-time data is required, but the data changes relatively infrequently. Instead of sending repeated __API requests__ to get live data, a __webhook__ can be triggered every time there is an update. This will ensure you have accurate data without having to make frequent __API requests__, which can be costly or use a lot of bandwidth.

* __Webhooks__ are also used to created notifications that are triggered by specific  events, making them very common for e-commerce, communication, social media and other platforms.


# Cons Of WebHooks
* __WebHooks__ can be __resource intensive__ to both the client and the server. If the client needs to notify many servers that an event has occurred, and a server needs to listen to a great deal of clients notifying of this change, you can very quickly run into a situation where your network grows uncontrollably. While HTTP does scale quite well, this is a definite negative to consider.

# How Can We Secure Webhooks?
* __Webhooks__ send data to the __webhook URL__ in the _client application_. Further, the __webhook URL__ is available to the public, which means that other than the __webhook server__, malicious users can also send fake data to the client application. To increase the security of the connection, we can:
    * Force HTTPS connection between the server and the client.
    * The server can only hash the message with a secret key held by the client and the server. This way, once the client receives the payload and the hash output, it can verify if the server actually sends the payload or not. To verify, the client uses the same hash function again with the same private key and checks if the output matches the one sent by the server.