# Password Cracking with John the Ripper

## Introduction
This project demonstrates the process of extracting and cracking password-protected **RAR files** using **John the Ripper** in a **Kali Linux Virtual Machine**. The goal is to showcase **password recovery techniques** using wordlists and hash extraction utilities.

## Tools Used
- **Kali Linux** (Virtual Machine)
- **John the Ripper** (Password Cracking Tool)
- **RockYou.txt** (Common Password Wordlist)
- **rar2john** (Hash Extraction Utility)

## Methodology

### Step 1: Extracting Hash from FILE1.rar
The first step is extracting the password hash from the RAR archive using `rar2john`.

```bash
rar2john FILE1.rar > hash.txt
```

![image](https://github.com/user-attachments/assets/0bbc50e9-0c51-47e2-b934-d88448cc4d0c)



### Step 2: Cracking FILE1.rar Password
Using John the Ripper with the **rockyou.txt** wordlist to crack the password:

```bash
john hash.txt --format=rar5 --wordlist=/usr/share/wordlists/rockyou.txt
```

![image](https://github.com/user-attachments/assets/88e38e2f-a4b7-47b8-874c-6afbab874e26)


To display the cracked password:

```bash
john --show hash.txt
```

✅ **Result:** The password for `FILE1.rar` was found: **Password**

### Step 3: Extracting a Custom Wordlist
After extracting the contents of `FILE1.rar`, a text file containing multiple words was found. These words were saved in **wordlist.test**, which was then used to crack the next file.

![image](https://github.com/user-attachments/assets/40138955-d9cb-4b8d-b6f8-7adb6a055a22)


### Step 4: Extracting Hash from FILE2.rar
Similarly, the hash for `FILE2.rar` was extracted:

```bash
rar2john FILE2.rar > hash2.txt
```

![Extracting Second Hash](images/extracting_second_hash.png)

### Step 5: Cracking FILE2.rar Password
Using John the Ripper with the **custom wordlist (wordlist.test)**:

```bash
john hash2.txt --format=rar5 --wordlist=wordlist.test
```

✅ **Result:** The password for `FILE2.rar` was found: **Str0ngP@55w0rd**

## Conclusion
This project demonstrates a common **password recovery scenario** using **John the Ripper** and **custom wordlists**. It highlights how attackers can crack weak passwords and reinforces the importance of using **strong, unique passwords**.
