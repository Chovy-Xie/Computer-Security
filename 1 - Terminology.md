# Terminology(术语)
> Key Aspects of CS: Confidentiality(), Integrity, Availability


## Vulnerabilities(漏洞) and Threats(威胁)

### Vulnerability
> A <b>vulnerability</b> is a weakness or flaw in a system, software, network, or process 
that could be exploited by an attacker to gain unauthorized access or cause damage.

 - Software Vulnerabilities (e.g., unpatched bugs, misconfigurations)
 - Hardware Vulnerabilities (e.g., firmware exploits, insecure loT devices)
 - Human Vulnerabilities (e.g., weak passwords, phishing susceptibility)

### Threat
> A <b>threat</b> is any potential danger that could exploit a vulnerability and 
cause harm to a system, data, or organization.

 - Cybercriminals (harkers, malicious insiders)
 - Malware (viruses, ransomware, spyware)
 - Natural Disasters (floods, fires affecting data centers)

### Key Difference: Vulnerability vs. Threat
 - A <b>vulnerability</b> is a weekness that could be exploited.
 - A <b>threat</b> is the entity or action that exploits a vulnerability to cause harm.


## Attackers: Means(能力), Opportunity(机会), and Motive(动机) (MOM)
> MOM model describes the three essential components an attacker must have to successfully carry out an attack.

### Means
> The skills, tools, and resources required to perform an attack.

 - Knowledge of hacking techniques
 - Malware(恶意软件), puhishing kits, exploit tools
 - Computing power for brute-force attacks

### Opportunity
> A chance to exploit a vulnerability in a system or network.

 - An unpatched software vulnerability
 - Weak passwords or lack of multi-factor authentication
 - A user clicking on a phishing link

### Motive
> The reason or intent behind the attack

 - Finance gain
 - Espionage 
 - Hacktivism
 - Intellectual challenge (some people see it as a game)
 - Revenge or personal vendettas

### Cybersecurity Implication

To prevent attacks, organizations must: 
 - Minimize opportunities (patch vulnerabilities, enforce strong security policies)
 - Reduce means (limit access to sensitive tools and information)
 - Understand motives (monitor threats and attacker behaviors)

No MOM = No Attack  -> If any of these three elements is missing, an attack is unlikely to occur.


## Model and Defense

### Model
> A concrete (usually abstracted) view of a system. 

To be useful, models must: 
 - Accurately reflect key features of real system
 - Be simple enough to understand and reason

### Defense (or control)
> A mechanism (tool, technology, or policy) put in place to reduce risk 

 - Remove a risk (remove or block a vulnerability)
 - Manage/mitigate risk (管控/缓解)
 - Transfer a risk (insurance, etc.)


## Computer Security - Goals
> The Big Three Goals of CS: CIA Triad

### Confidentiality(机密性)
> Avoiding unauthorized(未经授权) disclosure of information.

 - Ensures that only authorized individuals can access sensitive information.
 - Prevents unauthorized disclosure of data.
 - 保密. 避免未经授权<b>披露</b>信息

### Integrity(完整性)
> Avoiding unauthorized modification of information.

 - Ensures that data remains accurate, complete, and unaltered by unauthorized users.
 - Protects against modification, corruption, or destruction of data.
 - 完整. 避免未经授权<b>修改</b>信息

### Availability(可用性)
> Ensuring information or systems are available in a timely fashion to those authorized to access them.

 - Ensures that systems, networks, and data are accessible when needed.
 - Prevents disruptions caused by attacks, hardware failures, or software issues.
 - 可用. 确保信息或系统可及时提供给有权访问者

<ins>Caution:</ins> Availability is often misunderstood by students! 
Violations of availability are when an attacker makes systems/data unavailable to legitimate users. 
Not when an attacker gains availability to data they shouldn’t see (that’s a confidentiality violation).

### Why is the CIA Triad Important?

 - If <b>Confidentiality</b> is compromised -> Sensitive data is leaked.
 - If <b>Integrity</b> is compromised -> Data is tampered with or manipulated.
 - If <b>Availability</b> is compromised -> Users cannot access critical systems.

### Other goals that can be important in some situations

 - Non-repudiation(不可抵赖): Principals/subjects(委托人/主体) cannot deny actions later. 
 - Authentication(认证): Principals are who they claim to be.
 - Assurance(保证): How trust is provided or managed. 
 - Accountability(责任): or Accounting or Audit (会计或审计), Principals are responsible for actions. 