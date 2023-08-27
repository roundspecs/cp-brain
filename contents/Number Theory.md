# Primes
## Definitions
|Term      |# of distinct factors |
|----------|----------------------|
|One       |exactly 1             |
|Prime     |exactly 2             |
|Composite | more than 2          |
## Algorithms: Primality test $O(\sqrt n)$
```cpp
bool prime(int n) {
	if (n < 2) return false;
	for (int x = 2; x*x <= n; x++) {
		if (n%x == 0) return false;
	}
	return true;
}
```
# Prime Factorization
a.k.a *skeleton view*
$$n=p_1^{\alpha_1} p_2^{\alpha_2} ... p_n^{\alpha_n}$$
## Fundamental Theorem of Arithmetic

### Statement
Every integer greater than 1 can has a unique [[#Prime Factorization|prime factorization]]
### Explanation
$$1200=2^4\times3^1\times5^2$$
The theorem states two things about this example:
1. Prime factorization of 1200 exists
2. No matter how the prime factorization is done, there will always be four 2's, one 3 and two 5's
## Algorithms

### $O(\sqrt{x})$
The idea is to find `SPF(n)`, append it to `skeleton` and reduce `n` to `n/2`
Recall: every composite number has at least one prime factor less than or equal to the square root of itself
Therefore, as long as `n` is composite, `SPF(n)<=sqrt(n)`.
Finally, we are left with `n=1` or `n` is prime.
```cpp
vector<int> get_skeleton(int n) {
	vector<int> skeleton;
	for(int x = 2; x*x <= n; x++) {
		while (n%x == 0) {
			skeleton.push_back(x);
			n /= x;
		}
	}
	if(n>1) skeleton.push_back(n);
	return skeleton;
}
```
## Number of factors
$$\tau(n)=\prod_{i=1}^n (\alpha_i+1)$$
### Proof
Factors of `n` are unique and can be expressed as product of some prime factors of `n`
Therefore, $\tau(n)$ is the number of ways we can choose prime factors of `n`
## Sum of factors
$$\sigma(n)=\prod_{i=1}^n (1+p_i+p_i^2+...+p_i^{\alpha_i})$$
We know, $1+p_i+p_i^2+...+p_i^{\alpha_i}$ is the geometric series of $p$. Therefore, the sum of the geometric series $\alpha_i+1$ terms is $\frac{p_i^{\alpha_i+1}-1}{p_i-1}$.
Therefore, the equation can be simplified:
$$\sigma(n)=\prod_{i=1}^n \frac{p_i^{\alpha_i+1}-1}{p_i-1}$$
## Product of factors
$$\sigma(n)=n^{\tau(n)/2}$$
## Prime Number Theorem (PNT)
### Number of Primes
Number of primes between 1 and n is
$$\pi(n)\approx\frac{n}{\ln{n}}$$
### Density of Primes
Density of primes between 1 and n is
$$\frac{\pi(n)}{n}\approx\frac{1}{\ln{n}}$$

# Summation
## Identities
- $\sum{c\times f(n)}=c\times \sum{f(n)}$, $c$ is constant
- $\sum{(f(n)\pm g(n))}=\sum{f(n)}\pm \sum{g(n)}$
- $\sum_{i=1}^n\sum_{j=1}^n{a_ib_j}=(\sum_{i=1}^n{a_i})(\sum_{j=1}^n{b_j})$
### Practice:
- [AtCoder - ARC A - Simple Math](https://atcoder.jp/contests/arc107/tasks/arc107_a) 
