Topic 1) Data encryption 

Topic 1.1) Assymetric encryption.
This involves public key & private key. Receiver of the message sends across the public key to sender of the message.
Sender uses this public key to encrypt the message. Receiver would use private key it has to decrypt the encrypted message.

Note: Message encrypted using public key can only be decrypted by private key. So no other device which is not having private key will not be able to decrypt & read the original message.

RSA is an assymetric encryption.
RSA cryptography algorithm is also known as Public key encryption.

A limitation of RSA is that you cannot encrypt anything longer than the key size, which is 2048 bits (i.e. 256 bytes) in most of the cases.
(Public key encryption has a limitation that it can encrypt the data upto certain size at once.)
To avoid this limitation in case of large message, RSA can be used in following way:
Public key encryption can also be used to encrypt the symmetric key (symmetric key using which actual data to exchanged in encrypted). With this symmetric key encrypted using public key and data encrypted using symmetric key can be sent over the wire. Receiver in this case using Private key he has decrypts the first part to get symmetric key and using symmetric key decrypts the actual data.  

Another limitation of assymetric encryption is it is high CPU itensive & time consuming since encryption & decryption rely on complex maths formulas (http://www.muppetlabs.com/~breadbox/txt/rsa.html). So the standard practise is to encrypt the message with symmetric key. And encrypt the symmetric key with Public key of RSA. Receiver has Private key of RSA, receiver would use private key to decrypt & deduce symmetric key. Use this symmetric key to decrypt the message.

topic 1.1 A) How are the public key, private key pair generated.
http://www.muppetlabs.com/~breadbox/txt/rsa.html

topic 1.2) Symmetric encryption

topic 1.2A) How does symmetric encryption work?
Symmetric encryption schemes rely on a single key that is shared between two or more users. The same key is used to encrypt and decrypt the so-called plaintext (which represents the message or piece of data that is being encoded). The process of encryption consists of running a plaintext (input) through an encryption algorithm called a cipher, which in turn generates a ciphertext (output).
If the encryption scheme is strong enough, the only way for a person to read or access the information contained in the ciphertext is by using the corresponding key to decrypt it. The process of decryption is basically converting the ciphertext back to plaintext.
The security of symmetric encryption systems is based on how difficult it randomly guess the corresponding key to brute force them. 

A 128-bit key, for example, would take billions of years to guess using common computer hardware. The longer the encryption key is, the harder it becomes to crack it. Keys that are 256-bits length are generally regarded as highly secure and theoretically resistant to quantum computer brute force attacks. 

Two of the most common symmetric encryption schemes used today are based on block and stream ciphers. Block ciphers group data into blocks of predetermined size and each block is encrypted using the corresponding key and encryption algorithm (e.g., 128-bit plaintext is encrypted into 128-bit ciphertext). On the other hand, stream ciphers do not encrypt plaintext data by blocks, but rather by 1-bit increments (1-bit plaintext is encrypted into 1-bit ciphertext at a time).

The first major symmetric algorithm developed for computers in the United States was the Data Encryption Standard (DES), approved for use in the 1970s. The DES uses a 56-bit key.
DES has been replaced by the Advanced Encryption Standard (AES), which uses 128-, 192- or 256-bit keys

KEY of symmetric key encryption:
Think of the key as a decoder ring: the secret of the scrambled text cannot be read without the key. The key holds the information on all the switches and substitutions made to the original plain text. 
In symmetric encryption, the key is actually bundled with the algorithm; in this sense, the decoder ring is not universal. The changes and substitutions depend on the key, and vice versa because the sender and recipient share the key. 

DES:
As a symmetric encryption method, DES takes two inputs: the plaintext and the secret key (the same key is used for decryption). DES is a 64 bit block cipher, because the key works only on 64 bits of data at a time. They key itself is actually 56 bits, with 8 bits used for error checking. 
Once the message is received, it is split into 64 bit blocks of data. DES carries out several iterations and substitutions throughout the message in order to make it harder to crack the code.


