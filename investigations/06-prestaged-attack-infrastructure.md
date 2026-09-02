# Investigation 06 – Pre-Staged Attack Infrastructure

## Question

What IP address has Po1s0n1vy tied to domains that are pre-staged to attack Wayne Enterprises?

## Investigation

After identifying `prankglassinebracket.jumpingcrab.com` during the DNS investigation, I pivoted from the indicators found in Splunk into open-source threat intelligence.

The purpose of this step was to investigate infrastructure associated with Po1s0n1vy and determine whether domains connected to the group shared common infrastructure.

The OSINT investigation linked the pre-staged domains back to the same IP address already observed during the attack:

`23.22.63.114`

This provided additional context around the infrastructure being used by Po1s0n1vy.

## Finding

**IP Address:** `23.22.63.114`

## Investigation Method

**Splunk IOC → Domain/IP pivot → OSINT infrastructure correlation**

## SOC Takeaway

SIEM investigations do not always contain every piece of information needed to understand an attack. After identifying an IOC internally, a SOC analyst can pivot into threat intelligence and OSINT sources to investigate related domains, IP addresses, and attacker infrastructure.
