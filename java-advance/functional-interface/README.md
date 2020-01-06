# Functional interface

#### Là gì thế?

Functional interface là các interface mà chỉ có một phương thức trừu tượng.

#### Khác gì với các interface khác không?

Functional interface vẫn là interface nên vẫn có các tính chất của interface như bình thường. Tuy nhiên functional interface được dùng trong nhiều trường hợp nên có thêm một số cách viết khác. Xét một phương thức sau:

```java
public static ArrayList<Book> filter(ArrayList<Book> books) {
    ArrayList<Book> result = new ArrayList<>();
    for (Book b : books) {
        if (b.getYear() > 2000) {
            result.add(b);
        }
    }

    return result;
}
```

Phương thức trên làm nhiệm vụ lọc ra các quyển sách có năm xuất bản sau năm 2000 từ danh sách `books` ban đầu. Bây giờ giả sử mình muốn lọc theo theo tiêu chí khác, mình sẽ phải viết thêm phương thức `filter2` rất giống phương thức bên trên và chỉ thay biểu thức điều kiện trong câu lệnh `if`. Để phương thức `filter` được linh hoạt hơn, mình có thể dùng một `interface` để biểu diễn cho một tiêu chí như sau:

```java
public interface BookFilter {
    boolean apply(Book); // trong interface mọi phương thức mặc định là public
}
```

Phương thức `filter` viết lại để cho nhận một đối tượng `BookFilter`:

```java
public static ArrayList<Book> filter(ArrayList<Book> books, BookFilter func) {
    ArrayList<Book> result = new ArrayList<>();
    for (Book b : books) {
        if (func.apply(b)) {
            result.add(b);
        }
    }

    return result;
}
```

Khi ấy, muốn sử dụng phương thức `filter` để lọc ra các quyển sách xuất bản sau năm 2000, mình phải tạo thêm một lớp như sau:

```java
public class BookAfter2000Filter implements BookFilter {
    public boolean apply(Book b) {
        return b.getYear() > 2000;
    }
}
```

Sau đó sử dụng như sau:

```java
ArrayList<Book> books = new ArrayList<>();
...
BookFilter func = new BookAfter2000Filter();
ArrayList<Book> filteredBooks = filter(books, func);
```

Có thể thấy functional interface giống như một đối tượng đại diện cho một phương thức.

#### Viết như thế kia rõ dài .-.

Ừa, mỗi một tiêu chí lại phải có một lớp cụ thể thừa kế `BookFilter` trong khi lớp cụ thể đó thường chỉ dùng đúng một lần duy nhất. Vì thế, Java còn có cách viết anonymous class như sau (không cần có lớp `BookAfter2000Filter`):

```java
ArrayList<Book> books = new ArrayList<>();
...
ArrayList<Book> filteredBooks = filter(books, new BookFilter() {
    @Override
    public boolean apply(Book b) {
        return b.getYear() > 2000;
    }
});
```

Trong cách viết trên, mình tạo ra một lớp không có tên ghi đè phương thức `apply` của `BookFilter` đồng thời tạo luôn một đối tượng thuộc lớp đó. Nếu mình muốn lọc theo tiêu chí khác, giả sử lấy ra các quyển có tên bắt đầu bằng `"B"`, thì chỉ cần viết một anonymous class như sau:

```java
ArrayList<Book> filteredBooks = filter(books, new BookFilter() {
    @Override
    public boolean apply(Book b) {
        return b.getName().startsWith("B");
    }
});
```

#### Chỉ functional interface mới dùng anonymous class được thôi à?

Lớp nào cũng dùng được .-. Trong trong thân của lớp không tên có thể có nhiều phương thức cũng được.

#### Vẫn chưa thấy functional interface có gì mới cả @@

Riêng functional interface, ngoài cách viết dùng anonymous class còn có thể dùng biểu thức lambda như sau:

```java
ArrayList<Book> filteredBooks = filter(books, b -> b.getYear() > 2000);
```

hoặc


