# ◈ Secure

<p align="center">
  <img src="https://img.shields.io/badge/platform-Android-34A853?style=flat-square&logo=android&logoColor=white" alt="Android" />
  <img src="https://img.shields.io/badge/language-Kotlin%20%7C%20Java%20%7C%20Rust-F46623?style=flat-square&logo=kotlin&logoColor=white" alt="Kotlin | Java | Rust" />
  <img src="https://img.shields.io/badge/license-PolyForm%20Noncommercial-blue?style=flat-square" alt="License" />
  <img src="https://img.shields.io/badge/website-securelegion.org-5AF5F5?style=flat-square" alt="Website" />
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Tor-Hidden%20Services-7D4698?style=flat-square&logo=torproject&logoColor=white" alt="Tor" />
  <img src="https://img.shields.io/badge/Post--Quantum-ML--KEM--1024-FF6F00?style=flat-square" alt="Post-Quantum" />
  <img src="https://img.shields.io/badge/Solana-Wallet-9945FF?style=flat-square&logo=solana&logoColor=white" alt="Solana" />
  <img src="https://img.shields.io/badge/Zcash-Shielded-F4B728?style=flat-square&logo=zcash&logoColor=black" alt="Zcash" />
</p>

**Serverless • Post-Quantum Cryptography • Private Payments • Metadata Resistant • Patent Pending Technology • Tor Network**

A truly serverless P2P E2EE messaging system that eliminates metadata exposure. While other secure messengers protect your messages, Secure protects your identity, communication patterns, and social network from surveillance. No application servers know who you talk to, when you communicate, or where you are.

> "No servers. Metadata resistance. No compromises."

---

## ▸ The Problem We're Solving

### Current Secure Messengers Still Leak Your Privacy

Even the most secure messaging apps today have a fundamental flaw: **they protect your messages but expose your metadata**.

**What's metadata?** It's everything *except* the content of your messages:
- Who you talk to (your social network)
- When you communicate
- How often you message someone
- Your IP address and location
- Your contact list

**Why does this matter?**

> "We kill people based on metadata." — Former NSA Director Michael Hayden

Governments, corporations, and attackers don't need to read your messages. Knowing *who* you talk to and *when* tells them almost everything they need to know.

### Real-World Examples

- **Journalists**: A reporter's sources can be identified just by seeing who contacts them, even if messages are encrypted
- **Activists**: Protest organizers can be mapped by their communication patterns
- **Whistleblowers**: Simply connecting with a journalist can expose your identity
- **Anyone**: Your relationship network, daily routines, and social circle are exposed to whoever runs the messaging servers

**Secure eliminates application-level servers entirely.** Messages go directly peer-to-peer over Tor.

---

## ◆ What Makes Secure Different

### ◇ Truly Serverless P2P Architecture

Traditional secure messengers:
```
You → Signal Server (sees who, when, where) → Recipient
```

Secure:
```
You ←→ Tor Network ←→ Recipient
(No Secure-owned servers in the middle)
```

**No application servers** know:
- Who you're messaging
- When you're messaging
- Where you're messaging from
- Who's in your contact list
- Your communication patterns

### ◈ Post-Quantum Cryptography

**Hybrid X25519 + ML-KEM-1024 (Kyber-1024)** protects against "harvest now, decrypt later" attacks by quantum computers.

- Uses NIST-standardized ML-KEM (FIPS 203) post-quantum key encapsulation
- Combines classical X25519 ECDH with quantum-resistant Kyber-1024
- Secure if EITHER algorithm remains unbroken
- Future-proof encryption for sensitive communications

### ◇ Triple .onion Architecture

Three separate Tor hidden services provide complete anonymity:

1. **Friend-Request .onion** - Three-phase encrypted contact exchange
2. **Messaging .onion** - Direct peer-to-peer encrypted messaging
3. **Voice Calling .onion** - Encrypted peer-to-peer voice calls

All .onion addresses are deterministically generated from your seed phrase—your identity is self-sovereign and portable.

### ◆ Three-Phase Friend Request Protocol

**How you add contacts securely:**

**Phase 1 - PIN-Encrypted Initial Request (0x07)**
- Friend shares QR code with friend-discovery .onion + 10-digit PIN
- You send encrypted contact request to their friend-request.onion
- PIN prevents spam and unauthorized requests

**Phase 2 - Post-Quantum Hybrid Acceptance (0x08)**
- Recipient reviews request and sends full contact card back
- Encrypted with **X25519 + Kyber-1024** hybrid encryption
- Includes hybrid shared secret for quantum-resistant key chain

