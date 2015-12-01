<<<<<<< HEAD
# IIF experiment results:

This is the result of our implementation of the paper [An Invariant Inference Framework by
Active Learning and SVMs](./IIF.pdf) by Li Jiaying.

For you to run the experiments on your own machine, please follow the steps below to set up your experiment environment.

## Setup:

Dependencies:

* [libsvm](https://www.csie.ntu.edu.tw/~cjlin/libsvm/) remember to put {libsvm}/bin folder into $PATH
* [klee](https://klee.github.io/)

Optional dependencies:

* [libdwarf](http://pkgs.fedoraproject.org/repo/pkgs/libdwarf/) for C programs

**NOTE**: If you have difficulty in installing libdwarf, the following page may help you. 
[building hhvm dependencies]
(https://community.webfaction.com/questions/18567/building-hhvm-dependencies-libdwarf-not-finding-libelf)
```
wget 'http://www.prevanders.net/libdwarf-20140413.tar.gz'
tar -xzf libdwarf-20140413.tar.gz
cd dwarf-20140413/libdwarf
export CPPFLAGS="-I$HOME/include $CPPFLAGS"
export LDFLAGS="-L$HOME/lib $LDFLAGS"
./configure --prefix=$HOME
make
cp ./dwarf.h $HOME/include
cp ./libdwarf.h $HOME/include
cp ./libdwarf.a $HOME/lib
```

## Experiments results:
* [simple2](./simple2.html)
* [simple3](./simple3.html)
* [ex1](ex1.html)
* [f1a](f1a.html)
* [f2](f2.html)
* [substring1](substring1.html)
=======
# substring1

## source 
[Interpolants as Classifier](http://theory.stanford.edu/~aiken/publications/papers/cav12a.pdf) by Rahul Sharma, Aditya V. Nori, and Alex Aiken


## program
```c
int substring1(int* a) {
	int j = a[2];
	j = 0;
	int i = a[0];
	int k = a[1];

	iif_assume ((i >= 0) && (i <= k) && (k >= 0) && (k <= 100)); 
	while (i < k) {
		recordi(i, k, j);
		i++;	
		j++;
	}
	recordi(i, k, j);
	iif_assert(j < 101);
	return 0;
}
```




## Selective Learning Results:


```
TRY SVM method ...
[1][1]|-->> SVM: 0.02327864541825785{0}  +  0.006170230060452191{1}  +  -0.02327854503788141{2} >= -0.1330821244143965
[2]|-->> SVM: 0.04375718341654493{0}  +  -0.03047652676843789{1}  +  -0.04375274815613602{2} >= -3.535847132493362
[3]|-->> SVM: 0.04374740677814946{0}  +  -0.03046559658723145{1}  +  -0.04374740653447689{2} >= -3.534872587576281
[4]|-->> SVM: 0.08288511731815174{0}  +  -0.07806112694204881{1}  +  -0.08288514101945732{2} >= -7.816315276763142
[5]|-->> SVM: 0.08287289632757296{0}  +  -0.0780496227597693{1}  +  -0.08287293178025204{2} >= -7.815310793613884
[6]|-->> SVM: 0.08287289632757296{0}  +  -0.0780496227597693{1}  +  -0.08287293178025204{2} >= -7.815310793613884
--------------------------------------------------------------------------------------------------------------------
Finish running svm for 6 times.
  Hypothesis Invairant(Converged): {
		1.061797525692716{0}  +  -1{1}  +  -1.061797979925265{2} >= -100.1325889513753
  }
```

## Reason
>>>>>>> 087ef05fed1e56e1143f87de75b28bd9b1463654
