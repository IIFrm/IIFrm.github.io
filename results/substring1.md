# pldi08

## source 
[Interpolants as Classifier](http://theory.stanford.edu/~aiken/publications/papers/cav12a.pdf) by Rahul Sharma, Aditya V. Nori, and Alex Aiken


## program
```c
int substring1(int* a) {
	int j;
	int i = a[0];
	int k = a[1];

	iif_assume ((i >= 0) && (i <= k) && (k >= 0) && (k <= 100)); 
	while (i < k) {
		recordi(i, k);
		i++;	
		j++;
	}
	recordi(i, k);
	iif_assert(j >= 101);
	return 0;
}
```




## Selective Learning Results:


```
TRY SVM method ...
[1]}
Program BUG! Program have encountered a Counter-Example trace.
	Tr.0:(32,43)->(33,43)->(34,43)->(35,43)->(36,43)->(37,43)->(38,43)->(39,43)->(40,43)->(41,43)->(42,43)->(43,43)->end.
```

## Reason