**Phase 3 - Mutual Acknowledgment (0x08)**
- Original sender sends their full contact card
- Both parties now have complete contact information
- Bidirectional messaging enabled with post-quantum key chains

**No servers. No central directory. No phone numbers.**

### ◈ Ping-Pong Wake Protocol

**Messages only deliver when the recipient is online AND authenticates.**

```
SENDER                          RECIPIENT
  |                                 |
  |- Create encrypted message       |
  |- Store in local queue           |
  |- Send PING token --------------->|
  |   (via Tor hidden service)      |- Receive wake notification
  |                                 |- Authenticate (biometric)
  |<--------------- PONG -----------|
  |   (confirms online + authed)    |
  |- Send encrypted message -------->|
  |   (via Tor)                     |- Decrypt & display
  |<---------------- ACK ------------|
  |- Delete from queue              |
```

**Why this matters:**
- No messages sitting on servers waiting to be compromised
- Active consent required for message delivery
- If recipient's device is seized, your message never arrives
- Complete sender control over delivery

**Perfect for:**
- Sensitive sources and high-risk conversations
- When absolute security matters more than convenience
- Anyone who needs metadata-resistant communication

### ○ TAP Heartbeat Protocol

**Bidirectional online presence without servers.**

When your device connects to Tor, it broadcasts an encrypted "I'm online" signal to all contacts:

```
DEVICE A                        DEVICE B
  |                                 |
  |- Tor connects                   |
  |- Send TAP to all contacts ----->|
  |   (port 9151, encrypted)        |- Decrypt TAP
  |<------------- TAP_ACK -----------|- Confirm receipt
  |                                 |- ACH State Machine Checks:
  |                                 |  • Pending Pings FROM A?
  |                                 |  • Pending messages TO A:
  |                                 |    - MESSAGE_ACK received? → Skip
  |                                 |    - PONG_ACK received? → Skip
  |                                 |    - PING_ACK received? → Poll for PONG
  |                                 |    - No PING_ACK? → Retry Ping
```

**TAP triggers immediate retry of pending messages when contacts come online—no polling delays.**

### ◇ Advanced ACH State Machine

Sophisticated message tracking manages the entire delivery lifecycle:

- **PING_ACK**: Recipient's Tor hidden service is reachable
- **PONG_ACK**: Recipient authenticated and confirmed availability
- **MESSAGE_ACK**: Message delivered to recipient's device
- **TAP_ACK**: Bidirectional heartbeat confirmed

Exponential backoff retry logic and persistent queue management ensure guaranteed offline message delivery.

### ◆ Secure Pay - Built-In Private Payments

**Multi-chain cryptocurrency wallet integrated into messaging:**

- Zcash (ZEC) for maximum privacy with shielded transactions
- Solana (SOL/USDC/USDT) for fast, low-fee payments
- In-chat payment protocol based on NLx402 core logic
- Request money, send payments, view transaction history
- Hardware-backed wallet keys (StrongBox/TEE)

**Your Solana wallet is your messaging identity**—no phone numbers, no email, no registration.

### ○ Hardware-Backed Security

**Multi-Layered Access Control Hierarchy:**
- Keys stored in Android StrongBox (Pixel) or Trusted Execution Environment (Knox)
- Biometric authentication required on every app launch
- Argon2id password hashing for database encryption
- Domain-separated key derivation
- Memory zeroization (DOD 5220.22-M 3-pass standard)
- Duress PIN triggers cryptographic data wipe

### ◇ Panic Button Protection

**Duress PIN instantly wipes all evidence:**

1. **Cryptographic key destruction** (DOD 5220.22-M standard)
2. **Notifies all contacts** to delete queued messages for you
3. **Appears like authentication failure** (undetectable)
4. **Restores from seed phrase** when safe

No evidence. No queued messages. No metadata to analyze.

### ▸ Voice Messages Over P2P

**Send encrypted voice recordings directly peer-to-peer.**

Secure supports voice messages (up to ~3 minutes) transmitted via the same Ping-Pong Wake protocol:
- **AAC format**: High-quality audio, efficient compression
- **Same security model**: Voice only transmits after recipient authenticates
- **No servers involved**: Voice data never touches third-party infrastructure
- **Encrypted end-to-end**: XChaCha20-Poly1305 AEAD for voice payloads

