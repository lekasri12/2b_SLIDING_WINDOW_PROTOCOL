# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send: "))
l=list(range(size))
s=int(input("Enter Window Size: "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```

## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recieved from the server".encode())
```

## OUPUT
## CLIENT
![325083046-d557349d-8e2a-4de3-b8b0-deeacbecbd80](https://github.com/lekasri12/2b_SLIDING_WINDOW_PROTOCOL/assets/149037427/8450ef9e-6211-4c10-98f1-77b0eef46070)

## SERVER
![325083089-dae9abd8-aafa-4357-8188-c932d9b301df](https://github.com/lekasri12/2b_SLIDING_WINDOW_PROTOCOL/assets/149037427/f8b37e9a-687f-4bac-b77d-96089becbb15)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
