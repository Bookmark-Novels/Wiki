<!-- TITLE: Watchdog -->

Watchdog is a Python library for Bookmark that handles service registration and management for various Bookmark services.
# Specifications
- All operations must be idempotent
- Must have a library for interacting with it
- Must handle the registration of services with Consul
# Example Functions
| Name | Description | Return Value | Raises |
| --------- | ------- | ---- | --- | ---|
| `Watchdog(service_name, consul_token)` | Instantiates a new Watchdog object instance. | `Watchdog` object. | N/A |
| `Watchdog#register_service(service_id, address=None, checks=[<string>])` | Registers a service with Consul given a service name. | `True` or `False` depending on success. | `AlreadyRegisteredError`|

It is important to know that many services may be registered under the same name so services will need to provide a unique service ID. This is typically generated via UUID4.

Notice how `register_service` takes in 2 optional parameters. `address` should be the IPv4 **private network** address of the calling service if `None` is specified. Otherwise, the provided address should be used. `checks` specifies a list of health checks to be performed periodically by Consul. [Health check](https://www.consul.io/api/agent/check.html) documentation is here. Documentation on registering Consul services is [here](https://www.consul.io/api/agent/service.html).