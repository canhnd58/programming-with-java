# Package

*Kiến thức cần nhớ:* [class](../../terminology.md#class), [method](../../terminology.md#method), [field](../../terminology.md#field)

#### Lại còn package nữa à?
Ừa .-. nhưng package đơn giản lắm, chỉ để gộp các lớp lại vào một chỗ thôi.

#### Tạo ra một package như thế nào?
Nếu dùng NetBeans thì tạo một thư mục trong thư mục `src`, tên thư mục chính là tên package, sau đó tất cả các file trong thư mục thêm dòng `package <tên thư mục><dấu chấm phẩy>` ở đầu. Có thể tạo thư mục trong thư mục (package trong package), khi đó tên package sẽ là `<tên thư mục cha><dấu chấm><tên thư mục con>`. Ví dụ:

```
Project
    |---src
        |---shop
            |---user
            |   |---User.java
            |   |---Admin.java
            |   |---Client.java
            |
            |---order
            |   |---Order.java
            |   |---Item.java
            |   |---Cart.java
            |
            |---product
            |   |---Product.java
            |
            |---utils
                |---Date.java
                |---CurrencyConverter.java
```

Khi đó tên package của lớp `User` là `shop.user`, của lớp `Product` là `shop.product`.
Nội dung file `User.java` như sau:
```java
package shop.user;

public class User {
    ... // một số lệnh ở đây
}
```

#### Có quy tắc đặt tên package không?
Cách đặt tên giống tên biến, tuy nhiên nên ngắn gọn và để tất cả các chữ viết thường.

#### Có thể có các lớp cùng tên nhưng khác package không?
Có.

#### Lớp trong package này sử dụng lớp trong package khác được không?
Có, nhưng chỉ sử dụng được lớp, phương thức ([method](../../terminology.md#method)), trường ([field](../../terminology.md#field)) ở package khác nếu những lớp, phương thức, trường đó được khai báo với từ khoá `public`. Ví dụ lớp `Order` được khai báo như sau:

```java
// File Order.java
package shop.order;
public class Order {
    int id;

    public Order() {
        ...
    }
    public boolean cancel() {
        ...
    }
} 
```

thì các lớp trong package khác có thể tạo một đối tượng ([object](../../terminology.md#object)) `Order` mới do phương thức khởi tạo ([constructor](../../terminology.md#constructor)) được khai báo với từ khoá `public`, có thể gọi đến phương thức `cancel` nhưng không thể truy cập đến trường `id`.

Ngoài ra, khi lớp này dùng lớp khác phải viết đầy đủ tên lớp muốn dùng kèm tên package của lớp đó, ví dụ `shop.order.Order`. Chỉ khi các lớp cùng package hoặc lớp cần dùng được `import` thì mới không cần viết đầy đủ.

#### Import là sao?
Có ba cách truy cập đến lớp của các package khác:
- Dùng tên đầy đủ gồm tên package lẫn tên lớp. Ví dụ lớp `User` muốn sử dụng lớp `Order` trong package `shop.order` thì gọi `shop.order.Order`:

```java
// File User.java
package shop.user;

public class User {
    ...

    boolean cancelOrder(shop.order.Order anOrder) {
        anOrder.cancel();
        // Nếu viết anOrder.id sẽ bị lỗi biên dịch do id không khai báo với từ khoá public
        ...
    }
}
```

- Sử dụng từ khoá `import` kèm tên lớp ở đầu file muốn dùng, khi đó chỉ cần viết tên lớp là dùng được.

```java
// File User.java
package shop.user;

import shop.order.Order;

public class User {
    ...

    boolean cancelOrder(Order anOrder) {
        anOrder.cancel();
        ...
    }
}
```

- Sử dụng từ khoá `import` và dấu `*` để import tất cả lớp trong package.

```java
// File User.java
package shop.user;
import shop.order.*;

public class User {
    ...

    boolean cancelOrder(Order anOrder) {
        // Dùng được cả lớp Item và Cart
        anOrder.cancel();
        ...
    }
}
```

#### Vậy cứ khai báo cái gì thì để nó public hết luôn à?
Làm như vậy không bị lỗi biên dịch nhưng không đúng với các nguyên tắc lập trình lắm. Người lập trình nên cố gắng tách chương trình thành từng phần riêng biệt càng ít liên quan đến nhau càng tốt, phần này nên quan tâm đến phần khác ít nhất có thể. Ví dụ `id` của một đối tượng đơn hàng (`Order`) là thứ không nên bị thay đổi bởi những đối tượng khác cho nên không nên để là `public`.

Khi nào dùng `public` sẽ bàn cụ thể hơn ở phần *Lập trình hướng đối tượng với Java*, còn giờ cho hết `public` cũng được.

#### Import được các phương thức với trường của lớp khác không?
Có, nhưng chỉ import được [class variable](../../terminology.md#class-variable) được khai báo với từ khoá `final` và các [class method](../../terminology.md#class-method). Ví dụ trong lớp `Math` đã có sẵn:

```java
    public static final double PI = 3.141592653589793;
    public static double pow(double a, double b) {
        ...
    }
```

thì các lớp của mình có thể dùng biến `PI` và phương thức `pow` mà không cần ghi rõ `Math.PI` và `Math.pow` nếu thêm các dòng như sau ở đầu file:

```java
import static java.lang.Math.PI;
import static java.lang.Math.pow;
```

hoặc
```java
import static java.lang.Math.*;
```

Chú ý khi import các trường và phương thức thì có từ khoá `static` sau `import`.

#### Từ khoá final là gì?
Đó là từ khoá dùng khi khai báo biến để thể hiện biến đó sẽ không thay đổi giá trị trong suốt chương trình. Nếu có phần nào đó cố gắng gán biến đó sang một giá trị khác thì trình biên dịch sẽ báo lỗi.

#### Các từ khoá public static final có cần viết đúng thứ tự không?
Không, viết `final static public double PI = 3.141592653589793;` cũng được, miễn là phần `double PI = 3.141592653589793;` ở cuối.

#### Ô, lớp Math ở trong package java.lang à?
Ừa.

#### Sao bình thường dùng không cần import java.lang.Math nhỉ?
Khi biên dịch, trình biên dịch tự động thêm dòng `import java.lang.*;` vào trước các file mã nguồn của mình. Package `java.lang` chứa các lớp cơ bản nhất khi lập trình Java.

#### Package java.lang còn lớp nào nữa không?

Có các lớp:
    - `Math`: tính toán toán học, lượng giác.
    - `String`: khởi tạo và xử lý xâu kí tự.
    - `System`: đầu vào đầu ra chuẩn và một số phương thức liên quan đến hệ thống.
    - và một vài lớp nữa.

Có thể xem tất cả các lớp và phương thức các lớp trong package `java.lang` ở [đây](https://docs.oracle.com/javase/7/docs/api/java/lang/package-summary.html) hoặc lên google gõ `doc java.lang`. Các package đều có những tài liệu mô tả package có những gì và dùng như thế nào. 

#### String cũng là một lớp á, có thấy dùng từ khóa new để tạo đối tượng đâu?
Câu lệnh:

```java
String country = "Việt Nam";
```

thực ra là:

```java
String country = new String("Việt Nam");
```

Tức là biến `country` cũng là biến lưu tham chiếu. `String` được dùng nhiều trong khi người lập trình thì lại lười nên Java tạo ra cách viết thứ nhất để gõ cho nhanh. Ngoài ra, lớp `String` có rất nhiều phương thức giúp cho việc xử lý xâu:
- `int length()`: trả về số lượng kí tự có trong xâu.
- `char charAt(int index)`: trả về kí tự thứ `index` trong xâu (thứ tự tính từ `0`, tức là nếu `index = 0` thì đưa ra kí tự đầu tiên).
- `int compareTo(String anotherString)`: trả về `0` nếu hai xâu giống nhau, trả về một số âm nếu xâu đang xét (`this`) nhỏ hơn xâu `anotherString` theo [thứ tự từ điển](TLRD.md)
- `int indexOf(String str)`: trả về vị trí tính từ `0` của xâu `str` trong xâu đang xét, nếu không thì trả về `-1`.
- `String substring(int beginIndex, int endIndex)`: trả về một xâu con tính từ vị trí thứ `beginIndex` đến `endIndex-1`.

và một số phương thức khác tự tìm hiểu ở [đây](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html).

Ví dụ:

```java
public class Test {
    public static void main(String[] args) {
        String country = "Việt Nam";
        System.out.println(country.length());           // 8
        System.out.println(country.charAt(2));          // i
        System.out.println(country.compareTo("Vn"));    // một số âm nào đó
        System.out.println(country.indexOf("t N"));     // 3
        System.out.println(country.substring(1, 4));    // iệt
    }
}
```

.  
.  
.  

[Còn nữa, mà dài lắm đừng đọc](TLDR.md)

[Bài tập](exercise.md)

[Quay lại: Java căn bản](..)
