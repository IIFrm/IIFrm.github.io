# Invariant Inference Framework:

This is the result of our implementation of the paper [An Invariant Inference Framework by
Active Learning and SVMs](http://iifrm.github.io/PDF/AnInvariantInferenceFrameworkbyActiveLearningandSVMs.pdf) by Li Jiaying.

## Documentation
* [HTML](http://iifrm.github.io/doc/html/index.html) outdated
* [PDF](http://iifrm.github.io/doc/latex/refman.pdf) outdated

## Installation
For you to run the experiments on your own machine, please follow the steps below to set up your experiment environment.

#### pre-requirement
* [git](https://git-scm.com/downloads)
* [cmake](https://cmake.org/) version 2.8 or later
* [clang](http://clang.llvm.org/get_started.html)
* "make" and otherLLVM essential building tools, you can add if needed
* [z3](https://github.com/Z3Prover/z3) the installation folder should be "/usr" or "/usr/local", otherwise you should modify $Z3_ROOT in cmake.base in the project directory so cmake can find it. 
* [KLEE](https://klee.github.io/) only test llvm2.9 yet, so try to build KLEE by [build-llvm29](http://klee.github.io/build-llvm29/)


#### patch KLEE source code
This modification aims at generating smt2 file for each path condition.
The principle is to add a new method call``Massert'', and in its method handler we output the path condition to files.

* [download patch file](http://lijiaying.github.io/content/iif/klee_patch.tar.bz2) last update at 12:47pm on 10/03/2016

##### Note:
+ The patch files are tested successfully if you use them just between KLEE configure step and KLEE make step. (between step 5 and 6 in [build-llvm29](http://klee.github.io/build-llvm29/))
+ Unpack the bz2 file, and then you can find "klee.patch" which is the patch file for whole KLEE project, ignore any warning during your patching process.
```
$ls
klee klee.patch filepatch
$cd klee
$patch -p1 <../klee.patch
```
+ If the last step does not work, you can patch each file by yourself. The patches for affected files are located in "klee_patch/filepatch" folder.
+ After the patch, you can continue to proceed KLEE make step (step 6 in [build-llvm29](http://klee.github.io/build-llvm29/))


#### Get IIF
```
git clone git@github.com:IIFrm/IIF.git
```

#### Test IIF
```
cd IIF
mkdir build
./runtest test
./runtest conj
```

#### Notes
+ The folder 'backup/' and 'doc/' are not used currently.
+ The 'test', 'conj' are filenames located in 'cfg' folder without extension.

#### Add a new test
- Follow the format such as 'cfg/test.cfg', put your test case in 'cfg' folder.
- And then try to run the system and see what happens.



<!--#Optional dependencies:

#* [libdwarf](http://pkgs.fedoraproject.org/repo/pkgs/libdwarf/) for C programs

#	**NOTE**: If you have difficulty in installing libdwarf, the following page may help you. 
#	[building hhvm dependencies]
#	(https://community.webfaction.com/questions/18567/building-hhvm-dependencies-libdwarf-not-finding-libelf)
#	```
#	wget 'http://www.prevanders.net/libdwarf-20140413.tar.gz'
#	tar -xzf libdwarf-20140413.tar.gz
#	cd dwarf-20140413/libdwarf
#	export CPPFLAGS="-I$HOME/include $CPPFLAGS"
#	export LDFLAGS="-L$HOME/lib $LDFLAGS"
#	./configure --prefix=$HOME
#	make
#	cp ./dwarf.h $HOME/include
#	cp ./libdwarf.h $HOME/include
#	cp ./libdwarf.a $HOME/lib
#	```
-->

## Experiments results:[OLD]
* [conj](http://iifrm.github.io/results/conj.html)
* >[conj_good](http://iifrm.github.io/results/conj_good.html)
* >[conj_bad](http://iifrm.github.io/results/conj_bad.html)
* [diamond_false-unreach-call1](http://iifrm.github.io/results/diamond_false-unreach-call1.html)
* [diamond_false-unreach-call2](http://iifrm.github.io/results/diamond_false-unreach-call2.html)
* [overflow_false-unreach-call1](http://iifrm.github.io/results/overflow_false-unreach-call1.html)
* [ex1](http://iifrm.github.io/results/ex1.html)
* [f1a](http://iifrm.github.io/results/f1a.html)
* [f2](http://iifrm.github.io/results/f2.html)
* [f4](http://iifrm.github.io/results/f4.html)
* [pldi08](http://iifrm.github.io/results/pldi08.html)
* [substring1](http://iifrm.github.io/results/substring1.html)
* [f3](http://iifrm.github.io/results/f3.html)


## Experiments results:[NEW]
* [conj](http://iifrm.github.io/new_results/conj.html)
* [test](http://iifrm.github.io/new_results/test.html)
* [PV1](http://iifrm.github.io/new_results/PV1.html)
* [synergy.foo](http://iifrm.github.io/new_results/synergy.foo.html)
* [V2](http://iifrm.github.io/new_results/V2.html)


<!-- 
* [pldi08](http://iifrm.github.io/new_results/pldi08.html)
* [substring1](http://iifrm.github.io/new_results/substring1.html)
* [f3](http://iifrm.github.io/new_results/f3.html)
-->