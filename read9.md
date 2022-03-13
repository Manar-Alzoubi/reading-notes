# WRRC and Java

### HTTP Life Cycle 

#### Step 1: Local Processing

The request made by a browser is  : 

* browser extracts the "scheme"/protocol (HTTP)
* (www.example.com) ==> host
* optional port number
* resource path
* query strings that are specified in the form
    * <protocol>://<host><:optional port>/<path/to/resource><?query>
    * example: 
    * |http|://|www.example.com||:5000||/mainpage||?query=param&query2=param2|

* Now that the browser has hostname for the request, it needs to resolve an IP address:
    * The browser will look through its own cache of recently requested URLs
    * the operating system’s cache of recent queries
    * router’s cache
    *  DNS cache

#### Step 2: Resolve an IP

* resolving an IP from a "DNS server" is a sequence includes many steps, and includes failovers if the first request fails to return an address.

* If the cache lookup fails, your browser fires off a DNS request using UDP

* Your request will now have to travel many network devices to reach its target DNS server

* Once your request arrives at your configured DNS server, the server looks for the address associated with the requested hostname If it finds it, it sends a response. if the DNS server you have targeted cannot locate the given hostname, it passes the request along to another DNS server.If an address for the given domain cannot be resolved, the server responds with a failure and your browser returns an error.

* the requesting client now has a target IP

#### Step 3: Establish a TCP Connection

* the client has an IP address, it can send an HTTP request

* since the request is sent over TCP, which is a transport layer protocol like UDP, the client must open a TCP connection.

* One of the key differences between TCP and UDP is that TCP ensures delivery and ordered data transmission, done as a sequence number for every byte sent. This allows the receiver to re-order received packets back into their original order, and allows the sender to retransmit any packet that does not get acknowledged by the receiver

* The server must already be "listening" on a port, performing a passive open, after which the client can initiate an active open, and the handshake works as follows:

    * The client initiates the active open by sending a SYN "control" packet to the server

    * The server responds with a SYN-ACK message, which contains an acknowledgement number for the original message

    * the client sends an ACK message back to the server, which should match the SYN-ACK message’s acknowledgment number and ensure that our data is being delivered reliably

    * We now have a completed three-way handshake and an established connection where both the client and server have received acknowledgment of the connection from the other party


#### Step 4: Send an HTTP Request

* The request is made up of a "request line", request header, and a body. The "request line" is simply a line that indicates the HTTP method

* when HTTP request is sent, using TCPs magic sequence number powers, the server can ensure it receives the whole request, in the correct order.

* Once the server receives the request, processes it, and finds the resource being requested, it generates an HTTP response

* Once the response is generated, the server responds to the request


#### Step 5: Tearing Down and Cleaning Up 

* Once the response has been fully delivered, the client sends a FIN packet at the TCP level

* browser begins processing what it has received

* HTTP (Hyper*text **Transfer **Protocol) is an “application-layer protocol that generally assumes use of TCP as its “transport-layer protocol 


### Do a Simple HTTP Request in Java

####  way of performing HTTP requests in Java

##### HttpUrlConnection

* The HttpUrlConnection class allows us to perform basic HTTP requests without the use of any additional libraries.

#####  Creating a Request

* We can create an HttpUrlConnection instance using the openConnection() method of the URL class

* this method only creates a connection object but doesn't establish the connection

* HttpUrlConnection class is used for all types of requests by setting the requestMethod attribute to one of the values: GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE.

* create a connection to a given URL using GET method:

    >URL url = new URL("http://example.com");
    >
    >HttpURLConnection con = (HttpURLConnection) url.openConnection();
    >
    >con.setRequestMethod("GET");

#####  Adding Request Parameters

*  to add parameters to a request, we have to set the doOutput property to true, then write a String of the form param1=value¶m2=value to the OutputStream

* o facilitate the transformation of the parameter Map, we have written a utility class called ParameterStringBuilder containing a static method

##### Setting Request Headers

* Adding headers to a request can be achieved by using the setRequestProperty() method:
     * con.setRequestProperty("Content-Type", "application/json");

* To read the value of a header from a connection, we can use the getHeaderField() method:
    * String contentType = con.getHeaderField("Content-Type");

##### Configuring Timeouts

* HttpUrlConnection class allows setting the connect and read timeouts

* These values define the interval of time to wait for the connection to the server to be established or data to be available for reading. 

*  to set both timeout values to five seconds.

    > con.setConnectTimeout(5000);
    > con.setReadTimeout(5000);

##### Handling Cookies

    * read the cookies from a response
    * add the cookies to the cookie store
    * add the cookies to the request

##### Handling Redirects

    * enable or disable automatically following redirects for a specific connection
    * enable or disable automatic redirect for all connections


##### Reading the Response

* Reading the response of the request can be done by parsing the InputStream of the HttpUrlConnection instance.

* To execute the request, we can use the getResponseCode(), connect(), getInputStream() or getOutputStream() methods

* close the connection, we can use the disconnect() method


##### Reading the Response on Failed Requests

* if the request fails, trying to read the InputStream of the HttpUrlConnection instance won't work 

* we can consume the stream provided by HttpUrlConnection.getErrorStream()


##### Building the Full Response

* It's not possible to get the full response representation using the HttpUrlConnection instance

*  we can build it using some of the methods that the HttpUrlConnection instance offers

    * First, let's add the response status information

    * Next, we'll get the headers using getHeaderFields() and add each of them to our StringBuilder in the format HeaderName: HeaderValues
    
    * Finally, we'll read the response content