# SecureChat Project Report

## Title Page

---

<div align="center">

**Kathmandu University**

**Department of Computer Science and Engineering**

Dhulikhel, Kavre

<img src="./images/ku_logo.png" width="150px" alt="KU Logo" />

**A Project Report**

on

**SecureChat**

### A Secure LAN-Based Messaging Application

**Course No.: ENGG 102**

(Submitted in Partial Fulfillment of the Requirements for Year I / Semester II in Computer Engineering)

---

**Submitted by**

Maniraj Baral (26)  
Genius Bhandari (34)  
Aayush Bist (43)  
Prajwal Chamlagain (45)  
Pratish Chaudhary (49)

**Submitted to**

Supervisor's Name  
Department of Computer Science and Engineering

July 2026

</div>

---

# Abstract {#abstract}

SecureChat is a desktop-based messaging application developed using C++
and the Qt framework. The project follows a client--server architecture
and enables multiple users to communicate over a Local Area Network
(LAN) using TCP sockets.

The application provides real-time messaging through a graphical user
interface while implementing the Diffie--Hellman key exchange algorithm
to establish a shared secret for secure communication. The project
demonstrates practical concepts of computer networking, socket
programming, object-oriented programming, and GUI development.

The SecureChat application was successfully designed, implemented, and
tested. The results show reliable communication between multiple clients
in a LAN environment and provide a strong foundation for future
enhancements such as end-to-end encryption, internet-based
communication, and file sharing.

# Abbreviations {#abbreviations}

| Abbreviation | Meaning |
|---|---|
| API | Application Programming Interface |
| C++ | C Plus Plus |
| DH | Diffie--Hellman |
| GUI | Graphical User Interface |
| IDE | Integrated Development Environment |
| IP | Internet Protocol |
| LAN | Local Area Network |
| Qt | Cross-platform Application Framework |
| TCP | Transmission Control Protocol |
| UI | User Interface |

# Introduction

## Background

Communication systems play an important role in modern computing. Most
messaging applications rely on cloud-based services, making it difficult
for students to understand the underlying networking concepts. As a
result, practical knowledge of client--server communication and socket
programming is often limited.

SecureChat is a desktop messaging application developed to provide
hands-on experience with network and secure communication. It enables
users to exchange messages over a Local Area Network (LAN) while
demonstrating the practical implementation of computer networking
concepts.

## Project Overview

SecureChat is a client--server messaging application developed using C++
and the Qt framework. It allows multiple users to communicate in real
time over a local network. The server manages client connections and
sends messages to all connected users. The application also implements
the Diffie--Hellman key exchange algorithm to establish a shared secret
for secure communication.

## Problem Statement

Many commercial messaging applications hide the internal workings of
communication systems behind cloud-based services. This limits students'
practical understanding of networking concepts such as socket
programming, client--server architecture, and secure communication.

The SecureChat project addresses this problem by providing a simple
messaging application that demonstrates these concepts through practical
implementation.

## Scope of the Project

The SecureChat application is designed for communication within a Local
Area Network (LAN). It demonstrates real-time messaging, socket
programming, and basic secure communication. The modular design allows
future enhancements such as internet-based communication, file sharing,
and end-to-end encryption.

## Significance of the Project

This project helps students understand networking concepts through
practical implementation. It provides experience in client--server
programming, GUI development using Qt, and collaborative software
development using Git and GitHub.

## Objectives

The main objectives of the SecureChat project are:

- Develop a desktop-based messaging application.

- Implement client--server communication using TCP sockets.

- Support communication among multiple users.

- Design a user-friendly graphical interface using Qt.

- Implement secure key exchange using the Diffie--Hellman algorithm.

- Provide practical experience in networking and software development.

## Structure of the Report

The report is organized into the following chapters:

- **Chapter 1: Introduction** -- Presents the background, project
  overview, problem statement, objectives, scope, significance, and
  report structure.

- **Chapter 2: Literature Review** -- Discusses the concepts and
  technologies related to the project, including client--server
  architecture, socket programming, TCP/IP, and the Qt framework.

- **Chapter 3: System Analysis and Design** -- Describes the system
  requirements, architecture, major modules, and overall design of the
  SecureChat application.

- **Chapter 4: Implementation** -- Explains the implementation of the
  client, server, graphical user interface, networking, and security
  features.

