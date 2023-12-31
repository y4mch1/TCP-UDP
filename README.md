# TCP

1. What is the IP address and TCP port number used by the client computer (source) that is transferring the file to gaia.cs.umass.edu?

Open up your terminal and type this command  ```ping gaia.csumass.edu``` 
<img src = "https://media.discordapp.net/attachments/989175257732620410/1163487752306819194/image.png?ex=653fc168&is=652d4c68&hm=9c320ae073e57cb0fcc69a9a34cd7b9f087c9fc60b7eb8a5110d187c398ef99b&=&width=1269&height=700">

<img src = "https://cdn.discordapp.com/attachments/989175257732620410/1163488620670361664/image.png?ex=653fc237&is=652d4d37&hm=988769eca2c5b044e1d683b865c716add0b371325cba4a6abece1bd70523aa0b&">

IP address from the client computer is ```192.168.86.68``` and the port is  ```55639```

2. What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection?
<img src ="https://media.discordapp.net/attachments/989175257732620410/1163489799093629041/image.png?ex=653fc350&is=652d4e50&hm=008dbad0e393dbf7b059ebb2125312d9e98e2e82832023ae7289ba9920f8195a&=&width=1245&height=700">

```IP Destination = 128.119.245.12``` and ```Destination Port = 80```

3. What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? What is it in this TCP segment that identifies the segment as a SYN segment?Will the TCP receiver in this session be able to use Selective Acknowledgments?
<img src= "https://cdn.discordapp.com/attachments/989175257732620410/1163490637228818543/image.png?ex=653fc418&is=652d4f18&hm=c4f7d83e3bf0e866f01f78911fe84621eaae2ea2c1bfb57a5abb9b6b50a78375&">

Number of the TCP SYN segment adalah seq = 0 atau seq (raw) = 4236649187.
Flags 0x002(SYN) that identifies the segment as a SYN segment. Yes, it will, because SACK allowed in SYN Segment.

4. What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is it in the segment that identifies the segment as a SYNACK segment? What is the value of theAcknowledgementfield in the SYNACK segment? How did gaia.cs.umass.edu determine that value?
<img src="https://media.discordapp.net/attachments/989175257732620410/1163492140870029353/image.png?ex=653fc57f&is=652d507f&hm=bd86d38e78b20e90329acdb9b48cd20e808744ce657a225d3db6895d2aeb65dc&=&width=1245&height=700">

Sequence Number is 0 and Sequence Number (raw) is 1068969752. 0x012 (SYN, ACK) identifies the segment as a SYNACK segment. Acknowledgment number is 4236649188. From sequence number segmen SYN before, that is 4236649187, plus by one (ACK=Seq no+1).

5. What is the sequence number of the TCP segment containing the header of the HTTP POST command? How many bytes of data are contained in the payload (data) field of this TCP segment? Did all of the data in the transferred file alice.txt fit into this single segment?

<img src="https://cdn.discordapp.com/attachments/989175257732620410/1163493376264503326/image.png?ex=653fc6a5&is=652d51a5&hm=bf35b30a6af48745d78414cb96380497939884470ab6f25b4bbc9d8436575560&">

Sequence Number: 152041 and Sequence Number (raw): 4236801228, it has TCP payload (1385 bytes) and alice.txt 149kb, no it wont, because the packet was sent by MIME multipart.

6. Consider the TCP segment containing the HTTP “POST”as the first segment in the data transfer part of the TCP connection.

<img src = "https://cdn.discordapp.com/attachments/989175257732620410/1163494195722473553/image.png?ex=653fc768&is=652d5268&hm=f32177bd04d5aa6afae0c9ebe8b62e3354240e783c96b09b13883ba0f4fce645&">

At what time was the firstsegment(the onecontaining the HTTP POST) in the data-transfer part of the TCP connection sent?

<img src ="https://cdn.discordapp.com/attachments/989175257732620410/1163494573436326078/image.png?ex=653fc7c2&is=652d52c2&hm=9d9034e0fbb230c0fd07b10d3b2e082152d3507fbd0c10457f3a211ed76f6977&">

First pakcet was on 4th frame which means 0.24047 seconds.

At what timewas the ACK for this firstdata-containing segment received?

<img src ="https://cdn.discordapp.com/attachments/989175257732620410/1163494992870916217/image.png?ex=653fc826&is=652d5326&hm=f9858065142697c46dfb72ed026c4ac7db0c5049e907f2f024d46783163caa16&">

0.052671 seconds

