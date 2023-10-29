# Advanced Encryption Standard 128-bit (AES-128)

## Description

This is a simple implementation of the Advanced Encryption Standard 128 bits (AES-128) cipher in Python 3. AES-128 is a symmetric block cipher that encrypts and decrypts 128-bit blocks of data using keys of 128 bits. This implementation supports the ECB and CTR modes of operation. When using the CTR mode, the initialization vector (IV) must be 128 bits long.

## Module Usage

```python
from AES import encrypt, decrypt, Mode

plain_text = b"plain text"
key = bytes.fromhex("2b7e151628aed2a6abf7158809cf4f3c")
iv = bytes.fromhex("00112233445566778899aabbccddeeff")

# Encoding
cipher_text = encrypt(plain_text, key, Mode.CTR, iv)

# Decoding
plain_text = decrypt(cipher_text, key, Mode.CTR, iv)

```

## CLI Usage

```bash
usage: AES.py [-h] -in INPUT_FILE -out OUTPUT_FILE [-e] [-d] -k KEY [-iv IV] [-r ROUNDS] [-m {ECB,CTR}] [-v]

options:
  -h, --help            show this help message and exit
  -in INPUT_FILE, --input_file INPUT_FILE
  -out OUTPUT_FILE, --output_file OUTPUT_FILE
  -e, --encrypt
  -d, --decrypt
  -k KEY, --key KEY
  -iv IV
  -r ROUNDS, --rounds ROUNDS
  -m {ECB,CTR}, --mode {ECB,CTR}
  -v, --verbose
```

### Examples

#### Encrypting

```bash
$ python AES.py -e -in text.txt -out text.enc -k 2b7e151628aed2a6abf7158809cf4f3c -m CTR -iv 00112233445566778899aabbccddeeff -v
```

#### Decrypting

```bash
$ python AES.py -d -in text.enc -out text.txt -k 2b7e151628aed2a6abf7158809cf4f3c -m CTR -iv 00112233445566778899aabbccddeeff -v
```


## API

### encrypt(message: bytes, key: bytes, mode: Mode = Mode.ECB, iv: bytes = None, rounds: int = 11) -> bytes

Encrypts the given message using the given key and mode of operation. If the mode of operation is CTR, the initialization vector (IV) must be 128 bits long. The number of rounds can be specified, but the default value is 11.

#### Parameters

* **message** - The message to be encrypted.
* **key** - The key to be used for encryption.
* **mode** - The mode of operation to be used. The default value is ECB.
* **iv** - The initialization vector to be used. The default value is None.
* **rounds** - The number of rounds to be used. The default value is 11.

#### Returns

The encrypted message.

### decrypt(message: bytes, key: bytes, mode: Mode = Mode.ECB, iv: bytes = None, rounds: int = 11) -> bytes

#### Parameters

* **message** - The message to be decrypted.
* **key** - The key to be used for decryption.
* **mode** - The mode of operation to be used. The default value is ECB.
* **iv** - The initialization vector to be used. The default value is None.
* **rounds** - The number of rounds to be used. The default value is 11.

#### Returns

The decrypted message.

## Test

```bash
$ python -m unittest -v tests.py
```