Topic 1.3) Symmetric vs. asymmetric encryption
Symmetric encryption is one of the two major methods of encrypting data in modern computer systems. The other is asymmetric encryption, which is the major application of public key cryptography. The main difference between these methods is the fact that asymmetric systems use two keys rather than the one employed by the symmetric schemes. One of the keys can be publicly shared (public key), while the other must be kept in private (private key).
The use of two keys instead of one also produces a variety of functional differences between symmetric and asymmetric encryption. Asymmetric algorithms are more complex and slower than the symmetric ones. Because the public and private keys employed in asymmetric encryption are to some degree mathematically related, the keys themselves must also be considerably longer to provide a similar level of security offered by shorter symmetric keys.


Topic 1.4) Advantages and disadvantages
Symmetric algorithms provide a fairly high level of security while at the same time allowing for messages to be encrypted and decrypted quickly. The relative simplicity of symmetric systems is also a logistical advantage, as they require less computing power than the asymmetric ones. In addition, the security provided by symmetric encryption can be scaled up simply by increasing key lengths. For every single bit added to the length of a symmetric key, the difficulty of cracking the encryption through a brute force attack increases exponentially.
While symmetric encryption offers a wide range of benefits, there is one major disadvantage associated with it: the inherent problem of transmitting the keys used to encrypt and decrypt data. When these keys are shared over an unsecured connection, they are vulnerable to being intercepted by malicious third parties. If an unauthorized user gains access to a particular symmetric key, the security of any data encrypted using that key is compromised. To solve this problem, many web protocols use a combination of symmetric and asymmetric encryption to establish secure connections. Among the most prominent examples of such a hybrid system is the Transport Layer Security (TLS) cryptographic protocol used to secure large portions of the modern internet.

Topic 1.5) encryption vs signature vs MAC
Sender has assymetric key or public key of receiver. Sender encrypts the message. "Data is sent securely." This is data encryption.
Sender has it's own private key and receiver has public key corresponding to private key. Sender signs the message and then sends original message, signature. Receiver using public key verifies the signature generated by signing original message is same as signature received. "Authenticates sender and verifies data integrity". This is digital signature. (Note: message sent over n/w is not secured in this mode)

