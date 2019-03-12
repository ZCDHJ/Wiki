本页面主要分享一下在竞赛中经常/很多人会出现的错误。

-  由于运算符优先级产生的错误。
    -    `1 << 1+1` : 1 左移了 2，即该表达式返回的值是 `4` 。
    -   由于宏的展开，且未加括号导致的错误：
        ```cpp
        #define pwr(x) x* x
        pwr(2 + 2)
        ```
        该宏返回的值并非 $4^2 = 16$ 而是 $2+2\times 2+2 = 8$ 。

-  文件操作有可能会发生的错误。

    -   对拍时未清除文件指针即 `fclose(fp)` 就又令 `fp = fopen()` , 这会使得进程出现大量的文件野指针。
    -    `freopen()` 中的文件名未加 `.in` / `.out` 。

-   `int mian()` 。

-  无向图边表未开 2 倍。

-  多组数据未清空数组。

-  分治未判边界导致死递归。

-  读入优化未判断负数。

-  不正确地使用 `static` 修饰符。

-  `-1 >> 1 == 1` 。

- 写完 `struct` 或 `class` 忘记写分号。

- 存图下标从 0 开始输入节点未 -1.

- 赋值运算符和`==`不分。
    - 示例：
      ```cpp
      if(n=1)puts("Yes");
      else puts("No");
      ```
      无论 $n$ 的值之前为多少，输出肯定是`Yes`。
      

- 没有考虑数组下标出现负数的情况

- scanf 读入的时候没加 & 取地址符

- 在执行`ios::sync_with_stdio(false);`后混用两种IO，导致输出错乱。
    - 可以参考这个例子。
      ```cpp
      //这个例子将说明，关闭与stdio的同步后，混用两种IO的后果
      //建议单步运行来观察效果
      #include <iostream>
      #include <cstdio>
      using namespace std;
      int main()
      {
       ios::sync_with_stdio(false);
       //关闭IO后，cin/cout将使用独立缓冲区，而不是将输出同步至scanf/printf的缓冲区，从而减少IO耗时
       cout<<"a\n";
       //cout下，使用'\n'换行时，内容会被缓冲而不会被立刻输出，应该使用endl来换行并立刻刷新缓冲区
       printf("b\n");
       //printf的'\n'会刷新printf的缓冲区，导致输出错位
       cout<<"c\n";
       return 0;//程序结束时，cout的缓冲区才会被输出
      }
      ```
