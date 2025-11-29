# 🔑 Challenge 1: Decryption

---

## Problem Description

Decrypt the following ciphertext to find the flag.

**Keyword:** GLAB

**Key Letter:** E

C OPWIZ XU PBG SWFFO SBGNG KGJKFG NJWH, SCPB XQPPJIO PJ KNGOO WIZ OIWYEO PJ PWEG BJHG


# 🔍 Challenge 2: Metadata Hidden

---

## Problem Description

I discovered this file during an investigation. Someone is trying to hide information in the **metadata** (information about the data). Can you do a little forensic investigating... there seems to be something odd about the **camera description**.

You will need the **`arch.jpg`** file for this challenge.

## Task

Your objective is to uncover the hidden information (the **flag**) contained within the metadata of the `Arch.jpg` image file.

Start by inputting the `arch.jpg` file into your forensic tool ([CyberChef](https://gchq.github.io/CyberChef/)).

## Hints

* You will need to determine the **specific EXTRACT operation** used in CyberChef to handle camera and image-specific metadata. 
* The suspicious information is hidden in a field typically used for camera description. In image metadata, this often corresponds to the **Make** or **Model** tag.
* The final answer (the flag) will be in this format: `flag{something_hidden_here}`. 



# 🖼️ Challenge 3 — Beneath the Images

---

## Problem Description

We've intercepted a highly suspicious image file, **`cat.jpg`**. At first glance, it appears to be just a harmless photo, but forensic analysis suggests the image canvas has been intentionally manipulated to **hide text outside of the viewable area**.

The flag has been concealed by setting a height value in the image header that is too small for the image's actual content. Your task is to correct the header and reveal the secret message hidden below the visible image frame.

## Task

1.  Open the **`cat.jpg`** file in [CyberChef](https://gchq.github.io/CyberChef/).
2.  Locate the **Start of Frame (SOF0)** marker, which defines the image's dimensions.
3.  Identify the 2-byte hexadecimal value that sets the current **Image Height**.
4.  Calculate the new height required to display the full canvas. The full content requires you to **increase the current height metadata value by 96 pixels**.
5.  Convert this new total height back into a 2-byte hexadecimal value.
6.  Modify the image file's header with the new hexadecimal height value and re-render the image to capture the flag.

## Hints

* The **Start of Frame (SOF0)** marker is identified by the hexadecimal sequence **`FF C0`**.
* The Height value is a 2-byte hexadecimal number that is located immediately following the SOF0 marker and the 2-byte length segment.
  
![Challenge Image: Start of Frame](https://github.com/Landy2233/Beneath-the-Images-/blob/main/Start%20of%20Frame.png)

* You will need to use converters to switch between decimal and hexadecimal for your calculations:
    * **Hex to Decimal Converter:** [https://www.binaryhexconverter.com/hex-to-decimal-converter](https://www.binaryhexconverter.com/hex-to-decimal-converter)
    * **Decimal to Hex Converter:** [https://www.binaryhexconverter.com/decimal-to-hex-converter](https://www.binaryhexconverter.com/decimal-to-hex-converter)
* The flag is in the standard CTF format: `flag{something_hidden_here}`.

#  🔐 Challenge 4 — Password Cracking (John the Ripper + ZIP)

Your goal is to crack the password-protected ZIP file, extract the hidden trivia questions, and use the answers to form the flag.

---
📁 **Step 1 — Go to the folder where you saved the challenge files**

Navigate to the directory where YOU downloaded the files.

Example (Downloads):

    cd ~/Downloads


Or if you saved them somewhere else:

    cd ~/path/to/your/folder


Verify the files are present:

    ls


You should see:

trivia.zip
trivia_hash.txt

  
📚 **Step 2 — Download the rockyou wordlist**

Use curl to download rockyou.txt.gz:

    curl -L -o rockyou.txt.gz https://gitlab.com/kalilinux/packages/wordlists/-/raw/kali/master/rockyou.txt.gz

🗜️ **Step 3 — Extract the wordlist**

    gunzip rockyou.txt.gz


This creates:

rockyou.txt

🔨 **Step 4 — Crack the ZIP password using John the Ripper**

Run:

    john --wordlist=rockyou.txt trivia_hash.txt


If successful, John will eventually output something like:

password123       (trivia.zip/trivia.txt)



🔎 **Step 5 — Display the cracked password**

(Optional, but helpful):

    john --show trivia_hash.txt

📂 **Step 6 — Unzip the file**

unzip trivia.zip and enter the cracked password

This extracts:

trivia.txt

📖 **Step 7 — Read the trivia questions**

Answer the two questions located in the file extracted (trivia.txt):


🏁 **Step 8 — Submit the final flag**

Format:

flag{answer1_answer2}

