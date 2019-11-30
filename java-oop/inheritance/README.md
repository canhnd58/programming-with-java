# Thừa kế

*Kiến thức cần biết:* [class](../../terminology.md#class), [access modifier](../../terminology.md#access-modifier)

#### Thừa kế là gì?
Thừa kế ([inheritance](../../terminology.md#inheritance)) là nguyên tắc sử dụng những gì đã có của các đối tượng cho đối tượng mới, do rất nhiều đối tượng có tính chất tương tự nhau.

#### Sao mà cần thừa kế?
Để đỡ bị lặp [code](../../terminology.md#code), chương trình ngắn gọn.

#### Giờ muốn chương trình có tính thừa kế thì phải làm sao?
Sử dụng từ khoá `extends` khi khai báo lớp mới. Ví dụ:

```java
public class Pet {
    private String name;

    public void setName(String name) { this.name = name; }
    public String getName() { return name; }
}
```

```java
public class Cat extends Pet {
    public void meow() {
        System.out.println(this.getName() + ": meow!");
    }
}
```

```java
public class Dog extends Pet {
    public void bark() {
        System.out.println(this.getName() + ": woof!");
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Cat cat = new Cat();
        cat.setName("Dog");
        Dog dog = new Dog();
        dog.setName("Cat");

        cat.meow(); // In ra "Dog: meow!"
        dog.bark(); // In ra "Cat: woof!"
    }
}
```

Các đối tượng của lớp `Cat` và `Dog` đều có trường `name` và 2 phương thức `setName` và `getName` do lớp `Cat` và `Dog` thừa kế từ lớp `Pet`. Tuy nhiên cần chú ý đối tượng lớp `Cat` và `Dog` không thể truy cập trực tiếp đến trường `name` mà phải sử dụng thông qua phương thức `getName` như ở ví dụ. Lớp `Cat` và `Dog` được gọi là lớp con ([subclass](../../terminology.md#subclass)) của lớp `Pet`, lớp `Pet` được gọi là lớp cha ([super class](../../terminology.md#super-class)) của hai lớp kia. Nếu muốn các lớp con tuỳ ý thay đổi các trường của mình còn các lớp khác không thay đổi được thì lớp cha có thể sử dụng [access modifier](../../terminology.md#access-modifier) là `protected` thay cho `private`.

#### Sao bài trước phương thức meow là private mà?
Bài trước chưa bắt mèo kêu được còn giờ thì được rồi.

#### Lớp con thừa kế được những gì?
Lớp con thừa kế (dùng trực tiếp như của mình) được tất cả những [member variable](../../terminology.md#member-variable), [member method](../../terminology.md#member-method) và [inner class](../../terminology.md#inner-class) mà được khai báo với từ khoá `public` hay `protected` của lớp cha, trừ phương thức khởi tạo ([constructor](../../terminology.md#constructor)). Tuy nhiên, phương thức khởi tạo của lớp con có thể gọi đến phương thức khởi tạo của lớp cha bằng từ khoá `super`.

```java
public class Pet {
    private String name;

    public Pet(String name) {
        this.name = name;
    }
    ...
}
```

```java
public class Cat extends Pet {
    private String furColor;

    public Cat(String name, String furColor) {
        super(name);
        this.furColor = furColor;
    }
}
```


Câu lệnh `super(name)` là lời gọi đến phương thức khởi tạo một tham số (một đầu vào) của lớp `Pet`.

Cần chú ý khi tạo đối tượng lớp con thì chương trình cần tạo đối tượng lớp cha trước, vì thế phương thức khởi tạo của lớp con nếu không dùng từ khoá `super` thì trình biên dịch sẽ tự động thêm lời gọi đến hàm khởi tạo không có tham số của lớp cha. Lớp như sau:

```java
public class Cat extends Pet {
    private String furColor;

    public Cat(String name, String furColor) {
        this.name = name;
        this.furColor = furColor;
    }
}
```

khi biên dịch sẽ trở thành:

```java
public class Cat extends Pet {
    private String furColor;

    public Cat(String name, String furColor) {
        super();
        this.name = name;
        this.furColor = furColor;
    }
}
```

Nếu lớp cha không có phương thức khởi tạo không tham số mà lớp con có phương thức khởi tạo không gọi `super` sẽ bị lỗi biên dịch.

#### Khi nào nên dùng thừa kế?
Khi hai đối tượng có quan hệ *là một* (*is-a* relationship). Ví dụ chó là một thú nuôi thì lớp chó nên thừa kế từ lớp thú nuôi, tam giác là một hình vẽ thì lớp tam giác nên được thừa kế từ lớp hình vẽ.

#### Có lớp con của lớp con không?
Có, chẳng cần biết lớp cha thừa kế ở đâu chưa mình cứ thừa kế là có hết những cái `public` với `protected` của cha (thừa kế xong thì là của mình rồi).

#### Một lớp thừa kế nhiều lớp một lúc được không?
Java không cho phép một lớp thừa kế nhiều lớp. Ví dụ lớp `Dog` không được vừa là một `Pet` vừa là một `Food`, chọn một trong hai thôi. Có vài ngôn ngữ khác (như C++) cho phép đa thừa kế ([multiple-inheritance](../../terminology.md#multiple-inheritance)).

#### Có lớp nào không thừa kế được không?
Nếu lớp được khai báo thêm từ khoá `final` thì sẽ không thừa kế được.

```java
public final class Cat extends Pet {
    ...
}
```

```java
public class FluffyCat extends Cat { // Lỗi biên dịch
    ...
}
```

#### Không dùng thừa kế được không?
Mấy nguyên tắc lập trình hướng đối tượng là nên dùng thôi chứ không làm theo chương trình vẫn chạy. Tuy nhiên, bất cứ lớp nào trong Java nếu không viết gì thì trình biên dịch tựthêm `extends Object` tức là mọi lớp trong Java đều thừa kế từ lớp `Object`.

#### Tất cả đều thừa kế lớp Object thì có tác dụng gì?
Một biến tham chiếu thuộc kiểu dữ liệu cha có thể tham chiếu đến các đối tượng thuộc kiểu dữ liệu con. Ví dụ:

```java
Pet pet = new Cat();
```

Ta có thể tạo một mảng lưu các đối tượng bất kì như sau:
```java
Object[] objs = new Object[10];
objs[0] = new Cat();
objs[1] = new Dog();
objs[2] = new int[10]; // Mảng là một đối tượng
objs[3] = "Xau ki tu la mot doi tuong";
objs[4] = 1;
```

Ngoài ra có thể làm được một số thứ nữa nhờ vào việc các lớp đều thừa kế lớp `Object` và tính đa hình ở bài sau.

#### Các giá trị thuộc kiểu dữ liệu int có phải là đối tượng đâu nhỉ?
Đúng rồi, tuy nhiên trong Java có các lớp đặc biệt gọi là [wrapper class](../../terminology.md#wrapper-class). Với mỗi kiểu dữ liệu cơ sở có các wrapper class tương ứng:

|Kiểu dữ liệu|Wrapper class|
|---|---|
|`byte`|`Byte`|
|`short`|`Short`|
|`int`|`Integer`|
|`long`|`Long`|
|`float`|`Float`|
|`double`|`Double`|
|`char`|`Character`|
|`boolean`|`Boolean`|

Các wrapper class cũng lưu một giá trị giống với kiểu dữ liệu cơ sở nhưng tạo đối tượng và lưu tham chiếu. Ví dụ câu lệnh sau viết được bình thường:

```java
Integer i = 10; // thực ra là Integer i = new Integer(10);
```

Các giá trị cụ thể được trình biên dịch chuyển đổi từ kiểu kiểu dữ liệu cơ sở sang wrapper class và ngược lại khi cần thiết. Hoặc mình cũng có thể ghi rõ ép kiểu:

```java
int i = 1;
Integer objectI = (Integer) i;
```

Các wrapper class còn có nhiều phương thức khác nữa, tự tìm hiểu .-.

.  
.  
.  

*Từ khoá:* [inheritance](../../terminology.md#inheritance), [super class](../../terminology.md#super-class), [subclass](../../terminology.md#subclass)

[Bài tập](exercise.md)

[Quay lại: Lập trình hướng đối tượng với Java](..)
