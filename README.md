network
=======


What is does this role do?
--------------------------

This role configures and manages various different components of the network.  Most configuration is done via dhcpcd even when using static addressing.  This allows for configurations to be enforced by using a daemon rather than just specifying options in /etc/rc.local.


Meta
----

Files Managed:
  * /etc/hosts
  * /etc/hostname
  * /etc/dhcpcd.conf
  * /etc/iptables.d/
  * /etc/iptables.d/0common.rules
  * /etc/ip6tables.d/
  * /etc/ip6tables.d/0common.6rules
  * /usr/local/sbin/iptables-reload
  * /usr/libexec/dhcpcd-hooks/10-wpa_supplicant
  * /usr/share/dhcpcd/hooks/99-iptables
  * /var/service/dhcpcd

Defaults Provided:
  * network_managed_addressing: true
  * network_enable_wpa_supplicant: false
  * network_address_mode: dhcp
  * network_dns_mode: dhcp
  * network_dns: [8.8.8.8,8.8.4.4]
  * network_6dns: [2001:4860:4860::8888,2001:4860:4860::8844]
  * network_dhcp_options: [rapid_commit,domain_name_servers,domain_name,domain_search,host_name,classless_static_routes,ntp_servers,interface_mtu]
  * network_input_policy: DROP
  * network_output_policy: DROP

Variables Required:
  * None

Optional Variables:
  * network_address: a statically defined address with netmask in CIDR format
  * network_gateway: a statically defined gateway to be used in static mode

A lengthy discussion of what the variables do is available in defaults/main.yml, as well as a few undocumented variables that provide advanced capabilities.

Files Required:
  * None

Optional Files:
  * None

Conflicting Roles:
  * None

Depends On:
  * None
