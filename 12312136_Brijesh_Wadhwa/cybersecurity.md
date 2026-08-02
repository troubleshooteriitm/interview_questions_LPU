Cybersecurity Interview Handbook
Part 1 (Questions 1–25)
Python + Networking + Linux
Python
Q1. What is the difference between a list and a tuple in Python?
Answer

Both store ordered collections of data, but there are key differences.

List	Tuple
Mutable	Immutable
Uses []	Uses ()
Slower	Faster
More memory	Less memory

Example

my_list = [1,2,3]
my_list.append(4)

my_tuple = (1,2,3)
# my_tuple.append(4) ❌

Use a tuple when data should never change, such as an IOC represented as (IP, Timestamp).

Follow-up

Why are tuples faster?

Because Python doesn't need to allocate extra memory for modifications.

Q2. Explain *args and **kwargs.
Answer

*args

Allows multiple positional arguments.

def add(*args):
    return sum(args)

add(2,3,5)

**kwargs

Allows multiple keyword arguments.

def user(**kwargs):
    print(kwargs)

user(name="Brijesh", role="SOC")

Useful in Flask APIs where parameters vary.

Q3. What are decorators?
Answer

Decorators modify the behavior of a function without changing its code.

Example

def logger(func):

    def wrapper():
        print("Started")
        func()
        print("Finished")

    return wrapper


@logger
def hello():
    print("Hello")

Output

Started
Hello
Finished

Security tools often use decorators for authentication or logging.

Q4. Difference between deep copy and shallow copy.
Answer

Shallow copy copies references.

Deep copy copies actual objects.

import copy

a=[[1,2],[3,4]]

b=copy.copy(a)

c=copy.deepcopy(a)

If nested objects change,

copy.copy()

may also change.

Deep copy avoids this.

Q5. What are generators?
Answer

Generators produce values one at a time using yield.

def nums():
    for i in range(5):
        yield i

Advantages

Less memory
Faster for large datasets
Ideal for log processing
Q6. What is the difference between Flask and Streamlit?
Answer

Flask

Backend framework
REST APIs
Routing
Authentication

Streamlit

Data dashboards
Visualization
Rapid prototyping

In your Threat Intelligence Platform

Flask handled APIs.
Streamlit displayed enriched IOC dashboards.
Q7. Explain exception handling.
Answer
try:
    x=10/0

except ZeroDivisionError:
    print("Cannot divide")

finally:
    print("Done")

finally always executes.

Security tools use exception handling when API requests fail.

Q8. Difference between multithreading and multiprocessing.
Answer

Multithreading

Shared memory
Lightweight
Best for I/O

Multiprocessing

Separate memory
CPU intensive

Since Nmap spends most of its time waiting for network responses, multithreading is a suitable choice for scanning many hosts concurrently.

Networking
Q9. Explain the OSI Model.
Answer
Layer	Function
Application	HTTP DNS SMTP
Presentation	Encryption
Session	Session control
Transport	TCP UDP
Network	IP Routing
Data Link	MAC
Physical	Cable

Interviewers usually ask:

"Which layer does HTTPS work on?"

Application layer.

TLS encryption operates between Application and Transport.

Q10. TCP vs UDP.
Answer

TCP

Reliable
Connection-oriented
Ordered delivery

UDP

Fast
No acknowledgements
Connectionless

Examples

TCP

HTTPS
SSH
FTP

UDP

DNS
VoIP
Streaming
Q11. Three-way handshake.
Answer

TCP establishes a connection using:

Client

SYN

Server

SYN ACK

Client

ACK

Connection established.

Q12. What happens when you type google.com?
Answer
Browser checks cache.
DNS lookup resolves the IP address.
TCP three-way handshake.
TLS handshake for HTTPS.
HTTP request sent.
Server responds.
Browser renders the page.

This is a very common interview question.

Q13. What is DNS?
Answer

DNS converts domain names into IP addresses.

Example

google.com

↓

142.x.x.x

Without DNS, users would have to remember IP addresses.

