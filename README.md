This folder contains code related to streaming data to a server, node.cfg & nodePost are both client side.

- Server initially creates two threads, one to handle the queue and another to handle the client check ins
- Each client is assigned their own port and thread during the check in
- If disconnected, thread will be killed, client will attempt a recconect for approximately 90 seconds at the check in port
- Data from each thread is constantly added to a queue which is handled by one of the threads, constantly finding the correct file and appending, then closing
- Creates the csv if it does not exist, also creates the corresponding html page if it doesn't exist based on .default.html (copies it)
- Lots of try catches related to graceful failures and properly closing sockets for reuse
- Serial port reading only works with a baud rate of 9600 currently
