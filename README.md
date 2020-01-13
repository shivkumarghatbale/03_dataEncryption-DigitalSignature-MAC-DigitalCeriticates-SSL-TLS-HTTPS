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

Topic 1.5) encryption vs signature

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

2.1) Authentication over network

What is data signature: Private/public key explained earlier are used here. In case of data encryption generelly sender uses receiver's public key encrypt the data it wants to send to receiver. Receiver upon receiving the data uses it's owen private key to decrypt the message. Whereas signature is reverse case, here sender uses it's own private key to sign randomly generated data. Now user sends signed data and public key to receiver. Receiver uses public key of sender to validated the signed data. In this way receiver validates the sender. Data signature is used in validating the sender. 

There's one more way to perform authentication over n/w by using symmetric key. 
1) Client upon sign-up to a server (i.e. sign up to Gmail) creates paswword.
2) Now, hash of this password is shared with server securely.
3) Server stores this hash of passowrd against the user name in DB.
4) Next time when user logs in, user supplies user-name & password to the server (e.g. Gmail)
5) Either the password or hash of password along with user name is sent to server over secure channel.
6) Server retrives the hash of password from DB for the given user and compares it with hash of password it received as part of sign-in.
7) If hash mathces, then server confirms the identity of user.

https://access.redhat.com/documentation/en-US/Red_Hat_Certificate_System/8.0/html/Deployment_Guide/Introduction_to_Public_Key_Cryptography-Certificates_and_Authentication.html

2.1.a) Use of certificates in client to server authentication

2.1.b) Use of certificates in server to server authetication.

2.2) Data encryption over network


Topic 3) SSL certificates
SSL is a communication protocol that is used for securing communications (transactions) between two parties say client & server. Usually client is your web browser and server is website with whom you are interacting.

SSL: Secure Sockets Layer (SSL) protocol governs server authentication, client authentication, and encrypted communication between servers and clients.SSL is widely used on the Internet, especially for interactions that involve exchanging confidential information such as credit card numbers.





topic 4) Certificates from CA


https over TLS (newer) OR https over SSL (older)

Topic 5) MAC - Message authentication code (Used for authentication as well as integrity of message exchanged)

Topic 5 A) HMAC-SHA256 : Hash based Message Authentication Code. (Using symmetric key)
1) Creater of message first encrypts the message with secret it has, then computes hash. 
2) Creater sends a pair of message (i.e. unencrypted message) & hash computed in step (1) to receiver. (Note: in this type of MAC, user shall not care if the message is read by third party person. Message is not supposed to have sensitive info.)
3) Receiver encrypts the message (i.e. unencrypted message from step (2)) with secret key it has (i.e. creater & receiver should use same key) & computes the hash upon receiving pair of message & hash from sender.
4) If computed hash in step (3) & received hash matches then message is correct.
This way we validate data integrity (if message is modified in the transit, then hash computed by receiver will be different than received hash) and authenticity (i.e. if key used is different then computed hash will be different than received hash)
5) Based on the content of message, receiver would take different actions.

Topic 5 B) RSASHA256 (Using Assymmetric key):
