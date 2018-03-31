# docker-openmanage
The following packages are installed
- srvadmin-base
- srvadmin-storageservices

Note: after starting the container it may take a while before all services are usable. (±5 min) 

```
version: '2'
services:
 omsa:
    container_name: omsa
    image: dilanodroog/omsa
    network_mode: "host"
    restart: unless-stopped
    cap_add:
     - ALL
    privileged: true
    volumes:
     - "/lib/modules:/lib/modules:ro"
```

# Example commands

Start container using the above compose file as daemon
`docker-compose up -d`

View storage vdisk controller 0
`docker exec omsa omreport storage vdisk controller=0`

Start CC on vdisk 0 with controller 0
`docker exec omsa omconfig storage vdisk action=checkconsistency controller=0 vdisk=0`

View storage vdisks
`docker exec omsa omreport storage vdisk`
