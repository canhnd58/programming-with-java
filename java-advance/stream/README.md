# Stream

#### Học ở bài I/O rồi còn gì?

Stream ở bài này khác với stream như `InputStream` hay `OutputStream` ở bài trước.

#### Vậy stream bài này là gì? @@

`java.util.stream` là package bắt đầu xuất hiện trong phiên bản Java 8 cho phép Java có khả năng lập trình hàm (functional programming). Lập trình hàm là cách lập trình thiên về mô tả làm gì hơn là làm như thế nào. Lớp `Stream` đại diện cho một chuỗi tuần tự các phần tử và có rất nhiều phương thức để làm việc với các phần tử như lọc, tổng hợp, chuyển đổi các phần tử. Ví dụ có chương trình sau:

```java
public class ProgramWithoutStream {
    public static void main(String[] args) {
        String[] arr = {"Apple", "Coconut", "Orange", "Cat", "Dog"};
        for (String str : arr) {
            if (str.startsWith("C")) {
                String text = "I like " + str;
                System.out.println(text);
            }
        }
    }
}
```

Chương trình trên lọc ra các chuỗi trong mảng `arr` bắt đầu bằng `"C"`, sau đó in ra dòng `I like` kèm theo chuỗi thoả mãn. Có thể viết lại sử dụng `Stream` như sau:

```java
import java.util.Arrays;

public class ProgramWithStream {
    public static void main(String[] args) {
        String[] arr = {"Apple", "Coconut", "Orange", "Cat", "Dog"};
        Arrays
            .stream(arr)
            .filter(str -> str.startsWith("C"))
            .map(str -> "I like " + str)
            .forEach(str -> System.out.println(str));
    }
}
```

Phương thức `Arrays.stream` chuyển đổi một mảng thành một đối tượng thuộc kiểu `Stream`. Sau đó phương thức `filter` của đối tượng `Stream` lọc ra các phần tử thoả mãn biểu thức lambda rồi trả về `Stream` chứa các phần tử thoả mãn. `Stream` sau khi lọc gọi phương thức `map` để thêm dòng chữ `I like` vào trước từng phần tử. Phương thức `forEach` gọi phương thức `System.out.println` lên từng phần tử nên chương trình sẽ in ra:

```
I like Coconut
I like Cat
```

Câu lệnh cuối cùng còn có thể dùng tham chiếu phương thức:

```java
    .forEach(System.out::println);
```

#### Sao mà cần dùng stream, cứ dùng như cách một không được à?

Nếu dùng như cách một thì mọi thứ sẽ làm đúng như người lập trình viết ra (mình bảo máy tính từng bước thực hiện), làm theo cách 2 thì mình chỉ mô tả cho máy tính mình muốn làm gì (hãy lọc ra những cái này, chuyển đối cái này thành cái kia ...) máy tính tuỳ ý dùng cách gì miễn sao ra kết quả mình muốn nên máy tính dễ tối ưu chương trình cho mình hơn. Ví dụ bước nào thực hiện song song được máy tính có thể làm song song giúp mình.

#### Ngoài mảng ra thì còn cái gì có thể tạo thành stream?

Đối tượng thuộc lớp `Collection` có phương thức `stream` để chuyển đổi sang stream:

```
List<Integer> list = new List<>();
...
list
    .stream()
    .filter(...)
    .map(...)
    ...
```

#### Stream có những phương thức nào?

Package `java.util.stream` có một số lớp để biểu diễn stream như:

- `IntStream` đại diện cho stream các số nguyên kiểu `int`
- `LongStream` đại diện cho stream các số nguyên kiểu `long`
- `DoubleStream` đại diện cho stream các số thực kiểu `double`
- `Stream<T>` đại diện cho stream các đối tượng kiểu `T`

Các lớp này có phương thức `static of` để tạo ra đối tượng stream, ví dụ:

```java
IntStream.of(2, 3, 4, 1)
    .map(x -> x * x)
    .forEach(System.out.println); // In ra 4, 9, 16, 1
```

Stream còn có rất nhiều phương thức và được chia làm 2 loại là phương thức trung gian và phương thức cuối. Phương thức trung gian là các phương thức mà khi được gọi sẽ không được thực hiện luôn mà sẽ được ghi nhớ, đến khi phương thức cuối được gọi thì các phương thức trung gian mới được thực thi (để máy tính có thể tối ưu các lệnh). Các phương thức trung gian sẽ trả về một đối tượng stream mới nên có thể nối tiếp với các phương thức khác của stream, có những phương thức trung gian hay dùng như sau:

- `map`: chuyển đổi từng phần tử thành phần tử khác.
- `filter`: lọc ra các phần tử theo tiêu chí nào đó.
- `sorted`: sắp xếp các phần tử.

Các phương thức cuối không trả về một stream mà có thể trả về một giá trị hoặc không trả về gì, có những phương thức cuối như sau:

- `forEach`: làm gì đó với từng phần tử.
- `count`: đếm số lượng phần tử.
- `min`: tìm giá trị nhỏ nhất.
- `max`: tìm giá trị lớn nhất.
- `anyMatch`: trả về `true` nếu có một phần tử thoả mãn điều kiện.
- `allMatch`: trả về `true` nếu tất cả thoả mãn điều kiện.

Ví dụ:

```java
int cnt = (int) Stream
    .of("Hello", "World", "I", "am", "learning", "Stream")
    .map(String::length)
    .filter(x -> x == 5)
    .count();

System.out.println(cnt); // In ra 2
```

Chương trình trên đếm các xâu có độ dài là `5` từ danh sách các xâu ban đầu.

.  
.  
.  

[Quay lại: Java nâng cao](..)
