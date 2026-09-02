# Investigation 07 – Po1s0n1vy Associated Email

## Question

Based on the data gathered from this attack and common open-source intelligence sources for domain names, what email address is most likely associated with the Po1s0n1vy APT group?

## Investigation

After identifying infrastructure associated with Po1s0n1vy, I continued the investigation using open-source intelligence rather than relying only on the Splunk dataset.

I used the domains and IP address discovered during the earlier investigations as pivot points and reviewed historical domain-registration information associated with the infrastructure.

The historical registration information identified the following email address:

`lillian.rose@po1s0n1vy.com`

Because this information came from external domain intelligence rather than the internal Splunk logs, I treated it as OSINT enrichment of the indicators already discovered during the investigation.

## Finding

**Associated Email:** `lillian.rose@po1s0n1vy.com`

## Investigation Method

**Splunk IOC → Infrastructure pivot → Domain OSINT → Historical registration information**

## SOC Takeaway

Threat intelligence enrichment can provide context that is not available in SIEM telemetry alone. Pivoting from known domains and IP addresses into historical registration data can reveal additional infrastructure and identifiers that may be associated with a threat actor.
