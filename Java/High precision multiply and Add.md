### 高精度乘法
- 受到数值类型的位数限制，遇到大整数乘法的情况下，需要使用的高精度乘法
- 


1 大整数实现的就是高精度乘法
```java
    /*
    *高精度乘法
    */
import java.util.Scanner;

public class HighPrecisionMultiply{
  
    public static void main(String[] args){
        Scanner sc = nwe Scanner(System.in);
        BigInteger a = sc.nextBigInteger();
        BigInteger b = sc.nextBigInteger();
        System.out.println(a.multiply(b));
    }
}
```

2 实现
```java
import java.util.Scanner;

public class HighPrecisionMultiply {

    public String BigIntegerMultiply(String str1,String str2){
        StringBuilder res = new StringBuilder();
        int[] c = new int[2005];
        int[] a = new int[1005];
        int[] b = new int[1005];
        int str1len = str1.length();
        int str2len = str2.length();
        int j = 1,i;
        for (i = str1len-1; i >= 0; i--) {
            a[j++] = str1.charAt(i) - '0';
        }
        j = 1;
        for (i = str2len-1; i >= 0; i--) {
            b[j++] = str2.charAt(i) - '0';
        }
        for (i = 1; i <= str1len ; i++) {
            for (int k = 1; k <= str2len ; k++) {
                c[i+k-1] += a[i]*b[k];
            }
        }
        for (i = 1; i < str1len+str2len; i++) {
            c[i+1] += c[i]/10;
            c[i] %=10;
        }
        while(c[i] != 0 && i > 1){
            i--;
        }
        while(i>0){
           // System.out.print(c[i--]);
            res.append(c[i--]);
        }
        return res.toString();
    }


    public static void main(String[] args){
        Scanner scanner = new Scanner(System.in);
        String str1,str2;
        str1 = String.valueOf(scanner.nextInt());
        str2 = String.valueOf(scanner.nextInt());
        scanner.close();

        new HighPrecisionMultiply().BigIntegerMultiply(str1,str2);
    }
}
```