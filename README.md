# rudiIRC
An encrypted rudimentary IRC system for - CSE550 Network Security. The client-server software emulates an elementary IRC system which handles multiple clients. The clients can chat with another client or send a file easily. Additionally, all the conversations are encrypted using Needam Schroeder Model.

To install or test the software, see Install and Test section.

See the screenshot provided!

## Libraries
Posix threads library, fork()/exec(), socket io, OpenSSL

## Working Commands
`/msg`, `/msg_reply`, `/auth`, `/auth_reply`  


## Install and Test
Compile using the Makefile provided.

1. `make`
2. run `./server`
3. run multiple clients in different terminal windows/tabs using `./client`


## Assumptions

1. Server doesn't store client's long term shared secret key when the client registers for the first time. Everytime
2. /auth to retrieve session key, /msg will use session key to encrypt data. 
3. the client can not distinguish a correct message from a corrupted one, and cannot know if it the messages are encrypted with a wrong session key. 
4. Client cannot send messages without establishing a session key.
5. Assumes that this is just POC, and many small loopholes might be there.
6. Session keys are stored "just in case" for manual verification purpose. Note that no file i/o is being used anywhere.
7. Clients converse/authenticat each other using the server which acts as an intermediary.


## Attacks/Bugs/Errors

1. Prevents against reflection attack as it follows Needam Schroeder Model with CBC mode (reflection attack only works in ECB mode).
2. Prevents impersonation of clients.  Any adversary can't bruteforce or send fake packets.
3. Prevents impersonation of KDC.  Any adversary can't bruteforce or send fake packets to act as the intermediary server.
