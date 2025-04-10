# RSA Encryption Jupyter Notebook

## Overview

This Jupyter Notebook implements RSA encryption for a specific set of parameters. It calculates the public key pair, determines the RSA key length, computes the private key (d value), and encrypts a plaintext message.

## Features

- Calculates public key components (n, e) from given prime numbers
- Determines RSA key length in bits
- Computes the private key exponent (d)
- Performs RSA encryption on a plaintext message

## Requirements

- Jupyter Notebook
- Python 3.x
- SymPy library (for modular inverse calculation)

## Installation

If you don't have the SymPy library installed, run the following in a notebook cell:

```python
!pip install sympy
```

## Usage

Copy the following code into your Jupyter Notebook cell and run it:

```python
from sympy import mod_inverse

# Given values
p = 14437
q = 35267
e = 65539
plaintext = 31234134

# 1) Calculate n (modulus) and the public key pair
n = p * q
public_key = (n, e)
print(f"1) Public key pair (n, e): {public_key}")

# 2) Calculate the length of the RSA key in bits
key_length = n.bit_length()
print(f"2) Length of the key: {key_length} bits")

# 3) Calculate phi (Euler's totient function) and d value
phi = (p - 1) * (q - 1)
d = mod_inverse(e, phi)
print(f"3) d value: {d}")

# 4) Encrypt the plaintext using the public key (n, e)
ciphertext = pow(plaintext, e, n)
print(f"4) Encrypted ciphertext: {ciphertext}")
```

## Example Output

When you run the cell, you should see the following output:

```
1) Public key pair (n, e): (509149679, 65539)
2) Length of the key: 29 bits
3) d value: 132310531
4) Encrypted ciphertext: 31761379
```

## Mathematical Background

This notebook demonstrates the RSA algorithm with these key steps:

1. **Key Generation**:
   - Two prime numbers p and q are selected
   - n = p × q (modulus)
   - φ(n) = (p-1)(q-1) (Euler's totient function)
   - Choose e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
   - Compute d where d × e ≡ 1 (mod φ(n))

2. **Encryption**:
   - C = M^e mod n (where M is the plaintext)

3. **Decryption**:
   - M = C^d mod n (where C is the ciphertext)

## Note

You can modify the values of p, q, e, and plaintext in the notebook cell to experiment with different parameters. For educational purposes only - real-world cryptographic applications should use established libraries.


