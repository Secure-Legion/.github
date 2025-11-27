# ◈ Secure Legion LLC

**Private by Design • Serverless • Blockchain Integrated**

A decentralized messaging system that eliminates metadata exposure entirely. While other secure messengers protect your messages, Secure Legion protects your identity, communication patterns, and social network from surveillance. No servers know who you talk to, when you communicate, or where you are.

> The world's first truly metadata-free messaging system. No servers know who you talk to, when you talk, or where you are.

---

## ▸ The Problem We're Solving

### Current Secure Messengers Still Leak Your Privacy

Even the most secure messaging apps today have a dirty secret: **they protect your messages but expose your metadata**.

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

**Secure Legion eliminates metadata entirely.** Not just encrypts it—*eliminates it*.

---

## ◆ What Makes Secure Legion Different

### ◇ Zero Metadata by Design

Traditional secure messengers:
```
You → Signal Server (sees who, when, where) → Recipient
```

Secure Legion:
```
You ←→ Recipient (nobody in the middle)
```

**No servers** know:
- Who you're messaging
- When you're messaging
- Where you're messaging from
- Who's in your contact list
- Your communication patterns

### ◈ Ping-Pong Wake Protocol

**Messages only deliver when the recipient is online AND authenticates with biometric/PIN.** If their device is seized or offline, your message never arrives—ensuring zero failed deliveries and absolute sender control.

**How it works:**
1. **Wake Request**: Your device sends an encrypted "ping" over Tor
2. **Authentication**: Recipient must unlock their device to acknowledge
3. **Direct Delivery**: Message transmits peer-to-peer only after confirmation
4. **4-Tier ACK Tracking**: PING_ACK → PONG_ACK → MESSAGE_ACK → TAP_ACK
5. **Auto-Cleanup**: Messages delete after reading (or on timer)

**Why this matters:**
- No messages sitting on servers waiting to be compromised
- Active consent required for every message received
- Complete visibility into delivery status at each step
- If recipient's device is seized, your undelivered message never arrives

**Perfect for:**
- Sensitive sources and high-risk conversations
- When absolute security matters more than convenience
- Anyone who needs guaranteed metadata-free communication

### ◆ Your Wallet = Your Identity

Your cryptocurrency wallet isn't just for money—it's your messaging identity.

- **One key, two uses**: The same key secures your crypto *and* your messages
- **No phone numbers**: No email, no username, no personally identifiable information
- **Hardware protected**: Keys stored in your phone's security chip, never exposed
- **Multiple identities**: Create disposable identities for different conversations

### ◇ Panic Button Protection

**Duress PIN**: Enter your emergency PIN and Secure Legion:

