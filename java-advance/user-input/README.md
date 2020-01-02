# Đầu vào từ người dùng

#### Gì đây?
Từ trước tới giờ để kiểm tra chương trình chạy đúng hay sai mình đều phải thay đổi giá trị các biến trong mã nguồn ([source code](../../terminology.md#source-code)). Ngoài cách đó còn có cách nhập dữ liệu trong lúc chương trình đang chạy.

#### Làm sao để nhập dữ liệu lúc đang chạy?
Có thể sử dụng lớp `Scanner` trong package `java.util`. Lớp `Scanner` có các phương thức thành viên ([member method](../../terminology.md#member-method)) có tác dụng tạm dừng chương trình, đợi người dùng nhập vào từ bàn phím ấn Enter rồi chương trình mới chạy tiếp. Ví dụ:

```java
import java.util.Scanner;

public class ScannerExample {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("Hãy nhập vào tuổi của bạn: ");

        int age = scan.nextInt();
        scan.close();

        if (age > 25)
            System.out.println("Già quá!);
        else
            System.out.println("Vẫn còn trẻ lắm");
    }
}
```

Chương trình như trên sẽ in ra màn hình dòng chữ `Hãy nhập vào tuổi của bạn: `, sau đó đợi người dùng nhập vào một số nguyên rồi lưu vào biến `age`, biến `age` được dùng trong câu lệnh `if-else` để in ra màn hình dòng chữ `Già quá!` hoặc `Vẫn còn trẻ lắm`. Phương thức `close` được gọi ngay sau khi không cần dùng biến `scan` nữa để giải phóng vùng nhớ đã cấp cho đối tượng lớp `Scanner` tham chiếu bởi biến `scan`.

#### System.in là cái gì thế?
`System.in` và `System.out` là hai luồng dữ liệu ([data stream](../../terminology.md#data-stream)) vào ra chuẩn. `System.in` là đối tượng thuộc lớp `java.io.InputStream`, được tạo sẵn khi chạy chương trình, đại diện cho bàn phím. `System.out` là đối tượng thuộc lớp `java.io.PrintStream` đại diện cho màn hình.

Đối tượng `System.in` có các phương thức để đọc dữ liệu từ bàn phím tuy nhiên đối tượng Scanner hỗ trợ nhiều phương thức dễ dùng hơn cho nên mới dùng Scanner thay cho đọc trực tiếp từ `System.in`. `Scanner` cũng có thể đọc từ các luồng dữ liệu khác như file, network ... vì thế muốn đọc từ bàn phím phải truyền `System.in` vào hàm khởi tạo của lớp `Scanner`.

#### Có nextInt thì có nextDouble không?
Có, lớp `Scanner` có các phương thức sau để đọc dữ liệu:

|Phương thức|Ý nghĩa|
|---|---|
|`byte nextByte()`| Đọc một giá trị kiểu `byte`|
|`short nextShort()`| Đọc một giá trị kiểu `short`|
|`int nextInt()`| Đọc một giá trị kiểu `int`|
|`long nextLong()`| Đọc một giá trị kiểu `long`|
|`float nextFloat()`| Đọc một giá trị kiểu `float`|
|`double nextDouble()`| Đọc một giá trị kiểu `double`|
|`boolean nextBoolean()`| Đọc một giá trị kiểu `boolean`|
|`String next()`| Đọc một xâu đến khi gặp khoảng trắng|
|`String nextLine()`| Đọc một xâu là một dòng|

Các phương thức đều đọc đến một khoảng trắng (dấu cách, dấu tab hoặc dấu xuống dòng) thì dừng (không đọc khoảng trắng), trừ phương thức `nextLine` đọc đến dấu xuống dòng mới dừng (đọc cả dấu xuống dòng).

#### Nhưng mà nhập xong ấn Enter chương trình mới chạy tiếp mà?

Cứ mỗi khi mình ấn phím Enter thì những gì mình nhập sẽ đưa vào vùng nhớ đệm ([buffer](../../terminology.md#buffer)). Các phương thức của `Scanner` đọc từ vùng nhớ đệm chứ không phải đọc trực tiếp những gì mình gõ. Nếu không đọc được từ vùng nhớ đệm thì chương trình mới tạm dừng để đợi người dùng thêm dữ liệu vào vùng nhớ đệm. Ví dụ: 

```java

import java.util.Scanner;

public class ScannerExample {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a, b, c, d, e;

        System.out.print("Nhập a: ");
        a = scan.nextInt();
        System.out.print("Nhập b: ");
        b = scan.nextInt();
        System.out.print("Nhập c: ");
        c = scan.nextInt();
        System.out.print("Nhập d: ");
        d = scan.nextInt();
        System.out.print("Nhập e: ");
        e = scan.nextInt();

        scan.close();
    }
}
```

Khi chạy chương trình nhập vào như sau:

```
4
3 9 8
5
```

Chương trình chạy đến lệnh `a = scan.nextInt()` sẽ tạm dừng vì ban đầu vùng nhớ đệm chưa có gì. Mình gõ `4<Enter>` thì bộ nhớ đệm trở thành `4\n` (kí tự `\n` đại diện cho dấu xuống dòng), lệnh `a = scan.nextInt()` thấy số `4` nên gán vào biến `a`, xoá số `4` khỏi vùng nhớ đệm sau đó tiếp tục chạy các lệnh tiếp theo. Lệnh `b = scan.nextInt()` tạm dừng vì bộ nhớ đệm đang là `\n` không có số nào, mình gõ `3 9 8<Enter>` thì bộ nhớ đệm thành `\n3 9 8\n`. Lệnh `b = scan.nextInt()` bỏ qua dấu `\n` đầu tiên và thấy số `3` nên lưu `3` vào biến `b`, bộ nhớ đệm thành `9 8\n`. Lệnh `c = scan.nextInt()` và `d = scan.nextInt()` sẽ không dừng chương trình vì đọc được số `9` và `8` từ bộ nhớ đệm. Màn hình khi chạy chương trình với đầu vào như trên sẽ như sau:

```
Nhập a: 4
Nhập b: 3 9 8
Nhập c:
Nhập d:
Nhập e: 5
```

#### Có cần phải hiểu đến mức đấy không?
Cần thiết nếu chương trình sử dụng `nextLine` chung với các phương thức khác. Ví dụ chương trình nhập và tuổi của các thành viên trong gia đình như sau:

```java
public class Person implements Comparable {
    private int age;
    private String name;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    @Override
    public int compareTo(Object other) {
        return age - ((Person) other).age;
    }
}
```

```java
import java.util.Scanner;
import java.util.Arrays;

public class ScannerExample {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.print("Nhà bạn có bao nhiêu người: ");
        int len = scan.nextInt();

        Person[] members = new Person[len];
        for (int i = 0; i < len; i ++) {
            System.out.print("Nhập họ tên người thứ " + (i + 1) + ": ");
            String name = scan.nextLine();
            System.out.print("Nhập tuổi người thứ " + (i + 1) + ": ");
            int age = scan.nextInt();
            members[i] = new Person(name, age);
        }

        Arrays.sort(members);
        System.out.println("Người già nhất trong nhà bạn là: " + members[len-1].getName());
    }
}
```

Thử chạy chương trình trên trên [IDE](../../terminology.md#ide) của mình sẽ thấy chương trình chạy không đúng những gì mình muốn do phương thức `nextLine` đọc cả dấu xuống dòng còn các phương thức khác gặp dấu xuống dòng là dừng luôn (không xoá dấu xuống dòng ra khỏi vùng nhớ đệm).

Khi chương trình hiện lên dòng chữ `Nhà bạn có bao nhiêu người:` mà mình nhập vào `4<Enter>` thì bộ nhớ đệm trở thành `4\n`. Lệnh `nextInt` đầu tiên xoá số `4` nhưng không xoá `\n` nên bộ nhớ đệm là `\n`. Lệnh `nextLine` tiếp theo, không đợi người dùng nhập mà đọc đến khi gặp dấu `\n` và xoá cả dấu `\n` cho nên tên người đầu tiên sẽ là xâu rỗng và bộ nhớ đệm thành rỗng. Lệnh nhập tuổi tiếp theo sẽ đợi người dùng nhập. Để khắc phục lỗi này mình thêm một lệnh `nextLine` giữa `nextInt` và `nextLine` để xoá dấu `\n` khỏi vùng nhớ đệm.

```java
        ...
        for (int i = 0; i < len; i ++) {
            scan.nextLine();
            System.out.print("Nhập tên người thứ " + i + ": ");
            String name = scan.nextLine();
        ...
```

#### Sao lằng nhằng thế?
Không biết .-.

.  
.  
.  

[Quay lại: Java nâng cao](..)
