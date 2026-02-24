***This project has been created as part of the 42 curriculum by fmontini.***
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

# 🌐 What is a network?

* **A network is a group of devices connected to each other for communication.**

The router is the “center” that connects everyone.

# 📬 The IP
Every device in a network has an address.
* 👉 **The IP is the device's address on the network.**

```txt
192.168.1.5
```
---

# 🏘️ Subnet
The subnet is used to say:
**👉 “Who is part of my network?”**
**🏘️ Same network = direct communication**
If two devices:
have different IPs
but are on the same subnet
👉 they can talk to each other without going through the router.

## 🚪 When do you need a router?
You need a router when:
* the devices are NOT on the same network
* or when you want to go on the Internet
* The router is the bridge between different networks.


**Simple example.**

```txt
PC1 → 192.168.1.10
PC2 → 192.168.1.20
```

They both start with:

```txt
192.168.1.
```

**👉 This usually means they belong to the same network.**

One more step.
```txt
PC1 → 192.168.1.10
PC2 → 192.168.2.20

192.168.1.10
192.168.2.20
           ↑
        this number changes
```
If:  
PC1 → 192.168.1.10. 
PC2 → 192.168.2.20. 
**👉 They cannot communicate directly. A router is needed.**
---

# 📡 The Gateway
The gateway is simply:
**👉 the router's address.**

Mini mind map:
```txt
Same network → they communicate directly
Different network → a router (gateway) is needed
```
### 🔥 Concrete example
Imagine a home network:
```txt
Router (gateway)  → 192.168.1.1
PC1               → 192.168.1.10
PC2               → 192.168.1.20
Telephone         → 192.168.1.30
```
👉 The first three numbers are the same.
👉 Only the last number changes.
---

# The subnet mask 
The subnet mask is just a boundary line.
Concrete example:
```txt
IP:           192.168.5.25
Subnet mask:  255.255.255.0
```
That mask means:
```txt
192.168.5 | 25
↑ network     ↑ device
```
So with 255.255.255.0:
* The first 3 blocks = network
* The last block = devices
* If the “network” part is the same → they communicate directly
* If it is different → a router (gateway) is needed

# 🧠 HOW A NETWORK WORKS (Complete Diagram)
1️⃣ Structure of an IP
```txt
192.168.5.25
│   │   │   │
│   │   │   └── Device (home)
│   │   └────── Part of the network
│   └────────── Part of the network
└────────────── Part of the network
```

With subnet 255.255.255.0, this means:
```txt
NETWORK        | DEVICE
192.168.5      | 25
```
2️⃣ When do two PCs communicate directly?
Example:
```txt
PC1 → 192.168.5.10
PC2 → 192.168.5.200
Subnet → 255.255.255.0
```
Network part:
```txt
192.168.5
192.168.5
```
Equal → ✅ Direct communication

3️⃣ When is a router needed?
Example:
```txt
PC1 → 192.168.5.10
PC2 → 192.168.6.20
Subnet → 255.255.255.0
```
Network part:
```txt
192.168.5
192.168.6
```
Different → ❌
A router is needed.


**🏠 Complete diagram with router**
```txt
                Internet
                   │
                   │
            Router (Gateway)
            192.168.5.1
                   │
        ┌──────────┴──────────┐
        │                     │
PC1                         PC2
192.168.5.10            192.168.5.20
```
Rule:
* Everyone on the same network → communicates
* To exit → goes to the gateway
* Gateway = router IP


### 🎯 What does 255 really mean in the subnet?
Let's take:
```txt
Subnet: 255.255.255.0
```
Each block can range from 0 to 255.
But in the subnet, 255 does not mean “up to 255 devices.”
It means something much more specific:
👉 That block is completely part of the network.

🧠 Simple translation:
Each 255 means:
“This block is a network, not a device.”
Every 0 means:
“This block is for devices.”

**📦 Classic example**
```txt
IP:      192.168.5.25
Subnet:  255.255.255.0
```
Meaning:
```txt
NETWORK        | DEVICE
192.168.5   | 25
```
Because:
```txt
255.255.255.0
↑   ↑   ↑   ↓
R   R   R   D
```
R = network
D = device

🔥 So it does not mean:
“Up to 255 devices”
It means:
“The first 3 blocks are blocked as a network”

**🧠 Why 255?**
A block can be from 0 to 255 because it is made up of 8 bits.
255 in binary is:
```txt
11111111
```
All 1 = all network
All 0 = all device

**The subnet CANNOT be random numbers such as:**
```txt
255.10.200.0 ❌
```
The only valid values within each block are these:
```txt
0
128
192
224
240
248
252
254
255
```
Why?
Because in binary they must all be consecutive 1s and then all 0s.

# 🧠 What is Broadcast?

Every network has:  
1. A network address. 
2. A broadcast address. 
3. Device (host) addresses. 

# 🎯 What is a subnet mask really?
An IP address consists of 4 blocks:
```txt
192.168.10.77
```
Each block ranges from 0 to 255.
The subnet mask is used to divide that IP into:
- Network part
- Device part

🧠 Why those numbers (255, 224, etc.)?
Each block is made up of 8 bits.
In binary:
```txt
255 = 11111111
224 = 11100000
0   = 00000000
```
Basic rule:
* 👉 Bits set to 1 = network part
* 👉 Bits set to 0 = host part

📦 Simple example
```txt
Subnet 255.255.255.0
```
In binary:
```txt
11111111.11111111.11111111.00000000
```
Meaning:
The first 3 blocks = network
The last block = devices
That's why we only looked at the last number with that subnet.

