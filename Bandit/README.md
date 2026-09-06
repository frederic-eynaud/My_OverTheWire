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