```java
ArrayList<Book> filteredBooks = filter(books, b -> b.getName().startsWith("B"));
```

Vì functional interface chỉ có duy nhất một phương thức, nên có thể dùng dấu `->` (là hai dấu `-` và `>`) với vế trái là tham số truyền vào phương thức, vế phải là kết quả trả về của phương thức, trình biên dịch có thể tự suy ra đó chính là đối tượng `BookFilter` có phương thức `apply` được ghi đè. Ngoài ra mình cũng nên dùng annotation `FunctionalInterface` khi viết functional interface để trình biên dịch có thể đảm bảo mình không sử dụng sai:

```java
@FunctionalInterface
public interface BookFilter {
    public boolean apply(Book);
}
```

Biểu thức lambda cho mình cảm giác có thể truyền một chức năng làm tham số cho một phương thức.

#### Có nhất thiết tên phương thức trong BookFilter phải là apply không?

Không.

#### Phương thức trong functional interface nhận nhiều hơn một tham số thì sao?

Thì cách nhau bởi dấu phẩy và thêm cặp dấu ngoặc đơn trước `->`, ví dụ:

```java
public class Program {
    private interface Operator { // Inner interface mặc định là static
        int apply(int a, int b); // Phương thức trong interface mặc định là public
    }

    public static int operate(int a, int b, Operator func) {
        return func.apply(a, b);
    }

    public static void main(String[] args) {
        Operator addFunc = (a, b) -> a + b;
        Operator multiplyFunc = (a, b) -> a * b;

        int sum = operate(10, 15, addFunc); // sum = 25
        int product = operate(10, 15, multiplyFunc); // product = 150
    }
}
```

Bình thường trình biên dịch có thể tự suy ra được kiểu dữ liệu của các tham số trong biểu thức lambda nhưng mình cũng có thể ghi cụ thể kiểu dữ liệu như sau:

```java
    Operator addFunc = (int a, int b) -> a + b;
    Operator multiplyFunc = (int a, int b) -> a * b;
```

#### Không có tham số thì sao?

Thì chỉ có dấu ngoặc thôi: `() -> ...`

#### Thân của phương thức có nhiều hơn một lệnh thì sao?

Thì dùng dấu ngoặc nhọn:

```java
(a, b) -> {
    ...
    return ...;
}
```

Ngoài ra nếu biểu thức lambda chỉ có duy nhất một lệnh và thao tác chỉ trên các tham số phía trước `->`, mình còn có thể sử dụng tham chiếu phương thức (method reference) thay cho biểu thức lambda với cú pháp:

```
<tên lớp hoặc tên đối tượng><hai dấu hai chấm><tên phương thức>
```

Ví dụ:

- `x -> System.out.println(x)` tương đương với `System.out::println`
- `x -> x.length()` tương đương với `String::length` nếu `x` thuộc kiểu `String`

#### Functional interface có xuất hiện nhiều trong Java không?

Có, ví dụ phương thức `sort` trong `java.util.Arrays` còn có thể truyền thêm một đối tượng của interface `Comparator` để định nghĩa cách so sánh. Interface `Comparator` có một phương thức là `compare` nhận 2 tham số, trả về một số âm nếu tham số 1 sẽ đứng trước tham số 2 khi sắp xếp. Ví dụ để sắp xếp giảm dần các số nguyên:

```java
Integer[] arr = {3, 1, 6, 4, 2};
Arrays.sort(arr, new Comparator<Integer>() {
    @Override
    public int compare(Integer a, Integer b) {
        return b - a;
    }
});
```

Hay sử dụng biểu thức lambda:

```java
Integer[] arr = {3, 1, 6, 4, 2};
Arrays.sort(arr, (a, b) -> b - a);
```

Về sau lập trình có sự kiện (ví dụ lập trình có đồ hoạ) thì sẽ có các phương thức có nhiệm vụ như khi click chuột thì làm gì, mình sẽ cần truyền một chức năng (functional interface) vào cho phương thức đó.

.  
.  
.  

[Quay lại: Java nâng cao](..)
