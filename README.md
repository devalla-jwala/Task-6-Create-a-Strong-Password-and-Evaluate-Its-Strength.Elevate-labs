# Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs
Password strength, brute force attack, dictionary attack, authentication,  best practices.

##  Objective
Understand how password strength works, test passwords on strength checkers, and learn how to protect against brute force and dictionary attacks using Kali Linux.

---

##  Tools Used

| Tool                  | Type | Use                                 |
|-----------------------|------|--------------------------------------|
| Firefox (Pre-installed) | GUI  | Open password checker websites       |
| `cracklib-check`     | CLI  | Offline password strength check     |
| `pwscore`            | CLI  | Check password score out of 100     |
| `wordlists`          | Info | View common password files used in attacks |

---

##  Step-by-Step Instructions

###  Step 1: Open a Browser on Kali Linux

Open Firefox browser:

```bash
firefox https://www.passwordmeter.com &
```

Use this site to check password strength.

---

###  Step 2: Create Sample Passwords

Create 5 passwords of different strengths:

```bash
echo "password123" > passlist.txt
echo "Password123" >> passlist.txt
echo "P@ssw0rd123" >> passlist.txt
echo "Pa$$w0rd!2025" >> passlist.txt
echo "3xT#R%9^uLp@1Z" >> passlist.txt
```

![image alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/1.png)

---

###  Step 3: Install CLI Password Strength Tools

#### ✅ Option 1 – `cracklib-check`

```bash
sudo apt update
sudo apt install cracklib-runtime
cat passlist.txt | cracklib-check
```
![imagge alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/2.png)


📌 **Output**:
```
password123: it is based on a dictionary word
Password123: it is based on a dictionary word
P@ssw0rd123: OK
Pa$$w0rd!2025: OK
3xT#R%9^uLp@1Z: OK
```
![image alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/3.png)

---

####  Option 2 – `pwscore`

```bash
sudo apt sudo apt install libpwquality-tools

echo "password123" | pwscore
```
![image alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/5.png)

Repeat for each password.

 ** Output**:
```
0
25
45
75
100
```
![iamge alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/6.png)

---

###  Step 4: Optional – Use Online Password Checkers

Use browser-based tools for visual feedback:

- 🔗 https://www.passwordmeter.com
- 🔗 https://www.security.org/how-secure-is-my-password/

Enter your passwords and note the strength scores, suggestions, and estimated crack time.

![image alt](https://github.com/devalla-jwala/Task-6-Create-a-Strong-Password-and-Evaluate-Its-Strength.Elevate-labs/blob/a1e79ede51b5dd189b4285a79536553a10095692/7.png)
---

###  Step 5: Analyze the Results

| Password            | cracklib | pwscore | Online Tool Feedback |
|---------------------|----------|---------|------------------------|
| password123         | Weak     | 0       | Too common             |
| Password123         | Weak     | 25      | Predictable            |
| P@ssw0rd123         | OK       | 45      | Medium strength        |
| Pa$$w0rd!2025       | OK       | 75      | Strong password        |
| 3xT#R%9^uLp@1Z      | OK       | 100     | Very strong, secure    |

---

###  Step 6: Understand Common Attacks

####  Brute Force Attack
- Tries every combination of characters until it guesses the password.
- Short/simple passwords like `123456` or `abc123` get cracked in seconds.

####  Dictionary Attack
- Uses prebuilt lists of common passwords.
- Example: `rockyou.txt` found on Kali Linux.

View some common passwords from dictionary:

```bash
zcat /usr/share/wordlists/rockyou.txt.gz | head -n 10
```

---

###  Step 7: Tips Learned 

- ✅ Use **at least 12 characters**
- ✅ Combine **uppercase, lowercase, numbers, and symbols**
- ❌ Avoid real words, names, and personal info
- ❌ Never reuse passwords across sites
- ✅ Consider using a **password manager** like `KeePassXC`

---


###  Tools Used
- `cracklib-check` (CLI)
- `pwscore` (CLI)
- `PasswordMeter.com` (Online)

###  Test Results

| Password            | cracklib | pwscore | Feedback              |
|---------------------|----------|---------|------------------------|
| password123         | Weak     | 0       | Too common             |
| Password123         | Weak     | 25      | Add symbols            |
| P@ssw0rd123         | OK       | 45      | Medium strength        |
| Pa$$w0rd!2025       | OK       | 75      | Strong password        |
| 3xT#R%9^uLp@1Z      | OK       | 100     | Very strong, secure    |

---

##  Attack Summary

- **Brute Force**: Cracks simple passwords quickly.
- **Dictionary**: Uses known common passwords. Avoid dictionary words like `letmein`, `qwerty`, `football`.

---

##  Conclusion

Strong passwords are your **first defense** in cybersecurity. Tools like `pwscore`, `cracklib-check`, and online strength meters help you build secure credentials. Remember: **longer = stronger**.
