<h3 id='app-process'>Application::process</h3>
<h4 class='variant'>void process(Stream *client);</h4>
<h4 class='variant'>void process(Stream *client, char* buffer, int bufferLength);</h4>
<h4 class='variant'>void process(Client *client);</h4>
<h4 class='variant'>void process(Client *client, char* buffer, int bufferLength);</h4>

The method processes a connected client. Call this method in yout main loop when ever you have connected client available. 

The Client class is an Arduino defined base class so we can process requests from multiple different Stream implementations such as EthernetClient or WifiClient. For debugging purposes it is event possible to use the serial port.



The basic of version of process uses the internal buffer for storing the url of the request. The max length is defined in `SERVER_URL_BUFFER_SIZE`. The second overloaded version works exactly the same way but the buffer for storing the url of the HTTP request is given as a argument.

##### Example

```arduino
void loop() {
  WiFiClient client = server.available();

  if (client.connected()) {
    app.process(&client);
  }
}
```