- **Chapter 5: Testing and Results** -- Presents the testing process,
  test cases, and the results obtained during implementation.

- **Chapter 6: Limitations and Future Enhancements** -- Discusses the
  current limitations of the application and possible future
  improvements.

- **Chapter 7: Conclusion** -- Summarizes the project and the knowledge
  gained during its development.

# Literature Review

## Introduction

This chapter presents the concepts and technologies used in the
development of the SecureChat application. The project combines computer
networking, graphical user interface development, and basic cryptography
to create a secure desktop messaging application. Understanding these
concepts provides the theoretical foundation for the implementation of
the system.

## Client--Server Architecture

Client--server architecture is one of the most widely used communication
models in computer networks. In this model, a central server provides
services while one or more clients request those services. The server
manages client requests, processes data, and returns the appropriate
response. This architecture offers several advantages, including
centralized management, easier maintenance, and support for multiple
users. Since all communication passes through the server, it can
efficiently coordinate message exchange between connected clients.

SecureChat follows the client--server model. The server accepts incoming
client connections, manages active users, and broadcasts messages to all
connected clients, enabling real-time communication.

## TCP/IP Protocol

TCP/IP (Transmission Control Protocol/Internet Protocol) is the standard
protocol suite used for communication over computer networks.

The Internet Protocol (IP) is responsible for identifying devices and
routing data packets across the network. Transmission Control Protocol
(TCP) ensures reliable communication by checking for errors, maintaining
packet order, and retransmitting lost packets when necessary.

Since messaging applications require reliable communication, SecureChat
uses TCP sockets to ensure that messages are delivered accurately and in
the correct order.

## Qt Framework

Qt is a cross-platform application development framework widely used for
developing desktop applications with graphical user interfaces. It
supports Windows, Linux, and macOS.

Qt provides several useful libraries for GUI development, networking,
threading, and event handling. These libraries simplify application
development by providing ready-made classes for common programming
tasks.

SecureChat uses Qt Widgets for building the graphical user interface and
the Qt Network module for implementing TCP communication between the
client and server.

### Qt Socket Programming

Qt provides built-in networking classes that simplify socket programming
and make network application development easier. The two main classes
used in SecureChat are `QTcpServer` and `QTcpSocket`.

`QTcpServer` is responsible for listening to incoming client connections
and accepting connection requests. After a client connects,
communication is handled through `QTcpSocket`, which allows data to be
sent and received over a TCP connection.

Qt also uses the signal and slot mechanism to handle networking events
such as new connections, incoming messages, and client disconnections.
This event-driven approach reduces the complexity of socket programming
and makes the application more responsive.

In SecureChat, Qt socket programming is used to establish communication
between the server and multiple clients. It provides reliable message
transmission, simplifies network management, and integrates smoothly
with the graphical user interface developed using the Qt framework.

### QTcpServer

`QTcpServer` is a Qt class used to create a TCP server. It listens for
incoming client connection requests on a specified IP address and port
number. When a client attempts to connect, the server accepts the
connection and creates a socket for communication. In SecureChat,
`QTcpServer` is responsible for accepting multiple client connections
and managing communication between them.

### QTcpSocket

`QTcpSocket` is a Qt class used for TCP communication between the client
and the server. It establishes a connection, sends messages, and
receives data over the network. The class also detects events such as
successful connections, incoming messages, and client disconnections
through Qt's signal and slot mechanism. In SecureChat, each connected
client communicates with the server using a `QTcpSocket` object.

Together, `QTcpServer` and `QTcpSocket` provide reliable communication
over TCP and simplify the implementation of real-time messaging
applications. Their integration with the Qt framework makes network
programming easier while supporting efficient communication between
multiple clients and the server.

### QUdpSocket

QUdpSocket is a subclass of QAbstractSocket in Qt that enables
asynchronous, lightweight UDP datagram communication for applications
prioritizing speed and low overhead over guaranteed delivery. Working in
a connectionless fashion, it uses bind() to listen on a specified local
address/port and emits a readyRead() signal whenever incoming packets
arrive, which can then be processed with readDatagram() or
receiveDatagram(). In addition to basic unicast transfers using
writeDatagram(), QUdpSocket natively supports IP multicasting and
broadcasting, and it can optionally call connectToHost() to use standard
QIODevice stream methods (read() and write()) aimed at a dedicated
target.

