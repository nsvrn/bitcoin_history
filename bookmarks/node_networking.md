- Avoid DMZ as well as UPnP on the routers, routers usually enable UPnP by default but it should be disabled. If UPnP is enabled on a router then you can't control or know which device(s) on your network could be automatically exposing their IP/ports to the public internet.

- UPnP is OFF by default in both Core and Knots, [link](https://bitcoincore.org/en/2024/07/03/disclose_upnp_rce/)

- To make your node reachable, enable manual port forwarding for specific machine IP and it's port (8333) and convert bitcoind to a hardened systemd service.

- Some routers might have a VLAN option to create separate/isolated networks.

- By default a Bitcoin node running on an IPv4 clearnet, it won't be reachable unless UPnP is enabled in Bitcoin node config and UPnP is enabled on the router.

- To check if your node is reachable: bitnodes dot io 