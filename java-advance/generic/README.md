# Generic

#### Generic là gì?

Một lớp hay interface có thể có tham số là kiểu dữ liệu, khi đó lớp hay interface được gọi là kiểu generic (generic type).

#### Là sao?

Ví dụ có một lớp thể hiện một chiếc hộp, trong hộp đựng được một vật

```java
public class Box {
    private Object object;

    public void set(Object obj) {
        object = obj;
    }

    public Object get() {
        return object;
    }
}
```

Các phương thức nhận hoặc trả ra một đối tượng kiểu `Object` nên ta có thể truyền vào bất cứ thứ gì ta muốn (miễn là không phải kiểu dữ liệu cơ sở - primitive data type). Trình biên dịch không có cách nào để kiểm soát cách sử dụng đối tượng bên trong đối tượng `Box`. Ví dụ:

```java
Box box = new Box();
box.set(new Book());

Pen pen = (Pen) box.get();
```

Các câu lệnh trên vẫn sẽ biên dịch được, nhưng khi chạy sẽ bị lỗi do một đối tượng kiểu `Book` không thể ép kiểu sang `Pen` (giả sử `Book` và `Pen` không kế thừa nhau). Generic giúp đảm bảo sử dụng đúng các đối tượng ngay lúc biên dịch.

#### Bị lỗi lúc chạy rồi sửa cũng được mà?

Lỗi biên dịch mình sẽ luôn phát hiện ra luôn (do trình biên dịch báo), còn lỗi lúc chạy tuỳ thuộc vào mình chạy như thế nào, đầu vào là gì mà có thể sẽ không phát hiện ra. Nguy hiểm lắm .-.

#### Vậy sử dụng generic như thế nào?

Lớp `Box` có thể viết dưới dạng generic như sau:

```java
public class Box<T> {
    private T object;

    public void set(T obj) {
        object = obj;
    }

    public T get() {
        return object;
    }
}
```

`T` (nằm trong cặp dấu `<` và `>` khi định nghĩa lớp) là tham số đại diện cho kiểu dữ liệu mà lớp `Box` sẽ sử dụng. Dòng `private T object` khai báo đối tượng lớp `Box` sẽ có một đối tượng thuộc lớp `T`, phương thức `set` nhận vào một đối tượng `obj` thuộc lớp `T`, phương thức `get` trả ra một đối tượng cũng thuộc lớp `T`.

Khi sử dụng lớp generic như trên thì dùng như sau:

```java
Box<Book> box = new Box<Book>();
box.set(new Book());
Pen pen = (Pen) box.get(); // Bị lỗi biên dịch

Box<Pen> box2 = new Box<Pen>();
box2.set(new Pen());
Pen pen2 = box.get(); // OK
```

Khi viết `Box<Book>` thì tham số `T` trong lớp `Box` chuyển thành `Book`, đối tượng của lớp này chỉ chứa được đối tượng của lớp `Book` nên nếu ép kiểu `(Pen) box.get()` trình biên dịch sẽ biết và báo lỗi cho mình.

#### Nhận nhiều tham số kiểu dữ liệu được không?

Nếu nhiều tham số là kiểu dữ liệu thì các tham số cách nhau dấu phẩy trong cặp dấu `<` và `>`.

```java
public class Pair<K, V> {
    private K key;
    private V value;

    public Pair(K k, V v) {
        key = k;
        value = v;
    }

    public K getKey() {
        return key;
    }

    public V getValue() {
        return value;
    }
}
```

Khi sử dụng, các kiểu mình dùng cũng cách nhau bởi dấu phẩy

```java
Pair<String, Integer> pair = new Pair<String, Integer>("One", 1);
System.out.println(pair.getKey() + ": " + pair.getValue()); // In ra: One: 1
```

Để đỡ phải viết dài, ta còn có thể viết tắt như sau:

```java
Pair<String, Integer> pair = new Pair<>("One", 1);
System.out.println(pair.getKey() + ": " + pair.getValue()); // In ra: One: 1
```

Khi gặp lệnh `new Pair<>`, trình biên dịch sẽ suy đoán kiểu phù hợp dựa vào kiểu của tham chiếu ở vế trái.

Cần chú ý là không thể dùng các kiểu dữ liệu cơ sở làm tham số kiểu dữ liệu cho các lớp generic mà phải dùng các [wrapper class](../../terminology.md#wrapper-class) tương ứng.

#### Generic hay được sử dụng không?

Nhiều lớp và interface trong Java sử dụng generic, ví dụ interface `Comparable` thực ra là `Comparable<T>`.

```java
public interface Comparable<T> {
    public int compareTo(T t);
}
```

Ta có thể giới hạn đối tượng lớp `Book` chỉ có thể so sánh được với đối tượng khác cũng cùng lớp `Book` như sau:

```java
public class Book implements Comparable<Book> {
    @Override
    public int compareTo(Book other) {
        // ...
    }
}
```

#### Sao bình thường viết Comparable không cũng được mà?

Lớp `Box` viết generic như trên cũng có thể được sử dụng theo cách sau:

```java
Box box = new Box();
box.set(new Book());
Book book = (Book) box.get();
```

Khi đó tham số `T` sẽ được chuyển thành `Object`, tức là `box` có thể lưu được mọi loại đối tượng.

#### Hết chưa?

Mình còn có thể giới hạn được kiểu dữ liệu có thể đặt trong cặp dấu `<` và `>`. Ví dụ:

```java
public class Box<T extends Book> {
    // ...
}
```

Khi sử dụng lớp này, chỉ có thể thay `T` bằng các lớp thừa kế `Book`. Ngoài ra, nếu bên trong lớp `Box` không sử dụng đến `T` (vì có thể sử dụng `Book`) thì có thể dùng dấu `?` khi định nghĩa lớp `Box`

```java
public class Box<? extends Book> {
    // ...
}
```

Cũng có cả phương thức generic nữa nhưng thôi học nhiều quá lại chán mất .-.

.  
.  
.  

[Quay lại: Java nâng cao](..)
