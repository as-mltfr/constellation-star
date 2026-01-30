# CONSTELLATION Stars

**Stars** are the distributed probing agents of the CONSTELLATION platform.

Each Star is a lightweight, autonomous probe responsible for executing
network measurements and reporting results back to the CONSTELLATION Core.

> *Measuring the network, star by star.*

---

## 🌌 What is a Star?

A Star is a **pull-only** network probe:

- It never accepts inbound connections
- It periodically contacts the Core
- It executes assigned measurements
- It reports results in a secure and minimal way

This design minimizes attack surface and allows Stars to operate behind
NATs, firewalls, or restricted environments.

---

## ✨ Key Principles

- **Outbound-only communication**
- **Stateless by design**
- **Minimal trust**
- **Low resource usage**
- **Easy deployment**

Stars are designed to be disposable and replaceable.

---

## 🧱 Architecture Overview

Star → Core ├─ Heartbeat ├─ Capability report ├─ Measurement pull └─ Result submission  

The Core is always authoritative.
Stars never initiate measurements on their own.

---

## 🔐 Security Model

- Each Star authenticates using a unique token
- Tokens are issued by the Core and stored hashed server-side
- No sensitive data is stored permanently on the Star
- Communication is performed over HTTPS
- Rate limiting and size limits are enforced

If a Star stops communicating, it is considered **lost** after a defined
timeout.

---

## 🔄 Lifecycle

1. Star is registered in the Core
2. A token is issued
3. Star starts periodic heartbeats
4. Star pulls pending measurements
5. Star executes measurements
6. Results are sent back to the Core

If heartbeats stop:
- The Star is marked as **degraded**
- Then **lost**
- And may eventually be **retired**

---

## 🧪 Supported Measurements (v1)

Initial versions focus on basic active measurements:

- ICMP ping
- Traceroute
- (More to come)

Measurement support is advertised by each Star during heartbeats.

---

## 🚀 Deployment

Stars are intended to run on:

- VPS
- Bare metal
- Containers
- Lab or experimental networks (e.g. DN42)

They require:
- Python 3
- Outbound Internet (or DN42) connectivity
- No open ports

---

## 🧩 Project Status

Stars are currently under active development.

The protocol and behavior may change until the first stable release.
Backward compatibility is **not guaranteed** at this stage.

---

## 📜 License

CONSTELLATION Stars are licensed under the  
**GNU Affero General Public License v3.0**.

See the `LICENSE` file for full details.

---

## 🌠 About

CONSTELLATION is an independent, community-driven project and is not
affiliated with RIPE NCC.

The project is initiated and primarily developed in France 🇫🇷
