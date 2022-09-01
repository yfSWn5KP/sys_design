---
recall: header
---

### What is HTTP Long-Polling?

1) Client initiates an "update request" to server
1) If the server has an update, then:
   1) The server responds back immediately
1) Else, the server holds the connection open and waits until:
   1) There is an update to reply back with
   2) Or, the connection times out
2) After one of the above has occurred, the client will re-initiate the request cycle


### What are Websockets (WS)?

They are full-duplex, persistent TCP connections that enable bi-directional communication between the client and server.


### How are Websocket Connections established?

The handshake works like this...
 
1) The client sends an HTTP GET request to the server at `ws://<server>/<path>` and includes the following headers:
    ```yaml
    Connection: Upgrade
    Upgrade: websocket
    Sec-WebSocket-Key: <base64-of-client-chosen-nonce>
    ```
    1) (Note that `Upgrade: <protocol>` is a hop-by-hop header)
2) If the server accepts the websocket upgrade, then:
     1) The server responds back with a status code of `101`, i.e. `Switching Protocols`, and includes the following headers:
         ```yaml
         Connection: Upgrade
         Upgrade: websocket
         Sec-WebSocket-Accept: <base64-of-sha1-of-nonce-plus-websocket-guid>
         ```
     2) The client verifies the nonce and the handshake completes with an established websocket connection
3) If the server rejects the websocket upgrade, then:
     1) The server responds back with any status code other than `101`
 
The nonce-check prevents cross-site request forgery (CSRF) attacks.


### What are the 2 Classes of HTTP Headers that determine how the header is Proxied?

1) End-to-End Headers
1) Hop-by-Hop Headers


### What are End-to-End HTTP Headers?

A class of headers that are forwarded to the final recipient, implying:
 
1) They are proxied, unmodified between servers
1) They are included as part of any cache


### What are Hop-by-Hop HTTP Headers?

A class of headers that are only used by the immediate recipient, i.e. single transport-level connection, implying:
 
1) They are stripped and never proxied to the next hop/node
1) They are never cached
 
These headers can only be set via the `Connection` header


### What is the difference between Full-Duplex vs. Half-Duplex vs. Simplex Connections?

Full & Half both allow for bi-directional communication.
 
Full allows for both directions to occur simultaneously, e.g. phones.
 
Half only allows one-way transmission at any given time, e.g. walkie-talkies.
 
Simplex is uni-directional without the ability for the recipient to communicate back.


### What are Server-Sent Events (SSE)?

They are simplex, HTTP/1 connections that enable the server to send to the client (but not vice versa).
 
A client will request an SSE, which will open the long-lived connection and allow the server to stream events.
 
On the client-side, SSEs use the `EventSource` Javascript interface.


### What is the difference in memory-management  between an XHR and an SSE request?

Both requests are HTTP connections.
 
However, the entirety of an XHR result is buffered in memory.
 
Otoh, SSE connections can discard processed event messages.
 

### What are the Pros/Cons of SSEs usage of HTTP/1?

Pros:
* SSE fits in with normal internet traffic, e.g. corporate firewalls should allow it
* It may have wider support, e.g IOT devices
 
Cons:
* HTTP/1 limits browsers to a max of 6 connections per domain
  * An SSE connection consumes 1 of these 6


### What are some Differences between WS and SSE connections?

* WS is bi-directional
  * SSE is uni-directional
* WS is a multiplexed, TCP connection
  * SSE is a simplex HTTP/1 connection
* WS can have difficulties working behind corporate firewalls
  * SSE is just HTTP traffic
* WS can have difficulties with proxies (cannot inject headers or rewrite URLs with TCP)
  * SSE is just HTTP traffic
