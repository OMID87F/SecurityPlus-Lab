# 0
```Cisco-IOS
!VLAN configuraion:
vl 10
	name Servers
vl 20
	name Staff
vl 30
	name Guests
vl 99
	name Management
	
int vl 99
	no sh 
	ip addr 10.0.99.2 255.255.255.240
	ip dafault-gateway 10.0.991

!Trunk ports configuration:
int ra g0/0-2
	sw 
	sw tr enc dot1q
	sw mo tr
	sw tr all vl 10,20,30,99
	sw nonego
	do wr
```

# 1
```Cisco-IOS
!Unused ports shutdown:
int g0/3
	sh
int ra g1/0-3
	sh
int ra g2/0-3
	sh
int ra g3/0-3
	sh

!STP (Rapid PVST):
spa mo rap
spa vl 10,20,30,99 prio 4096
int ra g0/1-2
	spa guard root

!DHCP Snooping:
ip dhc snoo
no ip dhc snoo info opt
ip dhc snoo vl 10,20,30,99
int g0/0
ip dhc snoo trust

!DAI:
ip arp ins vl 10,20,30,99
ip arp ins val dst-mac src-mac ip
int ra g0/0-2
	ip arp ins trust

!IPSG:


```



# 2





# 3




# 4







# 5









# 6
