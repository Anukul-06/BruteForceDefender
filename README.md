# BruteForceDefender
A brute force attack is a method used by cyber attackers to gain unauthorized access to a system, network, or account by systematically attempting all possible combinations of passwords or encryption keys until the correct one is found.

# Getting Started
BruteForceDefender is a method or process for blocking the IP addresses of attackers who are continuously attempting to log in to the organization's portal.

# Tools required
  Hydra
  Wireshark
  iptables
  metasploit

# Hydra
  Hydra is a popular open-source tool used for performing brute force attacks on various protocols and services. It allows attackers to systematically try a large number of username and password combinations to 
  gain unauthorized access to a system. Hydra supports many different protocols, including HTTP, HTTPS, FTP, SMTP, and more, making it a versatile tool for penetration testers and malicious actors alike. Its 
  primary use is to test the strength of passwords and the security of login mechanisms in a controlled environment.

# Wireshark
  Wireshark is a widely-used open-source network protocol analyzer. It allows users to capture and interactively browse the traffic running on a computer network. Wireshark provides detailed information about the 
  data packets transmitted over the network, which can be used for network troubleshooting, analysis, software and protocol development, and education.

# iptables
  iptables is a command-line utility used to set up, maintain, and inspect the tables of IP packet filter rules in the Linux kernel. It is a vital tool for system administrators to manage network traffic and 
  enforce security policies on a Linux-based system.

# metasploit
  Metasploit is a comprehensive open-source framework used for penetration testing, security research, and vulnerability assessment. It provides security professionals and ethical hackers with the tools needed to   identify, exploit, and validate vulnerabilities in systems. Metasploit is highly extensible and supports a wide range of exploits, payloads, encoders, and auxiliary modules.

# Executing commands
  Firstly, we will create a .txt file for usernames as username.txt and passwords as 
  password.txt wordlists to perform a brute force attack. This can be done with the help of 
  hydra tool.
  You can use following command to perform a brute force attack on a login page
  
  ```sh
  $ hydra -L usernames.txt -P passwords.txt ssh://target_ip
  ```
  or
  ```sh
  $ hydra <ip> http-form-post "/dvwa/login.php: username-^USER&password-^PASS^&Login-submit:Login failed" -L username.txt -P pssword.txt
  ```

  **After the brute force attack is done**
  
  Now open Wireshark to capture and analyze the traffic on the login page.

  You will see a significant amount of traffic coming from a single network, indicating that someone is using this IP address to perform a brute force attack on our website.

  In the next part we will be using iptable rules to filter some of firewall rules  to block 
  the ip address of the attacker.

  To block the attacker ip address we can use the following command

  ```sh
  $ iptables -A INPUT -s <attacker ip> -j DROP
  ```

  Simillarly to unblock the ip address we can use the following command

  ```sh
  $ iptables -A INPUT -s <attacker ip> -j DROP
  ```

**Since this is used for testing purpose you can you the metasploit framework**

This is how we can detect and block the IP address of an attacker attempting to gain admin access through a brute force attack
  
