# 🧪 Konfiguracja VLAN / ROAS (Router on a stick) – Cisco Packet Tracer

---

### 🔧 Cel projektu:
Zbudowanie segmentowanej sieci LAN z podziałem na VLAN-y i obsługą routingu między nimi przez router za pomocą techniki Router-on-a-Stick (ROAS).

---

### 📌 Topologia:
3 VLAN-y:

VLAN10 – 10.0.0.0/26

VLAN20 – 10.0.0.64/26 

VLAN30 – 10.0.0.128/26 

2 switche L2: SW1 i SW2 (2960)

Router: R1 (2911)

Urządzenia końcowe: 7 PC w różnych VLAN-ach

![VLAN](https://github.com/user-attachments/assets/51fa8896-f8b5-4019-8cf0-1d4b04d43eb0)


---

### 📡 Funkcje projektu:
 - Segmentacja sieci z VLAN
 - Routing między VLAN z użyciem subinterfejsów
 - Konfiguracja trunków

--- 

### 🔍 Zastosowane komendy (Fragmenty):
#### Router R1:
```bash

interface g0/0.10

 - encapsulation dot1q 10
 
 - ip address 10.0.0.62 255.255.255.192

interface g0/0.20

 - encapsulation dot1q 20
 
 - ip address 10.0.0.126 255.255.255.192

interface g0/0.30

 - encapsulation dot1q 30
 
 - ip address 10.0.0.190 255.255.255.192

```
#### Switch trunk:

```bash
interface g0/1

 - switchport mode trunk
 
 - switchport trunk allowed vlan 10,20,30
 
 - switchport trunk native vlan 1001

```
#### Switch access port:
```bash

interface f0/1

 - switchport mode access
 
 - switchport access vlan 10

```
#### Switch (bezpieczeństwo):
```bash

interface range f0/5-24 

 - switchport access vlan 999 
 
 - shutdown 

```





---

### 🔐 Kluczowe elementy bezpieczeństwa:
 - Zmiana Native VLAN na inną niż VLAN1 (native vlan 1001) – zabezpieczenie przed atakami typu VLAN 
 hopping
 - Ograniczenie listy VLAN-ów na trunkach (allowed vlan)
 - Wyłączone nieużywane porty
 - Brak dostępu do VLAN 1 na portach użytkowników

---

### ❌ Najczęstsze błędy:
 - Zła wartość encapsulation dot1q (zły VLAN ID)
 - Brak trunk między switchami (problemy z propagacją VLAN)
 - Niezgodność VLAN-u przypisanego do portu z konfiguracją PC
 - Brak bramy domyślnej u użytkowników – brak komunikacji między VLAN-ami
 - Nieistniejący Vlan na switchu

--- 
### ✅ Wnioski końcowe:

 Projekt pokazał praktyczne znaczenie poprawnej segmentacji sieci oraz konfiguracji trunków. Wdrożenie zabezpieczeń na poziomie warstwy 2 (zmiana native VLAN, ograniczenie VLAN-ów) znacząco poprawia bezpieczeństwo sieci. ROAS pozwala na efektywny routing przy minimalnym wykorzystaniu zasobów sprzętowych.
 
---

### 📎 Dodatkowe Zasoby

 [💾 Plik Packet Tracer – projekt (.pkt)](./VLAN_ROAS.pkt)
 
 [📄 Pełna konfiguracja](./komendy.md)

 ---
