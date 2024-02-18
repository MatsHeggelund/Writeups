While traveling through the debris of exploded planets, a signal arrived. We've determined the alien alphabet used, but the message is still encrypted. Your mission is to decrypt the secret message.



This CTF challenge from the crypto category included a python script and a encoded flag

Encoded flag:
```
XfWEd9nZ7{4kw0ud7id9wYf_f76p7o}
```

The python script performed a rotational cipher based on the index of the character in the flag
```
if idx % 2 == 0:
        flag_enc += alphabet[(alphabet.index(char)+3) % len(alphabet)]
    else:
        flag_enc += alphabet[(alphabet.index(char)-3) % len(alphabet)]
```

This process is very easy to reverse. We can take the encoded flag, treat it as the plaintext, and rotate the characters back

```
if idx % 2 == 0:
        flag_enc += alphabet[(alphabet.index(char)-3) % len(alphabet)]
    else:
        flag_enc += alphabet[(alphabet.index(char)+3) % len(alphabet)]
```

We then get the flag:

UiTHack24{1nt3rg4lact1c_ca3s4r}
