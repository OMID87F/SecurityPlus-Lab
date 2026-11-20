# 0
```
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
	
int g0/0
	sw 
	sw tr enc dot1q
	sw mo tr
	sw tr all vl 20,30,99
	sw nonego
	do wr
	
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



```
>**نکته**:
>در حین راه‌اندازی Port Security روی Interfaceهایی که VMWare VM بهشون وصل بود **مجبور** به استفاده از`sw po max 2`شدم که دلیلش رو داخل بخش "**چالش‌ها**" نوشتم‼️


# 2





# 3




# 4







# 5









# 6
