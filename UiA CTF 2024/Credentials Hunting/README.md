This CTF challenge, from the Web category, provides us with a website at: https://credentials-hunting.chall.uiactf.no

This website redirects to the /login page: https://credentials-hunting.chall.uiactf.no/login

After attempting some basic SQLI low hanging fruits, I began looking for more information to recover the credentials.

Like with any web-based challenge, I check out the /robots.txt file. I then found:

```
User-agent: *
Disallow:

####################################
###### Notes while developing ######
####################################

- REMEMBER TO DELETE THIS BEFORE DEPLOYMENT!!!
- (hash your passwords in here, no cleartext in notes. Safety first team!)
- Boss is being a jerk, too short of a deadline
- When I wrote this, only God and I understood what I was doing. Now, God only knows
- Credentials while developing: admin - ec0d4ad57bd39659ea7263c15e44bb0e8b6628c3e087ae7f2ff0c1d216bf5da4 (see, I remembered to hash it!)
- Sidenote if I forget my password.... We will, we will, Rock You! God, I miss Eddie Murphy and the Queen...
- Sometimes I believe compiler ignores all my comments
- I'm too beatiful to be a developer
```

This gives us the hashed password for the admin user. I put this hash into a textfile and then run john the ripper on it with the rockyou.txt wordlist.

John cracked the password instantly: ```sashagray```

Using the username *admin* and password *sashagray* I was able to log in. I was immediately provided with the flag:

```UiACTF{Cr3d3ntial_Hunt_M4ster}```
