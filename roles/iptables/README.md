# iptables

This role provides the `iptables` handler used by many other roles
from the Void Ansible Roles collection.  It installs and configures
iptables, optionally enabling an SSH rule in the failsafe rules file.
If you use multiple vlans, you should probably not use the failsafe
rule and should instead write your own that allows ssh traffic from
only the vlan you intend.
