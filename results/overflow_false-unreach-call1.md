# diamond_false-unreach-call1

## source 
[sv-benchmark](http://sv-comp.sosy-lab.org/2015/benchmarks.php)

## program
```c
int func(int* a)
{
    int x;
    x = a[0];
    iif_assume(x % 2 == 0);
    while (x >= 10) {
        recordi(x);
        x += 2;
    }
    recordi(x);
    iif_assert(x % 2 == 0);
    return 0;
}
```



##Selective Learning Results:

```
TRY SVM method ...
[1]
Too many states (>10240) in one execution. Stop here.
```

## Reason