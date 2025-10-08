# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
#include <stdio.h>
#include <math.h>

long long mod_exp(long long base, long long exp, long long mod) {
    long long result = 1;
    base %= mod;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        exp /= 2;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long p = 23, g = 5, x = 6, k = 7, m = 15;
    long long y, c1, c2, temp, inv, m_dec;

    y = mod_exp(g, x, p);
    c1 = mod_exp(g, k, p);
    c2 = (m * mod_exp(y, k, p)) % p;

    temp = mod_exp(c1, x, p);
    inv = mod_exp(temp, p - 2, p);
    m_dec = (c2 * inv) % p;

    printf("Public key (p, g, y) = (%lld, %lld, %lld)\n", p, g, y);
    printf("Private key (x) = %lld\n", x);
    printf("Message (m) = %lld\n", m);
    printf("Encrypted (c1, c2) = (%lld, %lld)\n", c1, c2);
    printf("Decrypted message = %lld\n", m_dec);

    return 0;
}

```
### Developed by : Guru Prasath K M 
### Reg No : 212224230079

## Output:
<img width="422" height="288" alt="image" src="https://github.com/user-attachments/assets/b3a1b8b0-a6f4-4a5e-8577-8455465a0676" />


## Result:
The program is executed successfully.
