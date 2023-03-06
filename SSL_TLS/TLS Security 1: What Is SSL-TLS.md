Secure Sockets Layer (SSL) and Transport Layer Security (TLS) are cryptographic security protocols. They are used to make sure that network communication is secure. Their main goals are to provide _data integrity_ and _communication privacy_. SSL is now considered obsolete and insecure (even its latest version), so modern browsers such as Chrome or Firefox use TLS instead.

SSL and TLS are commonly used by web browsers to protect connections between web applications and web servers. Many other TCP-based protocols use TLS/SSL as well, including email (SMTP/POP3), instant messaging (XMPP), FTP, VoIP, VPN, and others.

Typically, when a service uses a secure connection the letter S is appended to the protocol name, for example, HTTPS, SMTPS, FTPS, SIPS. In most cases, SSL/TLS implementations are based on the OpenSSL library.

SSL and TLS are frameworks that use a lot of different cryptographic algorithms, for example, RSA and various Diffie–Hellman algorithms. The parties agree on which algorithm to use during initial communication.

SSL/TLS protocols use public-key cryptography. Except for encryption, this technology is also used to authenticate communicating parties. This means, that one or both parties know exactly who they are communicating with. This is crucial for such applications as online transactions because must be sure that we are transferring money to the person or company who are who they claim to be.

When a secure connection is established, the server sends its SSL/TSL certificate to the client. The certificate is then checked by the client against a trusted Certificate Authority CA, validating the server’s identity. Such a certificate cannot be falsified, so the client may be one hundred percent sure that they are communicating with the right server.

**Perfect forward secrecy (PFS)** is a mechanism that is used to protect the client if the private key of the server is compromised. Thanks to PFS, the attacker is not able to decrypt any previous TLS communications. To ensure perfect forward secrecy, we _use new keys for every session._ These keys are _valid only as long as the session is active_.

## what is openssl
OpenSSL is an open-source software library that provides a set of cryptographic functions, including encryption, decryption, digital signature generation and verification, and other related functions. It is widely used in a variety of applications, including web servers, email servers, and other types of networked applications that require secure communication.

OpenSSL supports a wide range of cryptographic algorithms, including symmetric-key algorithms like **AES**, **DES**, and **Blowfish**, as well as public-key algorithms like **RSA**, **Diffie-Hellman**, and **Elliptic Curve Cryptography (ECC)**. It also provides support for SSL/TLS protocols, which are used to establish secure communication channels over the internet.

In addition to the library itself, OpenSSL also includes a command-line tool called "`openssl`" that can be used to perform various cryptographic operations, including generating cryptographic keys and certificates, encrypting and decrypting data, and testing SSL/TLS connections. The `openssl` command can be used to perform a wide range of tasks related to cryptography and security, and is a popular tool among system administrators, security professionals, and developers.





