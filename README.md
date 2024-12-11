# Web-Application-Security-with-WordPress
**Objective**
The goal of this project is to perform a security assessment of a vulnerable WordPress application by scanning it for vulnerabilities using WPScan and conducting a brute-force attack using the Rockyou wordlist. This exercise demonstrates my ability to identify common security flaws in WordPress and apply best practices for securing web applications.


**Methodology**
1. Setting Up the Vulnerable WordPress
Docker Setup:
To simulate a vulnerable WordPress environment, I set up a Docker container using the Dan Duran DVWP (Docker WordPress Vulnerable Project). This setup allows for testing in a controlled environment with common vulnerabilities.
Steps to Set Up:

_git clone https://github.com/dandurandvwp/dvwp.git_
_cd dvwp_

_docker-compose up -d --build_

![image](https://github.com/user-attachments/assets/0fd2bd39-d422-41c7-8630-1e3ef4d13f53)

After completing these steps, the WordPress application was accessible at http://localhost:31337.
![image](https://github.com/user-attachments/assets/f3221c9a-9e30-49ae-bb96-abfd4723245a)

3. Generating API Token for WPScan
To scan the WordPress application, I generated an API token from WPScan, a widely used tool for identifying vulnerabilities in WordPress websites. I registered for a WPScan account to retrieve the API token.

4. Scanning for Vulnerabilities
Using WPScan, I conducted a vulnerability scan on the WordPress application, focusing on enumerating users to identify potential usernames for brute-force attacks.
_wpscan --url http://localhost:31337 --api-token <your_api_token> --e u_

5. Brute-Force Login

I performed a brute-force attack against the WordPress login page using the Rockyou wordlist, a widely known password dictionary. This test evaluated the strength of the passwords used on the WordPress site.
Details:
Login Page URL: http://localhost:31337/wp-admin
Command: wpscan --url http://localhost:<port>/wp-admin --passwords /usr/wordlist/rockyou.txt --enumerate u

**Results**

1. Outdated Plugins/Themes

WPScan flagged outdated plugins and themes, which could expose the application to known exploits.

Fix: Regularly update WordPress plugins and themes via the WordPress dashboard or by using WP-CLI to apply the latest security patches.

2. Brute-Force Weak Passwords

Weak passwords, especially those from the Rockyou wordlist, were identified, making it possible for attackers to gain unauthorized access to user accounts.

Fix: Implement strong, unique passwords for all accounts and enable multi-factor authentication (MFA) for added security.

3. User Enumeration

WPScan was able to enumerate valid usernames, allowing attackers to perform targeted brute-force attacks.

Fix: Use security plugins or custom code to disable user enumeration or obfuscate usernames to make it more difficult for attackers to guess valid accounts.

**Recommended Fixes**

Regular Updates:
Ensure that WordPress, plugins, and themes are kept up to date with the latest security patches to prevent known exploits.

Use Strong Passwords & Enable MFA:
Enforce the use of strong, unique passwords for all user accounts, and enable multi-factor authentication (MFA) to prevent unauthorized access.

Disable User Enumeration:
Prevent user enumeration by using plugins that hide or obfuscate usernames, making it harder for attackers to identify valid accounts.

Firewall Protection:
Implement a Web Application Firewall (WAF) to block malicious requests and prevent brute-force attacks.

Limit Login Attempts:
Set up a limit on login attempts to block brute-force attacks after several failed login attempts, thereby protecting user accounts.

**Conclusion**

This project enabled me to identify and mitigate common vulnerabilities in WordPress applications. I gained hands-on experience with WPScan, performing vulnerability scanning, and applying brute-force password cracking techniques. Through this process, I also learned how to strengthen web application security by following best practices such as regular updates, strong password policies, and multi-factor authentication.



