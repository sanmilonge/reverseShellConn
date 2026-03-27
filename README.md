# Python Reverse Shell (Client-Server)

A simple Python-based reverse shell that allows a server to remotely connect to and execute commands on a client machine via a TCP socket connection.

> ⚠️ **Disclaimer**: This project is for educational purposes only. Do not use it on systems you do not own or have explicit permission to test.

---

## Features

* Reverse TCP connection (client connects to server)
* Remote command execution
* Multi-client handling
* Interactive shell interface
* Directory navigation (`cd` support)
* Threaded server for handling connections
* Basic connection management (list, select, terminate)

---

## Project Structure

```
.
├── client.py   # Client-side reverse shell
└── server.py   # Server-side controller
```

---

## How It Works

1. The **server** listens for incoming connections.
2. The **client** initiates a connection to the server.
3. Once connected:

   * The server can send commands.
   * The client executes them and returns the output.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/reverse-shell-python.git
cd reverse-shell-python
```

---

### 2. Configure IP Address

Edit both files and replace:

```python
host = "192.168.0.75"
```

with your server's IP address.

---

### 3. Start the Server

```bash
python server.py
```

You should see:

```
Binding the Port: 9978
```

---

### 4. Run the Client

On the target machine:

```bash
python client.py
```

---

## Server Commands

| Command       | Description                  |
| ------------- | ---------------------------- |
| `list`        | Show all active connections  |
| `select <id>` | Connect to a specific client |
| `end <id>`    | Terminate a connection       |
| `help`        | Show available commands      |

---

## Client Interaction

After selecting a client:

* Enter any system command (e.g., `dir`, `ls`, `whoami`)
* Use `cd <directory>` to change directories
* Type `quit` to exit the session

---

## Technical Details

### Client

* Uses `socket` for communication
* Executes commands via `subprocess.Popen`
* Handles:

  * Command execution
  * Directory changes
  * Error handling
  * Encoding issues (UTF-8 safe)

### Server

* Multi-threaded using `threading`
* Maintains:

  * Active connections list
  * Client addresses
* Provides interactive CLI (`turtle>` prompt)

---

## ⚠️ Security Notice

This tool:

* Does **not** use encryption
* Does **not** implement authentication
* Sends data in plain text

⚠️ It is **not secure** for real-world deployment.

---

## Possible Improvements

* Add encryption (e.g., SSL/TLS)
* Implement authentication
* Improve command handling
* Add persistence options
* Create GUI interface
* Logging and auditing

---

## License

This project is licensed under the MIT License.

---

## Acknowledgements

Built for learning purposes in:

* Networking
* Python sockets
* Remote command execution

---

## Final Note

Use responsibly. Unauthorized access to systems is illegal.

---
