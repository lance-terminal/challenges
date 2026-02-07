# 04.Splunk AWSRaid Lab

| Field | Detail |
|-------|--------|
| **Issue** | [#4 - 04.Splunk AWSRaid Lab](https://github.com/lance-terminal/challenges/issues/4) |
| **Author** | @lance-terminal |
| **Labels** | CyberDefender |
| **Created** | 2026-02-07T21:01:27Z |
| **Closed** | 2026-02-07T22:44:45Z |

---

# [AWSRaid Lab](https://cyberdefenders.org/blueteam-ctf-challenges/awsraid/)
Investigate `AWS CloudTrail` logs using `Splunk` to identify unauthorized access, analyze configuration changes, and detect persistence mechanisms.

### Scenario
Your organization utilizes AWS to host critical data and applications. An incident has been reported that involves unauthorized access to data and potential exfiltration. The security team has detected unusual activities and needs to investigate the incident to determine the scope of the attack.



## Comments

---

**lance-terminal** — 2026-02-07T21:10:18Z

### Question 1
Knowing which user account was compromised is essential for understanding the attacker's initial entry point into the environment. What is the username of the compromised user?

```SQL
index="aws_cloudtrail"
eventSource="signin.amazonaws.com" -- find all events relating to signin
responseElements.ConsoleLogin="Failure" -- looking for failure messages
| bucket _time span=1m -- within 1 minute window
| stats count by _time, sourceIPAddress, userIdentity.userName -- username, IP
| where count > 1 -- more than 1 time
```
Looking for brute force attempt by seeing if any attempts made within 1 minute window that resulted in failure

**ANSWER**
`helpdesk.luke`

---

**lance-terminal** — 2026-02-07T21:11:10Z

### Question 2
We must investigate the events following the initial compromise to understand the attacker's motives. What is the timestamp for the first access to an S3 object by the attacker?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="GetObject"
| stats count by _time
```

**ANSWER**
`2023-11-02 09:55`



---

**lance-terminal** — 2026-02-07T21:12:11Z

### Question 3
Among the S3 buckets accessed by the attacker, one contains a DWG file. What is the name of this bucket?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
*.dwg
```
*Looking for extension `.dwg`

**ANSWER**
`product-designs-repository31183937`

---

**lance-terminal** — 2026-02-07T21:12:50Z

### Question 4
We've identified changes to a bucket's configuration that allowed public access, a significant security concern. What is the name of this particular S3 bucket?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="PutBucketPublicAccessBlock"
```

**ANSWER**
`backup-and-restore98825501`

---

**lance-terminal** — 2026-02-07T21:13:14Z

### Question 5
Creating a new user account is a common tactic attackers use to establish persistence in a compromised environment. What is the username of the account created by the attacker?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="CreateUser"
```

**ANSWER**
`marketing.mark`

---

**lance-terminal** — 2026-02-07T21:13:28Z

### Question 6
Following account creation, the attacker added the account to a specific group. What is the name of the group to which the account was added? 

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="AddUserToGroup"
```

**ANSWER**
`Admins`
