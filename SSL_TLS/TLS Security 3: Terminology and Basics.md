## Ciphers
Ciphers are methods/algorithms used to encrypt and decrypt data. TLS is a protocol that allows you to use many different methods/algorithms. They are provided as packages called cipher suites. Such a package has a different method/algorithm for each task.

## Block Ciphers
If you use a block cipher, data is split into fixed-length blocks (e.g. 64-bit or 128-bit blocks) and then encrypted. If the last block of data is shorter than the specified block length, the algorithm uses padding to fill the empty space. Blocks are usually padded using random data. Popular block ciphers include **AES**, **Blowfish**, **3DES**, **DES**, and **RC5**.


## Initialization Vector (IV)
An initialization vector is a pseudorandom fixed-size input used in encryption methods. The main purpose of an IV is starting off an encryption method. In cipher modes like Cipher Block Chaining (CBC) each block is XOR-ed with the previous block. In the first block, there is no previous block to XOR with. An Initialization Vector is used as an input to the first block to start off the process.

If IV is unique for each message, it is called a nonce, which means that it can only be used once. A nonce should be unpredictable. It is also used to prevent attackers from decrypting all messages by guessing the IV. If you use a nonce, the same plaintext may be encrypted using the same key into different ciphertext.

## Block Cipher Operation Modes
The block cipher mode of operation defines the relationships between blocks encoded using the cipher. There are different modes that were created to make it more difficult for an attacker to guess the original content of the message.

## Electronic Code Book (ECB)
When using ECB, each block of data is encrypted separately and they are then concatenated in the original order. Parallel processing is possible since blocks do not depend on one another. There is no need for an IV. The major problem of ECB is that if the same block of data is encrypted, it will always generate the same ciphertext. This makes it easier for the attacker to guess the original data based on repeating patterns.

