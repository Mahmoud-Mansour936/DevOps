# 00-Containerization

- At first each app has a lot of servers (service = individual server)
    - Database has a server
    - frontend has a server and so on…
- So, it makes high waste of resources and money even that we don’t use all of it and have a lot of servers that we don’t need all of that → so we use virtualization

## Virtualization

![23.png]("E:\study\DEVOPS\MY devops repo\Containerization\Docker\00-Containerization\images\23.png")

- To save more resources all services are applied on one server, but they were full separated from each other
- Each server is defined with part of hardware of the host server and has its own OS
- They are separated using the hypervisor
- Virtualization saves more resources, but still there are wasted ones for each dependencies for each VM like [ OS, Licenses, support …] → so we use containerization

## Containerization

![24.png](00-Containerization%2024594834a4e5804abae9c60bf9d2b431/24.png)

- All apps are using shared hardware → so each app will just use its resources, not have reserved ones
- They all applied on Host OS kernel and don’t need the shell of distros
    - If the host kernel is Linux so each container can use Linux distros [ Ubuntu, Debian, …]
- They are separated using containerization tool like Docker