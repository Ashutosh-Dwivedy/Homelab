# Homelab and network pentesting lab:
This is a repository containing both my personal homelab projects which I am setting up in order to learn about **networking**, **internet infrastructure** and get more control over my data as well as my security focused homelab which I use in order to practice and get **experience** in the field of **network pentetration testing**<br />

TL;DR:
- Services(Networking lab): adguard home(DNS forwarder+ad blocker), nginx(webpage), uptime-kuma(monitoring)
- Networking Lab VM(Ubuntu server) run on bridged adapter to allow network accessability
- Services(Pentesting lab): Kali linux VM, Metasploitable 2 VM
- Pentesting VM's kept on a host-only network to prevent intrusions
- Main drawback faced is lack of dedicated homelab hardware

## (1) Homelab for networking -
I currently have 3 different docker services running on an **Ubuntu LTS server** VM that I am running using VBox as a hypervisor on my main machine since I do not yet have dedicated hardware.<br />

The VM employs a bridged adapter allowing it to act as a seperate device on my home network which allows other devices to interact with it and utilise the hosted services.<br />
  **(a) Adguard:**
- I setup [adguard](https://hub.docker.com/r/adguard/adguardhome) as a *locally hosted DNS resolver/forwarder* + *network wide ad-blocking service*
- Allows me to see all DNS queries from my network in real-time  
- Prevents dependance on 3rd party software 
  **(b) Nginx**: 
- I setup [nginx](https://hub.docker.com/hardened-images/catalog/dhi/nginx) to learn the basics of self-hosting and specifically docker
- It's a simple *locally hosted webpage* that can be accessed by other devices on the network  
  **(c) Uptime-kuma**: 
- [Uptime-kuma](https://hub.docker.com/hardened-images/catalog/dhi/uptime-kuma) allows me to *monitor all the other services that I have setup*
- Allows for quick status checks and centralised management with ease of use  
       

## (2) Pentesting Lab:
Currenly I am running 2 virtual machines on VBox, (1) Kali linux VM which I employ as my attackbox (2) Metasploitable-2(intentionally vulnerable machine made to practice network attacks) VM which is used as the target machine<br />

Both of these virtual machines are kept on a host-only LAN configuration so that they can only see each other and my device(which acts as a router/switch for them performing NAT) to make sure vulnerable machines aren't publically visible potentially leading to an attacker compromising my network through it.<br />

Pentesting workflow-<br />
  **(a)Reconnaissance**
- All pentests done start off with **reconnaissance**
- This entails scanning the machine using a tool called **nmap** which allows me to get a layout of *open*, *closed* and *filtered ports*. 
- I use nmap scripts on such scans to automate some part of vuln discovery<br />
  **(b)Exploitation**
- Upon discovering an open port and a vulnerability I (if it is my first time exploiting) research, learn about and carry out *manual exploitation* of the service in order to get a deeper understanding 
- On subsequent attacks **metasploit** modules in order to automate the workflow<br />
  **(c)Post-exploitation**
- Once into the system the next part is to perform **post-exploitation** procedures
- This invloves checking what level of access we have and from there performing **privilege escalation** and/or **lateral movement** to get a greater reach and foothold into the system
- This is a part of the pentest process I still need to learn about and am working towards<br />
  **(d)Documentation**
- Documenting is something that is done throughout the entire process
- This includes commands ran, tools used, vulnerabilities and possible points of entry discovered during recon, exploits performed and all other steps taken throghout the pentest


## (3) Drawbacks/Limitations:
- One of the main issues that I currently face is the lack of dedicated harware which I can use to run my networking lab services
- Since I currently run everything off of my own laptop the services are only online as long as my device is
- This makes tracking, monitoring and features such as ad-blocking inconsistent and the whole process a little more frustrating
