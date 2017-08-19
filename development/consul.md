<!-- TITLE: Consul -->

Bookmark uses Consul for all configuration needs. By default, services will have access to a read-only KV store dedicated to their service. Developers will not be able to edit these KV-stores unless they are an approved contributor. To request access to Consul, please send an email to andrew@bookmarknovels.com.

**Developer Consul:** https://consul.dev.bookmark.services

**Gatekeeper Read-Only Consul:** https://gatekeeper.consul.dev.bookmark.services

# Accessing Consul from Services
In order to access Consul (and configuration values) through `Bookmark-Config` you will need a service token. You can obtain one by provisioning a Consul token from the developer portal.