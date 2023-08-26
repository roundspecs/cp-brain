## Definition
To express a number (greater than 1) as product of primes

- Prime factorization of a number is often called *skeleton view* because the prime factors are the bare-bones of a number

## Algorithms for Prime Factorization
### $O(\sqrt{x})$
The idea is to 
```cpp
vector<int> factors(int n) {
	vector<int> f;
	for (int x = 2; x*x <= n; x++) {
		while (n%x == 0) {
			f.push_back(x);
			n /= x;
		}
	}
	if (n > 1) f.push_back(n);
	return f;
}
```