## Diffie--Hellman Key Exchange

Diffie--Hellman is a public key exchange algorithm that enables two
communicating parties to establish a shared secret over an insecure
network.

Instead of directly sending the secret key, both parties exchange public
values and independently calculate the same shared key. Since the secret
itself is never transmitted, the communication becomes more secure.

In SecureChat, the Diffie--Hellman algorithm is used to demonstrate
secure key exchange before communication begins.

# Related Work

## Introduction

Several desktop messaging applications have been developed using
client--server architecture and socket programming. These applications
demonstrate real-time communication and provide a foundation for
understanding network programming.

## Existing Messaging Applications

Applications such as WhatsApp, Telegram, Discord, and Microsoft Teams
provide secure communication over the Internet. They support features
such as instant messaging, media sharing, voice calls, and end-to-end
encryption. However, these systems rely on cloud infrastructure and do
not expose their internal implementation.

## Academic Projects

Many academic networking projects focus on simple chat applications
using TCP sockets. These projects generally implement client--server
communication but often lack graphical user interfaces or secure
communication mechanisms.

Some examples of Academic Projects we came across are:

### SyncStream

SyncStream is a real-time, multi-user chat application built for
Windows. It allows multiple users to connect to a central server and
broadcast text messages in real time.

<div align="center">

<img src="./images/syncstream_server.png" width="500px" alt="SyncStream Server" />

*Figure: SyncStream Server*

</div>

<div align="center">

<img src="./images/syncstream_client.png" width="500px" alt="SyncStream Client" />

*Figure: SyncStream Client*

</div>

## Comparison with SecureChat

SecureChat is designed primarily for educational purposes. It combines
socket programming, GUI development using Qt, and the Diffie--Hellman
key exchange algorithm into a single desktop application. Unlike
commercial applications, it helps students understand the practical
implementation of networking concepts.

## Summary

The study of existing messaging systems and academic projects helped
identify the features required for SecureChat. These ideas were used to
design a simple, modular, and educational messaging application.

# System Analysis and Design

## Introduction

This chapter describes the design and overall structure of the
SecureChat application. It presents the system requirements,
architecture, major modules, and workflow of the application.

## System Requirements

### Hardware Requirements

- Processor: Intel Core i3 or equivalent

- RAM: Minimum 4 GB

- Storage: Minimum 200 MB free space

- Local Area Network (LAN)

### Software Requirements

- Operating System: Windows or Linux

- Qt Framework

- C++ Compiler

- CMake

- Git

## Functional Requirements

The SecureChat application provides the following features:

- Connect clients to the server.

- Exchange messages in real time.

- Support multiple connected users.

- Broadcast messages to all connected clients.

- Perform secure key exchange using Diffie--Hellman.

## Non-Functional Requirements

The system is designed to satisfy the following requirements:

- Reliable communication using TCP.

- Simple and user-friendly interface.

- Fast message transmission.

- Modular and maintainable code structure.

## System Architecture

SecureChat follows a client--server architecture. The server manages all
client connections and message broadcasting. Clients connect to the
server through TCP sockets, perform key exchange, and communicate by
sending and receiving messages over the network.

<div align="center">

<img src="./images/architecture.png" width="700px" alt="System Architecture of SecureChat" />

*Figure: System Architecture of SecureChat*

</div>

## Major Modules

The application consists of the following modules:

- **Server Module** -- Accepts client connections and broadcasts messages.

- **Client Module** -- Provides the user interface and manages communication with the server.

- **Communication Module** -- Handles TCP socket communication between the client and server.

- **Security Module** -- Performs the Diffie--Hellman key exchange for secure communication.

<div align="center">

<img src="./images/usecase.png" width="600px" alt="Use Case Diagram of SecureChat" />

*Figure: Use Case Diagram of SecureChat*

</div>

## System Workflow

The overall workflow of the SecureChat application is as follows:

1. Start the server application.
2. Connect one or more clients to the server.
3. Perform secure key exchange.
4. Exchange messages between users.
5. Broadcast messages to all connected clients.
6. Disconnect from the server after communication.

# Implementation

## Introduction

This chapter describes the implementation of the SecureChat application.
The project was developed using C++ and the Qt framework based on a
client--server architecture. The implementation consists of separate
client and server applications that communicate through TCP sockets
while providing a graphical user interface for users.