Q14. Explain HTTP methods.
Answer

GET

Retrieve data.

POST

Create data.

PUT

Replace data.

PATCH

Modify data.

DELETE

Delete resource.

Your Flask APIs likely used GET for IOC retrieval and POST for submitting indicators.

Q15. Difference between HTTP and HTTPS.
Answer

HTTP

Port 80
Plaintext
Not encrypted

HTTPS

Port 443
Uses TLS
Secure communication
Q16. What is ARP?
Answer

ARP maps an IP address to a MAC address within a local network.

Example

192.168.1.10

↓

00:1A:2B:3C:4D:5E

Attack

ARP Spoofing

Defense

Dynamic ARP Inspection.

Q17. What is NAT?
Answer

Network Address Translation translates private IP addresses into public IP addresses.

Benefits

Conserves IPv4 addresses
Hides internal devices
Linux
Q18. Difference between grep, awk, and sed.
Answer

grep

Searches text.

grep error logs.txt

awk

Processes columns.

awk '{print $1}'

sed

Edits text.

sed 's/http/https/'
Q19. Explain Linux permissions.
Answer
-rwxr-xr--

Owner

rwx

Group

r-x

Others

r--

Permission values

r=4

w=2

x=1

755 means

Owner

7

Group

5

Others

5
Q20. chmod vs chown.
Answer

chmod

Changes permissions.

chmod 755 file

chown

Changes ownership.

chown user file
Q21. How do you find large files in Linux?
Answer
find / -type f -size +100M

Useful for log analysis and storage management.

Q22. What is a process?
Answer

A process is a running instance of a program.

Useful commands

ps

top

htop

kill
Q23. Difference between soft link and hard link.
Answer

Soft Link

Shortcut
Can cross filesystems
Breaks if original is deleted

Hard Link

Same inode
Cannot cross filesystems
Continues to work if original filename is deleted (as long as another hard link exists)
Q24. What is the purpose of the /etc/passwd file?
Answer

It stores user account information such as username, UID, GID, home directory, and login shell.

Example entry:

brijesh:x:1001:1001:Brijesh:/home/brijesh:/bin/bash

Passwords are not stored here on modern Linux systems; they are stored in /etc/shadow, which has restricted permissions.

Q25. What is SSH and why is it secure?
Answer

SSH (Secure Shell) is a protocol for securely accessing remote systems over an encrypted connection, typically using port 22.

Security features:

Encrypts all communication.
Supports password and public key authentication.
Protects against eavesdropping and many man-in-the-middle attacks when host keys are verified.

Example:

ssh user@192.168.1.10
Follow-up

Why is SSH preferred over Telnet?

Because Telnet transmits data, including passwords, in plaintext, while SSH encrypts the entire session.



Threat Intelligence
Q26. What is Threat Intelligence?
Answer

Threat Intelligence (TI) is the process of collecting, analyzing, and sharing information about cyber threats to help organizations detect, prevent, and respond to attacks proactively.

Threat intelligence answers questions such as:

Who is attacking?
What tools and techniques are being used?
Which systems are being targeted?
How can we defend against these attacks?
Types of Threat Intelligence
Type	Description	Example
Strategic	High-level trends	Increase in ransomware attacks targeting healthcare
Tactical	Attacker TTPs	Use of PowerShell for lateral movement
Operational	Information about ongoing campaigns	Current phishing campaign impersonating Microsoft
Technical	Indicators of Compromise (IOCs)	Malicious IPs, domains, file hashes

Interview Tip: Mention all four types to demonstrate a solid understanding.

Q27. What are Indicators of Compromise (IOCs)?
Answer

IOCs are pieces of evidence that suggest a system may have been compromised.

Examples include:

Malicious IP addresses
Malicious domains
URLs
File hashes (MD5, SHA-1, SHA-256)
Registry keys
Mutex names
Email addresses
Process names

Example:

IP:
185.220.101.15

Domain:
fake-login-paypal.com

SHA256:
4f5b8d3...

