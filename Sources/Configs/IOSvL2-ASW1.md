# 0
```Cisco-IOS
!VLAN configuraion:
vl 10
	name Servers
vl 99
	name Management
	
int vl 99
	no sh 
	ip addr 10.0.99.3 255.255.255.240
	ip dafault-gateway 10.0.991

!Trunk port configuration:
int g0/0
	sw 
	sw tr enc dot1q
	sw mo tr
	sw tr all vl 10,99
	sw nonego
	do wr

!Access ports configuration:
int g1/0
	sw
	sw mo acc
	sw acc vl 99
	
int g2/0
	sw
	sw mo acc
	sw acc vl 10
	do wr
```

# 1
```Cisco-IOS
!Port Security:
int g1/0
	sw po
	sw po max 2
	sw po mac stick
	sw po vio shut
	do wr
	
int g2/0
	sw po
	sw po max 2
	sw po mac stick
	sw po vio shut
	do wr

!Unused ports shutdown:
int ra g0/1-3
	sh
int ra g1/1-3
	sh
int ra g2/1-3
	sh
int ra g3/0-3
	sh

!STP (Rapid PVST):
spa mo rap
spa vl 10,99 prio 61440
int g1/0
	spa portfast
	spa bpdugua en
int g2/0
	spa portfast
	spa bpdugua en

!DHCP Snooping:
ip dhc snoo
no ip dhc snoo info opt
ip dhc snoo vl 10,99
int g0/0
ip dhc snoo trust

!DAI:
ip arp ins vl 10,99
ip arp ins val dst-mac src-mac ip
int g0/0
	ip arp ins trust

!IPSG:
int g1/0
	ip ver source

!

```
>**نکته**:
>در حین راه‌اندازی Port Security روی Interfaceهایی که VMWare VM بهشون وصل بود **مجبور** به استفاده از`sw po max 2`شدم که دلیلش رو داخل بخش "**چالش‌ها**" نوشتم‼️


# 2





# 3




# 4







# 5









# 6