## Development Environment

The application was developed using the following tools:

- Programming Language: C++

- Framework: Qt 6

- IDE: Qt Creator

- Build System: CMake

- Version Control: Git and GitHub

- Operating System: Windows

## Project Structure

The SecureChat project is divided into two main parts:

- Server Application

- Client Application

The server manages all client connections and communication, whereas the
client provides the graphical interface for users to interact with the
system.

## Server Implementation

The server application is responsible for accepting client connections,
managing connected users, and broadcasting messages. It continuously
listens for new client requests and forwards messages to all connected
users.

The server consists of the following components:

- **mainwindow** -- Controls the main server window and manages communication.

- **authmanager** -- Handles user authentication and authorization.

- **ServerDiscoveryBeacon** -- Allows clients to discover the server automatically within the local network.

## Encryption Implementation

To provide secure communication between clients, SecureChat uses a
combination of the Diffie--Hellman (DH) key exchange algorithm, room key
exchange, and XOR-based encryption. The objective is to ensure that
messages remain confidential even though they are transmitted through
the server. The server only forwards encrypted messages and does not
know their actual contents.

### Key Exchange (Diffie--Hellman)

When a client connects to the server, the server sends two public
parameters: a large prime number ($p$) and a generator ($g$). Each
client then generates its own private key locally using a random 64-bit
integer generator provided by the Qt framework.

Using these values, each client calculates its public key using the
following equation:

$$\text{Public Key} = g^{\text{Private Key}} \bmod p$$

The calculated public key is then sent to the server, which distributes
it to the other connected clients. All calculations are performed using
the `long long` data type to reduce the possibility of precision errors.

### Room Key Generation and Distribution

Instead of encrypting messages directly with the Diffie--Hellman shared
secret, SecureChat generates a separate room key consisting of 26
randomly selected characters. This room key is created once by the room
leader and shared securely with every participant.

For each connected client, the room leader calculates a shared secret
using the following equation:

$$\text{Shared Secret} = (\text{Peer Public Key})^{\text{Leader Private Key}} \bmod p$$

Because of the mathematical properties of the Diffie--Hellman algorithm,
each client independently computes the same shared secret using the
leader's public key and its own private key.

The room leader encrypts the room key by applying the XOR operation with
the shared secret before sending it to each client. The receiving client
performs the same XOR operation using its computed shared secret to
recover the original room key.

### Message Encryption (XOR Cipher)

After all clients obtain the same room key, chat messages are encrypted
using a repeating-key XOR cipher.

The encryption process is represented by:

$$C = P \oplus K$$

where

- $P$ = Plaintext

- $K$ = Room Key

- $C$ = Ciphertext

The original message is recovered using the same operation:

$$P = C \oplus K$$

Since the room key contains only 26 characters, it is repeated
cyclically throughout the message:

$$C[i] = P[i] \oplus K[i \bmod \text{Length}(K)]$$

This method provides a simple demonstration of symmetric encryption for
educational purposes.

### Security Analysis

The Diffie--Hellman private key is generated randomly using a 64-bit
integer, making brute-force attacks computationally difficult.
Similarly, the 26-character room key provides a very large number of
possible combinations, making random guessing highly impractical.

Although the current implementation is intended primarily for
educational purposes, it demonstrates the basic concepts of secure key
exchange and encrypted communication between multiple users.

### Limitations

The current encryption implementation has several limitations:

- The application does not provide forward secrecy across different sessions.

- Message integrity and authentication are not implemented.

- The repeating-key XOR cipher is not considered cryptographically secure for real-world applications.

- Advanced encryption algorithms such as AES have not been implemented.

## Client Implementation

The client application provides an interactive graphical interface
through which users connect to the server and exchange messages. It
communicates with the server using TCP sockets and updates the interface
whenever new messages arrive.

The client is composed of the following components:

- **Login Window** -- Allows users to enter their credentials and the IP-address of the server where the server is hosted before joining the chat.

- **Main Window** -- Displays conversations and provides message input.

- **Auth Client** -- Communicates with the server for authentication.

- **Bubble Message** -- Displays chat messages in a user-friendly bubble format.

- **System Log Dialog** -- Displays important system messages and logs.

