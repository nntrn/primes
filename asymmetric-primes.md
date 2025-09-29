# asymmetric prime discovery

    C = (n • k) - 2

For every odd n, return the first candidate C that is a prime; otherwise, 
continue with the next k in the sequence 3, 5, 7, 9, ...

Example (n = 29):

    Step 1: (29 × 3) − 2 = 85   → not prime, rerun 
    Step 2: (29 × 5) − 2 = 143  → not prime, rerun 
    Step 3: (29 × 7) − 2 = 201  → not prime, rerun 
    Step 4: (29 × 9) − 2 = 259  → not prime, rerun 
    Step 5: (29 × 11) − 2 = 317 → prime

this has been tested on 1-500k (250k test cases for odds only) without 
any errors

    n    prime   x/y        k    steps
    ---- ------- ---------- ---- -------
    1    3       0.333333   5    2
    3    7       0.428571   3    1
    5    13      0.384615   3    1
    7    19      0.368421   3    1
    9    43      0.209302   5    2
    11   31      0.354838   3    1
    13   37      0.351351   3    1
    15   43      0.348837   3    1
    17   83      0.204819   5    2
    19   131     0.145038   7    3
    21   61      0.344262   3    1
    23   67      0.343283   3    1
    25   73      0.342465   3    1
    27   79      0.341772   3    1
    29   317     0.091482   11   5
    31   277     0.111913   9    4

---

## harmonic 

n/prime ≈ 1/k

    example:
    255/673 ≈ 1/3     # 0.334324
    135/673 ≈ 1/5      # 0.200594

this is true for all 1/k (guaranteed because -2 becomes more immaterial as primes get larger) 

examples: 
- "k=3" numbers are ~.33 just like 1/3
- "k=5" numbers are ~.20 just like 1/5
- "k=7" numbers are ~.14 just like 1/7
- "k=9" numbers are ~.11  just like 1/9

---

primes also repeat
as k gets largest (> 9), the prime is likely subsumable into into k=3,5,7,9 at a larger n. 
so skipping it at one n doesn't mean it won't reappear at another n

    (prime+2)/k = n
    where n is not a fraction, must divide cleanly 

example: 

    factors for 95421: 3, 17, 51, 1871, 5613, 31807

    (95419+2)/3 = 31807 (n=31807, k=3) 
    (95419+2)/17 = 5613 (n=5613, k=17)
    (95419+2)/51 = 1871 (n=1871, k=51)

a smaller k requires a larger n

---

[github.com/nntrn/primes](@nntrn) | [View project](https://github.com/nntrn/harmonic-primes)
