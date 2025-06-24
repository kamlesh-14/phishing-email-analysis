# Email Authentication: DKIM and SPF

Understanding SPF and DKIM helps in detecting spoofed or fake emails. Here’s a simple explanation:

---

##  What is SPF?

**SPF (Sender Policy Framework)** is a DNS record that tells mail servers which IP addresses are authorized to send emails on behalf of a domain.

### ✅ If SPF is configured correctly:
- Receivers know that the email came from an authorized sender.

### ❌ If not:
- Anyone can forge emails using that domain (common in phishing).

---

##  What is DKIM?

**DKIM (DomainKeys Identified Mail)** adds a digital signature to emails. The receiving server uses the sender’s public DNS key to verify if the email was really sent by that domain and wasn’t altered.

### ✅ If DKIM passes:
- The email is verified and trusted.

### ❌ If it fails or is missing:
- There’s a risk the email was forged or tampered with.

---

##  Example From Analysis:

In our phishing samples:

- **LastPass Email** → No valid SPF or DKIM present (indicates spoofing).
- **Microsoft Email** → DKIM missing, SPF mismatch found using [MXToolbox](https://mxtoolbox.com/EmailHeaders.aspx).

---

##  Why These Matter?

Phishing emails often lack SPF/DKIM or have fake signatures. Checking these via header analysis tools is a powerful first step in phishing detection.

> Use tools like [Google Admin Toolbox](https://toolbox.googleapps.com/apps/messageheader/) or MXToolbox to check SPF, DKIM, and DMARC in email headers.
