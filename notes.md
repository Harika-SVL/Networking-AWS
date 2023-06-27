## Private vs Public Network

=> Private Network: Network which cannot be accesed directly from internet
=> Public Network: Network which can be accessed from internet

* Private network cidr ranges :

=> 10.0.0.0/8: 10.0.0.0 to 10.255.255.255
=> 172.16.0.0/12: 172.16.0.0 -- 172.31.255.255
=> 192.168.0.0/16: 192.168.0.0 -- 192.168.255.255

* Here to know the bigger network : 
```
example
192.168.0.0/22 => hosts =32-22=10 => 2^10
192.168.0.0/24 => hosts =32-24=8 => 2^8
```
=> N (Network-ID) is always a fixed number
=> Network size = no.of host ID's ( So 22 is larger network than 24 ) 

## Subnets

* Subnet (sub networks) are parts of larger network

### Scenario

* Consider you need to create network with subnets for the following

1. A Building with 4 floors, Each floor requires 50 devices
```
each floor ~= 50
2^n ~= 50
n = 6
N = 32-6 = 26

building ~= 50 * 4 = 200
2^n ~= 200
n = 8
N = 24

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

building network: 192.168.0.0/24

BD SM: 11111111.11111111.11111111.00000000
FL SM: 11111111.11111111.11111111.11000000
----------------------------------------------
                                 .xx000000
                                 .00000000 => 192.168.0.0/26 (1st floor)
                                 .01000000 => 192.168.0.64/26 (2nd floor)
                                 .10000000 => 192.168.0.128/26 (3rd floor)
                                 .11000000 => 192.168.0.192/26 (4th floor)
```
* Each device requires 100 devices
```
each floor ~= 100
2^n ~= 100
n = 7
N = 25

building ~= 400
2^n ~= 400
n = 9
N = 23

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

172.16.0.0/23

BD SM: 11111111.11111111.11111110.00000000
FL SM: 11111111.11111111.11111111.10000000

----------------------------------------------
                                x.x0000000
                                0.00000000 => 172.16.0.0/25
                                0.10000000 => 172.16.0.128/25
                                1.00000000 => 172.16.1.0/25
                                1.10000000 => 172.16.1.128/25
```
* Each floor requires 30,000 devices
```
each floor ~= 30000
2^n ~= 30000
n = 15
N = 17

building ~= 120000
2^n ~= 120000
n = 17
N = 15

10.0.0.0/8
172.16.0.0/12

building: 10.0.0.0/15

BD SM: 11111111.11111110.00000000.00000000
FL SM: 11111111.11111111.10000000.00000000
  --------------------------------------------
                       x.x
                       0.00000000  => 10.0.0.0/17
                       0.10000000  => 10.0.128.0/17
                       1.00000000  => 10.1.0.0/17
                       1.10000000  => 10.1.128.0/17
```
2. Building with 8 floors

* Each floor requires 100 devices
```
each floor ~= 100
2^n ~= 100
n = 7
N = 25

building ~= 800
2^n ~= 800
n = 10
N = 22

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

bd: 192.168.0.0/22

BD SM: 11111111.11111111.11111100.00000000
FL SM: 11111111.11111111.11111111.10000000
--------------------------------------------
                               xx.x
                               00.00000000 => 192.168.0.0/25
                               00.10000000 => 192.168.0.128/25
                               01.00000000 => 192.168.1.0/25
                               01.10000000 => 192.168.1.128/25
                               10.00000000 => 192.168.2.0/25
                               10.10000000 => 192.168.2.128/25
                               11.00000000 => 192.168.3.0/25
                               11.10000000 => 192.168.3.128/25
```
* Each floor has 30,000 devices
```
each floor ~= 30,000
2^n ~30,000
n = 15
N = 17

building ~= 800
2^n ~= 800
n = 10
N = 22

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

bd: 172.16.0.0/22

BD SM: 11111111.11111111.11111100.00000000
FL SM: 11111111.11111111.10000000.00000000
--------------------------------------------
                          xxxxx     
                          00000    

                          11111     
```
* Each floor has 50 devices
```
each floor ~= 50
2^n ~= 50
n = 6
N = 32-6 = 26

building ~= 800
2^n ~= 800
n = 10
N = 22

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

building network: 192.168.0.0/26

BD SM: 11111111.11111111.11111100.00000000
FL SM: 11111111.11111111.11111111.11000000
----------------------------------------------
                               xx.xx  
                               0000  

                               1111
```
## Network Interface

* A device is connected to the network using Network interface

![Alt text](shots/1.PNG)

* The ip that the network interface recieves can be used to access the device/system/server
* A device can have multiple network interfaces
* Network interfaces gets an ip address assigned to it by DHCP (Dynamic Host Configuration Protocol) server

![Alt text](shots/2.PNG)

* In your home networks, wifi routers have built in DHCP which assigns the ip
* DHCP can assign dynamic ip or static ip depending on configuration.
* Interface gets the IPaddress whereas DHCP gives the IPaddress

## How can a private network access internet?

* Rule: Any server on public network will respond to other server in public network only.
* NAT (Network Address Translation) can help

![Alt text](shots/3.PNG)

## Rules in networking

* In networking we need to write rules (firewalls, routers, etc), Rules are designed to work with network id’s only
* Rules generally involve cidr ranges with focus on network id part

```
Specific network :

192.168.0.0/24
10.0.0.0/16

Any ip address :

0.0.0.0/0

specific ip address :

4.4.4.4/32
```