In your Threat Intelligence Platform, IOCs were enriched using AbuseIPDB, AlienVault OTX, WHOIS, and GeoIP.

Follow-up

Are IOCs enough to detect attacks?

No. Attackers can frequently change IOCs. Modern SOCs also rely on behavioral detection using TTPs.

Q28. What is the difference between IOC, IOA, and TTP?
Answer
IOC	IOA	TTP
Evidence after compromise	Suspicious activity	Attacker behavior
Static	Behavioral	Long-term techniques
IP, Domain	PowerShell downloading malware	Credential Dumping

Example:

IOC:

185.100.50.25

IOA:

PowerShell downloads payload from Internet

TTP:

MITRE T1059
Command and Scripting Interpreter

Interviewers like this question because it shows whether you understand modern detection methods.

Q29. What is Threat Intelligence Enrichment?
Answer

Enrichment is the process of adding contextual information to raw IOCs.

For example:

Original IOC:

8.8.8.8

Enriched Data:

Country
ASN
ISP
Abuse score
WHOIS data
VirusTotal detections
MITRE ATT&CK mapping

Enrichment helps analysts prioritize investigations.

Q30. Explain the Threat Intelligence Lifecycle.
Answer

The lifecycle consists of six stages:

Planning
Collection
Processing
Analysis
Dissemination
Feedback

Example:

Collect IPs from AbuseIPDB → Normalize into STIX → Analyze → Share with SOC → Receive feedback and improve.

STIX 2.1
Q31. What is STIX 2.1?
Answer

STIX (Structured Threat Information eXpression) is a standardized language for representing cyber threat intelligence.

Benefits:

Standardized data sharing
Machine-readable
Vendor-independent
Supports automation

Your platform used STIX 2.1 to normalize IOC data from multiple sources.

Q32. Why is STIX important?
Answer

Without STIX:

Vendor A

IP: 1.1.1.1

Vendor B

Malicious IP=1.1.1.1

Different formats.

With STIX:

All threat intelligence follows a common schema, making integration and automation easier.

Q33. What are some common STIX Objects?
Answer

Common STIX Domain Objects (SDOs):

Indicator
Malware
Attack Pattern
Threat Actor
Campaign
Tool
Vulnerability
Identity
Relationship
Observed Data

Example:

Indicator

↓

Relationship

↓

Malware

↓

Threat Actor
Q34. Difference between STIX and TAXII.
Answer
STIX	TAXII
Data format	Transport protocol
JSON based	HTTPS API
Defines objects	Shares objects

Think of it like:

STIX = PDF document

TAXII = Email used to send the PDF

MITRE ATT&CK
Q35. What is the MITRE ATT&CK Framework?
Answer

MITRE ATT&CK is a knowledge base that documents attacker behaviors observed in real-world attacks.

It helps defenders:

Detect attacks
Build detection rules
Perform threat hunting
Map alerts to attacker techniques
Q36. What are Tactics and Techniques?
Answer

Tactic = Why the attacker performs an action.

Technique = How the attacker performs it.

Example:

Tactic

Credential Access

↓

Technique

OS Credential Dumping
(T1003)
Q37. Explain one MITRE technique.
Answer

Technique:

T1059

Command and Scripting Interpreter

Attackers execute commands using:

PowerShell
Bash
CMD
Python

Detection:

Monitor unusual PowerShell execution
Detect encoded commands
Alert on suspicious parent-child processes
Q38. Why should SOC analysts map alerts to MITRE ATT&CK?
Answer

Benefits:

Understand attacker objectives
Improve detection coverage
Build threat-hunting queries
Identify gaps in monitoring
Standardize reporting across tools
OSINT
Q39. What is OSINT?
Answer

OSINT (Open Source Intelligence) is the collection and analysis of publicly available information.

Sources include:

WHOIS
Shodan
DNS records
GitHub
LinkedIn
Social media
Public repositories
Certificate Transparency logs

OSINT is commonly used during investigations to gather context about domains, IPs, or organizations.