- **Server Discoverer** -- Detects available servers on the local network.

## Graphical User Interface

The graphical user interface was developed using Qt Widgets. The
interface includes a login window, chat window, message display area,
and message input field. The design provides a simple and user-friendly
environment for communication.

The GUI updates automatically whenever new messages are received from
the server.

## Networking

Networking is implemented using the Qt Network module. TCP sockets
establish reliable communication between the client and server. The
server listens for incoming connections while multiple clients connect
using the server's IP address and port number.

Once connected, messages are transmitted through the server and
broadcast to all active clients in real time.

## Security Implementation

SecureChat demonstrates secure communication by implementing the
Diffie--Hellman key exchange algorithm. Before communication begins, the
client and server exchange public values and independently generate a
shared secret key.

The project also includes the QtEncryptionEngine module, which provides
encryption-related functionality for secure communication.

## Implementation Workflow

The overall implementation process follows these steps:

1. Start the server application.
2. Clients discover or connect to the server.
3. User authentication is performed.
4. Diffie--Hellman key exchange establishes a shared secret.
5. Messages are exchanged between connected users.
6. The server broadcasts messages to all active clients.
7. Clients disconnect when communication is complete.

# Testing and Results

## Introduction

This chapter presents the testing carried out on the SecureChat
application. The objective was to verify that the client and server
communicate correctly, messages are delivered successfully, and the
implemented features operate as expected.

## Testing Environment

The application was tested under the following environment:

- Operating System: Windows

- Framework: Qt 6

- Communication Protocol: TCP

- Network: Local Area Network (LAN)

- Multiple client instances connected to a single server

## Test Cases

| Test ID | Description | Result |
|---------|-------------|--------|
| TC-01 | Server starts successfully | Passed |
| TC-02 | Client connects to server | Passed |
| TC-03 | User authentication | Passed |
| TC-04 | Message transmission | Passed |
| TC-05 | Message broadcasting | Passed |
| TC-06 | Multiple clients communicate simultaneously | Passed |
| TC-07 | Server discovery | Passed |
| TC-08 | Secure key exchange | Passed |

## Results

The SecureChat application was successfully implemented and tested.
Multiple clients were able to connect to the server simultaneously and
exchange messages in real time. The server correctly broadcast messages
to all connected clients.

<div align="center">

<img src="./images/server_dashboard.jpeg" width="650px" alt="Server Dashboard" />

*Figure: Server Dashboard*

</div>

The authentication mechanism worked as expected, and users were able to
join the chat room successfully using the login interface.

<div align="center">

<img src="./images/login_window.jpeg" width="550px" alt="Client Login Window" />

*Figure: Client Login Window*

</div>

After successful login, users entered the chat room where messages could
be exchanged in real time. The member list and chat interface were
updated correctly during communication.

<div align="center">

<img src="./images/chat_window.jpeg" width="700px" alt="SecureChat Main Chat Window" />

*Figure: SecureChat Main Chat Window*

</div>

The Diffie--Hellman key exchange was successfully performed before
communication, and automatic server discovery simplified the connection
process within the local network.

# Project Planning and Management

## Introduction

Proper planning and management were essential for the successful
completion of the SecureChat project. The project was divided into
several phases to ensure systematic development and timely completion.

## Project Development Phases

The project was completed through the following phases:

- Requirement Analysis

- System Design

- GUI Development

- Client and Server Implementation

- Diffie--Hellman Integration

- Testing and Debugging

- Documentation

## Gantt Chart

<div align="center">

<img src="./images/ganttchart.png" width="800px" alt="Project Gantt Chart" />

*Figure: Project Gantt Chart*

</div>

## Team Responsibilities

| Member | Responsibility |
|--------|-----------------|
| Maniraj Baral | GUI development and functionality testing |
| Genius Bhandari | Security module and integration |
| Aayush Bist | Documentation and testing |
| Prajwal Chamlagain | Client module development and GUI testing |
| Pratish Chaudhary | Server implementation and networking |

## Summary

This chapter presented the project planning and management activities
carried out during the development of SecureChat. It described the
different phases of the project, the responsibilities assigned to each
team member, and the development schedule through the Gantt chart.

Proper planning, task distribution, and teamwork helped ensure that the
project was completed systematically and within the planned time.
Effective coordination among team members also contributed to the
successful implementation and documentation of the SecureChat
application.

