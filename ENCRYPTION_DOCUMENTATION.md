# Encryption & Export Compliance Declaration

**Application Name:** D-Ticket zu Apple Wallet  
**Bundle Identifier:** de.dticket.wallet  
**Version:** 1.1.0  
**Developer:** Fynn Hicken  
**Contact:** fynn.hicken@gmail.com  
**Date:** November 3, 2026  

---

## 1. Executive Summary
This document provides formal technical and regulatory documentation regarding the cryptographic functionality used in the iOS application **D-Ticket zu Apple Wallet** (`de.dticket.wallet`).

The application qualifies for **export exemption** under **U.S. Export Administration Regulations (EAR) Category 5, Part 2, Note 4** and **Section 740.17(b)(1)**, as cryptography is employed **strictly and exclusively for digital signatures and authentication** (generation of signed Apple Wallet `.pkpass` files). The application does not provide data confidentiality encryption for user storage, messages, or network transmissions.

---

## 2. Regulatory Classification (U.S. EAR)
* **Commerce Control List (CCL):** Category 5, Part 2 (Information Security)
* **Exemption Basis:** Note 4 to Category 5, Part 2:
  > *"Category 5 - Part 2 does not apply to items that incorporate or use cryptography to perform any of the following: (a) Authentication, digital signature, or data integrity..."*
* **License Exception:** ENC under 15 CFR § 740.17(b)(1) / Self-Classification eligible.
* **Non-Exempt Encryption:** None (`ITSAppUsesNonExemptEncryption = false`).

---

## 3. Cryptographic Purpose & Architecture
The application is a 100% local, on-device utility designed to convert German public transit ticket barcodes (Aztec format) into native Apple Wallet passes.

To comply with Apple Inc.'s mandatory **PassKit Package Specification**, every Apple Wallet pass (`.pkpass`) must contain a detached CMS / PKCS#7 signature file named `signature` that cryptographically signs the manifest containing file hashes.

The cryptographic workflow is entirely confined to:
1. Computing file hashes of pass package assets for `manifest.json`.
2. Generating a detached CMS / PKCS#7 signature over the manifest digest using an Apple-issued Pass Type ID certificate.
3. Importing the developer's pass certificate from an encrypted PKCS#12 container in memory.

**No user data encryption is performed.** The app operates entirely offline and does not establish network connections or encrypt external communications.

---

## 4. Cryptographic Algorithms, Key Sizes & Standards

| Purpose | Algorithm / Standard | Key Length / Hash Size | Framework / Implementation |
| :--- | :--- | :--- | :--- |
| **Pass Digital Signature** | RSA (PKCS#1 v1.5 / RFC 5652 CMS) | 2048-bit RSA Private Key | Apple `Security.framework` (`SecKeyCreateSignature`) |
| **CMS Digest Calculation** | SHA-256 (FIPS 180-4 / RFC 6234) | 256 bits | Apple `CryptoKit` (`SHA256.hash`) |
| **PassKit Manifest Hashing** | SHA-1 (mandated by Apple PassKit spec) | 160 bits | Apple `CryptoKit` (`Insecure.SHA1.hash`) |
| **In-Memory PKCS#12 Import** | Password-based key derivation (PBKDF2) | Standard iOS Security API | Apple `Security.framework` (`SecPKCS12Import`) |

---

## 5. Exclusively Native Operating System APIs
The application **does not contain any third-party, open-source (e.g. OpenSSL, libsodium), proprietary, or non-standard cryptographic code**.

All cryptographic calls are executed strictly through Apple’s native iOS system frameworks:
* `Security.framework`
* `CryptoKit.framework`

As per Apple Developer Guidelines and US BIS regulations, standard software utilizing standard operating system cryptographic APIs for authentication and digital signing is exempt from further CCATS filing requirements.

---

## 6. French Declaration (ANSSI) Exemption
Under decree n° 2011-1436 and the guidelines of the French National Cybersecurity Agency (ANSSI), cryptographic capabilities used solely to authenticate users or ensure the integrity of applications/passes are exempt from prior declaration or authorization.

---

**Certified by:**  
Fynn Hicken  
Lead Developer & Publisher  
fynn.hicken@gmail.com