1. **Wipes** all your keys and messages instantly
2. **Notifies** all your contacts to delete queued messages for you
3. **Appears** like a normal authentication failure (can't be detected)
4. **Restores** from your secret recovery phrase when safe

No evidence left behind. No messages waiting to be delivered. No metadata to analyze.

### ○ Voice Messages Over P2P

**Send encrypted voice recordings directly peer-to-peer.**

SecureLegion supports voice messages (up to ~3 minutes) transmitted via the same Ping-Pong Wake protocol:
- **AAC format**: High-quality audio, efficient compression
- **Same security model**: Voice only transmits after recipient authenticates
- **No servers involved**: Voice data never touches third-party infrastructure
- **Encrypted end-to-end**: XChaCha20-Poly1305 AEAD for voice payloads

**Why voice over P2P matters:**
- Traditional messengers store voice messages on servers (metadata exposure)
- SecureLegion voice messages transit peer-to-peer only when recipient confirms availability
- Prevents voice message "inboxes" that can be surveilled or subpoenaed
- Lower attack surface than video or arbitrary file sharing

**Note**: SecureLegion intentionally does NOT support:
- File attachments (prevents malware distribution)
- Images/videos (prevents exploit vectors in media codecs)
- Arbitrary documents (prevents phishing and embedded exploits)

This minimalist approach keeps the attack surface small and the codebase auditable.

---

## ○ How It Works (Simple Version)

### Finding Contacts

1. Everyone publishes an encrypted "contact card" on the blockchain
2. Only people who know your handle can find your card
3. Your card is encrypted—even the blockchain can't read it
4. No central directory = no list of all users

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

- **Blockchain**: Solana (fast & cheap) + IPFS via Crust Network for decentralized storage
- **Encryption**: Military-grade XChaCha20-Poly1305 + Ed25519 signatures + X25519 ECDH
- **Anonymity**: All traffic through Tor network
- **Hardware Security**: Keys in StrongBox (Android)

---

## ▣ Features

### ◈ Core Security
- ✓ **End-to-end encryption** for all messages (XChaCha20-Poly1305)
- ✓ **Zero metadata exposure** — no servers track anything
- ✓ **Forward secrecy** — ephemeral X25519 key exchange
- ✓ **No phone numbers** or personal identifiers required
- ✓ **Decentralized** — no company to compel or hack
- ✓ **Hardware key storage** — Android StrongBox/TEE

### ◆ Messaging Features
- ✓ **Ping-Pong Wake Protocol** — Messages only send when recipient confirms
- ✓ **4-tier ACK system** — Track delivery at every step (PING/PONG/MESSAGE/TAP)
- ✓ **Voice messages** — AAC audio up to ~3 minutes over P2P
- ✓ **Self-destruct timers** — DOD 5220.22-M secure deletion
- ✓ **Duress protection** — Panic PIN wipes everything
- ✓ **Blockchain identity** — Wallet-based, no registration
- ✓ **Screenshot protection** — Prevents screen capture and recording
- ✓ **Auto-lock** — Configurable inactivity timeout (30s-10min)

### ◇ Power User Features
- ✓ **Burner identities** — Create disposable identities
- ✓ **Open source** — Fully auditable code
- ✓ **No proprietary protocols** — Everything is documented
- ✓ **Tor bridges** — Snowflake, obfs4, meek for censorship circumvention

---

## ▸ Use Cases

### ◆ Journalists & Sources
- Protect source anonymity absolutely
- No server logs to subpoena
- Duress PIN if source is compromised

### ◇ Activists & Organizers
- Coordinate without revealing your network
- No metadata for surveillance
- Works in censored networks (via Tor)

### ◈ Legal Professionals
- Attorney-client privilege with technical safeguards
- No server to compromise
- Demonstrable security for compliance

### ○ Cryptocurrency Users
- Already understand wallet concepts
- Unified identity for finance + messaging
- Privacy-first mindset aligned

### ◆ Privacy Advocates
- Maximum security for those who need it
- Open source and auditable
- No compromises on privacy

---

## ▣ Project Status

**Current Phase:** Public Beta (v0.2.x) ✓
**Next Phase:** Stability & Performance Improvements ▸

### Roadmap

- [✓] Complete architecture design
- [✓] Security model documentation
- [✓] Core cryptographic library (Rust JNI)
- [✓] Blockchain integration (Solana + Crust Network IPFS)
- [✓] Ping-Pong Wake Protocol implementation
- [✓] Voice message support over P2P
- [✓] 4-tier ACK delivery tracking
- [✓] Public beta launch (Android app)
- [▸] Security audit (ongoing)
- [▸] Performance optimizations
- [▸] UI/UX improvements
- [ ] Group messaging
- [ ] Desktop client

---

## ◈ Why Open Source?

**Trust through transparency.**

Security products that ask for your trust need to prove they deserve it. Secure Legion is open source so:

- ◆ **Anyone can audit** the code for backdoors or vulnerabilities
- ◇ **Security researchers** can verify our claims
- ◈ **Community contributions** make it better
- ○ **Educational resource** for learning secure system design
- ▸ **Freedom** to run your own infrastructure

**"Don't trust, verify."** — Cryptocurrency saying that applies to secure messaging too

---

## ◇ What Secure Legion Does NOT Protect Against

We believe in honest communication about security limitations:

✗ **Compromised devices**: If your phone has malware, no app can protect you
✗ **Physical access**: Someone with your unlocked phone can see your messages
✗ **Screenshots**: We prevent screen capture, but can't stop cameras pointed at your screen
✗ **Endpoint attacks**: Attacks on your device itself are outside our threat model
✗ **Social engineering**: Technology can't fix human vulnerabilities

**What we DO protect:**
✓ Network surveillance and metadata collection
✓ Server compromises (because there are no servers with your data)
✓ Traffic analysis
✓ Social graph exposure
✓ Location tracking through messaging activity

Know your threat model. Use the right tool for your situation.

---

## ◆ Technical Deep Dive

Want the technical details? Check out our documentation:

- ▸ [**Architecture Documentation**](docs/architecture.md) — Complete technical specification
- ◈ [**Security Model**](docs/security.md) — Threat model and security guarantees
- ○ [**Ping-Pong Protocol**](docs/pingpong.md) — How our novel wake system works
- ◇ [**Blockchain Integration**](docs/blockchain.md) — Decentralized identity design
- ▣ [**Developer Guide**](docs/development.md) — Contributing to Secure Legion

---

## ◇ FAQ

### Is this like Signal?

Signal is excellent for message content encryption, but it runs centralized servers that see metadata. Secure Legion eliminates the servers entirely with direct peer-to-peer communication over Tor.

### Is this like Session?

Session is decentralized but all messages route through service nodes that can see timing patterns. Secure Legion's Ping-Pong mode has zero intermediaries for maximum security conversations.

### Why do I need a cryptocurrency wallet?

The wallet key serves as your messaging identity. This means:
1. No registration with personal info
2. Unforgeable identity (cryptographic proof)
3. Cross-chain support (use same identity on different blockchains)
4. Self-sovereign identity (you control it, not a company)

### Does this cost money?

Basic usage costs fractions of a cent (for blockchain directory updates).

### What about group chats?

Coming in future version. We're focusing on perfect 1-on-1 messaging first.

### Can I really trust this?

The code is open source. Get a security audit from a firm you trust. Verify the cryptography. Don't trust—verify.

### Why should I use this instead of [X]?

You shouldn't if [X] meets your threat model! Secure Legion is for people who need **absolutely no metadata leakage**. That's not everyone. Use the right tool for your needs.

---

## ▸ Get Involved

### For Users
- ◆ **Star this repo** if you support privacy technology
- ◇ **Share** with journalists, activists, and privacy advocates
- ○ **Suggest features** that would help your use case
- ▸ **Report issues** if you find problems

### For Developers
- ◈ **Contribute code** (see [CONTRIBUTING.md](CONTRIBUTING.md))
- ◆ **Security review** — help us find vulnerabilities
- ◇ **Documentation** — help make this accessible
- ○ **Testing** — ensure reliability across platforms

### For Security Researchers
- ▸ **Bug bounty program** (coming with public beta)
- ◈ **Academic research** — publish papers on the protocol
- ◆ **Cryptographic review** — verify our crypto implementation
- ◇ **Penetration testing** — help us harden the system

### For Privacy Advocates
- ○ **Spread awareness** of metadata privacy issues
- ▸ **Policy advocacy** — support strong encryption
- ◈ **Donations** — support development (details coming soon)


---

## ◆ Contact

- **Website**: [www.securelegion.org]
- **Email**: [info@securelegion.org]
- **Twitter/X**: [https://x.com/SecureLegion]
- **GitHub Issues**: [Right Here](../../issues)
- **Address**: [1309 Coffeen Avenue STE 1200
Sheridan Wyoming 82801]


**Security Disclosures**: Please report vulnerabilities responsibly via [SECURITY.md](SECURITY.md)

---

## ◇ License

PolyForm Noncommercial License 1.0.0

---

## ○ Acknowledgments

Secure Legion builds on the shoulders of giants:

- **Tor Project** — Anonymous communication infrastructure
- **Solana Foundation** — Fast, affordable blockchain
- **IPFS/Crust Network** — Decentralized storage
- **All privacy researchers** — Whose work makes this possible

Special thanks to the journalists, activists, and whistleblowers who inspired this project by risking everything to expose truth.

---

## ◈ Philosophy

> "Privacy is not about having something to hide. Privacy is about protecting everything you are."

Secure Legion exists because **privacy is a human right**, not a luxury. We believe:

- ○ Everyone deserves private communication
- ◆ Security tools should be open and auditable
- ◇ Different threats need different tools
- ◈ Users should understand their security, not just trust it
- ▸ Privacy technology should empower, not exploit

**We're building the messenger we wish existed when we needed it most.**

---

<p align="center">
  <strong>Secure Legion LLC — Private by Design</strong><br>
  No servers. No metadata. No compromises.
</p>

<p align="center">
  ◆ Star this repo if you believe in privacy ◆
</p>

---

CA: GFJbQ7WDQry73iTaGkJcXKjvi1ViFTFmHSENgz92jFPP
