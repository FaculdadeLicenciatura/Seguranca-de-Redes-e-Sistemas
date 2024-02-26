# Configuração fisica
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
