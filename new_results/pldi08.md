# pldi08


## program
```c
int pldi08(int* a){
	int x = a[0];
	int y = a[1];
	iif_assume (x < 0);
	while (x < 0) {
		recordi(x, y);
		x = x + y;
		y++;
	}

	recordi(x, y);
	iif_assert (y >= 0);
	return 0;
}
```




## Selective Learning Results:


```
TRY SVM method ...
[1]|-->> SVM: -0.04876532077990978{0}  +  0.04877200731779901{1} >= -0.7566347672148074

WARNING: reaching max number of iterations
[2]|-->> SVM: 0.01479691639724479{0}  +  0.008337470077094622{1} >= -1.99275704275351
--------------------------------------------------------------------------------------------------------------------
Finish running svm for 2 times.
  Cannot divide by SVM perfectly.
TRY SVM-I method ...
[1]
TIMEOUT!
```

After set to a longer timeout
```
TRY SVM method ...
[1]|-->> SVM: -0.08382932444102498{0}  +  0.05075266849751664{1} >= -1.129336707731195
[2]|-->> SVM: -0.1873036230939953{0}  +  0.1147957680177549{1} >= -3.809454316174424

WARNING: reaching max number of iterations
[3]|-->> SVM: -0.1200997921332601{0}  +  -0.01117605014587753{1} >= 1.05321448110044
--------------------------------------------------------------------------------------------------------------------
Finish running svm for 3 times.
  Cannot divide by SVM perfectly.
TRY SVM-I method ...
[1]
TIMEOUT!
```

## Reason