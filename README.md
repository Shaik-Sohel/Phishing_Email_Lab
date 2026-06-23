# 🛡️  Phishing Email Investigation Lab  #

## 🎯 Objective  
Analyze a phishing email sample with the malicious domain **`xtbmondo.com`** and IP **`143.92.60.168`** to identify spoofing, malicious indicators, and attacker intent.  

---

## 📂 Pre-requisites  
Before starting, make sure you have:  

- A text editor (**Notepad++ / VS Code**) OR an email client (**Thunderbird**) installed.  
- Access to basic **WHOIS** and **IP lookup** tools (online or CLI-based like `whois`, `dig`, `nslookup`).  
- Download the sample phishing email file:  
  👉 [Download Sample EML](./phishing_sample_2.eml)  

*(If running locally, place the `.eml` file in your working folder.)*  

---

## 🔑 Tasks  

1️⃣ What evidence in the email headers shows that the sender domain and IP (`xtbmondo.com` / `143.92.60.168`) are suspicious?  

2️⃣ How does the body content of the email attempt to trick the recipient into taking action?  

3️⃣ List the **Indicators of Compromise (IoCs)** found in this email that a SOC team should block or monitor.  

---

## 🔍 Guide: Analyze Headers with MXToolbox  

You can use **MXToolbox Email Header Analyzer** to make sense of raw headers.  

1. Open 👉 [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx).  
2. Open the `.eml` file in a **text editor**.  
3. Copy the **entire header section** (everything above the email body).  
   - Example includes fields like:  
     ```
     Received: from xtbmondo.com (143.92.60.168) ...
     Authentication-Results: spf=none ...
     X-Sender-IP: 143.92.60.168
     ```
4. Paste the headers into the **MXToolbox input box**.  
5. Click **Analyze Header**.  
6. Review the results:  
   - **Hop timeline** (shows the path the email took).  
   - **Sender IP** (should show `143.92.60.168`).  
   - **SPF/DKIM/DMARC** status (failed).  
   - Latency (to see how fast each mail server handled the message).  

👉 This tool makes it easier to **visualize suspicious hops and authentication failures**.  

---

## 📝 Conclusion  
This phishing email pretends to come from Microsoft but fails authentication checks (**SPF, DKIM, DMARC**), uses a malicious domain (**`xtbmondo.com`**), and routes replies to a fraudulent address.  

The body leverages **social engineering** (“Unusual sign-in activity”) to create urgency. By extracting IoCs (domain, IP, reply-to email, tracking pixel), defenders can block threats, improve detection, and train users to recognize phishing attempts.  

---
