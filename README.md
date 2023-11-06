<p align="center">
  <img src="https://github.com/jotavare/jotavare/blob/main/42/banner/new/42_netpractice_banner_new.png">
</p>

<p align="center">
	<img src="https://img.shields.io/badge/status-finished-success?color=%2312bab9&style=flat-square"/>
	<img src="https://img.shields.io/badge/evaluated-25%20%2F%2009%20%2F%202023-success?color=%2312bab9&style=flat-square"/>
	<img src="https://img.shields.io/badge/score-100%20%2F%20100-success?color=%2312bab9&style=flat-square"/>
	<img src="https://img.shields.io/github/languages/top/jotavare/netpractice?color=%2312bab9&style=flat-square"/>
	<img src="https://img.shields.io/github/last-commit/jotavare/netpractice?color=%2312bab9&style=flat-square"/>
	<a href='https://www.linkedin.com/in/joaoptoliveira' target="_blank"><img alt='Linkedin' src='https://img.shields.io/badge/LinkedIn-100000?style=flat-square&logo=Linkedin&logoColor=white&labelColor=0A66C2&color=0A66C2'/></a>
	<a href='https://profile.intra.42.fr/users/jotavare' target="_blank"><img alt='42' src='https://img.shields.io/badge/Porto-100000?style=flat-square&logo=42&logoColor=white&labelColor=000000&color=000000'/></a>
</p>

<p align="center">
	<a href="#about">About</a> •
	<a href="#how-to-use">How to use</a> •
	<a href="#license">License</a>
</p>

## ABOUT
NetPractice is a practical networking exercise aimed at exploring the fundamentals of networking. In this project, i will configure small-scale networks and delve into the world of TCP/IP addressing. The goal is to complete 10 levels, each designed to challenge and enhance my networking knowledge.

<a href="https://github.com/jotavare/netpractice/blob/main/subject/en_subject_netpractice.pdf">Click here</a> for the subject of this project.

## HOW TO USE
### EXECUTION
#### 1º - Change directory
```bash
cd netpractice/netpractice/exercices/
```

#### 2º - Open the index.html file
```bash
open -a "Google Chrome" index.html
```

### INFORMATION
#### Complete all 10 levels
> There will be a practice and evaluation mode.

- `Practice mode` - Insert your 42 intra username. You will do all 10 levels.
- `Evaluation mode` - 3 random leves from level 6 to level 10. You only have 15 minutes for all.

#### Buttons
> There will be 2 buttons on the top left corner (3 if you successfully completed a level).

- `Check again` - Verify whether your configuration was correct or not.
- `Get my config` - Download your configuration. It will be needed to turn in your assignment.
- `Next level` - Click on this button to get to the next level.

#### Important
Before moving to the next level, don’t forget to export your configuration using the Get my config button so you can put it in your Git repository.

## RESOURCES
### What is a subnet?

  A **subnet or a subnetwork** is a *network inside a network*. Subnets make networks more efficient.
  
  **Subnetting** is the process of stealing bits from the HOST part of IP address in order to divide the large network into smaller ones called subnets. After subnetting, we end up with **NETWORK SUBNET HOST** fields, and we always reserve an IP address to *identify the subnet* and another one to *identify the broadcast subnet address*, and through subnetting, network traffic can travel a shorter distance without passing through unnecessary routes to reach its destination.

### How to calculate a subnet mask from IP address step by step?

  We will work with the IP address `10.20.4.13/29`

  #### Step 1: Find Subnet Number:
    Subtract prefix number from /32
    32 - 29 = 3
    
    Calculate Subnet Mask:
    8 bits - 3 bits = 5 bits (Network bits turned on)
    
    You might be asking why 8 bits, 8 bits are required for each octet.
    
    |-------|-------|-------|-------|-------|-------|-------|-------|
    | 128   | 64    | 32    | 16    | 8     | 4     | 2     | 1     |
    |-------|-------|-------|-------|-------|-------|-------|-------|
    | 1     | 1     | 1     | 1     | 1     | 0     | 0     | 0     |
    |-------|-------|-------|-------|-------|-------|-------|-------|
    | 128 + | 64 +  | 32 +  | 16 +  | 8     | =     248             |
    |-------|-------|-------|-------|-------|-------|-------|-------|
    
    Subnet Mask = 255.255.255.248
  
  #### Step 2: Find Subnet Size:
    Raise 2 to the power of deducation (8 - 3 = 5) -> Let's called it n.
    
    2 ** n    = Subnet Size.
    2 ** 3    = Subnet Sizes for each subnet.
    2 * 2 * 2 = 8
    
    NOTE: 8 is the block size for the subnet, so for example:
    the increments will now be 0 8 16 24 32 and so on (we add 8 each time)
    
  #### Step 3: Find Broadcast Address:
    Subnet size - 1
    (2 ** n) - 1  = Broadcast Address
    (2 ** 3) - 1  = (8 - 1) = 7
  
  #### Step 4: Locate IP Address Subnet:
    Identify subnet block for IP address:
    -> Where in each increment is the address 10.20.4.13/29 located (0 8 16 32 40)?
    
    13 falls between 8 and 16 and therefore the address is in the valid host range of the subnet 10.20.4.8/29
  
  #### Step 5: Calculate The Valid Hosts:
    Subnet size - 2
    (2 ** n) - 2 = Valid Host Range
    (2 ** 3) - 2 = (8 - 2) = 6
    
  #### And from these steps, we can know 4 important things:
    
    Subnet Address    -> 10.20.4.8/29
    Min Host Address  -> 10.20.4.9/29
    Max Host Address  -> 10.20.4.14/29
    Broadcast Address -> 10.20.4.15/29

