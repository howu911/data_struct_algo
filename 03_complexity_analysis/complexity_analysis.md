# 大O复杂度表示法

所有代码的执行时间 T(n) 与每行代码的执行次数 f(n) 成正比。我们可以把这个规律总结成一个公式。

![image-20241117215127780](https://raw.githubusercontent.com/howu911/picx-images-hosting/master/data_struct_algo202411172151799.png)

以下面例子为例：

```c
 int cal(int n) {
   int sum = 0;
   int i = 1;
   int j = 1;
   for (; i <= n; ++i) {
     j = 1;
     for (; j <= n; ++j) {
       sum = sum +  i * j;
     }
   }
 }
```

第 2、3、4 行代码，每行都需要 1 个 unit_time 的执行时间，第 5、6 行代码循环执行了 n 遍，需要 2n * unit_time 的执行时间，第 7、8 行代码循环执行了 n2遍，所以需要 2n2 * unit_time 的执行时间。所以，整段代码总的执行时间 T(n) = (2n2+2n+3)*unit_time。

这就是大 O 时间复杂度表示法。大 O 时间复杂度实际上并不具体表示代码真正的执行时间，而是表示代码执行时间随数据规模增长的变化趋势，所以，也叫作渐进时间复杂度（asymptotic time complexity），简称时间复杂度。



# 时间复杂度分析

* 只关注循环执行次数最多的一段代码
* 加法法则：总复杂度等于量级最大的那段代码的复杂度
* 乘法法则：嵌套代码的复杂度等于嵌套内外代码复杂度的乘积



# 几种常见时间复杂度实例分析

![image-20241117222049105](https://raw.githubusercontent.com/howu911/picx-images-hosting/master/data_struct_algo202411172220134.png)

## O(1)

一般情况下，只要算法中不存在循环语句、递归语句，即使有成千上万行的代码，其时间复杂度也是Ο(1)。



## O(logn)、O(nlogn)

```c
 i=1;
 while (i <= n)  {
   i = i * 2;
 }
```



# 总结

![image-20241119223444500](https://raw.githubusercontent.com/howu911/picx-images-hosting/master/data_struct_algo202411192234540.png)





# 最好、最坏情况时间复杂度

```c
// n表示数组array的长度
int find(int[] array, int n, int x) {
  int i = 0;
  int pos = -1;
  for (; i < n; ++i) {
    if (array[i] == x) pos = i;
  }
  return pos;
}
```

最好情况时间复杂度就是，在最理想的情况下，执行这段代码的时间复杂度。就像我们刚刚讲到的，在最理想的情况下，要查找的变量 x 正好是数组的第一个元素，这个时候对应的时间复杂度就是最好情况时间复杂度。

最坏情况时间复杂度就是，在最糟糕的情况下，执行这段代码的时间复杂度。就像刚举的那个例子，如果数组中没有要查找的变量 x，我们需要把整个数组都遍历一遍才行，所以这种最糟糕情况下对应的时间复杂度就是最坏情况时间复杂度。



# 平均情况时间复杂度

要查找的变量 x 在数组中的位置，有 n+1 种情况：在数组的 0～n-1 位置中和不在数组中。我们把每种情况下，查找需要遍历的元素个数累加起来，然后再除以 n+1，就可以得到需要遍历的元素个数的平均值，即：

![image-20241119230959413](https://raw.githubusercontent.com/howu911/picx-images-hosting/master/data_struct_algo202411192309444.png)

实际上，在大多数情况下，我们并不需要区分最好、最坏、平均情况时间复杂度三种情况。像我们上一节课举的那些例子那样，很多时候，我们使用一个复杂度就可以满足需求了。只有同一块代码在不同的情况下，时间复杂度有量级的差距，我们才会使用这三种复杂度表示法来区分。