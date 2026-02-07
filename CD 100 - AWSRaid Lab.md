Source: `CyberDefender`
Category: `Cloud Forensics (AWS)`
Challenge: `Splunk`
Focus Area: `Persistence`, `Privilege Escalation`, `Credential Access`
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
*Looking for brute force attempt by seeing if any attempts made within 1 minute window that resulted in failure*

**ANSWER**
**`helpdesk.luke`**
### Question 2
We must investigate the events following the initial compromise to understand the attacker's motives. What is the timestamp for the first access to an S3 object by the attacker?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="GetObject"
| stats count by _time
```

**ANSWER**
**`2023-11-02 09:55`**

### Question 3
Among the S3 buckets accessed by the attacker, one contains a DWG file. What is the name of this bucket?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
*.dwg
```

**ANSWER**
**`product-designs-repository31183937`**

### Question 4
We've identified changes to a bucket's configuration that allowed public access, a significant security concern. What is the name of this particular S3 bucket?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="PutBucketPublicAccessBlock"
```

**ANSWER**
**`backup-and-restore98825501`**

### Question 5
Creating a new user account is a common tactic attackers use to establish persistence in a compromised environment. What is the username of the account created by the attacker?

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="CreateUser"
```

**ANSWER**
**`marketing.mark`**

### Question 6
Following account creation, the attacker added the account to a specific group. What is the name of the group to which the account was added? 

```SQL
index="aws_cloudtrail" 
userIdentity.userName="helpdesk.luke"
eventName="AddUserToGroup"
```

**ANSWER**
**`Admins`**