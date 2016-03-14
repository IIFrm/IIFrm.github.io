# conj

## cfg-file
```c
names= x
precondition=(x>=0) && (x<=50)
beforeloop=int loop_times = 10;
loopcondition=loop_times-- > 0
loop= if (x>50) x++;
		if (x == 0) {
			x ++;
		} else x--;
postcondition=(x>=0) && (x<=50)
```

## program
```c
# include "iif.h"
# include <iostream>
using namespace iif;

int loopFunction(int a[]) {
int x = a[0];

int loop_times = 10;
iif_assume((x>=0) && (x<=50));
while(loop_times-- > 0)
{
recordi(x);
 if (x>50) x++;
		if (x == 0) {
			x ++;
		} else x--;
}
recordi(x);
iif_assert((x>=0) && (x<=50));
return 0;
}


int main(int argc, char** argv)
 {
iifContext context("../tmp/conj.var", loopFunction, "loopFunction");
context.addLearner("linear");
return context.learn("../tmp/conj");
}
```



## Selective Learning Results:

```
lijiaying@workstation:~/Research/GitHub/IIF$ ./runtest.sh conj
Converting the given config file to a valid cplusplus file...Generating CMakeLists file for further construction...[DONE]
Build the project...
-- Configuring done
-- Generating done
-- Build files have been written to: /home/lijiaying/Research/GitHub/IIF/build
Scanning dependencies of target conj
[ 11%] Building CXX object CMakeFiles/conj.dir/test/conj.cpp.o
[ 22%] Building CXX object CMakeFiles/conj.dir/src/config.cpp.o
[ 33%] Building CXX object CMakeFiles/conj.dir/src/instrumentation.cpp.o
[ 44%] Building CXX object CMakeFiles/conj.dir/src/linear_learner.cpp.o
[ 55%] Building CXX object CMakeFiles/conj.dir/src/candidates.cpp.o
[ 66%] Building CXX object CMakeFiles/conj.dir/src/equation.cpp.o
[ 77%] Building CXX object CMakeFiles/conj.dir/src/iif.cpp.o
[ 88%] Building CXX object CMakeFiles/conj.dir/src/svm_core.cpp.o
Linking CXX executable conj
[100%] Built target conj
Running the project to generate invariant candidiate...
Using LINEAR kernel...
[1]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [10] {(33)+|(116)-||(-17)-|(124)-|(106)-|(-160)-|(61)-|(-163)-|(71)-|(103)-}
(2) prepare training data... +[11|31] ==> [11+|31-]

WARNING: $$reaching max number of iterations
(3) start training with mapping dimension {1}...|-->> -0.32 + (0.04)*x >= 0
(4) checking training traces. [78.57142857142857%] [FAIL] 
The problem is not linear separable by mapping 1.. Trying to project to a higher space 

(5) start training with mapping dimension {2}...|-->> 0.481687 + (0.0628258)*x + (-0.00142786)*(x*x) >= 0
-1 * x^2 + 44 * x + 338 = (a0x + b0) (a1x + b1)	unSAT
(6) checking training traces. [100%] [PASS]
(7) check convergence:         sv[3,4] [FF]   [FAIL] neXt round 
[2]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-102)-|(104)-||(-7)-|(-6)-|(50)+|(51)-|(50)+|(50)+|(52)-|(50)+}
(2) prepare training data... +[11|25] ==> [22+|56-]
(3) start training with mapping dimension {2}...|-->> 9.92411 + (1.60634)*x + (-0.0356964)*(x*x) >= 0
-1 * x^2 + 45 * x + 279 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[3]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-68)-|(-7)-||(52)-|(-5)-|(-7)-|(50)+|(50)+|(-5)-|(52)-|(52)-}
(2) prepare training data... +[0|12] ==> [22+|68-]
(3) start training with mapping dimension {2}...|-->> 8.26909 + (1.67189)*x + (-0.0363455)*(x*x) >= 0
-1 * x^2 + 46 * x + 228 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[4]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-40)-|(-196)-||(-4)-|(52)-|(50)+|(52)-|(-5)-|(51)-|(-6)-|(-5)-}
(2) prepare training data... +[0|23] ==> [22+|91-]
(3) start training with mapping dimension {2}...|-->> 6.55278 + (1.73987)*x + (-0.0370185)*(x*x) >= 0
-1 * x^2 + 47 * x + 178 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[5]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-91)-|(62)-||(-5)-|(52)-|(51)-|(-5)-|(50)+|(50)+|(-4)-|(51)-}
(2) prepare training data... +[0|12] ==> [22+|103-]
(3) start training with mapping dimension {2}...|-->> 6.55278 + (1.73987)*x + (-0.0370185)*(x*x) >= 0
-1 * x^2 + 47 * x + 178 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FT]  [FAIL] neXt round 
[6]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [18] {(110)-|(-11)-||(52)-|(-4)-|(52)-|(-3)-|(-3)-|(50)+|(50)+|(52)-|(52)-|(50)+|(-3)-|(52)-|(-4)-|(-5)-|(-5)-|(-3)-}
(2) prepare training data... +[0|2] ==> [22+|105-]
(3) start training with mapping dimension {2}...|-->> 4.7717 + (1.81042)*x + (-0.037717)*(x*x) >= 0
-1 * x^2 + 48 * x + 127 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [TF]   [FAIL] neXt round 
[7]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-99)-|(-55)-||(50)+|(-2)-|(51)-|(-3)-|(-4)-|(-3)-|(-4)-|(51)-}
(2) prepare training data... +[0|12] ==> [22+|117-]
(3) start training with mapping dimension {2}...|-->> 2.92212 + (1.88367)*x + (-0.0384423)*(x*x) >= 0
-1 * x^2 + 49 * x + 77 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[8]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(185)-|(48)+||(-2)-|(-3)-|(50)+|(-3)-|(52)-|(50)+|(-1)-|(-3)-}
(2) prepare training data... +[2|2] ==> [24+|119-]
(3) start training with mapping dimension {2}...|-->> 1 + (1.9598)*x + (-0.0391961)*(x*x) >= 0
-1 * x^2 + 50 * x + 26 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[9]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(71)-|(53)-||(52)-|(1)+|(52)-|(-1)-|(0)+|(1)+|(0)+|(-1)-}
(2) prepare training data... +[2|1] ==> [26+|120-]
(3) start training with mapping dimension {2}...|-->> 0.999704 + (1.96049)*x + (-0.0392098)*(x*x) >= 0
-1 * x^2 + 50 * x + 26 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[10]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [10] {(-153)-|(22)+||(52)-|(50)+|(52)-|(1)+|(50)+|(-1)-|(0)+|(1)+}
(2) prepare training data... +[11|7] ==> [37+|127-]
(3) start training with mapping dimension {2}...|-->> 0.99971 + (1.9605)*x + (-0.0392099)*(x*x) >= 0
-1 * x^2 + 50 * x + 26 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FT]  [FAIL] neXt round 
[11]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [18] {(14)+|(198)-||(50)+|(50)+|(0)+|(1)+|(50)+|(1)+|(50)+|(-1)-|(-1)-|(0)+|(50)+|(52)-|(50)+|(-1)-|(0)+|(0)+}
(2) prepare training data... +[8|1] ==> [45+|128-]
(3) start training with mapping dimension {2}...|-->> 0.999665 + (1.96046)*x + (-0.039209)*(x*x) >= 0
-1 * x^2 + 50 * x + 26 = (a0x + b0) (a1x + b1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [TT]  [SUCCESS] rounding off
--------------------------------------------------------------------------------------------------------------------
--->: 26 + (50)*x + (-1)*(x*x) >= 0[-0,52]
Candidates size = 1
Hypothesis Invariant(Converged): {
	0.99971 + (1.9605)*x + (-0.0392099)*(x*x) >= 0
}
save to file succeed.
Invariant file is located at tmp/conj.inv
26 + (50)*x + (-1)*(x*x) >= 0
Generating a new config file contains the invariant candidate...[Done]
Generating three C files to do the verification by KLEE[Done]
Compiling the C files and Run KLEE...
Compiling the C files and Run KLEE...1
	KLEE: output directory is "/home/lijiaying/Research/GitHub/IIF/tmp/conj_klee1/klee-out-0"
KLEE: ERROR: /home/lijiaying/Research/GitHub/IIF/tmp/conj_klee1/conj_klee1.c:8: invalid klee_assume call (provably false)
	KLEE: NOTE: now ignoring this error at this location
	->>Function<klee_assertion> $$filename:failAssert00001.smt2

	KLEE: done: total instructions = 49
	KLEE: done: completed paths = 2
	KLEE: done: generated tests = 2
	processing failAssert00001.smt2 --> unsat
	Compiling the C files and Run KLEE...
	Compiling the C files and Run KLEE...1
	KLEE: output directory is "/home/lijiaying/Research/GitHub/IIF/tmp/conj_klee2/klee-out-0"
	->>Function<klee_assertion> $$filename:failAssert00001.smt2
	->>Function<klee_assertion> $$filename:failAssert00002.smt2
	->>Function<klee_assertion> $$filename:failAssert00003.smt2
	KLEE: ERROR: /home/lijiaying/Research/GitHub/IIF/tmp/conj_klee2/conj_klee2.c:14: ASSERTION FAIL: 26 + (50)*x + (-1)*(x*x) >= 0
	KLEE: NOTE: now ignoring this error at this location

	KLEE: done: total instructions = 122
	KLEE: done: completed paths = 4
	KLEE: done: generated tests = 4
	processing failAssert00001.smt2 --> sat
	>>>NOT A VALID INVARIVANT...Reason: Property II (invariant && loopcondition =S=> invariant) FAILED. stop here...
```