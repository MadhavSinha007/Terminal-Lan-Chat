# Terminal LAN Chat

A simple, encrypted, multi-client chat application built in C++ that works over a local network (LAN) using TCP sockets.

This project demonstrates core system-level concepts such as networking, multithreading, file handling, and basic encryption, all within a terminal-based interface.

---

## Features

* Multi-user chat over LAN
* Username-based messaging
* Real-time message broadcasting
* Multithreaded client handling
* Session-based chat history (auto-saved)
* View previous chats using `/history`
* Basic end-to-end encryption (XOR-based)
* Terminal-based interface

---

## How It Works

* One machine runs as the server
* Multiple users connect as clients
* Clients send encrypted messages to the server
* The server forwards messages to all connected clients
* Each client:

  * Decrypts messages
  * Displays them
  * Saves them locally in a session file

---

## Project Structure

```
lan-chat/
│
├── src/
│   ├── main.cpp
│   ├── server/
│   │   └── Server.cpp
│   ├── client/
│   │   ├── Client.cpp
│   │   └── Receiver.cpp
│   ├── utils/
│   │   ├── FileHandler.cpp
│   │   ├── CommandHandler.cpp
│   │   └── Encryption.cpp
│
├── include/
│   ├── server/Server.hpp
│   ├── client/Client.hpp
│   ├── utils/
│   │   ├── FileHandler.hpp
│   │   ├── CommandHandler.hpp
│   │   └── Encryption.hpp
│
├── data/   # Chat logs stored here
```

---

## Compilation

Make sure you have a C++ compiler with C++17 support.

```
g++ src/**/*.cpp -Iinclude -pthread -std=c++17 -o chat
```

---

## Usage

### Start the Server

```
./chat server
```

The server will start and display its local IP address. Share this IP with other users on the same network.

---

### Start the Client

```
./chat client <server-ip>
```

Example:

```
./chat client 192.168.1.10
```

Enter your username when prompted.

---

## Commands

* `/history`
  Displays a list of previous chat sessions and allows you to view them.

---

## Requirements

* Linux-based system (or compatible environment)
* C++17 or later
* g++ compiler
* Devices connected to the same local network

---

## Notes

* The server acts only as a message relay and does not decrypt messages
* Encryption is implemented using XOR for learning purposes and is not secure for production use
* Each chat session is saved as a separate file in the `data/` directory

---

## Future Improvements

* Replace XOR encryption with a secure algorithm (e.g., AES)
* Add private messaging between users
* Display list of connected users
* Improve command system
* Add graphical user interface

---

## License

This project is open-source and available for educational purposes.