**Why voice over P2P matters:**
- Traditional messengers store voice messages on servers (metadata exposure)
- Secure voice messages transit peer-to-peer only when recipient confirms availability
- Prevents voice message "inboxes" that can be surveilled or subpoenaed
- Lower attack surface than video or arbitrary file sharing

**Note**: Secure intentionally does NOT support:
- File attachments (prevents malware distribution)
- Images/videos (prevents exploit vectors in media codecs)
- Arbitrary documents (prevents phishing and embedded exploits)

This minimalist approach keeps the attack surface small and the codebase auditable.

---

## ○ How It Works (Simple Version)

### Finding Contacts

**Three-Phase Friend Request Protocol over Tor:**

1. Friend shares QR code with friend-discovery .onion + 10-digit PIN
2. You scan QR code and send PIN-encrypted request to their friend-request.onion
3. They review and accept, sending back their full contact card encrypted with post-quantum hybrid cryptography
4. You send your full contact card back as mutual acknowledgment
5. Both parties now have each other's messaging .onion addresses

**No blockchain. No central directory. Direct peer-to-peer exchange.**

### Sending Messages (Ping-Pong Wake Protocol)

```
1. You: "Hey, ready to receive?" (encrypted PING over Tor)
2. Them: *unlocks phone, sees notification, authenticates*
3. Them: "Ready!" (encrypted PONG over Tor)
4. You: *sends encrypted message/voice directly peer-to-peer*
5. Them: *receives message, sends MESSAGE_ACK*
6. Them: *opens message, sends TAP_ACK (read receipt)*
```

**Nobody in the middle. Messages never sit on a server.**

**4-Tier ACK System provides granular tracking:**
- **PING_ACK**: Recipient's Tor hidden service is reachable
- **PONG_ACK**: Recipient authenticated and confirmed availability
- **MESSAGE_ACK**: Message delivered to recipient's device
- **TAP_ACK**: Recipient opened and viewed the message

### The Technology Stack

- **Cryptography**: XChaCha20-Poly1305 + Ed25519 + X25519 + ML-KEM-1024 (post-quantum)
- **Anonymity**: All traffic through Tor network (triple .onion architecture)
- **Hardware Security**: Keys in StrongBox/TEE (Android)
- **Payments**: Zcash (privacy) + Solana (speed)
- **Database**: SQLCipher with AES-256-GCM encryption

---

## ▣ Features

### ◈ Core Security
- ✓ **Post-Quantum Cryptography** — Hybrid X25519 + ML-KEM-1024 (NIST FIPS 203)
- ✓ **End-to-end encryption** — XChaCha20-Poly1305 AEAD for all messages
- ✓ **Per-message forward secrecy** — Bidirectional key ratcheting
- ✓ **Metadata resistant** — No servers track who, when, or where
- ✓ **Hardware key storage** — Android StrongBox/TEE
- ✓ **No phone numbers** — Wallet-based identity, no registration
- ✓ **Triple .onion architecture** — Friend requests, messaging, voice calling

### ◆ Messaging Features
- ✓ **Ping-Pong Wake Protocol** — Messages only send when recipient confirms
- ✓ **TAP Heartbeat System** — Bidirectional online presence with ACH state machine
- ✓ **4-tier ACK tracking** — PING_ACK → PONG_ACK → MESSAGE_ACK → TAP_ACK
- ✓ **Voice messages** — AAC audio up to ~3 minutes over P2P
- ✓ **Self-destruct timers** — DOD 5220.22-M secure deletion
- ✓ **Duress protection** — Panic PIN wipes everything instantly
- ✓ **Screenshot protection** — Prevents screen capture
- ✓ **Auto-lock** — Configurable inactivity timeout

### ◇ Privacy Features
- ✓ **Three-Phase Friend Protocol** — PIN + post-quantum hybrid encrypted exchange
- ✓ **No exit nodes** — All communication stays within Tor network
- ✓ **No push notifications** — No FCM, no APNs, no third-party infrastructure
- ✓ **Tor VPN mode** — System-wide Tor routing with OnionMasq (Arti)
- ✓ **Pluggable transports** — obfs4, Snowflake, webtunnel for censorship circumvention
- ✓ **Offline-first design** — Messages queue locally, deliver when recipient online

