# prime discoveries

Informal collection of generative prime rules

### [RULE 1](asymmetric-primes.md)
for every odd n, return the first candidate C that is a prime; otherwise, continue with the next k in the sequence 3, 5, 7, 9,... (confirmed: k < 300 when n < 1,000,000) 

C = (n • k) - 2 

this generation is also harmonic:  
n/C ≈ 1/k  

pseudo code:

    rule(n,k=3,limit=300) => isprime(n*k-2) ? (n*k-2) : (k+2<limit) && rule(n,k+2)


### [RULE 2](symmetric-primes.md) 
for every odd number n, an even number exist that can be added to and subtracted from n and yield a prime number on both sides (same odd number n, same even number e, two different primes)

prime = n ± e 

    rule(n,e) => isprime(n+e) && isprime(n-e) ? [n-e, n+e] : (n > e+2) && rule(n,e+2)


### RULE 3
for any odd number n, set dimension d and modify RULE 1 using a fractal dimensional scale to return a prime or a number with only prime factors (exluding 1 and itself)

C = (n • 3^d) – 2^d 

d=1: (n • 3) - 2  
d=2: (n • 9) - 4  
d=3: (n • 27) - 8  
d=4: (n • 81) - 16  
d=5: (n • 243) - 32  

    rule(n,d=1) => n*(3**d) - (2**d)


### RULE 4
for every n that ends in 5, keep dividing by 5 until you get a number that does not end in 5. this number will always be a prime, or a number with only prime factors (excluding 1 and itself) 

note: if the number doesn't divide cleanly then you have gone too far and must go back to the previous step

pseudo code: 

    rule(n)=> if n%5==0 then rule(n/5) else n end

example:  
step 1. 875 ÷ 5 = 175  
step 2. 175 ÷ 5 = 35  
step 3. 35 ÷ 5 = 7  

works on big random numbers:  
846295 ÷ 5 = 169259 (prime)  
1692595 ÷ 5 = 338519 (factors: 503, 673)  
75893245 ÷ 5 = 15178649 (factors: 67, 226547)

1234567891234567895 ÷ 5 = 98765431398765431 (factors are {373, 379, 701, 1021}) 

TODO: a version of this applies to numbers that end in 0 (subtract the final value by 1)

---

(c) annie tran