# Limitations and Future Enhancements

## Introduction

Although the SecureChat application successfully provides secure
communication over a Local Area Network (LAN), it has certain
limitations. This chapter discusses the current limitations of the
system and suggests possible enhancements for future development.

## Limitations

The current version of SecureChat has the following limitations:

- The application works only within a Local Area Network (LAN).

- File and media sharing are not supported.

- Group management features such as creating or deleting chat groups are not available.

- User accounts are limited to the implemented authentication mechanism.

- Message history is not permanently stored after the application is closed.

- The application is primarily designed for desktop platforms.

## Future Enhancements

The following improvements can be made in future versions of the application:

- Support communication over the Internet instead of only LAN.

- Implement end-to-end encryption for enhanced security.

- Add file, image, and document sharing.

- Store chat history in a database.

- Support voice and video communication.

- Improve group chat management features.

- Add push notifications and status indicators.

- Develop mobile versions of the application for Android and iOS.

## Summary

The current implementation of SecureChat demonstrates the fundamental
concepts of networking, client--server communication, and secure key
exchange. With additional features such as internet support,
multimedia sharing, and enhanced security, the application can be
further developed into a more complete messaging platform.

# Conclusion and References

## Conclusion

The SecureChat project successfully achieved its main objective of
developing a desktop-based messaging application using C++ and the Qt
framework. The application enables multiple users to communicate over a
Local Area Network (LAN) through a client--server architecture using TCP
sockets.

The project also demonstrated the use of the Diffie--Hellman key
exchange algorithm for secure communication and provided practical
experience in networking, GUI development, and software engineering.
Overall, SecureChat met the intended objectives and serves as a strong
foundation for future enhancements such as end-to-end encryption, file
sharing, and internet-based communication.

## References

1. Bjarne Stroustrup. *The C++ Programming Language (4th Edition)*.
   Addison-Wesley Professional, 2013.

2. Qt Documentation. Available: https://doc.qt.io/

3. Qt Network Module Documentation. Available:
   https://doc.qt.io/qt-6/qtnetwork-index.html

4. CMake Documentation. Available: https://cmake.org/documentation/

5. Git Documentation. Available: https://git-scm.com/doc

6. GitHub Documentation. Available: https://docs.github.com/

7. Academic Project - SyncStream by yadunand-kamath. Available:
   https://github.com/yadunand-kamath/SyncStream

8. Deffie-Hellman Key Exchange. Available:
   http://geeksforgeeks.org/computer-networks/implementation-diffie-hellman-algorithm/

9. GitHub Documentation. Available: https://docs.github.com/

10. XOR Cipher. Available:
    https://www.geeksforgeeks.org/dsa/xor-cipher/

11. QUdpSockets. Available: https://doc.qt.io/qt-6/qudpsocket.html

---

# Appendix

## A. Installation and Setup Guide

### A.1 Prerequisites

Before setting up SecureChat, ensure that your system meets the following requirements:

- **Qt 6.0 or higher** -- Download from https://www.qt.io/download
- **CMake 3.16 or higher** -- Download from https://cmake.org/download/
- **C++ Compiler** -- GCC (Linux), Clang (macOS), or MSVC (Windows)
- **Git** -- Download from https://git-scm.com/download

### A.2 Cloning the Repository

```bash
git clone https://github.com/PratishChaudhary/SecureChat.git
cd SecureChat
```

### A.3 Building the Project

#### On Windows (Qt Creator):

1. Open Qt Creator
2. Click **File → Open File or Project**
3. Navigate to the SecureChat directory and open **CMakeLists.txt**
4. Configure the project with your Qt installation
5. Click **Build → Build All**

#### On Linux/macOS (Command Line):

```bash
mkdir build
cd build
cmake ..
make
```

### A.4 Running the Application

#### Starting the Server:

```bash
./SecureChatServer
```

The server will listen on port 5555 by default.

#### Starting the Client:

```bash
./SecureChatClient
```

Enter the server's IP address and port number in the login window to connect.

---

## B. Code Samples

### B.1 TCP Server Implementation (Server Accept Connection)

