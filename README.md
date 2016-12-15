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
  * network_dns: [8.8.8.8,8.8.4.4]
  * network_6dns: [2001:4860:4860::8888,2001:4860:4860::8844]
  * network_dhcp_options: [rapid_commit,domain_name_servers,domain_name,domain_search,host_name,classless_static_routes,ntp_servers,interface_mtu]
  * network_input_policy: DROP
  * network_output_policy: DROP

Variables Required:
  * None

Optional Variables:
  * network_interfaces: Dictionary of interfaces to configure
      - name: Name of the interface as reported by `ip link show`; may use special value 'default' to select ansible_default_ipv{4,6} interface
        mode: static, dhcp, or disabled
        mode6: mode for IPv6 (static, dhcp, disabled)
        resolvermode: dhcp or static
        resolvermode6: mode for IPv6 (static, dhcp)
        addresses: list of addresses for static assignment, CIDR format
        addresses6: same as addresses, for IPv6
        resolvers: list of static IPv4 resolvers, required when mode is 'static' or resolvermode is 'static'
        resolvers6: list of static IPv6 resolvers, required when mode6 is 'static' or resolvermode6 is 'static'
        routers: list of routers for this interface, only specify more than 1 if you know what you are doing!
        routers6: list of IPv6 capable routers for this interface, only specify more than 1 if you know what you are doing!

Files Required:
  * None

Optional Files:
  * None

Conflicting Roles:
  * None

Depends On:
  * None
