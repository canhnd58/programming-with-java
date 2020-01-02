# Ngoại lệ

#### Không muốn biết

Ngoại lệ ([exception](../../terminology.md#exception)) là những vấn đề nảy sinh trong quá trình chạy chương trình. Ví dụ chương trình yêu cầu nhập một số nhưng người dùng lại nhập một xâu, hoặc truy cập phần tử ngoài mảng, hoặc khai báo biến nhưng máy tính hết bộ nhớ ...

#### Không muốn biết .-.

Khi chương trình chạy gặp ngoại lệ chương trình sẽ kết thúc luôn và báo lỗi, tuy nhiên không phải lúc nào mình cũng muốn dừng chương trình. Có thể sử dụng từ khoá `try` và `catch` để xử lý ngoại lệ như sau:

```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class ExceptionExample {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int age;
        System.out.print("Nhập vào tuổi: ");

        while (true) {
            try {
                age = scan.nextInt();
                break;
            } catch (InputMismatchException e) {
                System.out.print("Vui lòng nhập vào một số hợp lệ: ");
            }
        }
        scan.close();
        System.out.println("Tuổi của bạn là: " + age);
    }
}
```

Chương trình như trên yêu cầu người dùng nhập đến khi nào nhập một số mới dừng. Khối lệnh ([block](../../terminology.md#block)) ngay sau từ khoá `try` gồm các lệnh có thể gây ra ngoại lệ, nếu bất cứ lệnh nào trong khối lệnh đó gặp ngoại lệ `InputMismatchException` thì các lệnh tiếp theo trong khối lệnh sẽ không được thực hiện mà chương trình sẽ thực hiện khối lệnh ngay sau từ khoá `catch`. Nếu không có câu lệnh `try-catch` thì khi người dùng nhập vào một xâu chương trình sẽ báo lỗi và dừng luôn.

#### InputMismatchException e là gì?

Cách viết như vậy có nghĩa là khối lệnh `catch` sẽ xử lý các ngoại lệ thuộc lớp `InputMismatchException` hoặc các lớp con của nó, biến `e` sẽ lưu các thông tin liên quan đến ngoại lệ được xử lý. Nếu trong khối lệnh của `try` gặp các ngoại lệ khác thì chương trình vẫn sẽ báo lỗi và kết thúc.

#### Có thể xử lý nhiều ngoại lệ một lúc không?
Có thể có nhiều lệnh `catch` sau khối lệnh `try`:

```java
try {
    age = scan.nextInt();
} catch (InputMismatchException e) {
    System.out.println("Nhập một số cơ mà");
} catch (IllegalStateException e) {
    System.out.println("Scanner bị close rồi không đọc được");
}
```

Hoặc viết nhiều ngoại lệ trong một lệnh `catch` cách nhau bởi toán tử `|` như sau:

```java
try {
    age = nextInt();
} catch (InputMismatchException|IllegalStateException e) {
    System.out.println("Lỗi rồi");
}
```

#### Làm sao biết khi nào lệnh này gặp ngoại lệ nào?
Tra cứu phương thức muốn dùng sẽ có các ngoại lệ mà phương thức đó có thể gặp.

#### Biến e có những thông tin gì?
Biến `e` là tham chiếu đến một đối tượng ngoại lệ, bất cứ đối tượng ngoại lệ nào cũng thuộc lớp `java.lang.Throwable` có những phương thức sau:

- `String getMessage()`: Trả về một xâu mô tả lỗi vừa gặp.
- `void printStackTrace()`: In ra màn hình các phương thức đang được gọi khi gặp lỗi.
- Còn một số phương thức nữa cơ.

#### Không đặt tên là e được không?
Được, tên biến thôi mà.

#### Có nhiều loại ngoại lệ không?
Có 2 loại ngoại lệ thừa kế trực tiếp từ lớp `Throwable` là `Error` và `Exception` (ngoại lệ tiếng Anh là exception chỉ tất cả các lớp con của lớp `Throwable` không phải mỗi lớp `Exception`):

```
Throwable
   |---Error
   |    |---VirtualMachineError
   |    |   |---OutOfMemoryError
   |    |   |---StackOverflowError
   |    |   |---InternalError
   |    |   |---UnknownError
   |    |
   |    |---...
   |
   |---Exception
        |---RuntimeException
        |   |---NullPointerException
        |   |---IllegalArgumentException
        |   |---IndexOutOfBoundsException
        |   |---...
        |
        |---IOException
        |   |---FileNotFoundException
        |   |---...
        |
        |---...
```

`Error` là những vấn đề nằm ngoài kiểm soát của người lập trình (ví dụ hết bộ nhớ). Chương trình được lập trình tốt vẫn có thể gặp các lỗi này và người lập trình ít khi làm được gì với các lỗi này (trừ lỗi `OutOfMemoryError` hay `StackOverflowError` có thể do lập trình kém nên dùng quá nhiều bộ nhớ, cũng có thể do hết bộ nhớ thật).

`RuntimeException` là các lỗi lập trình được phát hiện trong quá trình chạy (runtime) chương trình. Ví dụ truy cập thuộc tính của tham chiếu null (`NullPointerException`) hay truy cập một phần tử nằm ngoài mảng (`IndexOutOfBoundsException`). Các lỗi này thường là do lập trình kém.

Lớp `Exception` và các lớp con không phải `RuntimeException` không phải là lỗi mà là cách thức để điều khiển luồng chạy của chương trình. Ví dụ lệnh mở một file thì file đó có thể tồn tại hoặc không, nếu file tồn tại lệnh đó trả về đối tượng đại diện cho file, nếu không thì *ném* ngoại lệ `FileNotFoundException`. Các phương thức có thể đưa ra các ngoại lệ loại này luôn phải khai báo các ngoại lệ có thể đưa ra. Các ngoại lệ này luôn phải được xử lý bởi người lập trình nếu không trình biên dịch sẽ báo lỗi. Vì thế các ngoại lệ này còn có tên là [checked exceptions](../../terminology.md#checked-exceptions) còn `Error` và `RuntimeException` còn có tên là [unchecked exceptions](../../terminology.md#unchecked_exceptions).

#### Làm sao để khai báo ngoại lệ cho phương thức?

Mình có thể tạo ngoại lệ riêng của mình như sau:
```java
public class OutOfMoneyException extends Exception {
}
```

Giả sử có lớp `Account` đại diện cho tài khoản ngân hàng:

```java
public class Account {
    private int balance; // Số dư tài khoản

    public Account() {
        balance = 0;
    }

    public void deposit(int amount) { // Thêm tiền
        balance += amount;
    }

    public void withdraw(int amount) throws OutOfMoneyException { // Rút tiền
        if (amount > balance)
            throw new OutOfMoneyException();

        balance -= amount;
    }
}
```

Ở ví dụ trên, phương thức `withdraw` khai báo là sẽ có thể có ngoại lệ `OutOfMoneyException` bằng từ khoá `throws`. Trong khối lệnh của phương thức, muốn đưa ra ngoại lệ thì dùng từ khoá `throw`, phương thức gặp lệnh `throw` sẽ kết thúc và không thực hiện các lệnh bên dưới. Tất cả các phương thức muốn sử dụng phương thức `withdraw` đều cần phải xử lý ngoại lệ bằng câu lệnh `try-catch` hoặc khai báo là sẽ đưa ra ngoại lệ `OutOfMoneyException`. Ví dụ:

```java
public class Person {
    private Account account;

    public Person {
        account = new Account();
    }

    public boolean buyBook() {
        try {
            account.withdraw(20000);
            return true;
        } catch (OutOfMoneyException e) {
            return false;
        }
    }
}
```

thì các phương thức gọi tới `buyBook` không cần xử lý ngoại lệ. Còn:

```java
    public boolean buyBook() throws OutOfMoneyException{
        account.withdraw(20000);
        return true;
    }
```

thì các phương thức gọi tới `buyBook` phải xử lý ngoại lệ hoặc lại khai báo là sẽ có ngoại lệ. Giả sử `main` gọi `buyBook`, `buyBook` gọi `withdraw`, nếu chương trình gặp ngoại lệ `OutOfMoneyException` do phương thức `withdraw` gây ra, ngoại lệ được chuyển tới `buyBook`, `buyBook` không xử lý thì chuyển tới `main`, `main` không xử lý thì chương trình báo lỗi `OutOfMoneyException` và kết thúc. Chú ý nếu `main` không xử lý thì `main` phải khai báo là có thể có `OutOfMoneyException` như sau, nếu không sẽ bị lỗi biên dịch do `OutOfMoneyException` là [checked exception](../../terminology.md#checked-exceptions) luôn phải được xử lý hoặc truyền cho phương thức khác xử lý bằng cách khai báo `throws`:

```java
public static void main(String[] args) throws OutOfMoneyException {
    ...
}
```

#### Phương thức có nhiều ngoại lệ thì sao?
Thì các ngoại lệ cách nhau bởi dấu `,` sau từ khoá `throws`:

```java
    public void withdraw(int amount) throws OutOfMoneyException, ServerException {
        if (...)
            throw new OutOfMoneyException();
        if (...)
            throw new ServerException();
        ...
    }
```

#### Có nhiều từ khoá liên quan đến ngoại lệ thế?
Ngoài `try`, `catch`, `throw` và `throws` còn có từ khoá `finally` nữa. Một lệnh `try` luôn phải theo sau là các lệnh `catch` hoặc lệnh `finally` hoặc cả hai. Khối lệnh `finally` sẽ được thực hiện dù có ngoại lệ xảy ra hay không. Ví dụ:

```java
public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    try {
        int a = nextInt();
    } catch (Exception e) {
        System.out.println("Lỗi rồi");
    } finally {
        scan.close();
    }
}
```

Câu lệnh `try-catch-finally` như trên đảm bảo phương thức `close` luôn được gọi dù ngoại lệ có xảy ra hay không.

.  
.  
.  

[Quay lại: Java nâng cao](..)