A digital signature scheme is a triple of probabilistic polynomial time algorithms, (G, S, V), satisfying: 
G (key-generator) generates a public key (pk), and a corresponding private key (sk), on input 1n, where n is the security parameter.
S (signing) returns a tag, t, on the inputs: the private key (sk), and a string (x). (tag AKA signature)
V (verifying) outputs accepted or rejected on the inputs: the public key (pk), a string (x), and a tag (t). (Accepts if tag t matches signature generated at receivers end by signing string (x) with public key (pk). Sign would not match if string (x) is changed in message transit (this verifying data integrity) OR if tag (t) is generated by other key than private key (sk) (this verifies authenticity).  Sign would only match if string (x) is not modified in transit & tag (t) is generated by private key (sk) which corresponds to public key (pk) generated in step G.

One digital signature scheme (of many) is based on RSA. To create signature keys, generate a RSA key pair containing a modulus, N, that is the product of two random secret distinct large primes, along with integers, e and d, such that e d ≡ 1 (mod φ(N)), where φ is the Euler phi-function (Basicaly φ(N) = no of co-prime number with N from 0 to N. If N is product of two prime numbers P,Q, then φ(N) = (P-1) * (Q-1)).  The signer's public key consists of N and e, and the signer's secret key contains d. 

Signature: To sign a message, m, the signer computes a signature, σ, such that σ ≡ md (mod N). To verify, the receiver checks that σ^e ≡ m (mod N).
(Encryption: On the other hand, if it's encryption then C = m^e (mod N) (where C is encrypted data for message m. N & e forms the public key). And m = c^d (mod N). N & c forms the private key).

As explained earlier, for digital signature, the actual message & signature is shared with receiver (And receiver verifies the sign & message according to above formula i.e. signature ^ e = message (mod N) where e,N are part of public key).
The problem is it's vulnerable to attacks. So instead of signing the message, we first hash the message then sign. Receiver at other end descrypts sign to get the hash. Then compute the hash for the message & if both the hash matches, then verification succeeds.

There are several reasons to sign such a hash (or message digest) instead of the whole document. 
- For efficiency
        The signature will be much shorter and thus save time since hashing is generally much faster than signing in practice.
- For compatibility
        Messages are typically bit strings, but some signature schemes operate on other domains (such as, in the case of RSA, numbers modulo a composite number N). A hash function can be used to convert an arbitrary input into the proper format.
- For integrity
        Without the hash function, the text "to be signed" may have to be split (separated) in blocks small enough for the signature scheme to act on them directly. However, the receiver of the signed blocks is not able to recognize if all the blocks are present and are he appropriate order.

Hence, encryption = send data secretely AND signature = state the authority of sender, data integrity (The purpose of encryption is to send a message secretly (confidentially) to the receiver. The purpose of digital signature is to prove your identity and your authorization of the document to any one who may be interested with it.)

MAC: Here sender and receiver share the same key. Sender first computes the hash of message & encrypts using key and sends across (unencrypted) message and encrypted hash. Receiver decrypts the encrypted hash using key to get hash of message & computes hash of (unencrypted) message received. If match occuers then verification (& data integrity) checks are done. 

Cryptographic primitive | Hash |    MAC    | Digital
Security Goal           |      |           | signature
------------------------+------+-----------+-------------
Integrity               |  Yes |    Yes    |   Yes
Authentication          |  No  |    Yes    |   Yes
Non-repudiation         |  No  |    No     |   Yes
------------------------+------+-----------+-------------
Kind of keys            | none | symmetric | asymmetric
                        |      |    keys   |    keys

Integrity: Can the recipient be confident that the message has not been accidentally modified?
Authentication: Can the recipient be confident that the message originates from the sender?
Non-repudiation: If the recipient passes the message and the proof to a third party, can the third party be confident that the message originated from the sender?

Both MAC & Digital signature does not gurrenty secrecy of message shared, whereas encryption gurrenties the secrecy of message shared.
(MAC is same as access key based AAD authentication. And digital signature is same as certificate based AAD authentication)

Topic 1.6) Digitial signature vs digital certificate
Digital Signature is an attachment to the electronic document which can be viewed as a signature. Once a document is signed, its data can not be altered without invalidating the signature. Digital Signature is created using signer’s key for encrypting the document.

A Digital Certificate is simply a computer file which helps in establishing your identity. It officially approves the relation between the holder of the certificate (the user) and a particular public key. Thus, a digital certificate should include the user name and the user’s public key. This will prove that the certain public key owned by a particular user.
A digital certificate consists of the following information: Subject name (User’s name is referred to as Subject name because a digital certificate can be issued to an individual, a group or an organization), Serial number, Validity date range and issuer name, etc.

digital certificates are used to verify the trustworthiness of a person (sender), while digital signatures are used to verify the trustworthiness of the data being sent.

The digital signature proves the authenticity of the digital document. On the other hand, digital certificate identifies the website.
A digital certificate is digitally signed and can be used to sign other documents digitally. Digital signature of CA is verified on the digital certificate.
Digital certificate creation process includes key generation, registration, verification and creation steps. In contrast, Digital signature process includes encryption and decryption of the message at the sender’s and receiver’s end respectively.

A) Authentication & security for message: 
A is sender of message and B is receiver of message. 
A has public key of B (PubKeyB) and B has public key of A (PubKeyA)
A has message M. A creates hash of of message M (Hash(M) = H).
A creats a signature (S) using it's private key (PriKeyA) and Hash of message (H) 
A encrypts the message M with B's PubKeyB (EM).
A sends encrypted message (EM) and digitial signature (S) to B.
B using PriKeyB decrypts EM to get M.
B hashes M to get H
B uses PubKeyA & signature S to get H. If both the hashes matches then it validates the authenticity of the message. Amd since encrypted message EM was sent over the n/w this ensures secureness of the message over n/w.


B) Authentication & security for message using SSL certificate: 
A is sender of message and B is receiver of message. 
A asks for B's SSL certificate.
A gets B's SSL certificate. SSL certificate has digital signature of trusted CA. A using public key of trusted CA verifies the digitial signature of trusted CA. Thus A validates identity of B. (i.e. A trusts CA since certificate has CA's signature)
A generates symmetric key and it encrypts using public key in certicate and sends it to B.
B decrypts the encrypted message using it's private key to get the symmetric key.
Now this symmetric key is used for sending data A to B and/or B to A. 
Since data encryption/decryption is faster using symmetric key (Assymetric encryption is nothing but a big mathematical formula which is high CPU intensive hence is avoided in longer/ more messages encryptions) this approach is preffered than earlier one where actual data was encrypted using public key.

