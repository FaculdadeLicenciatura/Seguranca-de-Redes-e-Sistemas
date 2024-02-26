![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/d4c55363-e720-4367-8884-f0fdb83ae6b2)# Configuração fisica
Swith e ROuter

Abri o Putty NO UBUNTO E USEI ESTE COMANDO PARA ME LIGAR:
```terminal
sudo putty /dev/ttyUSB0 -serial -sercfg 9600,8,n,1,N
```
depois de 5 minutos ele ligou e ficou assim: <br>
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/c8d9ec8b-7223-41df-b4b7-807aabd88f87)

agora fazer configuração basica que usei o do trabalho01.

```terminal
---------------------- Configuração de Router --------------------------
R1

enable
conf t
no ip domain-lookup
hostname R1
enable secret class
line console 0
password cisco
login
exit
line vty 0 4
password cisco
login
exit
interface g0/0
ip address 10.0.24.1 255.255.248.0
no shut
interface s0/0/0
ip address 10.0.32.1 255.255.255.252
clock rate 128000
no shut
interface s0/1/0
ip address 10.0.32.9 255.255.255.252
no shut
router ospf 1 
passive-interface g0/0
default-information originate
network 10.0.24.0 0.0.0.7 area 0
network 10.0.32.0 0.0.0.3 area 0
network 10.0.32.8 0.0.0.3 area 0
ip route 0.0.0.0 0.0.0.0 40.20.30.5

```
print:
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/5d5213e3-7972-4d7f-bf15-6ba39b384606)

```terminal
---------------------- Configuração de Switch --------------------------


Sw1
enable
conf t
no ip domain-lookup
hostname Sw1
enable secret class
line console 0
password cisco
login
exit
line vty 0 4
password cisco
login
exit
interface vlan 1
ip address 10.0.24.2 255.255.248.0
no shut
ip default-gateway 10.0.24.1
```
print:
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/112650c0-6c4a-4b0f-99ad-07a4e300daaf)

mostrar o ip:
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/6257d5d0-e74a-4ebd-9024-eae1cef97865)
<br>
As minhas configs do Switch:
```Terminal
Current configuration : 3826 bytes
!
version 12.2
no service pad
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname Sw1
!
boot-start-marker
boot-end-marker
!
enable secret 5 $1$wGke$YPaf0LmgigkkmzYflBUCt0
!
no aaa new-model
system mtu routing 1500
ip subnet-zero
!
!
no ip domain-lookup
!
!
crypto pki trustpoint TP-self-signed-4270035456
 enrollment selfsigned
 subject-name cn=IOS-Self-Signed-Certificate-4270035456
 revocation-check none
 rsakeypair TP-self-signed-4270035456
!
!
crypto pki certificate chain TP-self-signed-4270035456
 certificate self-signed 01
  3082023B 308201A4 A0030201 02020101 300D0609 2A864886 F70D0101 04050030
  31312F30 2D060355 04031326 494F532D 53656C66 2D536967 6E65642D 43657274
  69666963 6174652D 34323730 30333534 3536301E 170D3933 30333031 30303030
  35385A17 0D323030 31303130 30303030 305A3031 312F302D 06035504 03132649
  4F532D53 656C662D 5369676E 65642D43 65727469 66696361 74652D34 32373030
  33353435 3630819F 300D0609 2A864886 F70D0101 01050003 818D0030 81890281
  8100C9AA 64FB37DA BF1EFC70 FA824EC1 FBDB1A31 F21DDB75 1E56A8AC 8B742611
  794B516D CDA07DAD 3B422A32 0ED953BC EDBE820E 617D0FD6 4E679C81 89D93DB4
  72807C68 B74D8934 E1635A6C 69949D6E 79E2952D 05CBB68F 8B6859EF B22BB23A
  1828F39F 6F087ABD A47AA8C3 EB9A61F6 F7DF993B FAA2E556 79377F23 436EEFC6
  D92D0203 010001A3 63306130 0F060355 1D130101 FF040530 030101FF 300E0603
  551D1104 07300582 0353322E 301F0603 551D2304 18301680 142073C6 45D50639
  E39621F3 CFB2FC7E DD968BB6 26301D06 03551D0E 04160414 2073C645 D50639E3
  9621F3CF B2FC7EDD 968BB626 300D0609 2A864886 F70D0101 04050003 8181008E
  F353DD6D 56EF8B8C E5B40535 1A6883F4 870372B9 B8838219 E5BA3E5F 0C29AAE2
  2F24D463 0D0E53E8 D574C768 A3461A37 FEAF9159 EDA8DAAC DDC65624 B0736F4A
  3BBBB735 05F81E4E CD4DCD6E 6A08F5F9 C143A8E3 25489027 D55245C3 E7F577F8
  E643C74F 37A7F62E 5661DB62 B1F5AFB9 2E1BCDFB 3445A402 E4762CC4 E8BAD3
  quit
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
vlan internal allocation policy ascending
!
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface FastEthernet0/25
!
interface FastEthernet0/26
!
interface FastEthernet0/27
!
interface FastEthernet0/28
!
interface FastEthernet0/29
!
interface FastEthernet0/30
!
interface FastEthernet0/31
!
interface FastEthernet0/32
!
interface FastEthernet0/33
!
interface FastEthernet0/34
!
interface FastEthernet0/35
!
interface FastEthernet0/36
!
interface FastEthernet0/37
!
interface FastEthernet0/38
!
interface FastEthernet0/39
!
interface FastEthernet0/40
!
interface FastEthernet0/41
!
interface FastEthernet0/42
!
interface FastEthernet0/43
!
interface FastEthernet0/44
!
interface FastEthernet0/45
!
interface FastEthernet0/46
!
interface FastEthernet0/47
!
interface FastEthernet0/48
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 10.0.24.2 255.255.248.0
 no ip route-cache
!
ip default-gateway 10.0.24.1
ip http server
ip http secure-server
!
control-plane
!
banner motd ^C
Unauthorized access is strictly prohibited ^C
!
line con 0
 password cisco
 login
line vty 0 4
 password cisco
 login
line vty 5 15
 login
!
end
```
do router: <br>
```
Current configuration : 1196 bytes
!
! Last configuration change at 16:11:15 UTC Mon Feb 26 2024
!
version 16.9
service timestamps debug datetime msec
service timestamps log datetime msec
platform qfp utilization monitor load 80
no platform punt-keepalive disable-kernel-core
!
hostname R1
!
boot-start-marker
boot-end-marker
!
!
enable secret 5 $1$EV4X$4MRouA3VnbeOPOJl1pnJy1
!
no aaa new-model
!
no ip domain lookup
!
!
!
!
!
!
!
!
!
!
subscriber templating
!
!
!
!
vtp mode transparent
!
multilink bundle-name authenticated
!
!
!
!
!
license udi pid ISR4221/K9 sn FGL23283163
no license smart enable
diagnostic bootup level minimal
!
spanning-tree extend system-id
!
!
!
!
redundancy
 mode none
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface GigabitEthernet0/0/0
 no ip address
 negotiation auto
!
interface GigabitEthernet0/0/1
 ip address 10.0.24.1 255.255.248.0
 negotiation auto
!
interface Serial0/1/0
 ip address 10.0.32.9 255.255.255.252
!
interface Serial0/1/1
 no ip address
!
router ospf 1
!
ip forward-protocol nd
no ip http server
ip http secure-server
!
!
!
!
!
!
control-plane
!
!
line con 0
 password cisco
 login
 transport input none
 stopbits 1
line vty 0 4
 password cisco
 login
!
!
!
!
!
!
end

```
