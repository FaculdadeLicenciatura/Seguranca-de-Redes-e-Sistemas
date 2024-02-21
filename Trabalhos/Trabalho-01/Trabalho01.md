# Configurar Router

## Configuração Base
Part 1: Configure basic settings
a. Configure device name as shown in the topology.
```
enable
config t
```
b. Configure IP address as listed in Addressing Table.
```
hostname
```
```
interface g0/0
ip address 10.10.10.2 255.255.255.0
no shut
```
```
line con 0
password cisco
login
```
c. Assign cisco as the console and vty passwords.
```
line vty 0 4
password cisco
login
```
d. Assign class as the privileged EXEC password<br>
passowrd do router normalmente é sempre class
```
enable secret class
```
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/e173a8f8-9ddf-4bd5-8dc8-de3f55855404)

# Secure Passwords
Part 2: Secure Passwords
a. Using the command prompt on PC0, Telnet to Router1.
![Captura de ecrã 2024-02-21 153814](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/ecb6c204-d0a4-4644-8c95-8415bbb5241c)
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/0311acb0-23ff-45e4-b11e-194a75500ea9)
![Captura de ecrã 2024-02-21 153843](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/2fc42f23-bebf-4ed3-af17-be334703ef96)
<br> b. Save the current configuration so that any mistakes you might make can be reversed by toggling the 
power for Router1.
sniffer
![image](https://github.com/FaculdadeLicenciatura/Seguranca-de-Redes-e-Sistemas/assets/50460047/ee0ecf8d-3ca2-49f8-8965-f31b045e5f35)

c. Show the current configuration and note that the passwords are in plain text. Enter the command that 
encrypts plain text passwords:
```
enable class
Router1(config)# service password-encryption
```
d. Verify that the passwords are encrypted