What is the RTT for this first data-containing segment?

0.028624 seconds

What is the RTT value the seconddata-carrying TCP segment and its ACK?
<img src= "https://cdn.discordapp.com/attachments/989175257732620410/1163495762806706316/image.png?ex=653fc8de&is=652d53de&hm=85f7eeee74fe63333569b6bb11ecf0fed760568f7c4980e96a413dc42a7fd798&">
0.028628 seconds

7. What is the length (headerplus payload) ofeach ofthe first fourdata-carrying TCP segments?

frame: 4 : length = 32 + 1448 = 1480 bytes

frame: 5 : length = 32 + 1448 = 1480 bytes

frame: 6 : length = 32 + 1448 = 1480 bytes

frame: 7 : length = 32 + 1448 = 1480 bytes 

8. What is the minimum amount of available buffer space advertised to the client by gaia.cs.umass.eduamong these first fourdata-carrying TCP segments7? Does the lack of receiver buffer space ever throttle the senderfor these first four data-carrying segments?

<img src ="https://media.discordapp.net/attachments/989175257732620410/1163496455684763748/image.png?ex=653fc983&is=652d5483&hm=e1477953101ab8b176b2128bb672d1b466c2dd36787542d3f162b178716a07c7&=&width=1245&height=700">

Minimum amount of available buffer space adalah 131712. It is found that the receiver buffer space never throttles the sender because the window size value is always greater than the length of the segment being sent.

9. Are there any retransmitted segments in the trace file? What did you check for (in the trace) in order to answer this question?

Yes, there are, Retransmitted segments can be detected via sequence number. When resending, there are packets where the sequence number of the next packet is not greater than the sequence number of the previous packet.

10. How much data does the receiver typically acknowledgein an ACK among the first ten data-carrying segments sent from the client to gaia.cs.umass.edu? Can you identify cases where the receiver is ACKing every other received segment (see Table 3.2 in the text) among these first ten data-carrying segments?
 <img src= "https://media.discordapp.net/attachments/989175257732620410/1163497317748449300/image.png?ex=653fca51&is=652d5551&hm=a8b22705ab199866c012f058374f061a49439b636e82ff336c9e9792c87ff9aa&=&width=1104&height=258">

 the receiver typically acknowledge in an ACK among the first ten data-carrying segments sent from the client to gaia.cs.umass.edu is 1448 bytes in an ack. if the data is doubled then that segment is acking every other received segment. for example in second segment, the data is doubled from 1448 to 2896 bytes. so the receiver is acking every other received segment.

# UDP

1. Select one UDP packet from your trace. From this packet, determine how many fields there are in the UDP header. (You shouldn’t look in the textbook! Answer these questions directly from what you observe in the packet trace.) Name these fields.

<img src= "https://media.discordapp.net/attachments/989175257732620410/1163498849017544865/image.png?ex=653fcbbe&is=652d56be&hm=996bd43c0be1ccce9c9ef52568f85637b374941c8869cedab3e3c7292b9d22c0&=&width=1440&height=357">

Packet number : 5, SSDP (Simple Service Discovery Protocol), 4 field, source port, destination port, length, dan checksum. 

2. What is the length (in bytes) of each of the UDP header fields?

Source Port : 2 bytes, Destination Port : 2 bytes,Length : 2 bytes,Checksum : 2 bytes. Total 8 bytes.

3. The value in the Length field is the length of what? (You can consult the text for this answer). Verify your claim with your captured UDP packet.

The length field in a UDP packet is the size of the combined UDP header and UDP payload. From the packet above, it is found that the length of the UDP header is 8 bytes and the total length is 43 bytes so the length of the UDP payload is 43 - 8 = 35 bytes

4. What is the maximum number of bytes that can be included in a UDP payload? (Hint: the answer to this question can be determined by your answer to 2. above)

The maximum bytes that can be included in the UDP payload is (2^16-1) bytes including header bytes. So, the maximum bytes that can be included in the UDP payload is (2^16-1)-8 = 65527 bytes

5. What is the largest possible source port number? 

 65535, because the port is represented with 16 bits so the possible numbers are between 0 to 65535 (2^16 - 1)

6. What is the protocol number for UDP?
    17

7. a. What is the packet number of the first of these two UDP segments in the trace file? b. What is the packet number of the second of these two UDP segments in the trace file? c. Describe the relationship between the port numbers in the two packets

a. 15

b. 17

c. The source port for packet 15 is the destination port for packet 17 and it can be applied in the opposite.




