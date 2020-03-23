# Documents for hs-platform
Automated platform deployment to simulate an isolated small business local network for testing and user training lab.  

1. Use "edge-lab-bootstrap" (for rpi4 - acts as lab enpoint orchestration)
2. Edge-lab deploys "proxmox-HA-bootstrap" to 3 pre-defined mac address to create an HA VM cluster
3. Edge-lab deploys "drp-trainging-lab" that uses cloud-int and/or clone to deploy a number of "edge-lab-bootstrap-centos"
4. shane is happy... cat mods to make ralph use drp

## Components
1. DRP as DHCP for isolated network lab
2. DRP as deployment workflow for #1
3. DRP used to 'recycle and restore' for #1
4. Automated user simulation using both CLI and UI
5. Automated admin simulation for training

### Index
- [diagrams](diagrams)
- [images](images)

#### Notes
- [HackerStrike.com](https://www.hackerstrike.com/)
- [Slide Deck](https://drive.google.com/drive/folders/1No9s4_jFfRhRI16uf9B52u1u4ZQO_MCY)
- [Centralizing Windows Logs](https://www.loggly.com/ultimate-guide/centralizing-windows-logs/)
- [Cryptolocker Infection Methods](https://usa.kaspersky.com/resource-center/definitions/cryptolocker)
