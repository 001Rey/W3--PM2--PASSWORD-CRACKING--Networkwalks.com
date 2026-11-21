# Password Cracking with Networkwalks Tools

**Module:** W3-PM2 — Week 3, Project Module 2
**Program:** Networkwalks Cybersecurity & Ethical Hacking (Batch B084)
**Author:** Olusegun Olaniyan (Rey)

## Objective
Recover the password of an encrypted PDF (`My-Locked-PDF1.pdf`) using the Networkwalks **Hash Calculator** and **Password Cracker** tools, simulating a dictionary attack similar to John the Ripper.

## Tools Used
- [Networkwalks Hash Calculator](https://networkwalks.com/hash-calculator/) — extracts a crackable `$pdf$...` hash (pdf2john/hashcat compatible) from a password-protected PDF
- [Networkwalks Password Cracker](https://networkwalks.com/password-cracker/) — runs a dictionary attack against the extracted hash
- WPS Office PDF reader — to verify the recovered password unlocks the file

## Steps

1. **Extract the hash** — Uploaded `My-Locked-PDF1.pdf` to the Hash Calculator, which parsed the file locally and returned the hash:
   ```
   $pdf$4*4*128*-1060*1*16*55d1a5c14175da449753199e44971d32*32*777fd021a7f3c5ae598c0c6495c7f76e00000000000000000000000000000000*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1
   ```

2. **Run the dictionary attack** — Pasted the hash into the Password Cracker and started the built-in 100-word wordlist attack.

3. **Match found** — After 91/100 attempts, the tool matched the password: **`password1`**

4. **Unlock the PDF** — Opened `My-Locked-PDF1.pdf` and entered `password1` as the open password. The file decrypted successfully and revealed a "flag" page confirming lab completion:
   ```
   nw{networkwalks_flag1_jtr_270521_1}
   ```

## Result

| Item | Value |
|---|---|
| Target file | My-Locked-PDF1.pdf (65.2 KB) |
| Encryption | PDF Revision 4, Version 4, 128-bit key |
| Attack type | Dictionary attack (built-in 100-word list) |
| Attempts to crack | 91 |
| Cracked password | `password1` |
| Captured flag | `nw{networkwalks_flag1_jtr_270521_1}` |

## Screenshots
See [`/screenshots`](./screenshots):
1. `01-hash-extraction.png` — Hash extracted from the locked PDF via Hash Calculator
2. `02-password-cracked.png` — Dictionary attack matching `password1`
3. `03-flag-captured.png` — Flag revealed inside the unlocked PDF
4. `04-pdf-unlocked.png` — Password entered to unlock the PDF in WPS Office

## Key Takeaway
Weak, common passwords (e.g. `password1`) can be cracked in seconds with a small dictionary. The lab demonstrates why strong, unique passwords are essential: a short or common password is found almost instantly, while a longer, mixed-character password resists cracking for years.

## Reference
Full lab brief: [`W3-PM2-Password-Cracking-with-NW-Tools.pdf`](./W3-PM2-Password-Cracking-with-NW-Tools.pdf)
