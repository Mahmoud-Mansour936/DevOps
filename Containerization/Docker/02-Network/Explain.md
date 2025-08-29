# Explain

## Introduction

- After creating a container, it attaches to default network called `docker0`
- `docker0` just make containers communicate using IPs not with name “doesn’t have DNS service”
- So, to make them communicate using names “DNS” → create logical network for group of containers, and it make better isolation for each group of containers

## Network Drivers

- The mechanisms that implement networking inside Docker.

| **Network Type** | **Default Driver** | **Purpose** | **How It Works** |
| --- | --- | --- | --- |
| **bridge** | `bridge` | Default network for standalone containers | Creates a private internal network on the host; containers get a virtual Ethernet interface and communicate via the Docker bridge; outbound traffic is NATed to host’s IP |
| **host** | `host` | Removes network isolation between container and host | Container shares host’s networking namespace, IP, and ports directly |
| **overlay** | `overlay` | Connects containers across multiple Docker hosts in a cluster | Uses VXLAN to encapsulate traffic; requires Docker Swarm or orchestration |
| **macvlan** | `macvlan` | Makes container appear as a physical device on the network | Assigns each container its own MAC & IP from the physical network; bypasses Docker’s NAT |
| **none** | `null` | Disables networking entirely | No external network, only loopback interface (`127.0.0.1`) works |

## Default Network types

- `bridge` → Default for containers without a specified network.
- `host` → Host networking.
- `none` → No networking.

## Some notes

- **Same bridge network (default)** → Can talk **only by IP**, unless you create a **user-defined bridge** (then you can use container names).
- **Different networks** → Cannot talk unless connected to both networks.
- **Ports mapping (`p`)** → Allows external traffic from host to container
    - each container can run its app on same port in individually, ex: nginx on port 80 for each container
    - But each container uses different forwarded port in host
- Can’t be more than one host or none network (default host, none network)

## **Flow of Networking in Docker**

- Container starts → Gets virtual Ethernet interface (`veth`).
- `veth` pairs link container to **docker0** (bridge).
- Bridge connects to host interface.
- `iptables` rules handle NAT, port mapping, and isolation.