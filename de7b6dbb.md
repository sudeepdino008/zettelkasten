---
date: 2021-05-15T21:16
---

# Cryptography

## public key cryptography
- encryption of messages is one usecase: symmetric (con is a need to exchange keys over a separate secure channel) and asymmetric ( usually inefficient)
- Kerchkhoff's principle: the security of system must depend on the strength of the secret key and not on the complexity/obscurity of algorithm i.e. "security through obscutity" is not acceptable.
- another use case is authentication: knowing that a message was send by the right person and not a malicious party. Here, a shared key K is present, and a known authentication function `h(K, m)` is known. The message authentication code (MAC) generated is sent along with the message. The receiving party would verify by checking if `h(K,m) = a`. If not, the receiver knows that it was know signed by the expected sender.
 
- since asymmetric or public-key cryptography is inefficient, modern systems use a hybrid approach of establishing a shared secret key using PK cryptography, and then using symmetric key encryption.

- Public key infrastructure (PKI): associating identiy with public keys - "how do i know that this person owns this public key?"  
Certificate authorities, web of trust egc.

- cryptocurrencies have no inbuilt PKI: "not your keys, not your coins"
