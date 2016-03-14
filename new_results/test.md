# test

## cfg-file
```c
names= xa ya
precondition=xa + ya > 0
loopcondition=xa > 0
loop=xa--; 
ya++;
postcondition=ya >= 0
```

## program
```c
# include "iif.h"
# include <iostream>
using namespace iif;

int loopFunction(int a[]) {
int xa = a[0];
int ya = a[1];

iif_assume(xa + ya > 0);
while(xa > 0)
{
recordi(xa, ya);
xa--; 
ya++;
}
recordi(xa, ya);
iif_assert(ya >= 0);
return 0;
}


int main(int argc, char** argv)
 {
iifContext context("../tmp/test.var", loopFunction, "loopFunction");
context.addLearner("linear");
return context.learn("../tmp/test");
}

```

## Selective Learning Results:

```
lijiaying@workstation:~/Research/GitHub/IIF$ ./runtest.sh test
Converting the given config file to a valid cplusplus file...Generating CMakeLists file for further construction...[DONE]
Build the project...
-- Configuring done
-- Generating done
-- Build files have been written to: /home/lijiaying/Research/GitHub/IIF/build
Scanning dependencies of target test
[ 11%] Building CXX object CMakeFiles/test.dir/test/test.cpp.o
[ 22%] Building CXX object CMakeFiles/test.dir/src/config.cpp.o
[ 33%] Building CXX object CMakeFiles/test.dir/src/instrumentation.cpp.o
[ 44%] Building CXX object CMakeFiles/test.dir/src/linear_learner.cpp.o
[ 55%] Building CXX object CMakeFiles/test.dir/src/candidates.cpp.o
[ 66%] Building CXX object CMakeFiles/test.dir/src/equation.cpp.o
[ 77%] Building CXX object CMakeFiles/test.dir/src/iif.cpp.o
[ 88%] Building CXX object CMakeFiles/test.dir/src/svm_core.cpp.o
Linking CXX executable test
[100%] Built target test
Running the project to generate invariant candidiate...
Using LINEAR kernel...
[1]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-5,199)+|(199,-153)+|(190,-29)+|(133,-116)+||(-89,132)+|(-145,-117)-|(54,18)+|(-141,-30)-|(166,47)+|(-88,179)+|(13,115)+|(35,28)+|(100,45)+|(-23,-29)-|(22,11)+|(126,-184)-|(82,124)+|(-136,144)+|(-33,197)+|(-173,78)?}
(2) prepare training data... +[1009|130] ==> [1009+|130-]
(3) start training with mapping dimension {1}...|-->> 0.606943 + (0.0302999)*xa + (0.0313519)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:        [FF]   [FAIL] neXt round 
[2]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-200,-45)-|(161,128)+|(174,-180)-|(-103,139)+||(26,-48)-|(109,-131)-|(-88,66)?|(-83,61)?|(34,-55)-|(-35,15)?|(-35,13)?|(-25,3)?|(152,-173)-|(143,-163)-|(-42,20)?|(63,-85)-|(24,-45)-|(-165,143)?|(-183,163)?|(139,-160)-}
(2) prepare training data... +[163|583] ==> [1172+|713-]
(3) start training with mapping dimension {1}...|-->> -0.353355 + (0.104228)*xa + (0.107835)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[3,3] [FF]   [FAIL] neXt round 
[3]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(135,-188)-|(-106,-35)-|(91,133)+|(-85,-91)-||(88,-84)+|(-2,4)+|(-98,102)+|(-86,90)+|(53,-51)+|(-150,153)+|(-72,75)+|(104,-100)+|(-19,21)+|(-16,19)+|(-110,114)+|(47,-45)+|(-40,42)+|(140,-137)+|(52,-50)+|(26,-23)+}
(2) prepare training data... +[401|138] ==> [1573+|851-]
(3) start training with mapping dimension {1}...|-->> 0.5 + (0.25)*xa + (0.25)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[15,3] [FF]   [FAIL] neXt round 
[4]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-159,162)+|(166,4)+|(-128,-59)-|(182,-70)+||(57,-58)-|(28,-31)-|(101,-103)-|(-37,35)?|(-34,31)?|(51,-53)-|(-143,141)?|(-123,121)?|(138,-140)-|(51,-52)-|(137,-138)-|(76,-79)-|(-63,60)?|(-56,53)?|(136,-138)-|(-6,3)?}
(2) prepare training data... +[351|355] ==> [1924+|1206-]
(3) start training with mapping dimension {1}...|-->> -0.332667 + (0.666334)*xa + (0.666334)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[12,15] [FF]   [FAIL] neXt round 
[5]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-148,85)?|(-68,190)+|(-44,101)+|(-96,128)+||(-14,14)?|(47,-47)?|(-186,188)+|(-148,147)?|(89,-90)-|(81,-80)+|(-146,148)+|(-107,107)?|(93,-94)-|(194,-193)+|(-1,1)?|(-52,53)+|(-12,14)+|(-29,30)+|(-51,52)+|(125,-123)+}
(2) prepare training data... +[276|0] ==> [2200+|1206-]
(3) start training with mapping dimension {1}...|-->> -0.000672433 + (0.999888)*xa + (0.999884)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[11,12] [FF]   [FAIL] neXt round 
[6]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(59,121)+|(194,-167)+|(-5,123)+|(133,39)+||(-175,175)?|(-56,57)+|(48,-49)-|(-194,193)?|(-140,141)+|(153,-152)+|(-180,179)?|(162,-161)+|(-111,110)?|(57,-56)+|(-148,148)?|(119,-118)+|(-34,34)?|(-185,185)?|(185,-185)?|(-6,6)?}
(2) prepare training data... +[392|0] ==> [2592+|1206-]
(3) start training with mapping dimension {1}...|-->> 0.000790336 + (0.999787)*xa + (0.99979)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,11] [FF]   [FAIL] neXt round 
[7]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(161,-180)-|(139,-193)-|(168,125)+|(175,-86)+||(-156,155)?|(51,-51)?|(178,-179)-|(125,-126)-|(195,-197)-|(-131,131)?|(163,-163)?|(149,-150)-|(-87,85)?|(-39,37)?|(-124,122)?|(30,-32)-|(-90,88)?|(-170,168)?|(43,-44)-|(86,-87)-}
(2) prepare training data... +[345|400] ==> [2937+|1606-]
(3) start training with mapping dimension {1}...|-->> 0.000787438 + (0.999788)*xa + (0.999791)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[12,4] [FF]   [FAIL] neXt round 
[8]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(16,167)+|(-76,197)+|(161,158)+|(24,88)+||(151,-153)-|(162,-164)-|(76,-78)-|(-82,82)?|(-122,121)?|(-91,90)?|(150,-150)?|(-145,143)?|(134,-136)-|(117,-118)-|(-102,102)?|(95,-95)?|(193,-195)-|(182,-184)-|(137,-138)-|(198,-199)-}
(2) prepare training data... +[180|20] ==> [3117+|1626-]
(3) start training with mapping dimension {1}...|-->> (1)*xa + (1)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,12] [FF]   [FAIL] neXt round 
[9]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-60,-79)-|(-169,187)+|(-105,11)?|(183,-153)+||(63,-64)-|(87,-87)?|(120,-121)-|(85,-85)?|(28,-28)?|(-187,188)+|(-67,67)?|(155,-154)+|(117,-117)?|(-99,99)?|(163,-162)+|(-120,121)+|(190,-189)+|(131,-131)?|(93,-92)+|(157,-157)?}
(2) prepare training data... +[187|1] ==> [3304+|1627-]
(3) start training with mapping dimension {1}...|-->> 9.66338e-12 + (1)*xa + (1)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[6,4] [FF]   [FAIL] neXt round 
[10]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-150,-119)-|(-177,162)?|(-80,72)?|(-139,-193)-||(-192,191)?|(43,-44)-|(50,-51)-|(-153,152)?|(-106,104)?|(183,-183)?|(-147,146)?|(78,-78)?|(-69,67)?|(77,-78)-|(44,-45)-|(153,-154)-|(-125,125)?|(44,-44)?|(-109,109)?|(-111,109)?}
(2) prepare training data... +[0|2] ==> [3304+|1629-]
(3) start training with mapping dimension {1}...|-->> 9.66338e-12 + (1)*xa + (1)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[6,6] [FT]  [FAIL] neXt round 
[11]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [36] {(-42,115)+|(-12,160)+|(-131,-132)-|(-177,-58)-||(97,-98)-|(96,-98)-|(-191,189)?|(-134,132)?|(-167,167)?|(184,-184)?|(-109,109)?|(130,-132)-|(-95,95)?|(-92,91)?|(-112,110)?|(41,-41)?|(-197,196)?|(127,-129)-|(151,-153)-|(192,-192)?|(58,-59)-|(-7,7)?|(64,-64)?|(-155,155)?|(-99,97)?|(-63,63)?|(-11,9)?|(-98,96)?|(-169,168)?|(-41,41)?|(-71,71)?|(37,-37)?|(93,-93)?|(110,-110)?|(35,-35)?|(-161,160)?}
(2) prepare training data... +[2|2] ==> [3306+|1631-]
(3) start training with mapping dimension {1}...|-->> (1)*xa + (1)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,6] [TF]   [FAIL] neXt round 
[12]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-100,-129)-|(-108,-10)-|(-185,-179)-|(156,30)+||(-51,50)?|(-116,117)+|(-12,12)?|(-7,8)+|(151,-152)-|(-131,131)?|(132,-131)+|(55,-54)+|(117,-117)?|(-151,150)?|(-12,13)+|(129,-128)+|(131,-130)+|(85,-85)?|(-22,23)+|(65,-66)-}
(2) prepare training data... +[161|3] ==> [3467+|1634-]
(3) start training with mapping dimension {1}...|-->> (1)*xa + (1)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,4] [FF]   [FAIL] neXt round 
[13]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(111,-52)+|(56,-29)+|(180,73)+|(58,-81)-||(60,-59)+|(110,-109)+|(-152,152)?|(153,-152)+|(156,-156)?|(-71,71)?|(91,-92)-|(-81,81)?|(166,-165)+|(-77,78)+|(70,-69)+|(200,-199)+|(-36,36)?|(130,-129)+|(100,-99)+|(-86,85)?}
(2) prepare training data... +[300|59] ==> [3767+|1693-]
(3) start training with mapping dimension {1}...|-->> xa + ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[2,4] [FF]   [FAIL] neXt round 
[14]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(1,28)+|(31,-129)-|(-173,159)?|(-183,99)?||(138,-139)-|(139,-138)+|(-54,53)?|(133,-133)?|(-167,166)?|(153,-152)+|(23,-24)-|(182,-181)+|(34,-33)+|(33,-34)-|(-187,187)?|(22,-21)+|(164,-165)-|(-157,158)+|(-200,200)?|(-184,184)?}
(2) prepare training data... +[3|32] ==> [3770+|1725-]
(3) start training with mapping dimension {1}...|-->> -0.000212634 + (0.999785)*xa + (0.999787)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[5,2] [FF]   [FAIL] neXt round 
[15]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-123,-16)-|(87,9)+|(-30,-77)-|(-49,120)+||(-13,13)?|(-193,194)+|(80,-80)?|(-187,188)+|(136,-137)-|(184,-183)+|(109,-109)?|(92,-92)?|(-196,196)?|(-110,110)?|(-145,145)?|(-54,55)+|(-186,186)?|(-77,77)?|(43,-43)?|(-177,177)?}
(2) prepare training data... +[91|2] ==> [3861+|1727-]
(3) start training with mapping dimension {1}...|-->> 0.00065016 + (0.999786)*xa + (0.999788)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[5,5] [FF]   [FAIL] neXt round 
[16]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(-158,186)+|(42,99)+|(131,-140)-|(33,-31)+||(-102,102)?|(29,-30)-|(91,-91)?|(180,-181)-|(156,-158)-|(62,-62)?|(-198,197)?|(-40,40)?|(198,-199)-|(-83,82)?|(25,-27)-|(137,-137)?|(-62,61)?|(88,-89)-|(-62,62)?|(61,-61)?}
(2) prepare training data... +[44|132] ==> [3905+|1859-]
(3) start training with mapping dimension {1}...|-->> 0.000662419 + (0.999782)*xa + (0.999784)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,5] [FF]   [FAIL] neXt round 
[17]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [20] {(38,21)+|(-141,-163)-|(194,184)+|(91,44)+||(23,-25)-|(67,-67)?|(134,-134)?|(-90,90)?|(-2,1)?|(10,-11)-|(-198,196)?|(-103,101)?|(-181,181)?|(116,-117)-|(-159,159)?|(-142,142)?|(-65,63)?|(-95,94)?|(-98,98)?|(31,-33)-}
(2) prepare training data... +[287|1] ==> [4192+|1860-]
(3) start training with mapping dimension {1}...|-->> 0.000662419 + (0.999782)*xa + (0.999784)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,4] [FT]  [FAIL] neXt round 
[18]Linear SVM------------------------{1}------------------------------------------------------------------------------------
(1) execute programs... [36] {(153,17)+|(-188,-113)-|(48,-107)-|(2,139)+||(-78,77)?|(-17,17)?|(31,-31)?|(56,-57)-|(-68,68)?|(85,-87)-|(-155,155)?|(-78,76)?|(-113,112)?|(-120,118)?|(-199,198)?|(-198,197)?|(-131,131)?|(-13,13)?|(-66,64)?|(-159,158)?|(-133,132)?|(174,-175)-|(-187,186)?|(108,-109)-|(-50,50)?|(77,-79)-|(186,-187)-|(77,-78)-|(-137,135)?|(143,-143)?|(78,-79)-|(9,-9)?|(168,-169)-|(-141,141)?|(-24,22)?|(173,-175)-}
(2) prepare training data... +[0|50] ==> [4192+|1910-]
(3) start training with mapping dimension {1}...|-->> 0.000662419 + (0.999782)*xa + (0.999784)*ya >= 0
(4) checking training traces. [100%] [PASS]
(5) check convergence:         sv[4,4] [TT]  [SUCCESS] rounding off
--------------------------------------------------------------------------------------------------------------------
--->: 1 + xa + ya >= 0[-0,2]
Candidates size = 1
Hypothesis Invariant(Converged): {
    0.000662419 + (0.999782)*xa + (0.999784)*ya >= 0
}
save to file succeed.
Invariant file is located at tmp/test.inv
1 + xa + ya >= 0
Generating a new config file contains the invariant candidate...[Done]
Generating three C files to do the verification by KLEE[Done]
Compiling the C files and Run KLEE...
Compiling the C files and Run KLEE...1
KLEE: output directory is "/home/lijiaying/Research/GitHub/IIF/tmp/test_klee1/klee-out-0"
->>Function<klee_assertion> $$filename:failAssert00001.smt2
KLEE: ERROR: /home/lijiaying/Research/GitHub/IIF/tmp/test_klee1/test_klee1.c:11: ASSERTION FAIL: 1 + xa + ya >= 0
KLEE: NOTE: now ignoring this error at this location

KLEE: done: total instructions = 34
KLEE: done: completed paths = 2
KLEE: done: generated tests = 2
processing failAssert00001.smt2 --> sat
>>>NOT A VALID INVARIVANT...Reason: Property I (precondition ==> invariant) FAILED. stop here...

```
