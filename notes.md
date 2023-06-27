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