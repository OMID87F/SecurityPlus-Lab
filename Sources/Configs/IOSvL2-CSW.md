# 0
```
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

```



# 2





# 3




# 4







# 5









# 6
