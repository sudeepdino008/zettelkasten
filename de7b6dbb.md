---
date: 2021-05-15T21:16
---

# Cryptocurrency: Cryptography

## public key cryptography
- encryption of messages is one usecase: symmetric (con is a need to exchange keys over a separate secure channel) and asymmetric ( usually inefficient)
- Kerchkhoff's principle: the security of system must depend on the strength of the secret key and not on the complexity/obscurity of algorithm i.e. "security through obscutity" is not acceptable.
- another use case is authentication: knowing that a message was send by the right person and not a malicious party. Here, a shared key K is present, and a known authentication function `h(K, m)` is known. The message authentication code (MAC) generated is sent along with the message. The receiving party would verify by checking if `h(K,m) = MAC`. If yes, the receiver knows that it was know signed by the expected sender.
 
- since asymmetric or public-key cryptography is inefficient, modern systems use a hybrid approach of establishing a shared secret key using PK cryptography, and then using symmetric key encryption.

- symmetric or asymmetric cryptography allows you to securely communicate with someone else. But how do you know if that someone else is trustworthy? - **Public Key Infrastructure (PKI)**

- PKI: associating identiy with public keys - "how do i know that this person owns this public key?"  
Certificate authorities, web of trust egc.

- cryptocurrencies have no inbuilt PKI: "not your keys, not your coins"


## public keys != Addresses
following is for bitcoin:
- your address is `A(pk)` where `A` is a rather convoluted multi-hashing process. Thus. **P2PKH** ("pay to public key hash") as opposed to **P2PK** ("pay to public key")
- addresses are represented in **Base58Check** format - [1-9A-Za-z] without capital 'O', 0, 'l', 'I' - to  avoid confusion. Also includes a 4 byte checksum at the end.

### asymmetric key and digital signatures
- [[[5b23c238]]]

