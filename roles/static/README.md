# static

This role provisions static addressing on Void Linux.

The following variables are accepted:

  * `network_static_interfaces`
    * Object
      * `type` - (string) <vlan|trunk|basic> Type of interface
      * `name` - (string) <arbitrary> Name of the interface, must be a valid interface name.
      * `parent` - (string) Parent interface for vlan interfaces.
      * `addr` - (list<string>) List of addresses to assign to the interface.
  * `network_static_routes`
    * Object
      * `to` - (string) Route destination
      * `via` - (string) Next Hop
