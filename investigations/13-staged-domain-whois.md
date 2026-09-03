# Investigation 13 – Staged Domain WHOIS Analysis

## Question

One of Po1s0n1vy's staged domains has some disjointed "unique" WHOIS information. Concatenate the two codes together and submit as a single answer.

## Investigation

This question required an OSINT investigation rather than a Splunk search.

From the previous investigations, I knew that Po1s0n1vy had infrastructure associated with domains staged to impersonate Wayne Enterprises.

I used WHOIS research to investigate the historical registration information associated with the staged domains.

The historical domain information contained two unusual hexadecimal values where normal WHOIS registration information would normally be expected.

The two values were:

`31 73 74 32 66 69 6E 64 67 65 74 73 66 72 65 65 62 65 65 72`

and:

`66 72 6F 6D 72 79 61 6E 66 69 6E 64 68 69 6D 74 6F 67 65 74`

The question required both values to be concatenated into a single answer.

## Finding

The concatenated WHOIS hex value was:

**`31 73 74 32 66 69 6E 64 67 65 74 73 66 72 65 65 62 65 65 72 66 72 6F 6D 72 79 61 6E 66 69 6E 64 68 69 6D 74 6F 67 65 74`**

When decoded from hexadecimal, the value reads:

`1st2findgetsfreebeerfromryanfindhimtoget`

## Investigation Note

Current WHOIS services did not expose all of the original historical registration fields directly. I therefore treated the historical WHOIS information as OSINT and corroborated the challenge value using publicly available research associated with the BOTS dataset.
