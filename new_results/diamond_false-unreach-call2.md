# diamond_false-unreach-call1

## source 
[sv-benchmark](http://sv-comp.sosy-lab.org/2015/benchmarks.php)

## program
```c
int func(int* a)
{
    int x = 0, y;
    y = a[0];
    iif_assume(y >= 0);
    while ((x < 99) && (y >= 0)) {
        recordi(x);
        if (y % 2 == 0) x++;
        else x += 2;

        if (y % 2 == 0) x += 2;
        else x -= 2;

        if (y % 2 == 0) x += 2;
        else x += 2;

        if (y % 2 == 0) x += 2;
        else x -= 2;

        if (y % 2 == 0) x += 2;
        else x += 2;

        if (y % 2 == 0) x += 2;
        else x -= 4;

        if (y % 2 == 0) x += 2;
        else x += 4;

        if (y % 2 == 0) x += 2;
        else x += 2;

        if (y % 2 == 0) x += 2;
        else x -= 4;

        if (y % 2 == 0) x += 2;
        else x -= 4;
    }
    recordi(x);
    iif_assert(x % 2 == y % 2);
    return 0;
}
```



##Selective Learning Results:

```
TRY SVM method ...
[1]
Too many states (>10240) in one execution. Stop here.
```