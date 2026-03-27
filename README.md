# Python Reverse Shell (Client-Server)

![Language](https://img.shields.io/badge/Language-Python-blue)
![Status](https://img.shields.io/badge/Status-Experimental-orange)
![Networking](https://img.shields.io/badge/Type-Reverse%20Shell-red)
![License](https://img.shields.io/badge/License-Educational-lightgrey)

## Overview

This project implements a basic **reverse shell** using Python sockets. It enables a server to remotely execute commands on connected client machines over a TCP connection.

The system is designed to demonstrate concepts in:

* Network programming
* Client-server architecture
* Remote command execution
* Concurrent connection handling

---

## Architecture

The system follows a client-server model:

* **Server (`server.py`)**

  * Listens for incoming connections
  * Manages multiple clients
  * Provides an interactive command interface

* **Client (`client.py`)**

  * Initiates connection to the server
  * Executes received commands
  * Returns command output

---

## Features

* Reverse TCP connection (client → server)
* Multi-client handling using threading
* Remote command execution
* Directory navigation support (`cd`)
* Interactive shell interface
* Connection management (list, select, terminate)

---

## Project Structure

```bash
.
├── client.py   # Reverse shell client
├── server.py   # Command and control server
└── README.md   # Documentation
```

---

## How It Works

1. The server starts and listens on a specified IP and port
2. The client connects to the server
3. The server can:

   * View active connections
   * Select a client
   * Execute commands remotely
4. The client executes commands and returns output

---

## Setup and Usage

### 1. Configure IP Address

Update both files:

```python
host = "YOUR_SERVER_IP"
```

---

### 2. Start Server

```bash
python server.py
```

---

### 3. Run Client

```bash
python client.py
```

---

## Server Commands

| Command     | Description                     |
| ----------- | ------------------------------- |
| list        | List all active connections     |
| select <id> | Interact with a specific client |
| end <id>    | Terminate a connection          |
| help        | Display available commands      |

---

## Example Workflow

```
turtle> list
0   192.168.0.10   54321

turtle> select 0
192.168.0.10> whoami
user

192.168.0.10> cd Desktop
```

---

## Technical Details

* Uses Python `socket` module for communication
* Uses `subprocess.Popen` for command execution
* Handles encoding issues with UTF-8 fallbacks
* Thread-based architecture for concurrency

---

## Security Notice

This implementation:

* Does not include encryption
* Does not implement authentication
* Transmits data in plain text

It is not secure and must only be used in controlled, educational environments.

---

## Limitations

* No encryption (susceptible to interception)
* No authentication mechanism
* Limited error recovery
* Basic command parsing

---

## Future Improvements

* Implement SSL/TLS encryption
* Add authentication layer
* Improve command handling
* Add logging and monitoring
* Develop a graphical interface

---

## Author

Oluwasanmi Longe
GitHub: https://github.com/sanmilonge

---

## License

This project is intended for educational purposes only.
