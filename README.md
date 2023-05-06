Download Link: https://assignmentchef.com/product/solved-ece5484-project-4
<br>
The objective of this project is to reinforce your understanding of the TCP/IP protocol suite. In particular, you will use the Wireshark network protocol analyzer to examine details of TCP, UDP, and IP protocols from the TCP/IP protocol suite. You must:

<ol>

 <li>capture and analyze TCP segments;</li>

 <li>capture and analyze UDP datagrams;</li>

</ol>

<ul>

 <li>capture and analyze IP datagrams; and</li>

</ul>

<ol>

 <li>write and submit a brief written report. The written report is to provide answers to the questions posed in Sections 2, 3, and 4 below.</li>

</ol>

This project assumes you installed and gained familiarity with Wireshark in Project 3.

<h1>1.      TCP Capture and Analysis</h1>

For this part of the project, you will generate HTTP traffic, which is carried using TCP, and examine the resulting trace. Follow the steps below.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>

<ol>

 <li>Start Wireshark and set the interface to use to capture packets.</li>

 <li>Click on “Capture Options.” Be sure that the “Use promiscuous mode” is turned off (unchecked). Be sure that “Capture Filter” is blank (no capture filter should be set). This can also be done from the main Wireshark window using the “Capture:Interfaces” and the “Capture:Options” menus.</li>

 <li>Open your web browser and clear the cache.</li>

 <li>Begin packet capture by clicking the “Start” button. Or, from the main Wireshark window, choose the “Capture:Start” menu.</li>

 <li>Enter the URL <a href="http://www.ieee.org/">http://www.ieee.org</a> in your web browser. Wait long enough that the browser receives a response from the web server and then stop the capture using the “Capture:Stop” menu or using the stop button on the toolbar. NOTE: be sure to enter <a href="http://www.ieee.org/"><strong><sub>http://www.ieee.org</sub></strong></a><a href="http://www.ieee.org/">,</a> not https://www.ieee.org.</li>

 <li>Use the display filter to select the packets to be displayed in Wireshark by entering the IP address of the <a href="http://www.ieee.org/"><strong>ieee.or</strong></a><a href="http://www.ieee.org/"><strong><sub>g</sub></strong></a> web server, which in my capture is 23.0.16.220 , as “ip.host==23.0.16.220” (lowercase, no quotes) into the display filter specification window near the top of the Wireshark window. The IP address for <a href="http://www.ieee.org/"><strong><sub>www.ieee.org</sub></strong></a> may be different for you. So you’ll need to look for which IP address you got. This will change for each person. You might have the same IP as I did, but you may have another one. In my experience the server starts with 23 so you can try looking for that.</li>

 <li>Find the HTTP packet from your client to the host IP you found (www.ieee.org) that contains the first GET request (“GET / HTTP/1.1”).<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a></li>

 <li>Right click on the packet, select “Conversation Filter:TCP” as shown in Figure 1.</li>

</ol>

<strong>Figure 1. </strong>Selecting the TCP conversation.

First, consider the basics of the communication between your computer (the client) and www.ieee.org (the server) that is responding to the request. Answer the following questions in your report in Section 2.1.

Q 1.What is the IP address of the client?

Q 2.What is the port number used on the client for the TCP session with the server? Q 3.What is the IP address of the server?

Q 4.What is the port number used by the server for the TCP session with the client?

Next, consider TCP’s three-way handshake and use of acknowledgment numbers. Answer the following questions in your report in Section 2.1. Note that, by default, Wireshark specifies <em><sub>relative </sub></em>TCP sequence numbers. This is fine for this assignment, but do keep in mind that the actual initial sequence number is a more random number.<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a>

Q 5.What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and the server?

Q 6.What field and value in that field in the TCP segment identifies the segment as a SYN segment?

Q 7.What is the sequence number of the SYN/ACK segment sent by the server to the client in reply to the SYN from the client?

Q 8.What is the value of the acknowledgement number in the SYN/ACK segment sent by the server to the client?

Q 9.What does this acknowledgment number indicate?

Q 10.What field in the TCP segment and value in that field identifies the segment as a SYN/ACK segment? Q 11.Locate the first GET message sent to the server. What is the sequence number of this message? Q 12.What is the total length of the HTTP request containing the GET? Note that this message is the data field for TCP.

Q 13.Locate the TCP segment from the server that acknowledges the GET message. Does the acknowledgment number agree with what you would expect? Briefly explain why or why not. <strong><sub>Provide a screen shot of </sub>the Wireshark window displaying the information you use to answer this question.</strong>

<h1>2.      UDP Capture and Analysis</h1>

For this part of the project, you will use the “nslookup” command, which uses DNS, to generate some UDP traffic. DNS traffic is carried as UDP datagrams.

<ol>

 <li>Start Wireshark, if not already running, and clear the capture filter and the display filter.</li>

 <li>Begin packet capture by choosing “Capture:Interfaces” and then selecting “Start” for the appropriate network interface from which you wish to capture packets.</li>

 <li>From a command prompt<a href="#_ftn4" name="_ftnref4"><sup>[4]</sup></a> on your computer, enter “nslookup www.ece.vt.edu” which will use DNS to find the IP address associated with the host name www.ece.vt.edu. Wait for the response from the web server and then stop the capture in Wireshark.</li>

 <li>Use the display filter to select the packets to be displayed in Wireshark by entering “udp” (lowercase, no quotes) into the display filter specification window near the top of the Wireshark window.</li>

</ol>

Consider the fields in a UDP header. Answer the following questions in Section 2.2 of your report

