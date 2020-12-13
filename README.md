# Jarkom_Modul4_Lapres_E1
## UML CIDR
### Pembagian subnet
![](img/1.png)
### Kebutuhan IP
**Server**
|Subnet|Jumlah IP|Netmask
|------|---------|-------
|A1|2|/30
|A2|2|/30

**Client**
|Subnet|Jumlah IP|Netmask
|------|---------|-------
|A3|721|/22
|A4|252|/24
|A5|2|/30
|A6|521|/22
|A7|13|/28
|A8|502|/23
|A9|2|/30
|A10|2|/30
|A11|701|/22
|A12|2|/30
|A13|2021|/21
|A14|101|/25
|A15|1001|/22
|Total|5841|/19

### Pembagian IP
![](img/2.png)
### UML
#### Topologi

**[ROUTER]**
```
SURABAYA
PASURUAN
PROBOLINGGO
BATU
KEDIRI
MADIUN
BLITAR
```

**[CLIENT]**
```
BOJONEGORO
TULUNGAGUNG
NGANJUK
LUMAJANG
JOMBANG
SAMPANG
SIDOARJO
BANYUWANGI
JEMBER
BONDOWOSO
```

**[SERVER]**

```
MOJOKERTO
MALANG
```

```
A1/30 10.151.71.16
255.255.255.252
SURABAYA - 10.151.71.17
MOJOKERTO - 10.151.71.18

A15/22 192.168.64.0
255.255.252.0
SURABAYA - 192.168.64.1
SAMPANG - 192.168.64.2

A10/30 192.168.192.0
255.255.255.252
SURABAYA - 192.168.192.1
PASURUAN - 192.168.192.2

A11/22 192.168.160.0
255.255.252.0
PASURUAN - 192.168.160.1
SIDOARJO - 192.168.160.2

A12/30 192.168.144.0
255.255.255.252
PASURUAN - 192.168.144.1
PROBOLINGGO - 192.168.144.2

A13/21 192.168.128.0
255.255.248.0
PROBOLINGGO - 192.168.128.1
BANYUWANGI - 192.168.128.2
JEMBER - 192.168.132.1

A14/26 192.168.136.0
255.255.255.192
PROBOLINGGO - 192.168.136.1
BONDOWOSO - 192.168.136.2

A9/30 192.168.32.0
255.255.255.252
SURABAYA - 192.168.32.1
BATU - 192.168.32.2

A6/22 192.168.20.0
255.255.252.0
BATU - 192.168.20.1
NGANJUK - 192.168.20.2

A8/23 192.168.16.0
255.255.254.0
BATU - 192.168.16.1
MADIUN - 192.168.16.2
JOMBANG - 192.168.16.3

A7/28 192.168.18.0
255.255.255.240
MADIUN - 192.168.18.1
BOJONEGORO - 192.168.18.2

A5/30 192.168.8.0
255.255.255.252
BATU - 192.168.8.1
KEDIRI - 192.168.8.2

A2/30 10.151.71.20
255.255.255.252
KEDIRI - 10.151.71.21
MALANG - 10.151.71.22

A4/24 192.168.4.0
255.255.255.0
KEDIRI - 192.168.4.1
BLITAR - 192.168.4.2
LUMAJANG - 192.168.4.3

A3/27 192.168.0.0
255.255.255.224
BLITAR - 192.168.0.1
TULUNGAGUNG - 192.168.0.2
```

**Switch**
```
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch6 > /dev/null < /dev/null &
uml_switch -unix switch7 > /dev/null < /dev/null &
uml_switch -unix switch8 > /dev/null < /dev/null &
uml_switch -unix switch9 > /dev/null < /dev/null &
uml_switch -unix switch10 > /dev/null < /dev/null &
uml_switch -unix switch11 > /dev/null < /dev/null &
uml_switch -unix switch12 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch14 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
```

**Router**
```
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.70.9 eth1=daemon,,,switch15 eth2=daemon,,,switch10 eth3=daemon,,,switch9 eth4=daemon,,,switch1 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch10 eth1=daemon,,,switch12 eth2=daemon,,,switch11 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch12 eth1=daemon,,,switch14 eth2=daemon,,,switch13 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch9 eth1=daemon,,,switch5 eth2=daemon,,,switch6 eth3=daemon,,,switch8 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch4 eth2=daemon,,,switch2 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch4 eth1=daemon,,,switch3 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch8 eth1=daemon,,,switch7 mem=64M &
```

**Server**
```
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch2 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch1 mem=64M &
```

