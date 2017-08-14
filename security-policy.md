<!-- TITLE: Security Policies and Levels -->

Bookmark takes security very seriously. All stored data is given a security level ranging from 0-3.
# Security Level 0
A security level of 0 means that a resource is released to the public in its entirety. This would be source code for services libraries etc.
# Security Level 1
A security level of 1 means that a resource leakage would not be catastrophic but would still be undesirable. This mostly includes intellectual property that is not released to the public. Examples of these are URLs for internal tools secured by SSO and wiki pages for internal tools.
# Security Level 2
A security level of 2 means that a resource leakage could lead to harm for the user. This level includes things such as email address and last logged-in IP.
# Security Level 3
A security level of 3 means that a piece of data is sensitive enough that it could compromise Bookmark's operation if leaked. This includes encryption keys and access to development dataases.
# Security Level 4
A security level of 4 means that a piece of data is so sensitive and confidential that it could jeapardize Bookmark as an organization if leaked. This includes SSH keys to production servers and user financial information.