### Subnet Mask Chart
Here is a quick reference table for help when subnetting.
|Subnet Mask 	|CIDR |	Binary Notation| 	Network Bits| 	Host Bits| 	Available Addresses |
| -             | -    | -                                     | -    | -     | -           | 
|255.255.255.255| 	/32| 	11111111.11111111.11111111.11111111| 	32| 	0 | 	1       |
|255.255.255.254| 	/31| 	11111111.11111111.11111111.11111110| 	31| 	1 | 	2       |
|255.255.255.252| 	/30| 	11111111.11111111.11111111.11111100| 	30| 	2 | 	4       |
|255.255.255.248| 	/29| 	11111111.11111111.11111111.11111000| 	29| 	3 | 	8       |
|255.255.255.240| 	/28| 	11111111.11111111.11111111.11110000| 	28| 	4 | 	16      |
|255.255.255.224| 	/27| 	11111111.11111111.11111111.11100000| 	27| 	5 | 	32      |
|255.255.255.192| 	/26| 	11111111.11111111.11111111.11000000| 	26| 	6 | 	64      |
|255.255.255.128| 	/25|    11111111.11111111.11111111.10000000| 	25| 	7 | 	128     |
|255.255.255.0  | 	/24| 	11111111.11111111.11111111.00000000| 	24| 	8 | 	256     |		
|255.255.254.0  | 	/23| 	11111111.11111111.11111110.00000000| 	23| 	9 | 	512     |
|255.255.252.0  | 	/22| 	11111111.11111111.11111100.00000000| 	22| 	10| 	1024    |
|255.255.248.0  | 	/21| 	11111111.11111111.11111000.00000000| 	21| 	11| 	2048    |
|255.255.240.0  | 	/20| 	11111111.11111111.11110000.00000000| 	20| 	12| 	4096    |
|255.255.224.0  | 	/19| 	11111111.11111111.11100000.00000000| 	19| 	13| 	8192    |
|255.255.192.0  | 	/18| 	11111111.11111111.11000000.00000000| 	18| 	14| 	16384   |
|255.255.128.0  | 	/17| 	11111111.11111111.10000000.00000000| 	17| 	15| 	32768   |
|255.255.0.0    | 	/16| 	11111111.11111111.00000000.00000000| 	16| 	16| 	65536   |	
|255.254.0.0    | 	/15| 	11111111.11111110.00000000.00000000| 	15| 	17| 	131072  |
|255.252.0.0    | 	/14| 	11111111.11111100.00000000.00000000| 	14| 	18| 	262144  |
|255.248.0.0    | 	/13| 	11111111.11111000.00000000.00000000| 	13| 	19| 	524288  |
|255.240.0.0    | 	/12| 	11111111.11110000.00000000.00000000| 	12| 	20| 	1048576 |
|255.224.0.0    | 	/11| 	11111111.11100000.00000000.00000000| 	11| 	21| 	2097152 |
|255.192.0.0    | 	/10| 	11111111.11000000.00000000.00000000| 	10| 	22| 	4194304 |
|255.128.0.0    | 	/9 | 	11111111.10000000.00000000.00000000| 	9 | 	23| 	8388608 |
|255.0.0.0      |   /8 | 	11111111.00000000.00000000.00000000| 	8 | 	24| 	16777216| 

### A command line utility that will help you understand more about Address Manupilation:

    brew install ipcalc
   
   <p align="center">
     <img width="497" alt="Screen Shot 2023-05-21 at 10 55 03 PM" src="https://github.com/iimyzf/NetPractice/assets/63506492/0faa87a2-922a-44fb-b86a-594cb8f9d798">
   </p>

## LICENSE
<p>
This work is published under the terms of <a href="https://github.com/jotavare/jotavare/blob/main/LICENSE">42 Unlicense</a>.
</p>