Q 14.Select one UDP datagram to or from your computer that is part of the DNS transaction. Double click on the packet in the main Wireshark window to create a new window displaying the packet. From this datagram, list each field in the header and indicate the length of the field and its value for this datagram. <strong><sub>Provide a</sub></strong>

<strong>screen shot of the window displaying the information you use to answer questions Q14-Q17. </strong>Q 15.The value in the Length field is the length of what? Verify your answer with the captured UDP datagram considered in the previous question.

Q 16.What is the maximum number of bytes that can be included in a UDP payload?

Q 17.What is the protocol number associated with UDP? Express the answer in decimal.

Q 18.Examine a pair of UDP packets in which the first packet is sent by your host and the second packet is a reply to the first packet. Describe the relationship between the port numbers in the two packets.

<h1>3.      IP Analysis</h1>

For this part of the project, you will consider IP and routing in the Internet. You will generate traffic using a traceroute program. Traceroute allows you to trace the route from your host to any other host on the Internet, taking advantage of ICMP or ICMPv6<a href="#_ftn5" name="_ftnref5"><sup>[5]</sup></a> messages. Traceroute programs include “tracert” accessible from a command prompt in Windows, pingplotter<a href="#_ftn6" name="_ftnref6"><sup>[6]</sup></a> or similar program that runs as a Windows application, and “<em><sub>traceroute -I</sub></em>” on Linux systems. Follow these steps.

<ol>

 <li>Familiarize yourself with a traceroute program and trace the route to an IP address selected by you. (You need not include any output from this first step in your project report.)</li>

 <li>Start Wireshark and begin packet capture by choosing “Capture:Interfaces” and then selecting “Start” for the appropriate network interface from which you wish to capture packets.</li>

 <li>Perform a traceroute to host www.google.com. After the traceroute completes, stop the Wireshark capture.</li>

 <li>Use the display filter to select the packets to be displayed in Wireshark by entering “icmp” if using IPv4 or “icmpv6” if using IPv6 (lowercase, no quotes) into the display filter specification window near the top of the Wireshark window.</li>

</ol>

In the Wireshark trace, locate <em><sub>the first </sub></em>or earliest ICMP or ICMPv6 echo reply message. Use this message to answer the following questions in Section 2.3 of your report.

Q 19.Did your traceroute operation use ICMP or ICMPv6? <strong>Provide a screen shot of the Wireshark window displaying the information you use to answer question Q19-25. </strong>Q 20.What is the IP address of the host that generated the first TTL exceeded?

Q 21.Does this address match the destination address in the echo request messages?

Q 22.What is the content of the Protocol field of the datagram containing the echo reply? (Next Header if

IPv6)

Q 23.What is the purpose of this Protocol field? (Next Header if IPv6) Q 24.How many bytes are in the IP header?

Q 25.How many bytes are in the payload of the IP datagram? Briefly explain how you determine this value?

<h2>4.1.       Report</h2>

You must document your work on this project in a brief written report. Your report should contain the following items.

<ul>

 <li>At the top of the first page of your report, include: your name (as recorded by the university); your email address; and the assignment name (e.g., “ECE 5484, Project 4”). Do <em><sub>not </sub></em>include your Virginia Tech ID number or your social security number.</li>

 <li>The body of the report must contain the following sections. Use section numbers and headings to organize your report.</li>

</ul>

<em>Section 1 – Objectives</em>: Provide a very brief summary of the project objectives.

<em>Section 2 – Questions</em>: Answer the 25 questions specified in Sections 2, 3, and 4. Clearly indicate the question numbers associated with your answer. <strong>Include the three associated screen shots. </strong>Divide Section 2 into three subsections: 2.1. TCP, 2.2. UDP, and 2.3. IP.

<em>Section 3 – Conclusions</em>: Briefly discuss outcomes, including any significant observations, successes, or failures not discussed previously. Indicate the approximate number of hours you spent on this assignment. (The number of hours is just for the instructor to assess the suitability of this project assignment.)

Your writing should be well-organized, concise, and technical in nature. Your report should use complete, grammatically correct English sentences. Use section headings within the report that match the section names listed above. Every figure and table should have a caption and should be introduced in the body of the report.

<a href="#_ftnref1" name="_ftn1">[1]</a> Avoid running over a virtual private network (VPN) connection for the tests in Sections 2, 3, and 4.

<a href="#_ftnref2" name="_ftn2">[2]</a> Contemporary browsers may initiate multiple HTTP requests using different TCP sessions to simultaneously retrieve multiple page elements. Consider just a single TCP session, identified by the source and destination port numbers, when answering the questions in this section. This should be the first TCP session initiated by your browser, i.e., the one that includes the initial HTTP GET request.

<a href="#_ftnref3" name="_ftn3">[3]</a> Wireshark can display absolute sequence numbers. Go to the “Edit:Preferences” menu. Then, chose “Protocols” and “TCP” in the left-hand pane. Then, uncheck “Relative sequence numbers.”

<a href="#_ftnref4" name="_ftn4">[4]</a> With the Windows operating system, a command prompt is available in the “Accessories” folder under “All Programs” in the Start menu.

<a href="#_ftnref5" name="_ftn5">[5]</a> IPv6 is used in some networks. The host www.google.com supports both IPv4 and IPv6. Virginia Tech’s IP traffic to www.google.com is carried using IPv6. In this case, ICMPv6 is used instead of ICMP. If ICMPv6 is used, then the associated IP addresses will be IPv6 addresses. If you wish, you may configure your client to use only IPv4.

<a href="#_ftnref6" name="_ftn6">[6]</a> See <a href="http://www.pingplotter.com/">http://www.pingplotter.com.</a>