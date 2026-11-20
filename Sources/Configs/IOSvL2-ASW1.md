# 0
```
vl 10
	name Servers
vl 99
	name Management

int vl 99
	no sh 
	ip addr 10.0.99.3 255.255.255.240
	ip dafault-gateway 10.0.991
	
int g0/0
	sw 
	sw tr enc dot1q
	sw mo tr
	sw tr all vl 10,99
	sw nonego
	do wr
	
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




```
>**نکته**:
>در حین راه‌اندازی Port Security روی Interfaceهایی که VMWare VM بهشون وصل بود **مجبور** به استفاده از`sw po max 2`شدم که دلیلش رو داخل بخش "**چالش‌ها**" نوشتم‼️


# 2





# 3




# 4







# 5









# 6
