# Diffie-Hellman Key Exchange — Algorithm & CrypTool Steps
### Practical No. 10 | Network and Information Security (316317)

---

## PART A — Algorithm Steps (C Program)

**Step 1:** START

**Step 2:** Declare variables:
- `p` → large prime modulus
- `g` → primitive root / generator modulo p
- `a, b` → private keys of Alice and Bob
- `A, B` → public keys of Alice and Bob
- `s1, s2` → shared secrets computed by each party

**Step 3:** Implement helper function: `modularExponentiation(base, exp, mod)`
1. result ← 1
2. base ← base % mod
3. WHILE exp > 0 DO:
   - IF (exp % 2 == 1) THEN result ← (result × base) % mod
   - exp ← exp / 2  (integer division)
   - base ← (base × base) % mod
4. RETURN result

**Step 4:** Input public parameters `p` (prime) and `g` (generator)

**Step 5:** Alice chooses private key `a` (random integer, 1 < a < p-1)

**Step 6:** Bob chooses private key `b` (random integer, 1 < b < p-1)

**Step 7:** Alice computes her public key:
- A ← modularExponentiation(g, a, p)

**Step 8:** Bob computes his public key:
- B ← modularExponentiation(g, b, p)

**Step 9:** Alice sends A to Bob; Bob sends B to Alice
(exchange happens over the insecure channel)

**Step 10:** Alice computes shared secret:
- s1 ← modularExponentiation(B, a, p)

**Step 11:** Bob computes shared secret:
- s2 ← modularExponentiation(A, b, p)

**Step 12:** Verify:
- IF s1 == s2 THEN → Shared secret established = s1
- ELSE → ERROR: Keys do not match

**Step 13:** Display: p, g, A, B, and shared_secret

**Step 14:** STOP

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