```cpp
void Server::onNewConnection()
{
    QTcpSocket* socket = tcpServer->nextPendingConnection();
    
    if (socket == nullptr) {
        return;
    }
    
    connect(socket, &QTcpSocket::readyRead, this, &Server::onReadyRead);
    connect(socket, &QTcpSocket::disconnected, this, &Server::onClientDisconnected);
    
    clientSockets.append(socket);
    
    qDebug() << "New client connected from:" 
             << socket->peerAddress().toString() << ":"
             << socket->peerPort();
    
    logMessage("Client connected: " + socket->peerAddress().toString());
}
```

### B.2 Diffie-Hellman Key Generation

```cpp
long long DHKeyGenerator::generatePublicKey(long long privateKey, 
                                            long long generator, 
                                            long long prime)
{
    long long publicKey = 1;
    long long base = generator;
    long long exponent = privateKey;
    
    // Modular exponentiation: (base^exponent) mod prime
    while (exponent > 0) {
        if (exponent % 2 == 1) {
            publicKey = (publicKey * base) % prime;
        }
        exponent = exponent >> 1;
        base = (base * base) % prime;
    }
    
    return publicKey;
}

long long DHKeyGenerator::generateSharedSecret(long long peerPublicKey,
                                               long long privateKey,
                                               long long prime)
{
    return generatePublicKey(privateKey, peerPublicKey, prime);
}
```

### B.3 XOR Encryption Implementation

```cpp
QString Encryption::xorEncrypt(const QString& plaintext, 
                               const QString& key)
{
    QString ciphertext = plaintext;
    int keyLength = key.length();
    
    for (int i = 0; i < plaintext.length(); ++i) {
        int keyIndex = i % keyLength;
        ciphertext[i] = QChar(plaintext[i].unicode() ^ key[keyIndex].unicode());
    }
    
    return ciphertext;
}

QString Encryption::xorDecrypt(const QString& ciphertext,
                               const QString& key)
{
    // XOR decryption is the same as encryption
    return xorEncrypt(ciphertext, key);
}
```

### B.4 Client Connection to Server

```cpp
void Client::connectToServer(const QString& ipAddress, int port)
{
    if (tcpSocket->state() == QAbstractSocket::ConnectingState ||
        tcpSocket->state() == QAbstractSocket::ConnectedState) {
        return;
    }
    
    tcpSocket->connectToHost(ipAddress, port);
    
    if (!tcpSocket->waitForConnected(5000)) {
        emit connectionFailed("Failed to connect to server");
        return;
    }
    
    qDebug() << "Connected to server at" << ipAddress << ":" << port;
    emit connectionSucceeded();
}
```

### B.5 Message Broadcasting from Server

```cpp
void Server::broadcastMessage(const QString& senderName, 
                              const QString& encryptedMessage)
{
    QByteArray data;
    QDataStream out(&data, QIODevice::WriteOnly);
    
    out << senderName;
    out << encryptedMessage;
    out << QDateTime::currentDateTime().toString("hh:mm:ss");
    
    for (QTcpSocket* socket : clientSockets) {
        if (socket->state() == QAbstractSocket::ConnectedState) {
            socket->write(data);
            socket->flush();
        }
    }
    
    logMessage("Message broadcasted from: " + senderName);
}
```

---

## C. Configuration Files

### C.1 CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.16)
project(SecureChat)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt6 COMPONENTS 
    Core 
    Gui 
    Widgets 
    Network 
    REQUIRED
)

# Server executable
add_executable(SecureChatServer
    src/server/main.cpp
    src/server/server.cpp
    src/server/server.h
    src/server/authmanager.cpp
    src/server/authmanager.h
    src/security/encryption.cpp
    src/security/encryption.h
)

target_link_libraries(SecureChatServer
    Qt6::Core
    Qt6::Network
    Qt6::Gui
    Qt6::Widgets
)

# Client executable
add_executable(SecureChatClient
    src/client/main.cpp
    src/client/mainwindow.cpp
    src/client/mainwindow.h
    src/client/loginwindow.cpp
    src/client/loginwindow.h
    src/client/authclient.cpp
    src/client/authclient.h
    src/security/encryption.cpp
    src/security/encryption.h
)

