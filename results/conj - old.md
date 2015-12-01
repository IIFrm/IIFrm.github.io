# conj


## program
```c
int conj(int* a)
{
	int x;
	x = a[0];
	iif_assume((x >= 0) && (x <= 50));
	while (nondet()) {
		recordi(x);
		if (x >= 50) {
			x --;
		}
		else if (x <= 0) {
			x ++;
		}
		else {
			x += rand() %3 - 1;
		}
	}
	recordi(x);
	iif_assert((x >= 0) && (x <= 50));
	return 0;
}
```



##Selective Learning Results:

```
TRY SVM method ...

WARNING: reaching max number of iterations
[1]|-->> SVM: 0.1666666666860692{0} >= 3.999999998137355
--------------------------------------------------------------------------------------------------------------------
Finish running svm for 1 times.
  Cannot divide by SVM perfectly.
TRY SVM-I method ...
[1]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     -0.05555555555555555{0} >= -2.666666666666667 
	 |  /\ 0.1538461538461539{0} >= -0.6923076923076923 
	 ------------------------------------------------------
[2]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     -0.1176470588235294{0} >= -6.764705882352942 
	 |  /\ 0.3333333333333334{0} >= -0.3333333333333333 
	 ------------------------------------------------------
[3]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     0.5{0} >= -1 
	 |  /\ -0.6666666666666501{0} >= -33.66666666666583 
	 ------------------------------------------------------
[4]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     -2{0} >= -101 
	 |  /\ 2{0} >= -1 
	 ------------------------------------------------------
[5]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     -1.999999999998579{0} >= -100.9999999999281 
	 |  /\ 2{0} >= -1 
	 ------------------------------------------------------
[6]|-->> SVM-I:  
	 ------------------------------------------------------ 
	 |     -1.999999999999943{0} >= -100.9999999999973 
	 |  /\ 2{0} >= -1 
	 ------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------
Finish running svm_i for 6 times.
  Hypothesis Invairant(Converged): { 
	 ------------------------------------------------------ 
	 |     -1{0} >= -50.50000000000007 
	 |  /\ 2{0} >= -1 
	 ------------------------------------------------------
```