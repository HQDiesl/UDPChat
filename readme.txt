
/*********************************************************
* Program:   UDPEchoV1-2 -  client   and server
* Framework by James Martin
* Summary:  This is an implementation of a UDP version of ping.
*
* Usage :   client
*             <Server IP>
*             <Server Port>
*             [<Iteration Delay (usecs)>]
*             [<Message Size (bytes)>]
*             [<# of iterations>]
*             [<Debug Flag (default : 129)>]\n",
*
*
* Usage :    server
*             <Server Port>
*             [<Debug Flag (default : 129)>]\n",
*
*
*  This file contains the echo server code
*   debugFlag && 0x007f  = debugLevel
*   if (debugFlag && 0x80)
*        creates RTT.dat
*
*   debugLevel:
*    0:  nothing displayed except final result
*    1:  (default) adds errors and warning
*    2:  adds RTT samples
*    4:  some debug
*    5:  lots of debug
*
*    Ex.   debugFlag 2  Does NOT create RTT.dat, does show RTT samples to stdout
*                    129 :  only shows WARNINGs/Errors to stdout AND creates RTT.dat
*
*
*
*
*********************************************************/



*********************************************************

Harrison Diesl, Jawaun McKelvey, William Luttrell

TO OPERATE THE SERVER:
	1. First retrieve your IP using ifconfig. If using a VM, make sure network settings are set to Bridged Adapter.
	2. Distribute this IP to anyone who wishes to connect, as well as a port number you wish to use.
	3. Run the server with "./server <port> <debugFlag>"
	4. The server window will loop and indicate when a new user connects.  A user who disconnects then reconnects is listed as new.
	5. The server will also create a log file to keep a record of the entire chat. This will only be available to the user running the server.
	6. Users who attempt to connect past the limit will be dropped.
	7. To exit, issue a CNT-C

TO OPERATE THE CLIENT:
	1. Get the IP and port of the server you will connect to
	2. Run the client with "./client <serverIP> <port> <username>" where username is the name you wish to display to other users
	3. A child terminal will open labeled "CHAT BOARD". Click away from this terminal back to your main one--this terminal will function as a board to display all messages and mirrors what everyone online sees.
	4. Input messages in the command prompt of your main terminal, send using enter.  NOTE: apostrophes and quotations that are not bounded will throw an error and you will need to resend.
	5. If the connection is lost, you will have 5 attempts to reconnect by sending messages.  After that your client will be closed due to a non-recoverable connection.
	6. To exit the program, issue a CNT-C to your main terminal. This will be confirmed in the chat board with the message "CONNECTION CLOSED".
	7. Close the chat board by exiting out or issuing a CNT-C. Note that the chat log record is removed once disconnected,

*********************************************************
