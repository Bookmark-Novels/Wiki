<!-- TITLE: Watchdog -->

Watchdog is a Python library for Bookmark that handles service registration and management for various Bookmark services.
# Specifications
- All operations must be idempotent
- Must have a library for interacting with it
- Must handle the registration of services with Consul
# Example Functions
| Name | Description | Return Value | Raises |
| --------- | ------- | ---- | --- | ---|
| `Watchdog(consul_token)` | Instantiates a new Watchdog object instance. | `Watchdog` object. | N/A |
| `register_service(str: service_name, address=None, checks=[])` | Registers a service with Consul given a service name. | `True` or `False` depending on success. | 