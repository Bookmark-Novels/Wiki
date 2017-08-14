<!-- TITLE: Distributed Systems Design -->

Bookmark's speculated initial traffic is 150,000 unique views per day.

# Service Requirements
- Provide fast service while minimizing costs
- 99% SLA (roughly 1.7 hours of weekly downtime for maintenance etc)
- Secure
- **Consistently** service, at minimum, 500 queries per second

# Proposed Solution

- All applications are to be ran on multiple load-balanced nodes.
- All database queries are to be cached (by both redis **and** varnish).
- Utilize ElasticSearch for high-performance searching.
- Utilize Cassandra as a high-write NoSQL database.

## Server Requirements
- 1x Bookmark Server
- 2x Application Server
- 2x Gatekeeper Server
- 2x API Server
- 1x API Caching Server
- 1x Application Load Balancer
- 1x Gatekeeper Load Balancer
- 1x API Load Balancer*
- 1x redis master
- 1x redis slave
- 1x ElasticSearch Server
- 1x MySQL Server
- 1x Cassandra Server
- 1x Ein Server

*Non-critical requirement

## Misc. Requirements
- 1x Wildcard SSL Certificate
- 1x Domain Name

We propose a single server to host the Bookmark website, status page, and forums.

We propose two load balanced applications servers to handle all traffic that does not touch the database.

We propose two load balanced Gatekeeper servers to handle all authentication services.

We propose two API servers with a single caching layer to handle all API requests and read from the database if needed. The caching layer used will be Varnish. Varnish is also capable of acting as a standalone load balancer.

We propose master-slave redis servers to use as a global key-value store for all systems as well as to cache expensive database queries.

We propose a single ElasticSearch server to handle all our search needs across the entire platform.

We propose a single MySQL server to handle everything database related.

We propose a single Cassandra server to store all audit logs etc.

We propose a single Ein server to automatically invalidate updated cached items in redis and Varnish.

## Proposed Provider

We propose Linode as our hosting provider due to their relatively low price.
## Projected Monthly Costs

- 1x Bookmark Server = $40
- 2x Application Server = $20 x 2
- 2x Gatekeeper Server = $20 x 2
- 2x API Server = $20 x 2
- 1x API Caching Layer = $40
- 1x Application Load Balancer = $20 (Linode NodeBalancer)
- 1x Gatekeeper Load Blaancer = $20 (Linode NodeBalancer)
- 1x redis master = $40
- 1x redis slave = $40
- 1x ElasticSearch Server = $40
- 1x MySQL Server = $80
- 1x Cassandra Server = $40
- 1x Ein Server = $20

Total Projected Monthly Costs = $500

## Projected Annual Costs

- Domain Name = $20-$50
- Wildcard SSL Certificate = $100

Total Projected Annual Costs = $120-$150

## Projected Combined Annual Costs

$460 * 12 + $150 = $6150