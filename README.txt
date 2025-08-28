# Laboratory: Brute Force Attack

Welcome to the **Brute Force Attack** lab. In this exercise, you will learn how to identify and analyze events related to brute force attacks on Windows systems by examining event files. This lab is designed to strengthen your skills in incident detection and response within the cybersecurity field.

---

## Lab Contents

The ZIP archive includes the following files:

| Name                        | Size        | Date & Time           |
|-----------------------------|-------------|-----------------------|
| Bruteforce_Challenge.csv    | 6,032,687   | 2022-02-12 19:31      |
| Bruteforce_Challenge.evtx   | 69,632      | 2022-02-12 19:29      |
| Bruteforce_Challenge.txt    | 6,032,687   | 2022-02-12 19:31      |
| README.txt                  | 360         | 2022-02-12 19:35      |

---

## Objectives

- Identify authentication failure events on Windows systems.
- Recognize brute force attack patterns.
- Determine the target account, origin, and method of the attack.
- Use basic forensic analysis tools and Linux commands.

---

## Instructions

1. Download and extract the provided ZIP file.
2. Use the following commands in a Linux terminal to analyze the files.
3. Answer the analysis questions at the end of the exercise.

---

## Useful Commands

### 1. Determine the file type
```bash
file Bruteforce_Challenge.txt
```

### 2. Count authentication failure events
```bash
grep -i 'Audit Failure' Bruteforce_Challenge.txt | wc -l
```

### 3. Find the target account name
```bash
grep -i 'Account Name:' Bruteforce_Challenge.txt | sort | uniq
```

### 4. Identify the Windows Event ID for authentication failures
Search for "Event ID" and check the associated number:
```bash
grep -i 'Event ID' Bruteforce_Challenge.txt | sort | uniq
```

### 5. Extract the attacker's source IP address
```bash
grep -i 'Source Network Address' Bruteforce_Challenge.txt | sort | uniq
```

### 6. Check the country of the source IP address
Use an online tool such as [ipgeolocation.io](https://ipgeolocation.io/) to look up the IP.

### 7. Determine the range of source ports used by the attacker
```bash
grep -i "Source port" Bruteforce_Challenge.txt | awk '{print $NF}' | sort -n | uniq
```

---

## Analysis Questions

1. **How many Audit Failure events are logged?**  
   _Suggested command:_  
   `grep -i 'Audit Failure' Bruteforce_Challenge.txt | wc -l`

2. **What is the username of the target local account?**  
   _Suggested command:_  
   `grep -i 'Account Name:' Bruteforce_Challenge.txt | sort | uniq`

3. **What is the Windows Event ID associated with authentication failures?**  
   _Suggested command:_  
   `grep -i 'Event ID' Bruteforce_Challenge.txt | sort | uniq`

4. **What is the attacker's source IP address?**  
   _Suggested command:_  
   `grep -i 'Source Network Address' Bruteforce_Challenge.txt | sort | uniq`

5. **From which country does the identified IP originate?**  
   _Recommended lookup:_  
   [ipgeolocation.io](https://ipgeolocation.io/)

6. **What is the range of source ports used by the attacker?**  
   _Suggested command:_  
   `grep -i "Source port" Bruteforce_Challenge.txt | awk '{print $NF}' | sort -n | uniq`

---

## Recommended Resources

- [Event ID 4625 - Windows Security Log](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4625)
- [Linux grep manual](https://man7.org/linux/man-pages/man1/grep.1.html)
- [EVTX File Forensics](https://www.sentinelone.com/blog/evtx-files-windows-event-logs-forensics/)

---

## Credits

Lab developed by **Retr0duck**.  
Original repository: [cybersecurity-labs](https://github.com/Retr0duck/cybersecurity-labs)

---

## License

This laboratory is for educational use. See the LICENSE file for more details.