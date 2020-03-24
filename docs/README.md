# Documents for hs-platform
Automated platform deployment to simulate an isolated small business local network for testing and user training lab.  

1. Use "edge-lab-bootstrap" (for rpi4 - acts as lab enpoint orchestration)
2. Edge-lab deploys "proxmox-HA-bootstrap" to 3 pre-defined mac address to create an HA VM cluster
3. Edge-lab deploys "drp-trainging-lab" to 4 labs of 4 machines each
4. Edge-lab deploys deploy a number of "edge-lab-bootstrap-centos" via cloud-int and/or clone using proxmox CLI 
5. shane is happy - automated lab
6. cat mods lab, makes ralph happy

## Components
1. DRP workflow "edge-lab-bootstrap" on rpi4
2. DRP workflow "proxmox-HA-bootstrap"
3. DRP workflow "drp-trainging-lab"
4. DRP workflow "edge-lab-bootstrap-centos" on proxmox vm
5. edge-lab hardware (rpi4 x 4 stack... just because)
6. dc-lab hardware (hp/dell x 4 stack for HA proxmox)
7. managed switch (want to put vlan config into mix)
8. ceph or freenas storage (want to put some sort of storage workflow into the mix)

## Workplan
1. Start with edge-lab stack
2. Add shanes 
### Index
- [diagrams](diagrams)
- [images](images)

#### Notes
- [HackerStrike.com](https://www.hackerstrike.com/)
- [Slide Deck](https://drive.google.com/drive/folders/1No9s4_jFfRhRI16uf9B52u1u4ZQO_MCY)
- [Centralizing Windows Logs](https://www.loggly.com/ultimate-guide/centralizing-windows-logs/)
- [Cryptolocker Infection Methods](https://usa.kaspersky.com/resource-center/definitions/cryptolocker)
