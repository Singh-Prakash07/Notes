## 1. TCP Connection
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

## TCP Teardown
  + Just like the 3-Way Handshake opens a connection, the TCP 4-Way Teardown closes it.

  + Here is the play-by-play of how it works, assuming the Client initiates the disconnect.
### TCP 4-Way Teardown (FIN, ACK)
1. FIN (Finish): Client initiates the close
  + **The Action**: The client decides it has sent all its data and sends a packet with the FIN flag active.
  + **The Translation**: "Server, I have no more data to send to you. I am closing my outbound channel."
  + **The State**: The client enters the FIN-WAIT-1 state. Crucially, the client can no longer send data, but it can     still receive data.

2. ACK (Acknowledge): Server confirms the Client's close
  + **The Action**: The server receives the FIN packet and immediately replies with an ACK.
  + **The Translation**: "Understood, Client. I acknowledge your outbound channel is closed."
  + **The State (The "Half-Closed" phase)**: The client enters FIN-WAIT-2. The server can now finish sending any         remaining data it was processing. The connection is "half-closed."

3. FIN (Finish): Server initiates its own close
  + **The Action**: Once the server is completely done transmitting its final pieces of data, it sends its own FIN     packet to the client.
  + **The Translation**: "Client, I am also completely done sending data. I am closing my outbound channel."

4. ACK (Acknowledge): Client confirms the Server's close
  + **The Action**: The client receives the server's FIN and sends a final ACK in response.
  + **The Translation**: "Understood, Server. Both channels are closed. Goodbye."

 + The "Gotcha" Interview Concept: The TIME_WAIT State: "After the client sends that final ACK in Step 4, can it immediately destroy the socket and free up its memory?"

+ No. After sending the final ACK, the client enters a state called TIME_WAIT and waits for a specific duration         (usually twice the Maximum Segment Lifetime, or 2MSL—typically 1 to 4 minutes).
  +It does this for two reasons:
1. To handle a lost ACK: If that final ACK gets lost in transit, the server will assume its FIN was dropped and will re-transmit the FIN. The client must stay alive in TIME_WAIT so it can re-send the final ACK.
2. To prevent ghost packets: It ensures that any delayed packets from this old connection fully die out on the network before that specific port combination is reused for a brand-new connection."

Your Interview Summary Line
"The TCP 4-Way Teardown safely closes a full-duplex connection by shutting down each direction independently. It uses a FIN/ACK pair from the initiator, followed by a FIN/ACK pair from the receiver once all remaining data is flushed, ending in a TIME_WAIT state to ensure the final acknowledgment wasn't lost."
