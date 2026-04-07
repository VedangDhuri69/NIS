# Practical No. 10 — Diffie-Hellman Key Exchange Algorithm

**Course:** Network and Information Security (316317)
**Scheme:** K | **Semester:** VI
**Branch:** CM / CO / CW / IF / BD / SE

---

## I. Practical Significance

This practical introduces the **Diffie-Hellman Key Exchange (DHKE)** protocol — the first widely used public-key exchange method. It allows two parties to establish a **shared secret key** over an insecure channel **without ever transmitting the key itself**. The secret key can then be used for symmetric encryption. Students will understand how secure key exchange is achieved in real-world cryptography by using **CrypTool 1.4.42**.

---

## II. Industry / Employer Expected Outcome

Implement policies and guidelines to maintain **data security and privacy** during data transmission.

---

## III. Course Level Learning Outcome (CO)

**CO4** – Use tools and techniques to prevent cyber attacks.

---

## IV. Laboratory Learning Outcome (LLO)

**LLO 10.1:** Implement Diffie-Hellman key exchange encryption technique.

---

## V. Affective Domain Outcomes

1. **Ethical awareness** — Understanding that secure key management is essential for data privacy.
2. **Analytical skills** — Evaluating modular arithmetic and prime number role in cryptography.
3. **Attention to detail** — Correct implementation of exponentiation and modular operations.

---

## VI. Theoretical Background

### What is Diffie-Hellman Key Exchange (DHKE)?

The **Diffie–Hellman Key Exchange** is a cryptographic method that allows two parties to securely establish a **shared secret key** over an insecure communication channel. This shared key can then be used to encrypt further communications.

- **Introduced in:** 1976 by **Whitfield Diffie** and **Martin Hellman**
- **Based on:** The difficulty of the **Discrete Logarithm Problem (DLP)** in modular arithmetic
- **Type:** Asymmetric / Public Key protocol (for key agreement, not encryption directly)

---

## VII. Algorithm — Diffie-Hellman Key Exchange

### Public Parameters (Agreed Upon by Both Parties)

| Parameter | Description |
|-----------|-------------|
| `p` | A large **prime number** (publicly known) |
| `g` | A **primitive root / generator** modulo p (publicly known) |

### Step-by-Step Algorithm

```
Step 1: Both Alice and Bob publicly agree on:
        → A large prime number p
        → A generator g (primitive root mod p)

Step 2: Alice chooses a private key:
        → a  (secret, random integer: 1 < a < p-1)

Step 3: Bob chooses a private key:
        → b  (secret, random integer: 1 < b < p-1)

Step 4: Alice computes her PUBLIC key:
        → A = g^a mod p

Step 5: Bob computes his PUBLIC key:
        → B = g^b mod p

Step 6: Exchange public keys:
        → Alice sends A to Bob  (over insecure channel)
        → Bob sends B to Alice  (over insecure channel)

Step 7: Alice computes the Shared Secret using Bob's public key:
        → S = B^a mod p

Step 8: Bob computes the Shared Secret using Alice's public key:
        → S = A^b mod p

Step 9: VERIFY — Both values of S are mathematically equal:
        → S = g^(ab) mod p  ✓

Step 10: Both Alice and Bob now share the SAME secret key S
         WITHOUT ever transmitting it directly.
```

### Numerical Example (Small Numbers for Understanding)

| Step | Alice | Bob |
|------|-------|-----|
| Public Parameters | p = 23, g = 5 | p = 23, g = 5 |
| Private Key | a = 6 (secret) | b = 15 (secret) |
| Public Key Computation | A = 5⁶ mod 23 = **8** | B = 5¹⁵ mod 23 = **19** |
| Exchange | Alice sends **8** to Bob | Bob sends **19** to Alice |
| Shared Secret | S = 19⁶ mod 23 = **2** | S = 8¹⁵ mod 23 = **2** |

> ✅ **Both Alice and Bob compute the same shared secret = 2**, which becomes the symmetric encryption key.

---

## VIII. Resources Required

| Sr. No. | Resource | Specification |
|---------|----------|---------------|
| 1 | Hardware: Computer | i3–i5, RAM ≥ 2 GB, HDD ≥ 10 GB |
| 2 | Operating System | Windows XP / 7 onwards or Linux v5.0+ |
| 3 | Software / Tool | **CrypTool 1.4.42** |

---

## IX. CrypTool Steps — Diffie-Hellman Key Exchange (DHKE)

> **Tool Used:** CrypTool 1.4.42
> **Purpose:** Visually demonstrate and verify the Diffie-Hellman Key Exchange protocol

---

### ▶ Step 1: START — Open CrypTool

- Launch **CrypTool 1.4.42** on your system.
- The CrypTool main window will appear.

---

### ▶ Step 2: Navigate to Diffie-Hellman Demonstration

