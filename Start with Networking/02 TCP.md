
### 3-way handShake
+ The TCP 3-Way Handshake is the foundational mechanism that establishes a reliable, full-duplex connection between a
  client and a server before any actual application data (like an HTTP, websocket request) is sent.

#### The 3 Steps (SYN, SYN-ACK, ACK)
+ During this process, the client and server are primarily exchanging Sequence Numbers (SEQ). These numbers are how TCP tracks data order and detects missing packets later on.

1. SYN (Synchronize): The Client Reaches Out
  + **The Action**: The client sends a packet with the SYN flag active.
  + **The Data**: It includes a randomly generated Initial Sequence Number (e.g., Client_SEQ = 100).

  + **The Translation**: "Hi Server, I want to open a connection. I will track the bytes I send to you starting at          number 100."

2. SYN-ACK (Synchronize-Acknowledge): The Server Responds
  + **The Action**: The server receives the request, allocates memory (buffers) for the connection, and replies with      a packet that has both the SYN and ACK flags active.
  + **The Data**: It acknowledges the client's number by adding one (ACK = 101), and provides its own random sequence     number (Server_SEQ = 5000).
  + The Translation: "I hear you, Client, and I am ready to receive your byte 101. I also want to establish my half       of the connection. I will track my outgoing bytes starting at number 5000."

3. ACK (Acknowledge): The Client Confirms
  + **The Action**: The client receives the server's response. It allocates its own memory for the connection and         sends a final packet with just the ACK flag active.
  + **The Data**: It acknowledges the server's sequence number by adding one (ACK = 5001).
  + **The Translation**: "Got it, Server. I am ready to receive your byte 5001. Our two-way channel is officially         open."

"Because TCP is a full-duplex protocol—meaning both sides must be able to send and receive data reliably.
> [!NOTE]
> The first two steps (SYN, SYN-ACK) only prove that the client can send and the server can receive. The server still needs proof that its outgoing messages are actually reaching the client. That third step—the final ACK from the client—is the only way the server knows its return path is functioning. Without it, you only have a one-way connection."

+ It allows the client and server to synchronize their starting sequence numbers and allocate necessary memory buffers before a single byte of actual application data is transmitted.