📦 Subnet 255.255.255.224
224 in binary is:
```txt
11100000
```
Meaning:
3 bits network
5 bits host
This creates groups of 32 addresses.
Why?
- Because 2^5 = 32 possible hosts per network.
🎯 So what do those numbers do?
The subnet mask determines:
1. How many networks I can have
2. How many devices I can have per network

🧠 Let's start with the final block
Each block of an IP can range from:
* 0 to 255
How many numbers are there?  
👉 256 numbers in total.  
Because we include zero.  
🎯 Now let's look at the subnet. 
If the subnet is: 
```txt
255.255.255.224
```
The important number is 224.
224 in binary is:
```txt
11100000
```
This means:
3 network bits
5 host bits

**💡 Now the key point**
If I have 5 bits for hosts, how many values can I represent?  
Each bit can be 0 or 1.  
So:  
2^5 = 32. 
That's why each block is 32 addresses.  
🔥 Connection with 256 − 224. 
256 is the total possible in the block.  
224 is the value of the subnet.  
The difference is:  
256 − 224 = 32. 
That difference is the size of the block.  
🏘️ What does this mean in practice?  
With 255.255.255.224, the networks go like this:
```txt
0–31
32–63
64–95
96–127
128–159
160–191
192–223
224–255
```
Each group has 32 addresses.  
This is not a random formula.  
It is simply the number of possible combinations with the remaining bits.  

### 🎯 What does /30 mean?
The number after the slash indicates:  
* 👉 How many bits are network bits
Not how many hosts.

**🧠 Practical translation**
An IP is 32 bits long in total.
If I write:  
/30. 
It means:
* 👉 30 network bits
* 👉 2 host bits
Because 32 − 30 = 2.

**It only means this:**
**👉 The network is divided into groups of 4 addresses at a time**

📦 Concrete example. 
Blocks of 4:
```txt
0–3
4–7
8–11
12–15
16–19
```
Each block contains 4 numbers.

# Default Route
This means:  
* **For everything that is not in my network, go to the router.**
👉 It is a rule that says:
* **for all networks that I do not know, send everything to this IP (the router).**. 
It is a routing rule.
Machine A:
```txt
IP: 68.160.17.125
```
Router on side A:
```txt
68.160.17.126
```
So on Machine A you have to write:
```txt
default → 68.160.17.126
```

Machine A wants to talk to:
```txt
162.203.249.253. 
```


Is it on your network?  
No.  
So what should you do?  
Try talking directly. 
Send everything to the router (68.160.17.126). 
🚪 The router on side A is:  
68.160.17.126. 
That is the only device that A sees outside its network.  

**In the “Routes” field, NetPractice always asks:**
```txt
DESTINATION → NEXT HOP
```
That is:
```txt
Where do I want to go → Who should I deliver it to?
```
**🎯 For the default route**
The destination is:
```txt
0.0.0.0/0
```
Which means:  
All networks in the world
The next hop is:
```txt
68.160.17.126
```
Which is the router on side A.
💡 So Machine A will be:
```txt
0.0.0.0/0 → 68.160.17.126
```
In other words → For everything that is not on my network, go to the router.  
  
🔥 Why 0.0.0.0/0?
Because:
* **/0 means “no network bits”**. 
→ therefore “any destination”
It is the universal rule.

# CIDR → Subnet Mask → Network Size


| CIDR | Subnet Mask | Total IP   | Host         |
| ---- | ----------- | ---------- | ------------ |
| /8   | 255.0.0.0   | 16.777.216 | 16.777.214   |
| /9   | 255.128.0.0 | 8.388.608  | 8.388.606    |
| /10  | 255.192.0.0 | 4.194.304  | 4.194.302    |
| /11  | 255.224.0.0 | 2.097.152  | 2.097.150    |
| /12  | 255.240.0.0 | 1.048.576  | 1.048.574    |
| /13  | 255.248.0.0 | 524.288    | 524.286      |
| /14  | 255.252.0.0 | 262.144    | 262.142      |
| /15  | 255.254.0.0 | 131.072    | 131.070      |
| /16  | 255.255.0.0 | 65.536     | 65.534       |

| CIDR | Subnet Mask   | Total IP  | Host   |
| ---- | ------------- | --------- | ------ |
| /17  | 255.255.128.0 | 32.768    | 32.766 |
| /18  | 255.255.192.0 | 16.384    | 16.382 |
| /19  | 255.255.224.0 | 8.192     | 8.190  |
| /20  | 255.255.240.0 | 4.096     | 4.094  |
| /21  | 255.255.248.0 | 2.048     | 2.046  |
| /22  | 255.255.252.0 | 1.024     | 1.022  |
| /23  | 255.255.254.0 | 512       | 510    |
| /24  | 255.255.255.0 | 256       | 254    |

| CIDR | Subnet Mask     | Total IP | Host |
| ---- | --------------- | --------- | ---- |
| /25  | 255.255.255.128 | 128       | 126  |
| /26  | 255.255.255.192 | 64        | 62   |
| /27  | 255.255.255.224 | 32        | 30   |
| /28  | 255.255.255.240 | 16        | 14   |
| /29  | 255.255.255.248 | 8         | 6    |
| /30  | 255.255.255.252 | 4         | 2    |
| /31  | 255.255.255.254 | 2         | 0*   |
| /32  | 255.255.255.255 | 1         | 1    |
