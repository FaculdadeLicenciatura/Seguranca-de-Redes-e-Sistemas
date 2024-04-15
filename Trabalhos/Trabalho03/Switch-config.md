# Configuração de Switch
```
hostname Switch
no ip domain-lookup
interface <interface>
ip adress ...
clock rate 115200
no shut
router ospf 1
network x.x.x.x y.y.y.y arca
passive-interface <interface-lan>
```
