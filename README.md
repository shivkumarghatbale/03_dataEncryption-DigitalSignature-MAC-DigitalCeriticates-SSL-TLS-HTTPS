Topic 1) RSA 

This involves public key & private key. Receiver of the message sends across the public key to sender of the message.
Sender uses this public key to encrypt the message. Receiver would use private key it has to decrypt the encrypted message.

Note: Message encrypted using public key can only be decrypted by private key. So no other device which is not having private key will not be able to decrypt & read the original message.

RSA cryptography algorithm is also known as Public key encryption.

A limitation of RSA is that you cannot encrypt anything longer than the key size, which is 2048 bits (i.e. 256 bytes) in most of the cases.
(Public key encryption has a limitation that it can encrypt the data upto certain size at once.)
To avoid this limitation in case of large message, RSA can be used in following way:
Public key encryption can also be used to encrypt the symmetric key (symmetric key using which actual data to exchanged in encrypted). With this symmetric key encrypted using public key and data encrypted using symmetric key can be sent over the wire. Receiver in this case using Private key he has decrypts the first part to get symmetric key and using symmetric key decrypts the actual data.  

Another limitation of assymetric encryption is it is high CPU itensive & time consuming since encryption & decryption rely on maths (http://www.muppetlabs.com/~breadbox/txt/rsa.html). So the standard practise is to encrypt the message with symmetric key. And encrypt the symmetric key with Public key of RSA. Receiver has Private key of RSA, receiver would use private key to decrypt & get symmetric key. Use this symmetric key to decrypt the message.

topic 1A) How are the public key, private key pair generated.
http://www.muppetlabs.com/~breadbox/txt/rsa.html

topic 1B) How does symmtric encryption works
How does symmetric encryption work?
Symmetric encryption schemes rely on a single key that is shared between two or more users. The same key is used to encrypt and decrypt the so-called plaintext (which represents the message or piece of data that is being encoded). The process of encryption consists of running a plaintext (input) through an encryption algorithm called a cipher, which in turn generates a ciphertext (output).
If the encryption scheme is strong enough, the only way for a person to read or access the information contained in the ciphertext is by using the corresponding key to decrypt it. The process of decryption is basically converting the ciphertext back to plaintext.
The security of symmetric encryption systems is based on how difficult it randomly guess the corresponding key to brute force them. A 128-bit key, for example, would take billions of years to guess using common computer hardware. The longer the encryption key is, the harder it becomes to crack it. Keys that are 256-bits length are generally regarded as highly secure and theoretically resistant to quantum computer brute force attacks. 
Two of the most common symmetric encryption schemes used today are based on block and stream ciphers. Block ciphers group data into blocks of predetermined size and each block is encrypted using the corresponding key and encryption algorithm (e.g., 128-bit plaintext is encrypted into 128-bit ciphertext). On the other hand, stream ciphers do not encrypt plaintext data by blocks, but rather by 1-bit increments (1-bit plaintext is encrypted into 1-bit ciphertext at a time).

The first major symmetric algorithm developed for computers in the United States was the Data Encryption Standard (DES), approved for use in the 1970s. The DES uses a 56-bit key.
DES has been replaced by the Advanced Encryption Standard (AES), which uses 128-, 192- or 256-bit keys

KEY of symmetric key encryption:
Think of the key as a decoder ring: the secret of the scrambled text cannot be read without the key. The key holds the information on all the switches and substitutions made to the original plain text. 
In symmetric encryption, the key is actually bundled with the algorithm; in this sense, the decoder ring is not universal. The changes and substitutions depend on the key, and vice versa because the sender and recipient share the key. 

DES:
As a symmetric encryption method, DES takes two inputs: the plaintext and the secret key (the same key is used for decryption). DES is a 64 bit block cipher, because the key works only on 64 bits of data at a time. They key itself is actually 56 bits, with 8 bits used for error checking. 
Once the message is received, it is split into 64 bit blocks of data. DES carries out several iterations and substitutions throughout the message in order to make it harder to crack the code.


Symmetric vs. asymmetric encryption
Symmetric encryption is one of the two major methods of encrypting data in modern computer systems. The other is asymmetric encryption, which is the major application of public key cryptography. The main difference between these methods is the fact that asymmetric systems use two keys rather than the one employed by the symmetric schemes. One of the keys can be publicly shared (public key), while the other must be kept in private (private key).
The use of two keys instead of one also produces a variety of functional differences between symmetric and asymmetric encryption. Asymmetric algorithms are more complex and slower than the symmetric ones. Because the public and private keys employed in asymmetric encryption are to some degree mathematically related, the keys themselves must also be considerably longer to provide a similar level of security offered by shorter symmetric keys.


Advantages and disadvantages
Symmetric algorithms provide a fairly high level of security while at the same time allowing for messages to be encrypted and decrypted quickly. The relative simplicity of symmetric systems is also a logistical advantage, as they require less computing power than the asymmetric ones. In addition, the security provided by symmetric encryption can be scaled up simply by increasing key lengths. For every single bit added to the length of a symmetric key, the difficulty of cracking the encryption through a brute force attack increases exponentially.
While symmetric encryption offers a wide range of benefits, there is one major disadvantage associated with it: the inherent problem of transmitting the keys used to encrypt and decrypt data. When these keys are shared over an unsecured connection, they are vulnerable to being intercepted by malicious third parties. If an unauthorized user gains access to a particular symmetric key, the security of any data encrypted using that key is compromised. To solve this problem, many web protocols use a combination of symmetric and asymmetric encryption to establish secure connections. Among the most prominent examples of such a hybrid system is the Transport Layer Security (TLS) cryptographic protocol used to secure large portions of the modern internet.



HMAC-256 : Hash based Message Authentication Code.
Creater first encrypts the message with secret it has, then computes hash. 
Creater sends message (i.e. unencrypted message) & hash to receiver.
Receiver encrypts the message with secret key (i.e. creater & receiver should use same key) & computes the hash.
If computed hash & received hash matches then message is correct.
This way we validate data integrity (if message is modified in the transit, then hash computed by receiver will be different than received hash) and authenticity (i.e. if key used is different then computed hash will be different than received hash)

RSASHA256 :
