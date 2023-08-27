## $O(\sqrt{n})$
```cpp
vector<int> all_factors(int n) {
	vector<int> factors;
	for(int i=1; i*i<=n; i++) {
		if(n%i==0) {
			factors.push_back(i);
			if(i*i!=n)
				factors.push_back(n/i);
		}
	}
	return factors;
}
```