# Khai báo phương thức

*Kiến thức cần biết:* [JVM](../../terminology.md#jvm), [statement](../../terminology.md#statement), [block](../../terminology.md#block), [variable](../../terminology.md#variable), [expression](../../terminology.md#expression), [control-flow statement](../../terminology.md#control-flow-statement)

#### Giờ biết hết các kiểu câu lệnh trong Java rồi còn gì để học nữa?
Về cơ bản thì bất cứ chương trình nào cũng có thể viết thành chuỗi các [câu lệnh](../../terminology.md#statement) liên tục nhau trong [phương thức](../../terminology.md#method) `main`. Tuy nhiên nếu chương trình dài mà để tất cả mọi lệnh trong phương thức `main` thì sẽ khó quản lý [mã nguồn](../../terminology.md#source-code) nên một chương trình thường được chia thành nhiều phương thức, mỗi phương thức làm một nhiệm vụ riêng biệt.

Ngoài ra, một số đoạn [code](../../terminology.md#code) dùng đi dùng lại nhiều lần cũng nên được viết thành một phương thức.

#### Tạo một phương thức như thế nào?

Có thể tạo (hay còn gọi là khai báo - [declaration](../../terminology.md#declaration)) một phương thức đơn giản chỉ làm nhiệm vụ gộp các lệnh với cú pháp sau:

```
static void <tên phương thức><mở ngoặc đơn><đóng ngoặc đơn><khối lệnh>
```

Một phương thức được tạo ra luôn phải thuộc một lớp nên câu lệnh trên phải nằm trong khối lệnh ([block](../../terminology.md#block)) của một lớp. Muốn sử dụng phương thức mới tạo như trên thì sử dụng cú pháp sau:

```
<tên lớp><dấu chấm><tên phương thức><mở ngoặc đơn><đóng ngoặc đơn><dấu chấm phẩy>
```

Ví dụ:
```java
public class PrettyHello {
    static void drawLine() {
        System.out.println("*-----------------*");
    }

    public static void main(String[] args) {
        PrettyHello.drawLine();
        System.out.println("Hello World");
        PrettyHello.drawLine();
    }
}
```

Chương trình như trên sẽ in ra màn hình như sau:
```
*-----------------*
Hello World
*-----------------*
```

Ngoài ra, nếu hai phương thức cùng thuộc một lớp thì khi phương thức này gọi đến phương thức kia có thể bỏ đi tên lớp và dấu `.`. Ví dụ phương thức `main` có thể viết lại như sau:

```java
    public static void main(String[] args) {
        drawLine();
        System.out.println("Hello World");
        drawLine();
    }
```

#### Có thấy cái gì gọi đến phương thức main đâu nhỉ?
Phương thức main là phương thức đặc biệt, mình chỉ cần tạo ra thôi chứ không cần gọi tới. Với ví dụ như trên, khi ấn chạy chương trình thì JVM tự động gọi phương thức `PrettyHello.main();` để thực hiện các lệnh trong phương thức `main`.

#### Thế cái phần String[] args là gì?
Đó gọi là đầu vào ([input](../../terminology.md#input)) của phương thức. Phương thức có thể không nhận đầu vào, nhận một hay nhiều đầu vào, với các đầu vào khác nhau phương thức làm nhiệm vụ khác nhau. Ví dụ phương thức `Math.pow` nhận 2 đầu vào và phương thức `System.out.println` nhận một đầu vào.

Một phương thức đơn giản và nhận đầu vào có thể tạo ra bằng cú pháp như sau:

```
static void <tên phương thức><mở ngoặc đơn><kiểu dữ liệu đầu vào 1><dấu cách><tên đầu vào 1><dấu phẩy nếu có thêm đầu vào><kiểu dữ liệu và tên đầu vào khác nếu có><đóng ngoặc đơn><khối lệnh>
```

Gọi phương thức đó với cú pháp sau:

```
<tên lớp><dấu chấm><tên phương thức><mở ngoặc đơn><biểu thức thể hiện đầu vào 1><dấu phẩy nếu có đầu vào khác><biểu thức thể hiện đầu vào khác><đóng ngoặc đơn><dấu chấm phẩy>
```

Ví dụ:

```java
public class MultiGreet {
    static void greet(String name, int age) {
        System.out.print("Chào");
        if (age > 25)
            System.out.print(" cô ");
        else
            System.out.print(" bạn ");
        System.out.println(name);
    }

    public static void main(String[] args) {
        greet("A", 24);
        greet("B", 26);
    }
}
```

Chương trình trên sẽ in ra dòng chữ:
```
Chào cô A
Chào bạn B
```

#### Đầu vào phương thức main là gì vậy?
Có thể đưa đầu vào của chương trình bằng tham số dòng lệnh mà lười giải thích lắm bỏ qua đi.

#### Thế từ khoá void để làm gì?

Có 2 loại phương thức, một loại đưa ra một giá trị cụ thể ([literal](../../terminology.md#literal)) có thể làm toán hạng trong biểu thức (ví dụ `Math.pow`) và một loại không đưa ra giá trị gì (ví dụ `System.out.println`). Nếu là loại thứ 2 mình sẽ dùng từ khoá `void` khi tạo phương thức.

#### Thế loại phương thức có thể làm toán hạng thì tạo dư lào?

Phương thức để làm toán hạng thì khi gọi cần đưa ra một giá trị cụ thể ([literal](../../terminology.md#literal)) gọi là đầu ra ([output](../../terminology.md#output)), giống như biểu thức luôn đưa ra thành một giá trị cụ thể thì phương thức loại này cũng như vậy. Cú pháp tạo một phương thức loại này như thế này:

```
static <kiểu dữ liệu đầu ra><dấu cách><tên phương thức><mở ngoặc đơn><kiểu dữ liệu đầu vào 1><dấu cách><tên đầu vào 1><dấu phẩy nếu có thêm đầu vào><kiểu dữ liệu và tên đầu vào khác nếu có><đóng ngoặc đơn><khối lệnh>
```

Hơn nữa, trong phương thức loại này luôn cần một câu lệnh `return <biểu thức đầu ra><dấu chấm phẩy>` để thể hiện giá trị đầu ra cụ thể là giá trị nào.

Ví dụ:

```java
public class Factorial {

    // Phương thức tính giai thừa của một số n
    static int getFactorial(int n) {
        int result = 1;
        for (int i = 1; i <= n; i ++)
            result *= i;

        return result;
    }

    public static void main(String[] args) {
        int n = 3, m = 4;
        System.out.println("n! là: " + getFactorial(n));
        System.out.println("m! + 10 là " + (getFactorial(m) + 10));
    }
}
```

Chương trình trên sẽ in ra màn hình các dòng như sau:
```
n! là: 6
m! + 10 là: 34
```


#### Phương thức getFactorial là biến n còn phương thức main là biến m mà vẫn chạy được à?
Các biến tạo ra trong các phương thức không liên quan đến nhau (trong phương thức main tạo biến `a` trong phương thức khác vẫn tạo biến `a` được, 2 biến cùng tên nhưng là 2 biến khác nhau, đại diện cho 2 vùng nhớ khác nhau trong bộ nhớ). Biến ở trong phương thức này sẽ không dùng được ở trong phương thức khác, làm như vậy khi viết một phương thức sẽ không cần quan tâm phương thức khác đã tạo ra biến gì rồi.

Khi gọi một phương thức, kết quả của biểu thức trong cặp dấu ngoặc đơn sau tên phương thức sẽ được làm đầu vào cho phương thức được gọi. Ở ví dụ trên, khi gọi `getFactorial(n)` giá trị trong biến `n` của phương thức `main` (kết quả của biểu thức `n` là `3`) được copy sang đầu vào của phương thức `getFactorial`, tức là biến `n` trong dòng `static int getFactorial(int n) {` sẽ lưu giá trị `3` (nhưng 2 biến `n` vẫn là 2 biến khác nhau), sau đó mới thực hiện các lệnh bên trong khối lệnh của phương thức `getFactorial`.

#### Câu lệnh return cần phải ở cuối phương thức không?
Câu lệnh `return` có thể để bất cứ đâu trong phương thức. Khi chương trình gặp câu lệnh `return` phương thức đó sẽ kết thúc dù đằng sau vẫn còn lệnh chưa thực hiện.
Ví dụ:

```java
public class PrimeNumber {

    // Kiểm tra một số có phải nguyên tố hay không
    static boolean isPrime(int number) {
        for (int i = 2; i < number; i ++)
            if (number % i == 0)
                return false;

        return true;
    }

    public static void main(String[] args) {
        if (isPrime(19))
            System.out.println("19 là nguyên tố");
        else
            System.out.println("19 không phải nguyên tố");
    }
}
```

Với phương thức `isPrime` như trên, nếu `number` chia hết cho bất cứ số nào từ `2` đến `number - 1` thì kết quả của phương thức `isPrime` là `false` và kết thúc phương thức luôn (không thực hiện lệnh `return true` bên dưới). Nếu không chia hết cho số nào thì lệnh `return false` không được thực hiện nên kết quả phương thức là `true`.

Hơn nữa, câu lệnh `return` cũng có thể ở trong một phương thức không đưa ra đầu ra (phương thức `void`) để kết thúc luôn phương thức đó. Khi ấy, đằng sau lệnh `return` sẽ là dấu chấm phẩy luôn chứ không có biểu thức đầu ra.

#### Thế từ khoá static là gì?
Viết một phương thức không nhất thiết phải có từ khoá `static` nhưng ý nghĩa của phương thức sẽ khác. Sẽ đề cập rõ hơn ở bài tiếp theo, giờ phương thức nào cũng cho `static` vào đã.

#### Có quy tắc đặt tên phương thức không?
Cách đặt tên giống đặt tên biến.

#### Còn gì hay ho với phương thức nữa không?
Có một loại phương thức khá hay tên là phương thức đệ quy ([recursive method](../../terminology.md#recursive-method)).
Phương thức đệ quy là phương thức mà trong khối lệnh của nó gọi đến tên của chính nó.
Ví dụ:
```java
public class FactorialRecursive {

    // Phương thức tính giai thừa của một số n
    static int getFactorial(int n) {
        if (n <= 1)
            return 1;

        int result = getFactorial(n-1);
        return result * n;
    }

    public static void main(String[] args) {
        int n = 3, m = 4;
        System.out.println("n! là: " + getFactorial(n));
        System.out.println("m! + 10 là " + (getFactorial(m) + 10));
    }
}
```

Lệnh `getFactorial(n)` tức `getFactorial(3)` đưa ra kết quả là 6 do thực hiện các bước như sau:
1. `main` gọi `getFactorial(3)`
1. `getFactorial(3)` gọi `getFactorial(2)`
1. `getFactorial(2)` gọi `getFactorial(1)`
1. `getFactorial(1)` có đầu ra là `1` do gặp lệnh `return 1`, quay lại `getFactorial(2)` do lệnh `getFactorial(2)` chưa gặp lệnh `return`.
1. `getFactorial(2)` nhận được kết quả `1` từ `getFactorial(1)` và đưa đầu ra là `1 * 2` cho `getFactorial(3)`, quay lại `getFactorial(3)`.
1. `getFactorial(3)` nhận được kết quả `2` từ `getFactorial(2)` và đưa đầu ra là `2 * 3` cho `main`, quay lại `main`
1. `main` nhận được kết quả `6` từ `getFactorail(3)` và in ra màn hình `n! là 6`.

.  
.  
.  

[Bài tập](exercise.md)

[Quay lại: Java căn bản](..)
