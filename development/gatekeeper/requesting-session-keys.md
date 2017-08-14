<!-- TITLE: Requesting Session Keys -->
# Planned Specification for 1.0 Beta
This page only applies to users who access Bookmark from a non-Bookmark domain. In order to automatically log users in, pages must check with Gatekeeper to see if a user has a session key or not. The list of steps to go through is as follows:

Let **A** be a client.
Let **B** be a Gatekeeper instance.

- A requests a nonce from B passing B its origin ID
- B checks to see if any application with the given origin ID exists
- B generates a nonce and associates the nonce with A's origin ID (the nonce/origin combo is stored)
- B encrypts the nonce using Vault transit encryption and sends it to A
- A receives the encrypted nonce and decrypts it using vault transit decryption
- A makes a request to B asking B if the user has a session key set (A sends in the decrypted nonce along with its origin ID)
- B receives the request and checks to see if the nonce/origin ID combo matches what it has logged
- If everything is good then B sends A the user's session key as an encrypted string (if possible)

If B encounters any anomaly during this process than B will log the anomaly and not respond.