**Client**
```
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch15 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch14 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch13 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch13 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch11 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch4 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch3 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch6 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch7 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch8 mem=64M &
```

**Ingat iptables di surabaya**
```
bash iptables.sh
nano iptables.sh
```

**[iptables]**

    #!/bin/sh
    iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.168.0.0/16

**[Start interfaces config]**

```
nano /etc/network/interfaces
service networking restart
```

**ROUTER**
```
nano /etc/sysctl.conf
mv /etc/sysctl.conf /etc/baksysctl.conf
echo "net.ipv4.ip_forward=1" > /etc/sysctl.conf
cat /etc/baksysctl.conf >> /etc/sysctl.conf
sysctl -p
```

```
nano route.sh
#!/bin/bash
```

**[SURABAYA]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.70.10
netmask 255.255.255.252
gateway 10.151.70.9

auto eth1
iface eth1 inet static
address 192.168.64.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.168.192.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 192.168.32.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.151.71.17
netmask 255.255.255.252
#
ip route add 192.168.128.0/18 via 192.168.192.2 dev eth2
ip route add 192.168.0.0/19 via 192.168.32.2 dev eth3
ip route add 10.151.71.20/30 via 192.168.32.2 dev eth3
```
**[PASURUAN]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.192.2
netmask 255.255.255.252
gateway 192.168.192.1

auto eth1
iface eth1 inet static
address 192.168.144.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.160.1
netmask 255.255.252.0
#
ip route add 192.168.128.0/20 via 192.168.144.2 dev eth1
```

**[PROBOLINGGO]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.144.2
netmask 255.255.255.252
gateway 192.168.144.1

auto eth1
iface eth1 inet static
address 192.168.136.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 192.168.128.1
netmask 255.255.248.0
#
```
**[BATU]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.32.2
netmask 255.255.255.252
gateway 192.168.32.1

auto eth1
iface eth1 inet static
address 192.168.8.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.20.1
netmask 255.255.252.0

auto eth3
iface eth3 inet static
address 192.168.16.1
netmask 255.255.254.0
#
ip route add 192.168.18.0/28 via 192.168.16.2 dev eth3
ip route add 192.168.0.0/21 via 192.168.8.2 dev eth1
ip route add 10.151.71.20/30 via 192.168.8.2 dev eth1
```

**[KEDIRI]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.8.2
netmask 255.255.255.252
gateway 192.168.8.1

auto eth1
iface eth1 inet static
address 192.168.4.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.151.71.21
netmask 255.255.255.252
#
ip route add 192.168.0.0/27 via 192.168.4.2 dev eth1
```

**[BLITAR]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.4.2
netmask 255.255.255.0
gateway 192.168.4.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.224
#
```

**[MADIUN]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.16.2
netmask 255.255.254.0
gateway 192.168.16.1

auto eth1
iface eth1 inet static
address 192.168.18.1
netmask 255.255.255.240
#
```
#### SERVER START
**[MALANG]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.71.22
netmask 255.255.255.252
gateway 10.151.71.21
#
```

**[MOJOKERTO]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.71.18
netmask 255.255.255.252
gateway 10.151.71.17
#
```
#### CLIENT START
**[SAMPANG]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.64.2
netmask 255.255.252.0
gateway 192.168.64.1
#
```

**[BONDOWOSO]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.136.2
netmask 255.255.255.128
gateway 192.168.136.1
#
```

**[JEMBER]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.132.1
netmask 255.255.248.0
gateway 192.168.128.1
#
```

**[BANYUWANGI]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.128.2
netmask 255.255.248.0
gateway 192.168.128.1
#
```

**[SIDOARJO]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.160.2
netmask 255.255.252.0
gateway 192.168.160.1
#
```

**[LUMAJANG]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.4.3
netmask 255.255.255.0
gateway 192.168.4.1
#
```

**[TULUNGAGUNG]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.224
gateway 192.168.0.1
#
```

**[NGANJUK]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.20.2
netmask 255.255.252.0
gateway 192.168.20.1
#
```

**[BOJONEGORO]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.18.2
netmask 255.255.255.240
gateway 192.168.18.1
#
```

**[JOMBANG]**
```
#
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.16.3
netmask 255.255.254.0
gateway 192.168.16.1
#
```

![](img/3.png)
![](img/4.png)

## CPT VLSM
### Pembagian subnet
![](img/5.png)
### Kebutuhan IP
![](img/6.png)
### Tree
![](img/7.png)
### Pembagian NID
![](img/8.png)

![](img/9.png)
### Routing
![](img/10.png)
