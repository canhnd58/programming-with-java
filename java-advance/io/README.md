# Java I/O

#### Là gì thế?

I/O là viết tắt của Input/Output (Vào/Ra). Java có package java.io chứa các lớp giúp chương trình đọc và ghi dữ liệu. Mình đã làm quen với đọc dữ liệu từ bàn phím và ghi dữ liệu ra màn hình, tuy nhiên dữ liệu còn có thể đọc và ghi từ file, mạng, thiết bị ngoại vi khác ...

#### Java.io có những lớp nào?

Nơi lấy dữ liệu để đọc gọi là nguồn dữ liệu (data source), nơi ghi dữ liệu ra gọi là đích dữ liệu (data sink). Việc xử lý vào ra dữ liệu trong Java được thực hiện thông qua khái niệm luồng (stream), luồng là chuỗi các byte liên tục mà mình có thể đọc ra hoặc ghi vào. Luồng cho phép thao tác tuần tự với nguồn và đích dữ liệu. Có hai lớp trừu tượng cơ bản nhất trong package java.io là `InputStream` đại diện cho luồng kết nối với nguồn dữ liệu và `OutputStream` đại diện cho luồng kết nối với đích dữ liệu.

Bên cạnh luồng các byte còn có luồng các kí tự, xử lý dữ liệu dưới dạng chuỗi các kí tự liên tục, được thể hiện bằng 2 lớp trừu tượng `Reader` và `Writer`.

Luồng làm việc với các byte còn gọi là luồng nhị phân, luồng làm việc với các kí tự gọi là luồng kí tự.

#### Dùng như thế nào?

Bởi vì các nguồn vào và ra thường nằm ngoài kiểm soát của chương trình nên các phương thức của các lớp này thường có ngoại lệ. Ví dụ nguồn dữ liệu là file thì lệnh đọc từ một file có thể có ngoại lệ `IOException` khi chương trình không có quyền đọc file đó. Các lớp này đều `implements` interface `Closable` nên đều có phương thức:
- `void close() throws IOException`: đóng luồng, giải phóng những tài nguyên mà chương trình sử dụng với luồng này.

`InputStream` và `OutputStream` làm việc với dữ liệu dưới dạng các byte (mọi thứ trong chương trình thực ra đều được lưu thành các byte, ví dụ số `65` lưu bằng 4 byte, kí tự `'1'` lưu bằng 2 byte). `InputStream` có các phương thức sau:
- `int read() throws IOException`: đọc byte tiếp theo, trả về số trong khoảng `0-255` đại diện cho byte đó (1 byte = 8 bit lưu được 2^8 = 256 số khác nhau) hoặc trả về `-1` nếu kết thúc luồng.
- `int read(byte[] b) throws IOException`: đọc tối đa `b.length` byte vào mảng `b`, phương thức trả về số byte đọc được, trả về `-1` nếu không còn byte nào trong luồng.

`OutputStream` có các phương thức sau:
- `void write(int b) throws IOException`: Viết byte `b` vào luồng.
- `void write(byte[] b) throws IOException`: Viết `b.length` byte từ mảng `b` vào luồng.

`Reader` và `Writer` làm việc với dữ liệu dưới dạng các kí tự (ví dụ muốn lưu số `65` vào một file thì mình chuyển nó thành 2 kí tự `'6'` và `'5'` rồi lưu). `Reader` có các phương thức:
- `void int read() throws IOException`: đọc một kí tự tiếp theo, trả về một số đại diện cho kí tự đọc được hoặc `-1` nếu kết thúc luồng.
- `void int read(char[] b) throws IOException`: đọc tối đa `b.length` kí tự vào mảng `b`, phương thức trả về số kí tự đọc được, trả về `-1` nếu đã kết thúc luồng.

`Writer` có các phương thức sau:
- `void write(int c) throws IOException`: Viết một kí tự vào luồng.
- `void write(String s) throws IOException`: Viết một xâu vào luồng.
- `void write(char[] b) throws IOException`: Viết một mảng kí tự vào luồng.

Ngoài ra còn có lớp `InputStreamReader` thừa kế từ `Reader` và `OutputStreamWriter` thừa kế từ `Writer` để chuyển đổi luồng nhị phân (luồng byte) sang luồng kí tự:

```java
OutputStream bos = ...;
Writer cos = new OutputStreamWriter(bos);
```

#### Cho ví dụ đi!

`InputStream`, `OutputStream`, `Reader` và `Writer` đều là lớp trừu tượng không ví dụ được. Để đọc và ghi dữ liệu vào file có các lớp cụ thể: `FileInputStream`, `FileOutputStream`, `FileReader`, `FileWriter`. Các lớp này có phương thức khởi tạo nhận vào một xâu là đường dẫn đến file hoặc nhận vào một đối tượng thuộc lớp `java.io.File` và có thể có ngoại lệ `FileNotFoundException` khi không tìm thấy file`. Ví dụ:

```java
import java.io.*;

