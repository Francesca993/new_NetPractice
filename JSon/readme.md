***This project has been created as part of the 42 curriculum by fmontini.***
---

# NetPractice

## Description

NetPractice is a practical networking project focused on understanding the fundamentals of TCP/IP addressing and network configuration.

The goal of the project is to correctly configure small simulated networks so that all devices can communicate according to given objectives.

Through 10 different levels, the student must:
- Configure IP addresses
- Set correct subnet masks
- Define default gateways
- Understand routing logic
- Ensure proper communication between hosts across different networks

Each level presents a broken network diagram. The objective is to modify the available configuration fields until the network becomes fully functional.

This project strengthens understanding of how real-world networking works at a logical level.

---

## How It Works

The project provides a local web-based training interface.

Each level contains:
- A network diagram (hosts, routers, switches)
- One or more communication goals (e.g., Host A must reach Host B)
- Editable fields for IP, mask, gateway, and routes
- Logs explaining routing failures

To succeed, the student must:
1. Analyze the network structure.
2. Determine network boundaries using subnet masks.
3. Configure correct IP addresses.
4. Add default routes when necessary.
5. Ensure bidirectional communication.

There are 10 levels in total.

---

## Instructions

### Running the Training Interface

1. Download the project archive from the intra.
2. Extract it into a folder.
3. Run:

```bash
./run.sh
```
---

## Resources

### Learning Materials

During the project, I relied on introductory networking material to understand how addressing and routing actually work in practice.
I studied subnetting, routing logic and IP communication using educational networking videos and curated YouTube playlists focused on beginner networking concepts.

Peer-to-peer discussions with other students were also an essential part of the learning process, helping me reason about routing errors and validate my understanding.

### AI Usage

AI was used strictly as a learning assistant.

I used it to:

* clarify networking concepts (subnet masks, gateways, routing decisions)
* verify my reasoning after solving an exercise
* better understand why a configuration was failing

No level configuration was generated automatically.
All exercises were solved manually and I ensured I fully understood every solution.
---

## Networking Concepts Studied

### 🌐 What is a network

A network is a group of devices connected to communicate with each other.
In NetPractice the devices are hosts connected through switches and routers.

---

### 📬 IP Address (TCP/IP Addressing)

Every device has an address on the network.

Example:
192.168.1.5

The IP identifies a machine so packets know where to go.
If the IP is wrong, communication simply cannot happen.

---

### 🏘️ Subnet

The subnet answers one question:

"Who is part of my network?"

If two devices:

* have different IPs
* but belong to the same subnet

→ they communicate directly.

If they are not in the same subnet → a router is needed.

---

### The Subnet Mask

The subnet mask is a boundary line between:

* network part
* device part

Example:
IP: 192.168.5.25
Mask: 255.255.255.0

Meaning:
192.168.5 | 25

If the network part is equal → direct communication
If different → packet must go to the router

I used the mask to determine:

* valid host ranges
* network address
* broadcast address
* when communication is possible without routing

---

### 🚪 Default Gateway

The gateway is simply the router's address.

Rule:
Same network → communicate directly
Different network → send to gateway

The default route means:
"For every unknown network, send the packet to the router."

In NetPractice this is written as:
0.0.0.0/0 → router IP

---

### 📡 Routers

Routers connect different networks.

They receive a packet and decide:

* deliver locally
* or forward it to another network

Most failing levels in the project were caused by a missing or incorrect route.

---

### 🔌 Switches

Switches connect devices inside the same local network.
They do not route traffic; they only allow local communication.

---

### 📢 Network & Broadcast Addresses

Each subnet contains:

* a network address (cannot be assigned)
* a broadcast address (cannot be assigned)
* valid host addresses

Assigning one of these incorrectly prevents communication.

---

### 🧠 Routing Logic

A host follows this order:

1. Check if the destination is inside its subnet
2. If yes → send directly
3. If not → send to the default gateway

Understanding this logic was the key to solving the levels.

---

