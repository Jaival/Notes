![[tcp-three-way-handshake-simple.png]]
+ For example, to read this article on your device, your device first sent a message to the server called an SYN (Synchronize Sequence Number).
+ Then the server sends back an acknowledgement message called a SYN-ACK.
+ When your device receives the SYN-ACK from the server, it sends an ACK acknowledgment message back, which establishes the connection.
+ Once a TCP connection is established between two devices, the protocol guarantees that all data is transmitted.
+ Going back to the example of your device , once the three-way handshake is complete, the News server can start sending all the data your device's web browser needs to render this article.
+ All devices break up data into small packets before sending them over the internet. Those packets then need to be reassembled on the other end.
+ So when the server sends the HTML, CSS, images, and other code for this article, it breaks everything into small packets of data before sending them to your device. Your device then reassembles those packets into the files and images it needs to render this article.
+ TCP ensures that these packets all arrive to your device. If any packets are lost along the way, TCP makes it easy for your device to let the server know it's missing data, and for the server to resend those packets.
+ Once your device receives all the data it needs to render the article, TCP automatically terminates the connection between the two devices with a method similar to the three-way handshake, this time using FIN and ACK packets.