### ○ Payment Features
- ✓ **Multi-chain wallet** — Zcash (ZEC) + Solana (SOL/USDC/USDT)
- ✓ **Secure Pay protocol** — In-chat payments based on NLx402 core logic
- ✓ **Hardware-backed keys** — Wallet keys in StrongBox/TEE
- ✓ **Payment requests** — Request money with custom amounts and memos
- ✓ **Transaction history** — Encrypted local storage

---

## ▸ Use Cases

### ◆ Journalists & Sources
- Protect source anonymity with metadata resistance
- No server logs to subpoena
- Duress PIN if source is compromised
- Post-quantum encryption for long-term secrecy

### ◇ Activists & Organizers
- Coordinate without revealing your network
- Works in censored networks (Tor + pluggable transports)
- No metadata for surveillance
- Offline-first messaging for unreliable connectivity

### ◈ Legal Professionals
- Attorney-client privilege with technical safeguards
- Hardware-backed key storage for compliance
- Demonstrable security for regulatory requirements
- Secure Pay for client payments

### ○ Cryptocurrency Users
- Wallet-based identity (familiar paradigm)
- Integrated payments without switching apps
- Hardware security for wallet keys
- Privacy-first mindset aligned

### ◆ Privacy Advocates
- Maximum security for high-risk conversations
- Open source and auditable
- No compromises on privacy
- Community-driven development

---

## ▣ Project Status

**Current Phase:** Public Beta (v0.7.x) ✓
**Next Phase:** Stability & Performance Improvements ▸

### Roadmap

- [✓] Post-quantum cryptography implementation
- [✓] Triple .onion architecture
- [✓] Three-phase friend request protocol
- [✓] Ping-Pong wake protocol
- [✓] TAP heartbeat system
- [✓] ACH state machine
- [✓] Secure Pay integration
- [✓] Voice messages over P2P
- [✓] Tor VPN mode
- [✓] Public beta launch (Android app)
- [▸] Security audit (ongoing)
- [▸] Performance optimizations
- [▸] UI/UX improvements
- [ ] Group messaging
- [ ] Desktop client

---

## ◈ Why Open Source?

**Trust through transparency.**

Security products that ask for your trust need to prove they deserve it. Secure is open source so:

- ◆ **Anyone can audit** the code for backdoors or vulnerabilities
- ◇ **Security researchers** can verify our claims
- ◈ **Community contributions** make it better
- ○ **Educational resource** for learning secure system design
- ▸ **Freedom** to run your own infrastructure

**"Don't trust, verify."**

---

## ◇ What Secure Does NOT Protect Against

We believe in honest communication about security limitations:

**Not Protected:**
- ✗ Hardware implants in the device itself (physical supply chain attacks)
- ✗ Endpoint security failures (keyloggers, screen recorders, clipboard sniffers)
- ✗ Social engineering attacks (phishing, impersonation)
- ✗ Physical coercion ($5 wrench attack - duress PIN provides limited defense)

**What We DO Protect:**
- ✓ Network surveillance and metadata collection
- ✓ Server compromises (no servers exist with your data)
- ✓ Traffic analysis (Tor hidden services obscure patterns)
- ✓ Future quantum computer attacks (ML-KEM-1024 post-quantum crypto)
- ✓ Key extraction attacks (hardware-backed keys in StrongBox/TEE)

**Know your threat model. Use the right tool for your situation.**

---

## ◆ Technical Deep Dive

Want the technical details? Check out our documentation:

