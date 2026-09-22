## Homelab and network pentesting lab:
This is a repository containing both my personal homelab projects which I am setting up in order to learn about **networking**, **internet infrastructure** and get more control over my data as well as my security focused homelab which I use in order to practice and get **experience** in the field of **network pentetration testing**

# (1) Homelab for networking -
I currently have 3 different docker services running on an **Ubuntu LTS server** VM that I am running using VBox as a hypervisor on my main machine since I do not yet have dedicated hardware.
The VM employs a bridges adapter allowing it to act as a seperate device on my home network which allows other devices to interact with it and utilise the hosted services.
  (a) **Adguard**: I setup [adguard](https://hub.docker.com/r/adguard/adguardhome) as a *locally hosted DNS resolver/forwarder* that allows me to see all DNS queries from my network in real-time as well as letting me employ a *network wide ad-blocking service* that does rely on any 3rd party software that I send my personal data to
  (b) **Nginx**: I setup [nginx](https://hub.docker.com/hardened-images/catalog/dhi/nginx) a one of my first containers to learn the ins and outs of self-hosting and specifically docker, it's a simple *locally hosted webpage* that can be accessed by other devices on the network at a specific port that it mapped to nginx port 80(where nginx serves the site)
  (c) **Uptime-kuma**: [Uptime-kuma](https://hub.docker.com/hardened-images/catalog/dhi/uptime-kuma) is a service that allows me to *monitor all the other services that I have setup*(whether they are online and responsive or not) which makes it a no-brainer to include in any homelab setup 

In my current setup the main drawback that I am facing is the *lack of dedicated hardware* especially with adguard since it only works as a DNS forwarder *as long as my device is online and connected to the network*, otherwise the network defaults to a backup DNS I setup which makes ad-blocking and other features inconsistent.


# (2) Pentesting Lab:
Currenly I am running 2 virtual machines on VBox, one is a kali linux VM which I employ as my attackbox and a metasploitable-2(intentionally vulnerable machine made to practice network attacks) VM which is used as the target machine which I practice against.
Both of thee virtual machines are kept on a host-only LAN configuration so that they can only see each other and my device(which acts as a router/switch for them performing NAT) to make sure vulnerable machines aren't publically visible potentially leading to an attacker compromising my network through it.

Pentesting workflow-
  (a) All pentests done start off with **recon**, for me this is scanning the machine using a tool called **nmap** which allows me to scan the target machines ports and get a layout of *open*, *closed* and *filtered ports*. I use nmap scripts on such scans to automate some part of vuln discovery
  (b) Upon the discovery of an open port and a vulnerability I (if it is my first time exploiting) research, learn about and carry out *manual exploitation* of the service in order to get a deeper understanding and on subsequent attacks **metasploit** modules in order to automate the workflow
  (c) Once into the system the next part is to perform **post-exploitation** procedures, this invloved checking what level of access the vulnerability gave us and from there performing **privilege escalation** and/or **lateral movement** to get a greater reach and footholf into the system(*this is a part of the pentest process I still need to learn about and am working towards*)
  (d) **Documenting** is something that is done throughout the entire process, this includes commands ran, tools used, vulnerabilities and possible points of entry discovered during recon, exploits performed and all other steps taken throghout the pentest

