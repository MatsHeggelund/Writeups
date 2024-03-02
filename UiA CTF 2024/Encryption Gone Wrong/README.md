In this ctf challenge, from the Crypto category, we are provided with the following values:
```
n = 221 
e = 7 
c = 136 79 91 50 33 60 98 44 146 146 51 56 103 15 51 216 56 114 75 43 5 142 51 75 79 202 103 31
```
This looks like RSA, but the ciphertext values look strange to me.

I begin by finding the factors for n. I use factor.db: ```http://factordb.com/index.php?query=221``` and find p = 17, q = 13

Since the ciphertext values look seperate, I try performing the RSA decryption on each of them. I add the values to an array.

I wrote the following python script to decode the ciphertexts:

```
from Crypto.Util.number import long_to_bytes

n = 221
e = 7
c = [136, 79, 91, 50, 33, 60, 98, 44, 146, 146, 51, 56, 103, 15, 51, 216, 56, 114, 75, 43, 5, 142, 51, 75, 79, 202, 103, 31]

p = 17
q = 13

phi = (p - 1)*(q - 1)
d = pow(e, -1, phi)

plaintext = ""
for char in c:
        plaintext += str(long_to_bytes(pow(char, d, n)).decode())
print(plaintext)
```

Running this scripts provides us with the flag: ```UiACTF{Ikk3_gL3m_Krypt3ring}```