- ▸ [**Android App**](https://github.com/Secure-Legion/android) — Kotlin/Java Android application
- ◈ [**Crypto Library**](https://github.com/Secure-Legion/securelegion-crypto) — Open-source Rust cryptography, CRDT, Tor/Arti, audio, wallet
- ○ [**Download Beta**](https://securelegion.org/download) — Try it yourself
- ◇ [**Documentation**](https://securelegion.org/docs) — Technical architecture
- ▣ [**Roadmap**](https://securelegion.org/roadmap) — Development timeline

---

## ◇ FAQ

### Is this like Signal?

Signal is excellent for message content encryption, but it runs centralized servers that see metadata. Secure eliminates application servers entirely with direct peer-to-peer communication over Tor.

### Is this like Session?

Session is decentralized but all messages route through service nodes that can see timing patterns. Secure's Ping-Pong protocol with TAP heartbeat has zero intermediaries for maximum security.

### Why do I need a cryptocurrency wallet?

The Solana wallet key serves as your messaging identity. This means:
1. No registration with personal info
2. Unforgeable identity (cryptographic proof)
3. Self-sovereign identity (you control it, not a company)
4. Integrated payments for Secure Pay

### Does this cost money?

The app is free. Messaging has no costs (peer-to-peer over Tor). Payments use standard blockchain transaction fees (fractions of a cent on Solana, ~$0.01 for Zcash shielded transactions).

### What about group chats?

Coming in future version. We're focusing on perfect 1-on-1 messaging with post-quantum security first.

### Can I really trust this?

The code is open source. Get a security audit from a firm you trust. Verify the cryptography. Don't trust—verify.

### Why should I use this instead of [X]?

You shouldn't if [X] meets your threat model! Secure is for people who need **metadata resistance and post-quantum security**. That's not everyone. Use the right tool for your needs.

---

## ▸ Get Involved

### For Users
- ◆ **Star this organization** if you support privacy technology
- ◇ **Download the beta** at [securelegion.org/download](https://securelegion.org/download)
- ○ **Share** with journalists, activists, and privacy advocates
- ▸ **Report issues** if you find problems

### For Developers
- ◈ **Contribute code** — See repository CONTRIBUTING.md files
- ◆ **Security review** — Help us find vulnerabilities
- ◇ **Documentation** — Make this accessible to everyone
- ○ **Testing** — Ensure reliability across devices

### For Security Researchers
- ▸ **Cryptographic review** — Verify our crypto implementation
- ◈ **Penetration testing** — Help us harden the system
- ◆ **Academic research** — Publish papers on the protocols
- ◇ **Responsible disclosure** — Email dev@securelegion.org

### For Privacy Advocates
- ○ **Spread awareness** of metadata privacy issues
- ▸ **Policy advocacy** — Support strong encryption laws
- ◈ **Education** — Teach others about threat models

---

## ◆ Contact

- **Website**: [securelegion.org](https://securelegion.org)
- **Email**: contact@securelegion.org
- **Twitter/X**: [@SecureLegion](https://x.com/SecureLegion)
- **GitHub**: [Secure-Legion](https://github.com/Secure-Legion)
- **Address**: 1309 Coffeen Avenue STE 1200, Sheridan, Wyoming 82801

**Security Issues**: dev@securelegion.org (48-hour response for critical vulnerabilities)

---

## ◇ License

**PolyForm Noncommercial License 1.0.0**

Commercial licensing available — contact@securelegion.org

---

## ○ Acknowledgments

Secure builds on the work of privacy and cryptography pioneers:

**Post-Quantum Cryptography:**
- NIST - ML-KEM-1024 standardization (FIPS 203)
- pqc_kyber - Rust implementation

**Cryptography:**
- RustCrypto - XChaCha20-Poly1305 implementation
- Dalek Cryptography - Ed25519 and X25519 primitives
- Argon2 - Password hashing

**Networking:**
- Tor Project - Anonymous routing infrastructure
- Guardian Project - tor-android and OnionMasq
- IPtProxy - Pluggable transports

**Blockchain:**
- Zcash - Privacy-focused cryptocurrency
- Solana - High-performance blockchain
- Electric Coin Company - Zcash Android SDK

**Payment Protocol:**
- PCEF (Perkins Coie Entrepreneur Fund) - 501(c)(3) nonprofit; NLx402 payment protocol core logic

**Special thanks** to the journalists, activists, and whistleblowers who inspired this project by risking everything to expose truth.

---

## ◈ Philosophy

> "Privacy is not about having something to hide. Privacy is about protecting everything you are."

Secure exists because **privacy is a human right**, not a luxury. We believe:

- ○ Everyone deserves private communication
- ◆ Security tools should be open and auditable
- ◇ Different threats need different tools
- ◈ Users should understand their security, not just trust it
- ▸ Privacy technology should empower, not exploit

**We're building the messenger we wish existed when we needed it most.**

---

<p align="center">
  <strong>Secure — Private by Design</strong><br>
  No servers. Metadata resistance. No compromises.
</p>

<p align="center">
  ◆ Star this organization if you believe in privacy ◆
</p>

---

## ◇ Support Development

**Donate to support privacy technology:**

- **Solana (SOL)**: `7i3oi9YFquREM3LgD6KgAxxBsoSooSBRxwKKnKLLKJY2` - **Bitcoin (BTC)**: `bc1q3wdxa7tw6nr93r2tmrg488h4k6jrsj8hk5nzxd` 
- **Ethereum (ETH)**: `0xbD12aF5bf24ded147FBAae1F5795CE9357131F8B` 

---
                                                                Powered by $SECURE 
