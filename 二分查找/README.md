## 标准二分的框架

```java
while(st < ed)

{

    int mid= st  + (ed-st)/2;

    if( r[mid] < target)

        st = mid+1;

    else

        ed = mid;

}

return st;
```

## 二分有几个关键点需要注意：

1. 二分的关键就是st和ed两个指针如何移动。需要记住的是，**st只会往大的方向移动，ed只会往小方向移动。**
2. mid= st  + (ed-st)/2 而不用 mid = (st + ed) / 2 是因为后面的情况当**st+ed很大时可能会产生溢出。**
3. 注意避免死循环(一般就考虑最后两个数的极端情况)：
  - 当`mid = st  + (ed-st)/2 ` 时，mid偏向左边（一般求小于等于target的数），所以st必须移动`st = mid+1`，否则就可能会死循环。
  - 当`mid = st  + (ed-st)/2 + 1`，mid偏向右边（一般是求大于等于target的数），所以ed必须移动`ed = mid -1`，否则可能死循环


4. 一般来说，如果是求恰好找到的，可以多加一个等于的时候退出
5. 有时候，我们不好判断到底判断条件里`<`还是`<=`的时候，可以把条件限定在2个数A，B（一般来说，此时的mid = A）和target：
   - A（mid） < target，我们需要st还是ed移动
   - A（mid） = target，我们需要st还是ed移动

## 二分相关的题目

注意一般二分查找前提是**有序**，要不是题目已经确保有序了，要不就是自己先做一个排序。



一般有几种：

### 猜数问题 （374题）

这种题目一般是说找到里面特定的数字，这个数字是确定存在的，所以肯定会有一个一定匹配的问题,所以一般我们在判断条件中把`if(r[mid] == target)` 单独提出来。



### 找位置 （35题）

这类题目一般是说找到一个数它应该在数组中的位置，就是完整的套用框架。



### 找边界（34题）

这类题目有点麻烦，它需要用两次分别找左右边界。这里就需要考虑里面**可能有和目标数相同的数**。这时候就要特别注意是使用`<=`还是`<`，而在找右边界的时候，需要移动`ed`,这时候`mid`在原来的基础要+1（看注意3）





