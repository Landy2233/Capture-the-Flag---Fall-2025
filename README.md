# Challenge 1: Decryption

---

Keyword: GLAB

O DTBTO BZ CLLMY HHFXP PFUALF XZAN, CTTI HFTUUYS UU ARFYD AOJ DNBIVS UU EALK SONK.


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
4.  Calculate the new height required to display the full canvas. The full content requires you to **increase the current height metadata value by 2,000 pixels**.
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
