# Splunk Basics - Did you SIEM?

## What is the attacker IP found attacking and compromising the web server?
```
index=main sourcetype=web_traffic user_agent!=*Mozilla* user_agent!=*Chrome* user_agent!=*Safari* user_agent!=*Firefox*
```
clicked on client ips and the one on the top with most requests was the compromised server
```
198.51.100.55
```
## Which day was the peak traffic in the logs? (Format: YYYY-MM-DD)
in the graph above its clearly 12th oct 2025
```
2025-10-12
```
## What is the count of Havij user_agent events found in the logs?
clicked on user_agents on the left panel and there it was
``
993
``
## How many path traversal attempts to access sensitive files on the server were observed?
clicked on paths and the one where it was trying to pull passwords was the one
```
658
```
## Examine the firewall logs. How many bytes were transferred to the C2 server IP from the compromised web server?
```
sourcetype=firewall_logs action="ALLOWED" | stats sum(bytes_transferred) by src_ip
```
and there it was
``
126167
``
