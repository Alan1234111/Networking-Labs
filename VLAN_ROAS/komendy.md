# 💻 Konfiguracja urządzeń – Cisco Packet Tracer



## 🔁 SW1 – Switch 1

```bash
enable
configure terminal

vlan 10
vlan 20
vlan 30
vlan 999
name parking

interface range f0/1-2
 switchport mode access
 switchport access vlan 10

interface range f0/3-4
 switchport mode access
 switchport access vlan 10

interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,30
 switchport trunk native vlan 1001

interface range f0/5-24
 switchport mode access
 switchport access vlan 999
 shutdown

interface g0/2
 switchport mode access
 switchport access vlan 999
 shutdown
```

## 🔁 SW2 – Switch 2
```bash

enable
configure terminal

vlan 10
vlan 20
vlan 30
vlan 999
name parking

interface f0/1
 switchport mode access
 switchport access vlan 20

interface range f0/2-3
 switchport mode access
 switchport access vlan 10

interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,30
 switchport trunk native vlan 1001

interface g0/2
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
 switchport trunk native vlan 1001

interface range f0/4-24
 switchport mode access
 switchport access vlan 999
 shutdown
```

## 🔁 R1 - Router 1
```bash
enable
configure terminal

interface g0/0
 no shutdown

interface g0/0.10
 encapsulation dot1Q 10
 ip address 10.0.0.62 255.255.255.192

interface g0/0.20
 encapsulation dot1Q 20
 ip address 10.0.0.126 255.255.255.192

interface g0/0.30
 encapsulation dot1Q 30
 ip address 10.0.0.190 255.255.255.192
```
