
# HTTP request lifecycle


#### Lets start with the steps of this lifecycle :


Step 1: Local Processing
Your browser extracts the "scheme"/protocol (we have established
that this will be HTTP), host (www.example.com),
and optional port number, resource path, and query strings that are specified in the form
<protocol>://<host><:optional port>/<path/to/resource><?query>. An example is |http|://|www.example.com||:5000||/mainpage||?query=param&query2=param2|
Now that the browser has the intended hostname for the request, it needs to resolve an IP address1. The browser will then look through its own cache of recently requested URLs, the operating system’s cache of recent
 queries, your router’s cache, and your DNS cache.

Step 2: Resolve an IP
1. Like the processing done locally, resolving an IP from a "DNS server"2 is a sequence that includes many steps, and includes failovers if the first request fails to return an address
2. Your request will now have to travel many network devices to reach its target DNS server
3. Once your request arrives at your configured DNS server, the server looks for the address associated with the requested hostname. If it finds one, it sends a response. If, on the other hand, the DNS server you have targeted cannot locate the given hostname, it passes the request along to another DNS server it is configured to defer to
4. We will assume the request is successful though, given that all of this is still a precursor. If the response makes it back (remember, with UDP there’s no guarantee!), the requesting client now has a target IP. It will also have received a piece of information as part of the answer that will let it know how long the returned answer can be cached for

Step 3: Establish a TCP Connection
Now that the client has an IP address, it can send an HTTP5 request, right? Almost, but first, since the request is sent over TCP6, which is a transport layer protocol like UDP, the client must open a TCP connection.

1. One of the key differences between TCP and UDP is that TCP ensures delivery and ordered data transmission. Much of this is done very simply, using what’s known as a sequence number for every byte sent. This allows the receiver to re-order received packets back into their original order, and allows the sender to retransmit any packet that does not get acknowledged by the receiver.
2. These guarantees and more can be found on Wikipedia, and are worth reading about, but what’s most relevant is that TCP connections are opened using what’s known as a three-way handshake


Step 4: Send an HTTP Request

1. The request is made up of a "request line", request header, and a body
2. Once the HTTP request is sent, it follows a similar routing procedure as the one discussed earlier, with the difference being that using TCPs magic sequence number powers, the server can ensure it receives the whole request, in the correct order.
3. Once the server receives the request, processes it, and finds the resource being requested, it generates an HTTP response
4. Once the response is generated, the server responds to the request.


Step 5: Tearing Down and Cleaning Up
1. Once the response has been fully delivered, the client sends a FIN packet at the TCP level, to which the server responds with an ACK, and then generally sends a FIN of its own, which the client responds to with its own ACK signal
2. At this point, your browser begins processing what it has received.


![HTTP_request_response](https://user-images.githubusercontent.com/79080942/125158996-40d82200-e17d-11eb-8502-f63d79263c40.jpg)







