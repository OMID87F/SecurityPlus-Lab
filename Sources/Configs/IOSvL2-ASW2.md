# 0
```Cisco-IOS
!VLAN configuraion:
vl 20
	name Staff
vl 30
	name Guests
vl 99
	name Management 
	
int vl 99
	no sh 
	ip addr 10.0.99.4 255.255.255.240
	ip dafault-gateway 10.0.991

!Trunk port configuration:
int g0/0
	sw 
	sw tr enc dot1q
	sw mo tr
	sw tr all vl 20,30,99
	sw nonego
	do wr

!Access ports configuration:
int ra g1/0-1
	sw
	sw mo acc
	sw acc vl 20
	
int ra g2/0-1
	sw
	sw mo acc
	sw acc vl 30
	do wr
```

# 1
```Cisco-IOS
!Port Security:
int ra g1/0-1
	sw po
	sw po max 2
	sw po mac stick
	sw po vio shut
	do wr
	
int ra g2/0-1
	sw po
	sw po max 1
	sw po mac stick
	sw po vio shut
	do wr	

!Unused ports shutdown:
int ra g0/1-3
	sh
int ra g1/2-3
	sh
int ra g2/2-3
	sh
int ra g3/0-3
	sh

!STP (Rapid PVST):
spa mo rap
spa vl 20,30,99 prio 61440
int ra g1/0-1
	spa portfast
	spa bpdugua en
int ra g2/0-1
	spa portfast
	spa bpdugua en

!DHCP Snooping:
ip dhc snoo
no ip dhc snoo info opt
ip dhc snoo vl 20,30,99
int g0/0
ip dhc snoo trust

!DAI:
ip arp ins vl 20,30,99
ip arp ins val dst-mac src-mac ip
int g0/0
	ip arp ins trust

!IPSG:
int ra g1/0-1
	ip ver source
int ra g2/0-1
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
