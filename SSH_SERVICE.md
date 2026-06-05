[---

## **File 3: `SSH_SERVICE.md`**

```markdown
# Deep-Dive: SSH Service & Cryptographic Infrastructure Security

## 1. Architectural Placement & Cryptographic Handshake
The Secure Shell (SSH) protocol operates over **Port 22** on standard TCP connections. It provides an encrypted, authenticated transport tunnel across untrusted perimeters, replacing insecure legacy cleartext protocols like Telnet.

### Cryptographic Handshake Pipeline
When establishing a session with the SSH daemon (`sshd`), the protocol cascades across three distinct cryptographic layers:

```text
[Client]                                                         [Server (sshd)]
   │                                                                    │
   ├────── 1. Asymmetric Key Exchange (Diffie-Hellman / RSA) ───────────┤
   │       * Identity Validation & Verification                         │
   │       * Generation of Session Key                                  │
   │                                                                    │
   ├────── 2. Symmetric Encryption Tunnel (AES-GCM / ChaCha20) ─────────┤
   │       * Bulk Data Transmission Enclosed                            │
   │                                                                    │
   └────── 3. Cryptographic Data Integrity (HMAC SHA-256) ──────────────┘
           * Tamper-Proof Packet Validation]
