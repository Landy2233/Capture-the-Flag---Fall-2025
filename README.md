# 🔍 Forensics/Steganography: Metadata Hidden

---

## Problem Description

I discovered this file during an investigation. Someone is trying to hide information in the **metadata** (information about the data). Can you do a little forensic investigating... there seems to be something odd about the **camera description**.

You will need the **`Arch.jpg`** file for this challenge.

## Task

Your objective is to uncover the hidden information (the **flag**) contained within the metadata of the `Arch.jpg` image file.

Start by inputting the `Arch.jpg` file into your forensic tool ([CyberChef](https://gchq.github.io/CyberChef/)).

## Hints

* You will need to determine the **specific EXTRACT operation** used in CyberChef to handle camera and image-specific metadata. 
* The suspicious information is hidden in a field typically used for camera description. In image metadata, this often corresponds to the **Make** or **Model** tag.
* The final answer (the flag) will be in this format: `flag{something_hidden_here}`. 
