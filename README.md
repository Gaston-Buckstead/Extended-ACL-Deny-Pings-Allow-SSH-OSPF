# Extended-ACL-Deny-Pings-Allow-SSH
<img width="620" height="256" alt="image" src="https://github.com/user-attachments/assets/eeb7868f-5857-4ac2-8f05-790212b4abae" />

## Objective
Block ICMP (ping) traffic and allow SSH access using an extended ACL.

## Network 
Built in Cisco Packet Tracer with 3 Router + 2 PCs

## Result
- Pings blocked ❌  
- SSH allowed ✅

## Ping From PC-West to PC-East
<img width="349" height="287" alt="image" src="https://github.com/user-attachments/assets/459c0dc0-f70b-4ac7-9a34-e7e0920829d0" />

## Successful SSH from PC-West to HQ Router
<img width="200" height="169" alt="image" src="https://github.com/user-attachments/assets/d0b0d1e7-f269-4517-b4a5-ccd366955693" />

## Configuration

### Extended ACL
#### RW:
ip access-list extended DENY_PINGS_WEST

 permit tcp 10.10.10.0 0.0.0.255 any eq 22
 
 deny icmp host 10.10.10.10 any echo
 
### OSPF Routing
#### RW: 

router ospf 100

 router-id 2.2.2.2
 
 log-adjacency-changes
 
 network 10.1.1.0 0.0.0.255 area 0
 
 network 10.10.10.0 0.0.0.255 area 0
