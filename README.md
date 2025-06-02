# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
# AIM:
To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .
## DESIGN STEPS:
### Step 1:
Install kali linux either in partition or virtual box or in live mode
### Step 2:
Investigate on the various categories of tools as follows:
### Step 3:
Open terminal and try execute some kali linux commands
## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system
## OUTPUT:
![1](https://github.com/user-attachments/assets/930eeb87-451f-4d27-bc58-67ca8fb0369c)
POSTGRESQL
msfdb :
![2](https://github.com/user-attachments/assets/8586ca9f-3770-4bd1-a7fa-d0b543046e2c)
msfdb :
## OUTPUT:
![3](https://github.com/user-attachments/assets/a682d7d9-71f7-4316-afe6-3986a706d28c)
Invoke msfconsole:
## OUTPUT:
![4](https://github.com/user-attachments/assets/d7473d21-343f-49c0-8aa7-c3a75e71ea14)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
![5](https://github.com/user-attachments/assets/16a47ffc-4333-4afe-8e30-37a52e1de4ab)
## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![6](https://github.com/user-attachments/assets/c0d021b0-ad32-4dd4-9fbe-4f91516d5813)
## Step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24
## OUTPUT:
![7](https://github.com/user-attachments/assets/d493a593-52d6-44ff-8011-08e8a5307b41)
Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l
## OUTPUT:
![8](https://github.com/user-attachments/assets/bed83ff5-0e61-4eca-ae78-7b64b93ed107)
Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit
## OUTPUT:
![9](https://github.com/user-attachments/assets/407d8b6a-97e4-4a3c-8968-5ee4a20fe8dc)
The info command provides information regarding a module or platform,
## OUTPUT:
![10](https://github.com/user-attachments/assets/ee932dca-ca90-4aa8-8b08-802379adac04)
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
## OUTPUT:
![11](https://github.com/user-attachments/assets/720c949b-8ea4-4ccc-be64-9bcb8405d431)
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
## OUTPUT:
![12](https://github.com/user-attachments/assets/ea3d4e00-1625-4ca0-8b02-add44d28e808)
use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
![13](https://github.com/user-attachments/assets/d0b191df-04a9-4861-b1a0-733ac33d7c5b)
Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
![14](https://github.com/user-attachments/assets/e22bac41-b011-4930-958e-c9fdb37aaa58)
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
![15](https://github.com/user-attachments/assets/12a79854-75e2-483d-9818-8c045578eb84)
set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
## OUTPUT:
![16](https://github.com/user-attachments/assets/7a4bc0f7-0a15-42d4-8627-04c1cbca14be)
## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
