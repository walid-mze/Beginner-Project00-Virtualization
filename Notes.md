## What is an SSH(Secure protovol):
 - from my understanding it is a secure way that allow a computer to communicate with another server or a another computer.
 - it is used to send files, log in into github and run commands on another machine.
 - it works as follows : my computer create two keys : private(speciallt for me / secret)  and public key (given to a server), the server store just the public key and when i connect , the server sent a challenge and my computer signs with my private key then some math is done there and then the acess is granted .
 - Ssh is running as a background process  called sshd
 - that sshd listens for incoming connections on a specific port (default 22)
 - in this step we have to change this port to 1111
 - to connect to the vm i need only the ip adress of the server and the ssh port
   

   
