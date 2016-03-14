# PV1

## cfg-file
```c
names=x y
precondition=(x<0) || (y>0)
loopcondition=x<0
loop=x=x+y;
y++;
postcondition=y>0
```


## program
```c
# include "iif.h"
# include <iostream>
using namespace iif;

int loopFunction(int a[]) {
int x = a[0];
int y = a[1];

iif_assume((x<0) || (y>0));
while(x<0)
{
recordi(x, y);
x=x+y;
y++;
}
recordi(x, y);
iif_assert(y>0);
return 0;
}


int main(int argc, char** argv)
 {
iifContext context("../tmp/PV1.var", loopFunction, "loopFunction");
context.addLearner("linear");
return context.learn("../tmp/PV1");
}
```




## Selective Learning Results:
```c
lijiaying@workstation:~/Research/GitHub/IIF$ ./runtest.sh PV1
Converting the given config file to a valid cplusplus file...Generating CMakeLists file for further construction...[DONE]
Build the project...
-- Configuring done
-- Generating done
-- Build files have been written to: /home/lijiaying/Research/GitHub/IIF/build
Scanning dependencies of target PV1
[ 11%] Building CXX object CMakeFiles/PV1.dir/test/PV1.cpp.o
[ 22%] Building CXX object CMakeFiles/PV1.dir/src/config.cpp.o
[ 33%] Building CXX object CMakeFiles/PV1.dir/src/instrumentation.cpp.o
[ 44%] Building CXX object CMakeFiles/PV1.dir/src/linear_learner.cpp.o
[ 55%] Building CXX object CMakeFiles/PV1.dir/src/candidates.cpp.o
[ 66%] Building CXX object CMakeFiles/PV1.dir/src/equation.cpp.o
[ 77%] Building CXX object CMakeFiles/PV1.dir/src/iif.cpp.o
[ 88%] Building CXX object CMakeFiles/PV1.dir/src/svm_core.cpp.o
Linking CXX executable PV1
[100%] Built target PV1
Running the project to generate invariant candidiate...
Using LINEAR kernel...
[1]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(113,85)+|(18,90)+|(42,-176)-|(26,-122)-||(152,-24)-|(126,142)+|(87,-105)-|(-45,-70)+|(34,-167)-|(67,30)+|(82,-109)-|(-43,3)+|(-24,187)+|(-134,26)+|(72,-18)-|(-171,57)+|(-60,120)+|(-54,182)+|(145,-155)-|(-68,169)+}
(2) prepare training data... +[174|8] ==> [174+|8-]
(3) start training with mapping dimension {1}...|-->> 2.13734 + (-0.0340521)*x + (0.0381383)*y >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:        [FF]   [FAIL] neXt round 
[2]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(94,-70)-|(184,-19)-|(25,-62)-|(184,-68)-||(162,98)+|(40,-22)-|(122,59)+|(-21,-84)+|(71,9)+|(6,-57)-|(95,31)+|(-114,-176)+|(256,192)+|(-84,-147)+|(35,-27)-|(170,108)+|(114,50)+|(233,170)+|(-23,-85)+|(102,40)+}
(2) prepare training data... +[1005|7] ==> [1179+|15-]

WARNING: $$reaching max number of iterations
(3) start training with mapping dimension {1}...|-->> -1.05987 + (-0.0141482)*x + (-0.00253962)*y >= 0
(4) checking training traces. [97.73869346733667%] [FAIL] 
The problem is not linear separable by mapping 1.. Trying to project to a higher space 


WARNING: $$reaching max number of iterations
(5) start training with mapping dimension {2}...|-->> 0.636025 + (-0.0159897)*x + (0.0430042)*y + (0.000124707)*(x*x) + (0.000648999)*(x*y) + (0.000345906)*(y*y) >= 0
1 * x^2 + 3 * y^2 + 5 * xy + -128 * x + 345 * y + 5101 = (a0x + b0y + c0) (a1x + b1y + c1)	unSAT
(6) checking training traces. [100%] [PASS]
(7) check convergence:         sv[7,6] [FF]   [FAIL] neXt round 
[3]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [20] {(16,-7)-|(-63,-76)+|(42,186)+|(-118,22)+||(97,-138)-|(-109,52)+|(-77,146)+|(-98,171)+|(-143,60)+|(-149,-101)+|(-13,89)+|(-62,-48)+|(-197,115)+|(0,-154)-|(16,167)+|(16,-168)-|(33,-175)-|(-44,-126)+|(-117,111)+|(169,180)+}
(2) prepare training data... +[745|5] ==> [1924+|20-]

WARNING: $$reaching max number of iterations
(3) start training with mapping dimension {2}...|-->> 0.318694 + (-0.0473379)*x + (0.0783544)*y + (0.000463202)*(x*x) + (0.00151169)*(x*y) + (0.000481591)*(y*y) >= 0
1 * x^2 + 1 * y^2 + 3 * xy + -102 * x + 169 * y + 689 = (a0x + b0y + c0) (a1x + b1y + c1)	unSAT
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[7,7] [FF]   [FAIL] neXt round 
[4]Linear SVM------------------------{2}------------------------------------------------------------------------------------
(1) execute programs... [20] {(174,-141)-|(105,-31)-|(-122,-194)+|(-61,8)+||(139,64)+|(108,-75)-|(-48,-82)+|(77,28)+|(-168,-123)+|(147,49)+|(-84,-38)+|(154,149)+|(60,-18)-|(-105,144)+|(-108,-136)+|(196,-62)-|(-77,100)+|(180,74)+|(179,-8)-|(-118,117)+}
(2) prepare training data... +[1183|6] ==> [3107+|26-]

WARNING: $$reaching max number of iterations
(3) start training with mapping dimension {2}...|-->> 0.305566 + (-0.0452692)*x + (0.0805544)*y + (0.000262748)*(x*x) + (0.00137277)*(x*y) + (0.000563055)*(y*y) >= 0
1 * x^2 + 2 * y^2 + 5 * xy + -172 * x + 307 * y + 1163 = (a0x + b0y + c0) (a1x + b1y + c1)	unSAT
(4) checking training traces. [99.7446536865624%] [FAIL] 
The problem is not linear separable by mapping 2.. Trying to project to a higher space 


WARNING: $$reaching max number of iterations
(5) start training with mapping dimension {3}...|-->> 0.484771 + (-0.000214419)*x + (0.000269608)*y + (0.00228754)*(x*x) + (0.00362742)*(x*y) + (0.00328375)*(y*y) + (-8.32075e-05)*(x*x*x) + (0.000421826)*(x*x*y) + (-0.000537056)*(x*y*y) + (0.000159923)*(y*y*y) >= 0
-1 * x^3 + 2 * y^3 + 5 * x^2y + -6 * xy^2 + 27 * x^2 + 39 * y^2 + 44 * xy + -3 * x + 3 * y + 5827 = (a0x + b0y + c0) (a1x + b1y + c1) (a2x + b2y + c2)	unSAT
(6) checking training traces. [100%] [PASS]
(7) check convergence:         sv[6,7] [FF]   [FAIL] neXt round 
[5]Linear SVM------------------------{3}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-145,190)+|(-159,7)+|(-93,192)+|(-166,13)+||(-59,-147)+|(-139,57)+|(16,-113)-|(79,-52)-|(69,174)+|(-36,-167)+|(-90,-40)+|(45,34)+|(-68,24)+|(-93,-16)+|(-185,62)+|(-100,-57)+|(51,15)+|(150,-169)-|(6,-144)-|(44,147)+}
(2) prepare training data... +[921|4] ==> [4028+|30-]

WARNING: $$reaching max number of iterations
(3) start training with mapping dimension {3}...|-->> 0.670619 + (-0.000207252)*x + (0.000263836)*y + (0.00131059)*(x*x) + (0.00313433)*(x*y) + (0.00239591)*(y*y) + (-7.34627e-05)*(x*x*x) + (0.000322611)*(x*x*y) + (-0.000346288)*(x*y*y) + (7.90479e-05)*(y*y*y) >= 0
-1 * x^3 + 1 * y^3 + 4 * x^2y + -5 * xy^2 + 18 * x^2 + 33 * y^2 + 43 * xy + -3 * x + 4 * y + 9129 = (a0x + b0y + c0) (a1x + b1y + c1) (a2x + b2y + c2)	unSAT
(4) checking training traces. [98.0039428289798%] [FAIL] 
The problem is not linear separable by mapping 3.. Trying to project to a higher space 
--------------------------------------------------------------------------------------------------------------------
Cannot divide by SVM perfectly.
save to file succeed.
can not separate using default paramater
try more parameters to get a perfect classifier
```