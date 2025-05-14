
# 🛡️Sheeld VPN/Proxy

This project is composed of 3 main repositories that together build a decentralized VPN tunnel with SOCKS5 proxying.

![enter image description here](https://sheeld.xyz/assets/readme-banner.png)

## 📦 Repositories

-   **[Node (Server)](https://github.com/leostelon/sheeld-network)** – A peer-to-peer (P2P) network node built with Node.js (CommonJS) and GunDB for decentralized data synchronization.
-   **[Android Client](https://github.com/leostelon/sheeld-android)** – Native Android app written in Java, using VPN tunneling and SOCKS5.	
-   **[Frontend (Website Landing)](https://github.com/leostelon/sheeld-landing)** – Landing page and documentation website.
    

----------

## 🧩 Node.js Server

**Language**: Node.js (CommonJS)

### Tech/Features:

-   **GUN** – A peer-to-peer (P2P) graph database used to synchronize data between nodes in a decentralized network using conflict-free replicated data types (CRDTs).
-   **SOCKS5** – -   A network protocol that allows clients to route traffic through a proxy server. In this system, it is used to tunnel traffic from clients (e.g., Android app) to the decentralized network via proxy nodes.
-   **Bootnode** – An initial peer node that new nodes connect to for bootstrapping into the network. It provides the latest peer list and handles tasks like syncing and payment updates. Bootnodes can be customized by specifying a different URL.
-   **Helius** – A webhook service used to integrate with the Solana blockchain. It processes on-chain payment events by calling configured bootnode endpoints to notify them of relevant transactions.
-   **Production** – Currently restricted due to security issues (open node can access client data).
-   **Encryption** – Work in progress.

----------

## 📱 Android Client

**Tech Stack**: Java, Native Android

### Features:

-   **VpnService** – Leverages Android’s `VpnService` API to create a virtual network interface (TUN). All outbound device traffic is intercepted and redirected through this interface.
-   **Sockstun** – A native Android binary (inspired by `tun2socks`) that reads raw IP packets from the TUN interface and forwards them through a SOCKS5 proxy. Communicates with the Android app via JNI (Java Native Interface).
-   **Sol4k** – A Java wrapper for Solana RPC APIs, used to interact with the Solana blockchain. Enables the client to initiate and sign transactions for payment processing.
----------

## 🌐 Frontend (Website)

A minimal landing site that:
    
-   Written in plain HTML/CSS/JS
- Links to downloads or installation instructions.
-   Includes real-time stats.
    

----------

## 🛠 Local Development

### Start a Node:
```bash
git clone https://github.com/leostelon/sheeld-network
cd sheeld-network
npm install
npm run start
```
### 🔐 Environment Configuration

Create a `.env` file in the root of the `sheeld-network` directory with the following content:
```env
NETWORK="dev"
IS_BOOT_NODE="true"
IP="0.0.0.0" #local ip if your testing on local network
PORT=3000
SECRET=secret #empty for open network
```
> ⚠️ Replace the dummy values with actual configuration values for your environment.
----
### 🧭 Experimental Branch

The main branch includes core functionality and default configurations. For GunDB-specific networking support, use the `gun` branch:

#### 🔀 Switch to the GunDB-enabled branch:
```
git fetch
git checkout gun
```

The `gun` branch includes:
-   GunDB integration for peer discovery and data replication
-   Default bootnode configured with GunDB peers
----------
### Run Android Client:

Install the APK or build with Android Studio. Configure the Node server IP and start the VPN.

----------

## 🚧 Roadmap

- Enable end-to-end encryption  
- Harden production nodes  
- Auto node discovery  
- Multi-platform client support
- Reward System
