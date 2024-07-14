
---
Enum4linux is a command-line tool designed for enumerating information from Windows systems in network security assessments. It specializes in extracting details such as user accounts, group memberships, shares, policies, and system configuration from Windows domains. By leveraging [[SMB]] (Server Message Block) protocol interactions, Enum4linux can retrieve user names, their associated security identifiers (SIDs), group memberships, enumerate available shares with their permissions, and fetch details about password policies and other system-level configurations. This information is crucial for assessing the security posture of Windows networks, aiding penetration testers and security professionals in identifying potential vulnerabilities and strengthening network defenses accordingly.

The command to use this tools is the following

```
enum4linux -a 127.0.0.1
```

We are going to discover all the information about [[SMB]]