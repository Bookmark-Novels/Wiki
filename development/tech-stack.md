<!-- TITLE: Technology Stack -->
# Gatekeeper
Bookmark's authentication/SSO service. Responsible for managing user sessions.

- Python
- Flask
- SQLAlchemy
- MySQL
- Cassandra
- HTML
- CSS
- JavaScript
- ReactJS
# Asgard
Bookmark's platform service. Responsible for providing micro-site management capabilities and rendering the public-facing frontend of sites.

- Python
- Flask
- SQLAlchemy
- MySQL
- redis
- Cassandra
- HTML
- CSS
- JavaScript
- ReactJS
# Provider
Bookmark's read-only API service. Responsible for servicing Asgard's requests when rendering public-facing content.

- Flask
- SQLAlchemy
- MySQL
- redis
# Ein

Bookmark's dependency manager. Responsible for notifying services of any dependency conflicts when multiple people edit dependent resources (table of contents depends on the titles of chapters). Ein is also responsible for invalidating cached data when updates arrive.

- Golang or Elixir
# Watchdog
Bookmark's cluster supervisor. Responsible for keeping track of what application instances are available and updating the database when changes occur. Also responsible for restarting any offline applications. 

- Golang or Java