# Design choices
- Use openssl CLI for encryption/decryption, key generation
    - Assuming we have a file called 'encryptme' and a file 'key' generated with openssl ``openssl enc -aes-256-cbc -k secret -P -md sha256`` where secret is really just some noise to make 
    - Encrypt with ``openssl enc -aes-256-cbc -e -in encryptme -out encrypted -pass file:key``
    - Decrypt with ``openssl enc -aes-256-cbc -d -in encrypted -pass file:key``

- We will choose one of the algorithms given ``openssl ciphers -v 'AES+HIGH'``

# Resources

[Man page](https://www.openssl.org/docs/man1.0.1/apps/openssl.html)

[Intro page](https://users.dcc.uchile.cl/~pcamacho/tutorial/crypto/openssl/openssl_intro.html)

[AES wiki](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

[Security vulnerabilities in password managers](https://team-sik.org/trent_portfolio/password-manager-apps/)

[Paper on password manager databases](https://www.cs.ox.ac.uk/files/6487/pwvault.pdf)

[Google drive api](https://developers.google.com/drive/)

### Good reference projects (Similar password managers):

[pass](https://www.passwordstore.org/) - Cons: it stores the passwords in a series of files (directories), giving away that a user has an account with a given site - Pros: ``pass -c`` is really cool, we should steal that. Their design is very solid and well though through. We should steal most of it...

[KeePass](https://en.wikipedia.org/wiki/KeePass) - Mainly windows based...

LessPass is terrible, it just uses a master password and the website name to generate a password.
 No data storage. [See this article for an explanation why deterministic PM's are terrible](https://tonyarcieri.com/4-fatal-flaws-in-deterministic-password-managers)
