# AES_GCM_Python

## General information about AES-GCM
GCM provides data integrity and confidentiality (it belongs to the class of authenticated encryption with associated data - AEAD).
For further information about GCM i recommend to have a look at <i>http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf</i>. You can also have a look at <i>https://en.wikipedia.org/wiki/Galois/Counter_Mode</i>.

## Security
- For any given key, GCM is limited to encrypting 2^39 - 256 bits of plain data (64GiB)!
- It's security depends on a <b>unique nonce for every encryption performed with the same key</b>. Have a look at <i>http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf</i>.
- The authentication strength depends o the length of it's tag. The longer the tag (128 bit / 16 byte maximum) the better. 
- For information about Key Establishment have a look at section 8.1 in <i>http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf</i>.

## Information about my implementation

### General
I use pycryptodomex which you need to install. Example command for pip: pip install pycryptodomex
### nonce
I use a pseudo random nonce with 64 bytes length. If high security is needed or something like file encryption is wanted, I would recommend using a deterministic nonce, like described in section 8.2.1 in <i>http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf</i>. As the pycryptodomex implementation supports 16 byte nonces, I would use a 16 byte nonce. If you change the length of the nonce, the decrypt function must be adapted to the new length.
### authentication tag
I use the longest possible tag length, which ensures the highest possible authentication strength.
### Key Generation
Generates a random key. For information about Key Establishment have a look at section 8.1 in <i>http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf</i>.
