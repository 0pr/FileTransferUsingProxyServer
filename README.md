# FileTransferUsingProxyServer

This project is based on file transmission using MP QUIC for step 1 and implementation of the paper M. Kheirkhah and M. Lee, "AMP: An Adaptive Multipath TCP for Data Center Networks," 2019 (IFIP Networking), Warsaw, Poland, 2019, pp. 1-9, doi: 10.23919/IFIPNetworking.2019.8816848.

In Step 1 we have successfully transfered file from server to client using Multi Path QUIC transfer Protocol.
We have used the decocninck mpquic repository.First we have downloaded all the required dependencies like go,quicgo minitopo
and minitopo extensions.
We have made a few changes in the code of client.
In particular we  have initialised the variable to store the response from the server.Then a new file is created which has same name as that of server and contents of the variable in it are placed in it.The file name variable is initialised as the last path of the url given by the client.Then using wireshark we test the
transfer of file in single path as well as multipath.

QUIC is a protocol which combines the functions of HTTP/2, TLS, and TCP directly over UDP to reduce the latency of client-server
communication. MPQUIC, a major extension for QUIC that enables a
QUIC connection across multiple subflows, keeping into consideration compatibility goals in order to achieve a seamless deployment of the new protocol on
systems and infrastructures.

Steps:

1.Client sends request to proxy server.
2.The proxy server checks its directory for the requested file.
3.If it is present in the directory then it is transmitted to the client
4.If file is not present in proxy server's directory, the proxy server asks the main server for the file.
5.Main server transfers the file to the proxy server.
6.Proxy server maintains a copy of the file and transfers it to the client.

Commands:

Compile main server : $gcc server.c -o server.o -lpthread

Run main server  (runs on port 5010) : $./server.o

Compile proxy server : $gcc proxy.c -o proxy.o -lpthread

Run proxy server (runs on port 5000) : $./proxy 127.0.0.1 5010 5000

Compile client : $gcc client.c -o client.o -lpthread

Run client : $./client.o


