This is a challenge problem intended for future students of Athenian's Advanced Computer Science (Honors) course to try
during the cryptography lab.

One of the most common secure encryption methods used today is RSA (Rivest–Shamir–Adleman), named after its creators.
It is a two-key crypto-system, in which a public key is used to encrypt a message, then a private key corresponding to
the public key is required to decrypt it.

The public key consists of two parts: the encryption exponent *e* and the modulus *n*. To encrypt a message *m*, one 
converts it into an integer, then calculates the ciphertext *c ≡ m<sup>e</sup> (mod n)*.

The private key is one value: the decryption exponent *d*. To decrypt a message, one simply calculates *c<sup>d</sup> ≡
(m<sup>e</sup>)<sup>d</sup> ≡ m (mod n)*.

However, determining the decryption and encryption exponents is non-trivial. The first step is to choose two prime
numbers, *p* and *q*. Ideally, *p* and *q* should be very large, to make brute-forcing harder. Next you calculate *n = 
pq*, and find the least common multiple *x* of *p - 1* and *q - 1*. Then you choose an integer *e* such that *e* is 
greater than 2 and less than *x*, and *e* and *x* are coprime. Finally, calculate *d* as the multiplicative inverse of 
*e* modulo *x*, such that *de = 1 (mod x)*.

Your job is to decrypt the message 720956824 which was encrypted with the public key (*e* = 65537, *n* = 1903446227).
Good luck!

Important information:

You can use the [Euclidean algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm) to calculate the GCD of two
numbers, the formula *lcm(a,b) = ab / gcd(a,b)* to find the LCM of two numbers, and the 
[extended Euclidean algorithm](https://en.wikipedia.org/wiki/Extended_Euclidean_algorithm#Computing_multiplicative_inverses_in_modular_structures) 
to find the multiplicative inverse of a number which is coprime to a modulo.

You will need to use longs when decrypting the message. Also remember that *c<sup>d</sup> (mod n) = c<sup>a</sup> (mod n) 
\* c<sup>b</sup> (mod n)* while *a + b = d,* and you can and should reduce *c<sup>a</sup>* and *c<sup>b</sup>* before 
multiplying them.