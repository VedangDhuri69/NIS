# Diffie-Hellman Key Exchange — Algorithm & CrypTool Steps
### Practical No. 10 | Network and Information Security (316317)

---

## PART A — Algorithm Steps

Step 1 — Agree on Public Parameters: Both parties publicly agree on:

A large prime number p A primitive root (generator) g modulo p

Step 2 — Choose Private Keys (Secret):

Alice chooses private key a, Bob chooses private key b, Both values remain secret.

Step 3 — Compute Public Keys:

Alice computes: A = g^a mod p Bob computes: B = g^b mod p

Step 4 — Exchange Public Keys:

Alice sends A to Bob (over insecure channel). Bob sends B to Alice (over insecure channel).

Step 5 — Compute Shared Secret:

Alice computes: S = B^a mod p Bob computes: S = A^b mod p Mathematically, both arrive at: S = g^ab mod p ✅

---

## PART B — CrypTool 1.4.42 Steps

**Step 1:** Open **CrypTool 1.4.42** application on your computer.

**Step 2:** From the menu bar, navigate to:
`Indiv. Procedures → Protocols → Diffie-Hellman Demonstration`

**Step 3:** Set Public Parameters:
- CrypTool generates a large prime number **(p)** → Accept it.
- CrypTool generates a generator **(g)** → Accept it.
- Both p and g are public (visible to everyone).

**Step 4:** Choose Secret Private Keys:
- Alice selects her private number **a** (kept hidden).
- Bob selects his private number **b** (kept hidden).

**Step 5:** Create Public Keys:
- Alice computes: **A = g^a mod p**
- Bob computes: **B = g^b mod p**
- CrypTool displays both computed public values.

**Step 6:** Exchange Public Keys:
- Alice sends **A** to Bob.
- Bob sends **B** to Alice.
- These values travel over the insecure channel.

**Step 7:** Generate the Session Key (Shared Secret):
- Alice computes: **S = B^a mod p**
- Bob computes: **S = A^b mod p**
- Both computations produce the same result.

**Step 8:** Verify:
- CrypTool displays the **same session key S** for both Alice and Bob.
- Key exchange is **successful**.
- This shared secret S is now used as the symmetric encryption key.