target_link_libraries(SecureChatClient
    Qt6::Core
    Qt6::Network
    Qt6::Gui
    Qt6::Widgets
)
```

### C.2 Server Configuration (config.txt)

```
# SecureChat Server Configuration
SERVER_PORT=5555
MAX_CONNECTIONS=100
MESSAGE_BUFFER_SIZE=4096
DH_PRIME=10007
DH_GENERATOR=5
HEARTBEAT_INTERVAL=30000
LOG_FILE=server.log
ENABLE_ENCRYPTION=true
```

---

## D. Protocol Specification

### D.1 Message Format

All messages transmitted between client and server follow this format:

```
[Message Type (1 byte)] [Length (4 bytes)] [Payload (variable)]
```

**Message Types:**
- `0x01` -- Authentication Request
- `0x02` -- Authentication Response
- `0x03` -- DH Public Key Exchange
- `0x04` -- Room Key Distribution
- `0x05` -- Chat Message
- `0x06` -- User List Update
- `0x07` -- Disconnect Notification
- `0x08` -- Server Discovery Beacon

### D.2 Authentication Protocol

1. Client sends username and password (encrypted with DH shared secret)
2. Server validates credentials against user database
3. Server responds with success/failure status
4. Upon success, server initiates DH key exchange

### D.3 Diffie-Hellman Exchange Sequence

```
Client                              Server
  |                                   |
  |------ DH_REQUEST ------->         |
  |                                   |
  |    <----- P, G, ServerPublicKey --|
  |                                   |
  |----- ClientPublicKey ---->        |
  |                                   |
  |    <----- EncryptedRoomKey -------|
  |                                   |
  V                                   V
```

---

## E. Troubleshooting Guide

### E.1 Connection Issues

**Problem:** Client cannot connect to server
- **Solution 1:** Verify server is running: Check if port 5555 is open using `netstat -an`
- **Solution 2:** Verify IP address: Use `ipconfig` (Windows) or `ifconfig` (Linux) to find correct server IP
- **Solution 3:** Check firewall: Ensure firewall permits connection on port 5555

### E.2 Build Errors

**Problem:** "Qt libraries not found"
- **Solution:** Set Qt path in CMake: `-DQt6_DIR=/path/to/qt6/lib/cmake/Qt6`

**Problem:** "C++ compiler not found"
- **Solution:** Install a C++ compiler appropriate for your OS

### E.3 Encryption Issues

**Problem:** Messages appear corrupted after encryption
- **Solution 1:** Verify DH key exchange completed successfully
- **Solution 2:** Check that both client and server have the same room key
- **Solution 3:** Ensure XOR cipher is applied correctly

### E.4 Performance Issues

**Problem:** Messages delayed or slow transmission
- **Solution 1:** Reduce MAX_CONNECTIONS if server is overloaded
- **Solution 2:** Increase MESSAGE_BUFFER_SIZE in configuration
- **Solution 3:** Check network bandwidth and latency with `ping`

---

## F. Testing Scenarios

### F.1 Single Client Test

1. Start server
2. Start one client
3. Authenticate with credentials
4. Send test messages
5. Verify messages appear in UI
6. Disconnect

### F.2 Multiple Client Test

1. Start server
2. Start 3-5 client instances
3. Authenticate all clients
4. Have each client send messages
5. Verify all clients receive all messages
6. Disconnect clients one by one

### F.3 Security Test

1. Start server and client
2. Use packet sniffer (Wireshark) to capture traffic
3. Verify messages are encrypted in transit
4. Attempt to decrypt without knowing room key
5. Verify decryption fails

---

## G. Additional Resources

- **Qt Documentation:** https://doc.qt.io/qt-6/
- **Socket Programming Guide:** https://doc.qt.io/qt-6/qtsockets-index.html
- **Cryptography Basics:** https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange
- **CMake Tutorial:** https://cmake.org/cmake/help/latest/guide/tutorial/index.html
- **GitHub Repository:** https://github.com/PratishChaudhary/SecureChat

---

## H. Known Issues and Workarounds

| Issue | Workaround | Status |
|-------|-----------|--------|
| Connection timeout after 5 minutes of inactivity | Implement heartbeat mechanism | In Progress |
| Memory leak with long-running servers | Profile with Valgrind and fix allocations | Open |
| GUI becomes unresponsive during large message broadcasts | Use threading for network operations | Planned |
| XOR cipher weak against frequency analysis | Implement AES encryption | Future Enhancement |
| No persistence of chat history | Implement SQLite database | Planned |

