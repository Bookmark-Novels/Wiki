<!-- TITLE: Watchdog -->

Watchdog is a Python library and service for Bookmark that handles service registration and management for various Bookmark services.
# Purpose
Watchdog is needed to verify service identities when performing cross-service requests.
# Specifications
- Must have a REST API
- Must have a library for interacting with it
- Must handle the registration of services with Consul
- Must poll a `/watchdog/health` endpoint every `X` seconds and update the `bookmark_watchdog_services` table (not yet created)
# REST Endpoints
## Register Service
```
POST /register
Accepts: TEXT/JSON
Produces: TEXT/JSON
Required Headers: X-Watchdog-Token

Sample Payload:
{
    "service_id": <string>
}

Sample Response:
200 Status Code
{
    "error": null,
		"success": true
}

Sample Response:
400 Status Code
{
    "error": "unauthorized",
		"success": false
}

Sample Response:
500 Status Code
{
    "error": "internal server error",
		"success": false
}
```
## Service Exists
```
POST /service-exists
Accepts: TEXT/JSON
Produces: TEXT/JSON
Required Headers: X-Watchdog-Token

Sample Payload:
{
    "service_id": <string>
}

Sample Response:
200 Status Code
{
    "error": null,
		"success": true,
		"exists": true
}

Sample Response:
400 Status Code
{
    "error": "unauthorized",
		"success": false,
		"exists": null
}

Sample Response:
500 Status Code
{
    "error": "internal server error",
		"success": false,
		"exists": null
}
```
# Example Library Functions
| Name | Description | Return Value | Raises |
| --- | --- | --- | --- | --- |
| `Watchdog(watchdog_token)` | Instantiates a new Watchdog object instance. | `Watchdog` object. | N/A |
| `Watchdog#register_service(service_id)` | Registers a service with Watchdog given a service ID. | `True` or `False` depending on success. | `AlreadyRegisteredError`|
| `Watchdog#service_exists(service_id)` | Checks whether or not a service exists in Watchdog and is available. | `True` or `False` depending on whether or not a service with the given ID exists and is available. | N/A |

Services will be required to provide a Watchdog token before use. Watchdog tokens can be provisioned in the developer portal (actual button tba) and are stored inside the MySQL table `bookmark_watchdog_tokens` (also tba). The Watchdog service URL is `https://watchdog.dev.bookmark.services` and `https://watchdog.bookmark.services`.
# Health Checks
Health checks are to be performed by watchdog periodically. Watchdog should query a `/health/health` endpoint. This endpoint should return status 200 if a service is alive. The response body will be ignored.