public class FileOutputStreamExample {
    public static void main(String[] args) {
        FileOutputStream os = null;
        try {
            os = new FileOutputStream("C:\\Users\Canh\Desktop\example.dat");
            os.write(65);
        } catch (Exception e) {
            System.out.println("File bị sao ý");
        } finally {
            try {
                if (os != null) {
                    os.close();
                }
            } catch(IOException e) {
                System.out.println("Không đóng được file");
            }
        }
    }
}
```

Chương trình trên tạo ra file `example.dat` và lưu số 65 dưới dạng byte vào file đó. Do các thao tác với luồng dữ liệu thường phải gọi đến phương thức `close()` dù có ngoại lệ xảy ra hay không nên trong Java có cách viết tắt cho chương trình trên như sau:

```java
import java.io.*;

public class FileOutputStreamExample {
    public static void main(String[] args) {
        try (FileOutputStream os = new FileOutputStream("C:\\Users\Canh\Desktop\example.dat")) {
            os.write(65);
        } catch (Exception e) {
            System.out.println("File bị sao ý");
        }
    }
}
```

Đối tượng `os` tạo ra trong cặp dấu ngoặc đơn sau từ khoá `try` như trên sẽ tự động gọi phương thức `close` sau khi kết thúc các khối lệnh sau `try` (hoặc `catch` nếu có ngoại lệ xảy ra). Nếu muốn đóng nhiều đối tượng thì các lệnh tạo đối tượng luồng sau trong cặp dấu ngoặc sau từ khoá `try` cách nhau bởi dấu `;`


```java
try (
    OutputStream os = new ...;
    InputStream is = new ...;
    ...
) {
    ...
}
```

Để đọc từ file vừa tạo có thể viết một chương trình khác như sau:

```java
import java.io.*;

public class FileInputStreamExample {
    public static void main(String[] args) {
        try (InputStream is = new FileInputStream("C:\\Users\Canh\Desktop\example.dat")) {
            int number = is.read();
            System.out.println(number);
        } catch (Exception e) {
            System.out.println("File bị sao ý");
        }
    }
}
```

Chương trình sẽ in ra số `65` nếu file `example.dat` được tạo ra bằng chương trình bên trên. Nếu mình dùng hệ điều hành để mở file example.dat sẽ không thấy số `65` do số `65` lưu dưới dạng nhị phân (sẽ thấy chữ `A`) trong khi chương trình đọc file mặc định của hệ điều hành (chương trình Notepad trong Windows) đọc file dưới dạng văn bản (các kí tự). Nếu thay `FileOutputStream` bằng `FileWriter` và thay lệnh `write` như sau (file văn bản nên đặt đuôi là `.txt`):

```java
os.write("65");
```

Thì mình có thể mở file `example.dat` bằng hệ điều hành và thấy 2 kí tự `6` và `5`.

#### Vậy dùng luồng nhị phân hay luồng kí tự?

Bản chất mọi thứ trên máy tính đều lưu thành các byte nên các file thường lưu dưới dạng nhị phân (các byte) nếu file đó chỉ dùng cho chương trình của mình. Còn nếu muốn chương trình ngoài (ví dụ Notepad) cũng đọc được thì có thể lưu dưới dạng kí tự. Chủ yếu thấy cái nào tiện hơn thì dùng.

#### Hết chưa?

Còn có lớp để tăng tốc độ xử lý các luồng bằng việc sử dụng bộ nhớ đệm (buffer): `BufferedInputStream`, `BufferedOutputStream`, `BufferedReader`, `BufferedWriter`. Việc đọc và ghi nhiều dữ liệu một lúc ra các thiết bị ngoài thường nhanh hơn đọc và ghi nhiều lần mỗi lần ít dữ liệu (đi đi lại lại nhiều mỗi lần mang một ít lần lâu hơn đi một lần nhưng mang nhiều .-.). Khi sử dụng các lớp có buffer, dù mình có đọc từng kí tự một bằng `read(int)` thì luồng sẽ vẫn đọc nhiều kí tự, trả ra cho mình một kí tự còn các kí tự còn lại lưu vào buffer (buffer chỉ là một mạng tạo thêm), những lần đọc sau sẽ đọc từ buffer nếu vẫn còn dữ liệu trong buffer.

Ví dụ về cách dùng:
```java
try (BufferedReader br = new BufferedReader(new FileReader("example.txt"))) {
    ...
} catch (Exception e) {
    ...
}
```

Cũng có cả các lớp như `PrintStream` (thừa kế từ `OutputStream`) và `PrintWriter` (thừa kế từ `Writer`) có thêm các phương thức để dễ dàng ghi vào luồng như `print`, `println` ...

.  
.  
.  

[Quay lại: Java nâng cao](..)

