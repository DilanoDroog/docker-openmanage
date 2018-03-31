# docker-openmanage
The following packages are installed
- srvadmin-base
- srvadmin-storageservices

Note: after starting the container it may take a while before all services are usable. (±5 min) 

```
version: '2'
services:
 osma:
    container_name: osma
    image: dilanodroog/osma
    network_mode: "host"
    restart: unless-stopped
    cap_add:
     - ALL
    privileged: true
    volumes:
     - "/lib/modules:/lib/modules:ro"
```
# Example commands
`docker-compose up -d`
`docker exec osma omreport storage vdisk controller=0
`docker exec osma omconfig storage vdisk action=checkconsistency controller=0 vdisk=0`
`docker exec osma omreport storage vdisk`