Q40. What information can WHOIS provide?
Answer

WHOIS provides registration details for domains.

Typical information:

Registrar
Registration date
Expiration date
Name servers
Registrant (if not privacy-protected)

This information can help identify recently registered domains that may be suspicious.

SOC & SIEM
Q41. What is a SIEM?
Answer

SIEM (Security Information and Event Management) collects, stores, correlates, and analyzes logs from multiple systems.

Typical log sources:

Firewalls
Servers
Active Directory
Endpoint protection
Network devices
Cloud services

Common SIEM platforms:

Splunk
Microsoft Sentinel
IBM QRadar
Elastic Security
Q42. Difference between SIEM and SOAR.
Answer
SIEM	SOAR
Collects and analyzes logs	Automates response actions
Generates alerts	Executes playbooks
Detects incidents	Responds to incidents

Example:

SIEM detects repeated failed logins.
SOAR automatically disables the affected account and notifies the SOC.
Q43. What is Log Correlation?
Answer

Log correlation is the process of combining events from multiple sources to identify suspicious activity.

Example:

Firewall
↓

VPN Login

↓

Windows Event Logs

↓

EDR Alert

Viewed individually, each event may appear normal. Together, they may indicate a compromised account.

Q44. Explain the SOC Alert Triage Process.
Answer

A SOC analyst typically follows these steps:

Receive the alert.
Validate whether it is a true or false positive.
Gather additional context (user, host, IP, process, logs).
Determine severity and impact.
Contain the threat if required.
Escalate or close the incident.
Document findings.

Documentation is essential because it supports future investigations and audits.

Q45. What is a False Positive?
Answer

A false positive occurs when a security tool reports malicious activity that is actually legitimate.

Example:

An administrator runs PowerShell for maintenance, but the SIEM flags it as suspicious.

Reducing false positives improves analyst efficiency and helps prevent alert fatigue.

Incident Response
Q46. What are the phases of Incident Response?
Answer

The standard incident response lifecycle includes:

Preparation
Identification
Containment
Eradication
Recovery
Lessons Learned

Interviewers often expect you to know these phases in order.

Q47. What would you do if an employee reports a phishing email?
Answer

A structured response would be:

Ask the employee not to interact with the email.
Analyze the email headers and attachments.
Review embedded URLs in a safe environment.
Search for similar emails across the organization.
Block malicious domains or sender addresses if confirmed.
Remove the email from affected mailboxes if possible.
Document the investigation and update detection rules if necessary.
Q48. What should you check when investigating a suspicious IP address?
Answer

Useful checks include:

Abuse reputation (e.g., AbuseIPDB)
GeoIP location
ASN and ISP
WHOIS information
Threat intelligence feeds
Historical communication with internal systems
Firewall and proxy logs
Related DNS activity

This is similar to the enrichment workflow you implemented in your project.

Q49. What is the difference between a vulnerability, an exploit, and a threat?
Answer
Term	Meaning
Vulnerability	A weakness in a system
Exploit	Code or technique that takes advantage of a vulnerability
Threat	Anything capable of exploiting a vulnerability and causing harm

Example:

Vulnerability: Unpatched web server.
Exploit: Public exploit targeting that server.
Threat: An attacker using the exploit.
Q50. Suppose your SIEM reports 500 failed login attempts followed by a successful login from the same IP. How would you investigate?
Answer

A methodical investigation could include:

Determine which account was affected.
Check whether the source IP is known or has a poor reputation.
Review the login timeline and authentication logs.
Identify whether MFA was used or bypassed.
Look for additional activity after the successful login (new processes, privilege escalation, unusual file access).
Search for similar attempts against other accounts.
If compromise is suspected:
Disable or lock the account.
Reset credentials.
Isolate affected systems if necessary.
Notify the incident response team.
Document the investigation and recommend preventive measures, such as rate limiting, MFA enforcement, or improved detection rules.

Why this is a strong answer: It demonstrates structured thinking, log analysis skills, and an understanding of containment and recovery rather than focusing only on the failed logins.