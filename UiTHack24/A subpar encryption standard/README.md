*While looking around in the remains of an enemy spaceship you find some code. In their hurry they must have forgotten that there were more steps to do.*

This CTF challenge from the crypto category included a python script and a encoded flag

Encoded flag:
```
fc f9 20 52 ef fb 7f 23 18 21 aa b6 92 4d 3c ef 8f 92 4d 40 cf 40 f9 2 9f 43 ef 4d 50 ff
```

The python script is a *Rijndael* encryption algorithm which uses a Rijndael S-box (substitution box). This algorithm is better known as AES.
To decrypt the flag, we have to find the inverse transformation of each hexadecimal character in the encrypted flag, using the s_box constructed in the python script

```
***
Rest of the encrypt.py code, excluding main
***

def construct_s_box_inverse():
    s_box_inverse = [0] * 256
    for x in range(256):
        s_box_value = rijndael_sbox(x)
        s_box_inverse[s_box_value] = x
    return s_box_inverse

encrypted_flag_hex = ["fc", "f9", "20", "52", "ef", "fb", "7f", "23", "18", "21", "aa", "b6", "92", "4d", "3c", "ef", "8f", "92", "4d", "40", "cf", "40", "f9", "2", "9f", "43", "ef", "4d", "50", "ff"]
s_box_inverse = construct_s_box_inverse()
decrypted_flag = ''.join(chr(s_box_inverse[int(hex_val, 16)]) for hex_val in encrypted_flag_hex)
print(decrypted_flag)
```

The flag is then retrieved by running the script.

UiTHack24{bytemaster_rijndael}