Topic 2) Certificates
Certificates have a purpose: to establish trust.

What all the things a certificate generally has?
- certificate version number
- Certificate issuer (e.g. CN = Thawte RSA CA 2018, OU = www.digicert.com, O = DigiCert Inc, C = US)   (CN - CN stands for common name, generally DNS name)
- Certificate Thumbprint (e.g. cdab029a5d8270733d3c23780de47311e90f27fe)
- Certificate serial number (e.g. 05a0622301d54be4288bb743e2f2b510)
- Certificate valid from (e.g. 22 May 2018 05:30:00)
- Certificate valid to (e.g. 20 June 2020 17:30:00)
- Subject (CN = quora.com)
- Subject Alternate Name (e.g. DNS Name=*.fs.quoracdn.net, DNS Name=*.qr.ae, DNS Name=*.quora.com, DNS Name=*.tch.quora.com, DNS Name=*.tch.www.quora.com)
- Public key (e.g. 2048 bits in case of RSA)
- Signature hash algorithm (e.g. SHA256)
- Signature algorithm (SHA256RSA) etc

What all the things can be achieved by using certificates:
- Identification / Authentication:
    The persons / entities with whom we are communicating are really who they say they are.

- Confidentiality:
    The information within the message or transaction is kept confidential. It may only be read and understood by the intended sender and receiver.

- Integrity:
    The information within the message or transaction is not tampered accidentally or deliberately with en route without all parties involved being aware of the tampering.

- Non-Repudiation:
    The sender cannot deny sending the message or transaction, and the receiver cannot deny receiving it.

- Access Control:
    Access to the protected information is only realized by the intended person or entity.


Why digital certificate:
the problem with digital signature is that one cannot identify true indentity of sender & it's public key. Digital certificate is a way of associating an entity with a public key. (certificate = entity name + entity public key )

2.1) Authentication over network

https://access.redhat.com/documentation/en-US/Red_Hat_Certificate_System/8.0/html/Deployment_Guide/Introduction_to_Public_Key_Cryptography-Certificates_and_Authentication.html

2.1.a) Use of certificates in client to server authentication

2.1.b) Use of certificates in server to server authetication.

2.2) Data encryption over network


Topic 3) SSL certificates
SSL is a communication protocol that is used for securing communications (transactions) between two parties say client & server. Usually client is your web browser and server is website with whom you are interacting.

SSL: Secure Sockets Layer (SSL) protocol governs server authentication, client authentication, and encrypted communication between servers and clients.SSL is widely used on the Internet, especially for interactions that involve exchanging confidential information such as credit card numbers.

How SSL Certificates Work
A browser or server attempts to connect to a website (i.e. a web server) secured with SSL. The browser/server requests that the web server identify itself.
The web server sends the browser/server a copy of its SSL certificate. 
The browser/server checks to see whether or not it trusts the SSL certificate. (browser/server may choose to validate certificate with CA or validate digital signature of CA on the certificate.) If so, it creates a key, encrypts it using public key of certificate and sends it to web server. Web server decrypts the message using it's private key to get the key of client.
The web server sends back a digitally signed acknowledgement to start an SSL encrypted session.
Encrypted data is shared between the browser/server and the web server.

This way data sent from client to server is encrypted using web server's public key. And data sent from web server to client is encrypted using client's symmetric key. 

HTTP + SSL = HTTPS. HTTPS means communication between browser & web server is encrypted. SSL certificate is web server's digital certificate issued by trusted CA.

How it works:
A is browser and B is web server.
A requests secure pages from B.
B sends it's SSL certificate to A. SSL certificate has digital signature of trusted CA. A using public key of trusted CA verifies the digitial signature of trusted CA. Thus A validates identity of B. (i.e. A trusts CA & certificate has CA's signature that means A trust certificate.)
A generates symmetric key and it encrypts using public key in certicate and sends it to B.
B decrypts the encrypted message using it's private key to get the symmetric key.
Now this symmetric key is used for sending data A to B and/or B to A. 

https over TLS (newer) OR https over SSL (older)

