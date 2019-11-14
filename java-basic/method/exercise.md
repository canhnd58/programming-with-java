# Bài tập: Khai báo phương thức

### Bài 1:

Chương trình như sau in ra gì? Vì sao?

```java
public class Swapper {
    static void swap(int a, int b) {
        int tmp = a;
        a = b;
        b = a;
    }

    public static void main(String[] args) {
        int a = 5, b = 10;
        swap(a, b);
        System.out.println(a);
        System.out.println(b);
    }
}
```

### Bài 2:
Viết một phương thức tên `printStar` nhận đầu vào là một số nguyên `n` và làm nhiệm vụ in ra màn hình `n` dấu `*` trên cùng một hàng, sau đó xuống dòng.
Trong cùng class đó, viết phương thức `main` có một biến `n`, sử dụng câu lệnh lặp để gọi đến phương thức `printStar(n)` `n` lần.
Kết quả sẽ in ra màn hình hình vuông các dấu `*` có kích thước `n x n`.

### Bài 3:
Tương tự bài 2, nhưng in ra màn hình tam giác vuông với mỗi cạnh góc vuông có `n` dấu `*`. Ví dụ `n = 4`:
```
*
**
***
****
```

### Bài 4:

Viết một phương thức tên `GCD` nhận đầu vào là hai số nguyên dương và đưa ra ước chung lớn nhất của 2 số nguyên đó. Gợi ý: cần sử dụng vòng lặp.

Viết tiếp một phương thức tên `isCoprime` nhận đầu vào là hai số nguyên dương và đưa ra đầu ra là `true` nếu hai số đó là nguyên tố cùng nhau, nếu không đưa ra `false`. Hai số là nguyên tố cùng nhau khi ước chung lớn nhất của chúng là `1`.

Viết phương thức `main` sử dụng phương thức `isCoprime` để in ra màn hình tất cả các số nguyên tố cùng nhau với `n` và nhỏ hơn `n`.

### Bài 5:

Không sử dụng phương thức `Math.pow`, viết phương thức `pow` nhận đầu vào là hai số nguyên `a`, `b` và đưa ra kết quả `a` mũ `b` theo hai cách: một cách sử dụng câu lệnh lặp và một cách sử dụng đệ quy.
