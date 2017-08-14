<!-- TITLE: Gatekeeper -->

Gatekeeper is Bookmark's global authentication service and is responsible for authenticating users across all Bookmark sites and services. Gatekeeper is engineered so that your login status persists whereever you are whether that be a Bookmark domain site or a site on some other domain.
# Overall Architecture
Gatekeeper works by granting a session key to users when they successfully log in. This session key is persisted across all Bookmark subdomains. In the event that a user accesses Asgard from a non-Bookmark domain, Gatekeeper can still keep teh user logged in by providing encrypted session keys to Asgard. These encrypted session keys are decrypted and then persisted on the accessor domain.

# Accessing Gatekeeper
Gatekeeper may be accessed at https://auth.bookmarknovels.com and http://auth.dev.bookmarknovels.com.