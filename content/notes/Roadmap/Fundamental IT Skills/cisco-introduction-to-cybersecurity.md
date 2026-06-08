+++
title = 'Cisco Introduction to Cybersecurity'
date = 2026-05-18T15:04:15+06:00
tags = ["note", "roadmap", "cyber"]
type = "fundamentalITSkills"
roadmap_section = "Fundamental IT Skills"
roadmap_topic = ""
tools = []
summary = ""
+++

This course consists of five modules and a final exam and should take you approximately six hours to complete.

On completing this course

1. Explain the basics of being safe online, including what cybersecurity is and its potential impact.
2. Explain the most common cyber threats, attacks and vulnerabilities.
3. Explain how organizations can protect their operations against these attacks.
4. Access various information and resources to explore the different career options in cybersecurity.

<!--more-->
## Module 1: Introduction to Cybersecurity

### What is Cybersecurity

It is an ongoing effort to protect 1. indivisuals, 2. organizations, 3. governments from digital attacts by protecting networked systems and data from unauthorized use or harm.

### Organizational Data

1. Traditional Data
    - Transactional data:  
        buying selling production
    - Intellectual property:  
        patents trademarks, new-product-plan trade secret
    - Financial data

2. IoT

### The cube

1. The foundational principles protect info
    - confidentiality
    - integrety
    - availability
2. protection in each stage 
    - processing  (data in process)
    - starage (data at rest)
    - transmission (data in transit)
3. security measures to protect
    - awareness
    - technology
    - policy

### Attakers

1. Amateurs (script kiddies)
2. Hackers  
   white, gray, black hat attackers
3. Organied hackers  
   - hacktivists make political statement
   - terrorists
   - state sponsored

## Modaule 2: Attacks, Concepts and Techniques

### Types of Malware

- spyware
- adware
- backdoor
- ransomware
- scareware
- rootkit
- virus
- trojan horse
- worms

### Methods of infiltration 

- social engineering
- denial of service
- distributed DoS
- botnet
- on-path attacks
- seo poisoning
- wi-fi password cracking
- password attacks 
- advanced persistent threats

### Meltdown and spectre


### Categories of software vulnerabilities

- buffer overflow
- non-validated input
- race conditions
- weakness in security practicies
- acces control problems

Cryptojacking is illegal mining of crypto without the knowledge of device owner.

## Module 3: Protecting your Date and Privacy

## Module 4: Protecting the Organization

### Nmap Port Scanning

`sudo nmap [ip]` 
`sudo nmap -sS [ip]`
`sudo nmap -sV [ip]`
`nmap --script default [ip]`
`curl ifconfig.me`

`nmap -T Aggressive -A [ip]` this commands output is this:

```
❯ nmap -T Aggressive -A [ip]
Starting Nmap 7.99 ( https://nmap.org ) at 2026-06-05 11:06 +0600
Nmap scan report for [ip]
Host is up (0.012s latency).
Not shown: 987 closed tcp ports (conn-refused)
PORT     STATE    SERVICE        VERSION
21/tcp   filtered ftp
22/tcp   filtered ssh
23/tcp   filtered telnet
80/tcp   open     http           MikroTik router config httpd
|_http-title: RouterOS router configuration page
| http-robots.txt: 1 disallowed entry 
|_/
161/tcp  filtered snmp
179/tcp  open     tcpwrapped
443/tcp  filtered https
1723/tcp filtered pptp
2000/tcp open     bandwidth-test MikroTik bandwidth-test server
2002/tcp filtered globe
8080/tcp filtered http-proxy
8088/tcp filtered radan-http
8291/tcp filtered winbox
Service Info: OS: RouterOS; Device: router; CPE: cpe:/o:mikrotik:routeros

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.05 seconds

~ took 13s 
```

### Security appliances

1. Routers      basic traffic filter
2. Firewalls    identify & block by filtering communication based on

     - Network layes  
     source & destination ip addr
        
     - Transport layer  
     source & destination data ports & connection state
        
     - Application layer  
     based on application, program or service
        
     - Context aware layer  
     user, device, role, application type and threat profile
        
     - Proxy server  
     filters web content requests like URLs, domain names, and media types
        
     - Reverse proxy server  
     placed in front of web servers and protect, hide, offload, destribute access 
        
     - Network address translation (NAT) firewall  
     hides private addresses of network hosts
        
     - Host-based  
     filters ports and system service calls on single pc
        
4. IPS(Intrusion prevention systems)    traffic signature math and block

     - IDS   only detect, log and report, runs parallel offline

     - IPS   block deny based on positive rule or signature match

6. VPN      enctypted tunnel for remote
7. Antimalware and antivirus    behave & signature to analyse & block
8. Others : web & email security, decryption device, client access control, etc.

Behavior-Based detection tool Honeypot.

Netflow

### Penetration Testing

1. Planning  
   gathers info about vulnerabilities, exploits footprinting
2. Scanning  
   active reconnaissance:
    port scanning
    vulnerability scanning
    estabilishing active connection (enumeration)
3. Gain access
4. Maintain access
5. Analysis and report

### Risk Management process

- Frame the risk
- Assess the risk
- Respond to the risk
- Monitor the risk

### CSIRT(Computer Security Incident Response Team)

Forum of Incident Response and Security Teams (FIRST)  
The National Safety Information Exchange (NSIE)  
The Defense Security Information Exchange (DSIE)  
The DNS Operations Analysis and Research Center (DNS-OARC)

### Incident detection and prevention

SIEM (Security Information and Event Management) collects and analyzes security alerts, logs and other real-time and historical data from security devices on the network to facilitate early detection off cyber attacks.

DLP (Data Loss Prevention) system id designed to stop sensiteive data from begin stolen/escaping from a network.  
Data in use  
Data in motion  
Data at rest

## Module 5:
