# Configurar Router

## Configuração Base
```
enable
config t
```

```
hostname
```
```
interface g0/0
ip adress 10.10.10.2 255.255.255.0
no shut
```
```
line con 0
password cisco
login
```
```
line vty 0 4
password cisco
login
```
```
enable secret class
```
