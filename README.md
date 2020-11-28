import socket
import time
import sys
print("\n Welcome to Chat Room")
print("\n Initialising. . . . ")
time.sleep(1)
s = socket.socket()
shost = socket.gethostname()
ip = socket.gethostbyname(shost)
print(shost, "(",ip,")\n")
host = input(str("ENter the server address to connect: "))
name = input(str("Enter your Name: "))
port = 8888
print("\n trying to connect to ", host)
time.sleep(1)
s.connect((host, port))
print("Connected. . . \n")
s.send(name.encode())
s_name = s.recv(1024)
s_name = s_name.decode()
print(s_name, "has joined the Chat Room")

while True:
	message = s.recv(1024)
	message = message.decode()
	print(s_name , ":", message)
	message = input(str("Me: "))
	s.send(message.encode())
