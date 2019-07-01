#### 一、题目描述

>   最近FJ为他的奶牛们开设了数学分析课，FJ知道若要学好这门课，必须有一个好的三角函数基本功。
>   所以他准备和奶牛们做一个“Sine之舞”的游戏，寓教于乐，提高奶牛们的计算能力。
>         不妨设
>         An=sin(1–sin(2+sin(3–sin(4+...sin(n))...)
>         Sn=(...(A1+n)A2+n-1)A3+...+2)An+1
>         FJ想让奶牛们计算Sn的值，请你帮助FJ打印出Sn的完整表达式，以方便奶牛们做题。
>
>   输入
>          仅有一个数：N<201。
>   输出
>          请输出相应的表达式Sn，以一个换行符结束。输出中不得含有多余的空格或换行、回车符。
>   样例输入
>           3
>   样例输出
>          ((sin(1)+3)sin(1-sin(2))+2)sin(1-sin(2+sin(3)))+1



#### 二、代码

```java
package com.nuc.zp.datastructures.recursion;

import java.util.Scanner;
/**
 * 题目描述
 * 最近FJ为他的奶牛们开设了数学分析课，FJ知道若要学好这门课，必须有一个好的三角函数基本功。
 * 所以他准备和奶牛们做一个“Sine之舞”的游戏，寓教于乐，提高奶牛们的计算能力。
 * 不妨设
 * An=sin(1–sin(2+sin(3–sin(4+...sin(n))...)
 * Sn=(...(A1+n)A2+n-1)A3+...+2)An+1
 * FJ想让奶牛们计算Sn的值，请你帮助FJ打印出Sn的完整表达式，以方便奶牛们做题。
 * <p>
 * 输入
 * 仅有一个数：N<201。
 * 输出
 * 请输出相应的表达式Sn，以一个换行符结束。输出中不得含有多余的空格或换行、回车符。
 * 样例输入
 * 3
 * 样例输出
 * ((sin(1)+3)sin(1-sin(2))+2)sin(1-sin(2+sin(3)))+1
 * <p>
 * A1=sin(1)
 * A2=sin(1-sin(2))
 * A3=sin(1-sin(2+sin(3)))
 * <p>
 * ((A1+3)A2+2)A3+1
 * <p>
 * S1=(A1)+1
 * S2=(A1+2)A2+1
 * S3=（(A1+3)A2+2)A3+1
 */
public class SineDance1 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        SineDance1 sineDance1 = new SineDance1();
        while (scanner.hasNext()) {
            int n = scanner.nextInt();
            sineDance1.show(n);
        }

    }

    private void show(int n) {
        if (n < 0) {
            return;
        }
        System.out.println(Sn(n, n + 1));
    }

    private String Sn(int n, int N) {
        if (n == 1 && N - n == 1) {
            return An(1, 1) + "+1";
        }
        if (n == 1 && N - n > 1) {
            return An(1, 1) + "+" + (N - n) + ")";
        }
        String kuohao = (N - n == 1) ? "" : ")";
        return "(" + Sn(n - 1, N) + An(n, n) + "+" + (N - n) + kuohao;
    }

    private String An(int n, int N) {
        String fuhao = "";
        if (N > 2) {
            fuhao = n == 1 ? "" : (N - n + 1) % 2 == 0 ? "+" : "-";
        } else {
            fuhao = (n == 1) ? "" : "-";
        }
        if (n == 0) {
            return "";
        }
        return "sin(" + (N - n + 1) + fuhao + An(n - 1, N) + ")";
    }
}
```