- From the **menu bar**, click:
  ```
  Indiv. Procedures → Protocols → Diffie-Hellman Demonstration
  ```
- The **Diffie-Hellman Demonstration** dialog/window will open.

---

### ▶ Step 3: Set Public Parameters (p and g)

- In the demonstration window:
  - Click **Generate** to generate a large **prime number p** → Accept it.
  - Click **Generate** to generate a **generator g** (primitive root mod p) → Accept it.
- Both **p** and **g** are now set as **public parameters** (visible to everyone).

---

### ▶ Step 4: Choose Private Keys (Secrets)

- **Alice** selects her **private number `a`** — this value remains hidden/secret.
- **Bob** selects his **private number `b`** — this value remains hidden/secret.
- Enter these private values in their respective fields in the tool.

---

### ▶ Step 5: Create Public Keys (Shared Values)

- CrypTool automatically computes:
  - **Alice's public key:** `A = g^a mod p`
  - **Bob's public key:** `B = g^b mod p`
- These computed values are the **public keys** that will be exchanged.

---

### ▶ Step 6: Exchange Public Keys

- **Alice sends A to Bob** (over the insecure channel).
- **Bob sends B to Alice** (over the insecure channel).
- CrypTool visually shows this key exchange process.

---

### ▶ Step 7: Generate the Session Key (Shared Secret)

- Alice computes: `S = B^a mod p`
- Bob computes: `S = A^b mod p`
- CrypTool calculates both values and **both results are identical**.

---

### ▶ Step 8: Verify the Shared Secret

- CrypTool **displays the same session key S** for both Alice and Bob.
- This confirms: **Key Exchange is Successful ✓**
- A **common secret session key S** is now shared by both Alice and Bob.
- This key can be used for symmetric encryption of further communication.

---

### ▶ Step 9: STOP

---

## X. CrypTool Steps — Summary Flowchart

```
Open CrypTool 1.4.42
        ↓
Indiv. Procedures → Protocols → Diffie-Hellman Demonstration
        ↓
Generate public parameters: p (prime) and g (generator)
        ↓
Alice enters private key: a  |  Bob enters private key: b
        ↓
CrypTool computes: A = g^a mod p  |  B = g^b mod p
        ↓
Exchange: Alice sends A → Bob  |  Bob sends B → Alice
        ↓
CrypTool computes shared secret:
   Alice: S = B^a mod p  |  Bob: S = A^b mod p
        ↓
Verify: S (Alice) == S (Bob) → KEY EXCHANGE SUCCESSFUL ✓
        ↓
STOP
```

---

## XI. Precautions

1. Ensure **CrypTool 1.4.42** is properly installed before starting the practical.
2. The **prime number p** must be a valid large prime for security.
3. Private keys `a` and `b` must be kept **completely secret** — never shared.
4. Ensure the **generator g** is a valid **primitive root modulo p**.
5. Save screenshots at each step to record the output for your practical file.
6. Do not confuse **public keys (A, B)** with the **shared secret key (S)**.

---

## XII. Practical Related Questions

1. What is the **Discrete Logarithm Problem** and why is it important for DH security?
2. Why can an eavesdropper who intercepts both A and B **not compute the shared secret S**?
3. What are the **public** and **private** components in Diffie-Hellman key exchange?
4. Differentiate between **key exchange** and **encryption** in the context of DH.
5. What is a **primitive root (generator)** and how is it chosen?
6. Perform the Diffie-Hellman key exchange manually with p = 11, g = 2, a = 3, b = 5. Verify the shared secret.
7. What is the **Man-in-the-Middle (MITM) attack** on DH and how can it be prevented?

---

## XIII. References

1. Stallings, W. & Brown, L., 2014. *Computer Security: Principles and Practice.* Pearson.
2. NPTEL, 2022. Introduction to Information Security. [https://archive.nptel.ac.in/courses/106/106/106106129/](https://archive.nptel.ac.in/courses/106/106/106106129/)
3. Virtual Labs, IIIT Hyderabad — Cryptography Experiments: [https://cse29iiith.vlabs.ac.in/List%20of%20experiments.html](https://cse29iiith.vlabs.ac.in/List%20of%20experiments.html)
4. CrypTool Project: [https://www.cryptool.org](https://www.cryptool.org)

---

## XIV. Assessment Scheme

| Performance Indicators | Weightage | Marks |
|------------------------|-----------|-------|
| Following correct DH procedure in CrypTool | 30% | — |
| Correct key generation and exchange steps | 30% | — |
| Quality of output (session key verified) | 20% | — |
| Answer to sample questions | 20% | — |
| **Process-related Assessment** | — | **15 Marks** |
| **Product-related Assessment** | — | **10 Marks** |
| **Total** | **100%** | **25 Marks** |

---

*Maharashtra State Board of Technical Education — 'K' Scheme | Course: Network and Information Security (316317)*
