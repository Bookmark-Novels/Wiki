<!-- TITLE: Security Efforts -->

In an effort to secure data, Bookmark encrypts all sensitive data at rest. Information is encrypted and decrypted using a shared key. This shared key is stored on application servers.

Data stored in redis is **not** encrypted. This is because redis should not be used to store sensitive or protected data.