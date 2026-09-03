# Splunk BOTS v1 SOC Investigation

## About This Project

I worked through the Splunk Boss of the SOC (BOTS) v1 dataset to get more hands-on practice investigating security incidents in Splunk.

The investigation follows a simulated attack against Wayne Enterprises. I started with the initial web activity and worked through different parts of the attack, including reconnaissance, brute-force attempts, malware activity and eventually Cerber ransomware.

I documented each investigation separately so I could show the SPL searches I used, what I found in the logs and how I reached each answer.

## How I Investigated It

I didn't rely on one log source throughout the investigation.

Depending on what I was looking for, I had to move between different logs and use previous findings to decide where to look next.

Some of the data sources I worked with included:

- Sysmon
- Windows Security logs
- Suricata
- SMB traffic
- Windows Registry
- FortiGate UTM logs

I mainly used Splunk and SPL for the investigation, but I also used tools such as VirusTotal, CyberChef and OSINT when the logs alone weren't enough.

One thing I ran into while working with the dataset was that some Sysmon fields were not automatically extracted in my Splunk environment. For those events, I had to work with the raw XML and use `rex` to extract fields such as `CommandLine`, `ParentProcessId` and `TargetFilename`.

That made the investigation more useful because I wasn't always working with perfectly prepared data.

## Investigations

I completed 30 investigations covering different stages of the attack.

### Web Attack & Attacker Infrastructure

1. [Web Vulnerability Scanning](investigations/01-web-vulnerability-scanning.md)
2. [Vulnerability Scanner Identification](investigations/02-vulnerability-scanner-identification.md)
3. [CMS Identification](investigations/03-cms-identification.md)
4. [Website Defacement](investigations/04-website-defacement-file.md)
5. [Dynamic DNS FQDN](investigations/05-dynamic-dns-fqdn.md)
6. [Pre-Staged Attack Infrastructure](investigations/06-prestaged-attack-infrastructure.md)
7. [Attacker Email Identification](investigations/07-po1s0n1vy-associated-email.md)

### Brute Force & Malware Activity

8. [Brute-Force Attack](investigations/08-brute-force-attack.md)
9. [Malicious Executable Upload](investigations/09-malicious-executable-upload.md)
10. [Executable MD5](investigations/10-executable-md5.md)
11. [Spear-Phishing Malware OSINT](investigations/11-spear-phishing-malware-osint.md)
12. [Malware Hex Code](investigations/12-malware-hex-code.md)
13. [Staged Domain WHOIS Investigation](investigations/13-staged-domain-whois.md)
14. [First Brute-Force Password](investigations/14-first-brute-force-password.md)
15. [Coldplay Password](investigations/15-coldplay-brute-force-password.md)
16. [Correct Administrator Password](investigations/16-correct-admin-password.md)
17. [Average Password Length](investigations/17-average-password-length.md)
18. [Unique Passwords Attempted](investigations/18-unique-passwords-attempted.md)

### Endpoint & Cerber Ransomware

19. [Compromised Workstation IP](investigations/19-we8105desk-ip-address.md)
20. [Cerber Suricata Signature](investigations/20-cerber-suricata-signature.md)
21. [Cerber Ransomware FQDN](investigations/21-cerber-ransomware-fqdn.md)
22. [First Suspicious Domain](investigations/22-first-suspicious-domain.md)
23. [VBScript Command Length](investigations/23-vbscript-command-length.md)
24. [USB Device Identification](investigations/24-usb-device-identification.md)
25. [File Server IP Address](investigations/25-file-server-ip-address.md)
26. [PDF Files Encrypted](investigations/26-distinct-pdf-files-encrypted.md)
27. [Malware Parent Process ID](investigations/27-121214-parent-process-id.md)
28. [TXT Files Encrypted](investigations/28-cerber-txt-files-encrypted.md)
29. [Cerber Encryptor File](investigations/29-cerber-encryptor-file.md)
30. [Cerber Steganography](investigations/30-cerber-steganography.md)

## What I Learned

The biggest thing I took from this project was that an investigation isn't usually solved with one search.

A lot of the questions required me to find one piece of information first and then use that as a pivot into another log source.

For example, I moved between network traffic, Windows events, Sysmon process activity, Registry data and SMB activity while following the Cerber infection.

I also got more comfortable using SPL commands such as:

- `search`
- `where`
- `stats`
- `dc()`
- `rex`
- `eval`
- `table`
- `sort`
- `dedup`

The final Cerber investigation was also a good example of knowing when Splunk isn't enough. After identifying `mhtr.jpg` in the network logs, I had to use OSINT to understand why a JPEG was being used during the infection. That research showed that Cerber was hiding malicious content inside the image using steganography.

Overall, this project helped me get more comfortable following evidence across different security logs instead of treating every alert or question as a separate investigation.

## Repository Structure

```text
Splunk-BOTS-v1-SOC-Investigation/
├── investigations/     # Investigation notes and SPL queries
├── screenshots/        # Evidence from Splunk and OSINT
├── LICENSE
└── README.md
```

## Dataset

This project uses the Splunk Boss of the SOC (BOTS) v1 dataset.

The dataset is a simulated security environment created for blue-team investigation and Splunk practice.
