# NETWORKWALKS-HOROIHEOMA-B084-WK3-PASSWORD-CRACKING-WITH-JOHN-THE-RIPPER

# Week 3 – Password Cracking with John the Ripper (JTR), Johnny GUI & HexStrike MCP

## Project Overview

This project is part of **Week 3 – Project Module 1** of my Cybersecurity & Ethical Hacking learning journey with Networkwalks.

In this practical, I explored how password-protected PDF files can be recovered using password-cracking tools like **John the Ripper (JTR)** and its graphical interface, **Johnny GUI**.

Along with the main tasks, I also completed the optional AI-assisted lab, where I installed and configured **HexStrike MCP Server with Claude Desktop on Kali Linux** and used it to interact with John the Ripper to recover the password of a locked PDF.

This was a good opportunity to get hands-on experience with traditional password-cracking tools as well as explore how AI can work alongside cybersecurity tools.

## 🛠️ Tools Used

- John the Ripper (JTR)
- Johnny GUI
- HexStrike AI MCP Server
- Claude Desktop
- Kali Linux
- Windows PC
- PDF Hash Extractor
- RockYou Wordlist (`rockyou.txt`)

## ⚙️ Tasks Completed

### 1. John the Ripper & Johnny GUI

- Downloaded and set up John the Ripper on my Windows PC.
- Installed and opened Johnny GUI.
- Extracted the hash from the password-protected PDF.
- Saved the extracted hash in a text file (`hash1.txt`).
- Imported the hash file into Johnny GUI.
- Started the password recovery process.
- Successfully recovered the password and opened the protected PDF.

### 2. Networkwalks Lab Exercises

- Went through the provided JTR and Networkwalks lab materials.
- Opened and reviewed all three PDF documents provided for the exercises.
- Followed the instructions and completed the practical tasks.
- Practiced the password recovery process using the provided tools.

### 3. Optional Task – HexStrike MCP & AI-Assisted Password Cracking

I also decided to try the optional task, which involved setting up HexStrike MCP and connecting it with Claude Desktop in Kali Linux.

Here's what I worked on:

- Installed Claude Desktop on my Kali Linux VM.
- Cloned the HexStrike AI repository from GitHub.
- Created a Python virtual environment and installed the required dependencies.
- Set up and started the HexStrike MCP server.
- Configured the MCP server in Claude Desktop.
- Verified that the server was running and accessible through Claude Desktop.
- Used Claude Desktop to interact with the HexStrike MCP server.
- Checked the John the Ripper installation and its version.
- Used the provided PDF file to calculate its hash.
- Asked Claude to use John the Ripper through HexStrike MCP with the `rockyou.txt` wordlist.
- Successfully recovered the PDF password.
- Opened the previously locked PDF file using the recovered password.

## 📚 What I Learned

Through these exercises, I got a better understanding of:

- How password-protected PDF files work.
- How hashes can be extracted from PDF documents.
- How John the Ripper performs dictionary-based password attacks.
- How to use Johnny GUI instead of working entirely through the terminal.
- How wordlists like RockYou are used during password recovery.
- How to install and configure an MCP server in Kali Linux.
- How Claude Desktop connects with external tools through MCP.
- How AI can be used to interact with existing cybersecurity tools.
- Why using strong and complex passwords is important.

One of the most interesting parts for me was setting up HexStrike MCP and getting it to work with Claude Desktop. It was interesting to see how an AI assistant could interact with a tool like John the Ripper and help perform the password recovery process.

## 📸 Project Evidence

Screenshots and supporting documentation are included to show the work completed during the practical.

Some of the evidence includes:

- JTR and Johnny GUI setup.
- PDF hash extraction.
- Password recovery using Johnny GUI.
- HexStrike AI repository setup.
- Claude Desktop installation.
- MCP server configuration and execution.
- Claude Desktop and HexStrike MCP integration.
- AI-assisted password recovery using John the Ripper.
- Successfully opening the recovered PDF.

## 🔐 Ethical Considerations

All the exercises were performed for learning purposes using the practice files provided as part of the Networkwalks lab.

Password-cracking tools should only be used on files and systems you own or have explicit permission to test.

## 🔗 Resources

- [John the Ripper – Official Website](https://www.openwall.com/john/)
- [Johnny GUI – Official Documentation](https://openwall.info/wiki/john/johnny)
- [HexStrike AI – GitHub Repository](https://github.com/0x4m4/hexstrike-ai)
- [Claude Desktop Debian – GitHub Repository](https://github.com/aaddrick/claude-desktop-debian)
- [Networkwalks](https://www.networkwalks.com/)

## ✅ Project Status

**Completed Successfully**

Completed the JTR and Johnny GUI practical exercises, reviewed all three provided lab PDFs, and went a step further by completing the optional HexStrike MCP setup and AI-assisted PDF password recovery in Kali Linux.

Another step forward in my cybersecurity learning journey! 🚀
