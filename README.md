 # Week 3 Project — Password Cracking Lab

This is my write-up for Week 3 (Project Modules 1 & 2) of the Networkwalks Cybersecurity & Ethical Hacking course.

The task was to crack the password of a locked PDF file called `My Locked PDF1.pdf`. I did it two ways:
1. With John the Ripper + Johnny on Windows
2. With the Networkwalks online tools

Both ways gave me the same password: `password1`

---

## What this is about

When you put a password on a file like a PDF or ZIP, the password is stored in a scrambled form called a **hash**. If you can pull that hash out of the file, you can use a cracking tool to keep guessing words until it finds one that matches. That's basically what this lab was about.

I did it on Windows 10. On Kali Linux, John the Ripper is already installed so you can skip the download part.

---

## Method 1: John the Ripper + Johnny

**What I downloaded**
- John the Ripper (Jumbo version) from https://www.openwall.com/john/
- Johnny GUI from https://openwall.info/wiki/john/johnny

**Steps I followed**

1. Installed Johnny by running `johnnyInstaller.exe`.
2. Opened Johnny and went to **Settings**. It said it couldn't find John, so I clicked **Browse**.
3. Found `john.exe` inside the `run` folder (it was in `Downloads\JTR_John_1.9.0-jumbo-1-win64\run`). This part took me a while to find.
4. Johnny needs a hash file, not the PDF itself. So I opened the OnlineHashCrack PDF hash extractor: https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php
5. Uploaded `My Locked PDF1.pdf` and copied the hash. It starts with `$pdf$...`
6. Pasted the hash into Notepad and saved it as `hash1.txt`.
7. In Johnny, clicked **Open password file** and picked `hash1.txt`.
8. Clicked **Start new attack** and waited.
9. The password showed up in the Password column: `password1`
10. Opened the PDF with that password and it worked.

---

## Method 2: Networkwalks tools

This one was much faster because nothing had to be installed.

1. Went to the Hash Calculator: https://networkwalks.com/hash-calculator/
2. Clicked the **PDF** tab and uploaded `My Locked PDF1.pdf`.
3. The tool gave me the hash (again starting with `$pdf$...`). I copied the whole thing.
4. Went to the Password Cracker: https://networkwalks.com/password-cracker/
5. Pasted the hash and clicked **Start Cracking**.
6. It cracked it and showed the password: `password1`

---

## What I learned

- Encryption and hashing are not the same thing. Encryption can be reversed with a key. Hashing is one-way.
- But PDFs store their password as a hash, and if you can extract that hash, weak passwords can be cracked quickly.
- `password1` got cracked really fast because it's basically a dictionary word with a number on the end. A longer, random password would have taken way longer.
- Having the hash is the important part. Once you have it, the rest is just the tool guessing.

---

## Note

I only did this on the PDF file given in the course, on my own machine. This is for learning about why strong passwords matter — not for trying on files you don't own.

---

## Links I used

- John the Ripper: https://www.openwall.com/john/
- Johnny GUI: https://openwall.info/wiki/john/johnny
- OnlineHashCrack PDF extractor: https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php
- Networkwalks Hash Calculator: https://networkwalks.com/hash-calculator/
- Networkwalks Password Cracker: https://networkwalks.com/password-cracker/
