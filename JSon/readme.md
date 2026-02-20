*This project has been created as part of the 42 curriculum by fmontini.*

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
## Project Overview Table

| Section | Details |
|----------|----------|
| **Manual Server Start** | `python3 -m http.server 49242` → Open `http://localhost:49242` |
| **Using the Interface** | Enter your login → Fix the network → Click **Check again** → Click **Get my config** → Export one file per level |
| **Required Exports** | 10 configuration files (one per level) |
| **Repository Structure** | All 10 exported files must be placed at the root of the repository |
| **Defense Requirements** | 3 random levels solved live |
| **Allowed Tools During Defense** | No external tools allowed; basic calculator (`bc`) tolerated |

---

## Networking Concepts Studied

| Concept | What Was Learned |
|----------|----------------|
| **TCP/IP Addressing** | How IP addresses uniquely identify devices within a network |
| **Subnet Masks** | Network portion, host portion, network size, usable hosts, broadcast address |
| **CIDR Notation** | Meaning of prefixes (/24, /30, /16), total addresses, usable hosts, network blocks |
| **Default Gateway** | How packets are forwarded outside the local subnet |
| **Routing Tables** | Configuration of `Destination → Next Hop` including `0.0.0.0/0 → <gateway>` |
| **Routers vs Switches** | Switch connects devices inside the same network; router connects different networks |
| **OSI Model** | Logical addressing at Layer 3 (Network Layer) |

---

## Resources

| Type                 | Content                                 |
|----------------------|-----------------------------------------|
| **Concepts Studied** | TCP/IP model, subnetting, CIDR, binary IP representation, routing logic, default routes, broadcast and network addresses, OSI layers |
| **References**       | RFC 791 (Internet Protocol), RFC 950 (Subnetting), Cisco Networking Fundamentals, MDN Web Docs |

---

## AI Usage

| Purpose                   | How AI Was Used                                          |
|---------------------------|----------------------------------------------------------|
| Theoretical Clarification | Understanding networking concepts                        |
| Calculation Verification  | Checking subnetting calculations                         |
| Documentation Support     | Structuring and refining the README                      |
| Responsibility            | All configurations solved manually and fully understood  |

---

## Learning Outcomes

| Skill Developed      | Description                                                 |
|----------------------|-------------------------------------------------------------|
| Subnetting Mastery   | Deeper understanding of subnet calculation                  |
| CIDR Confidence      | Ability to calculate network size quickly                   |
| Routing Debugging    | Identifying and fixing forwarding issues                    |
| Packet Flow Understanding | Clear mental model of how data moves across networks   |
| Evaluation Readiness | Problem-solving under time constraints                      |
