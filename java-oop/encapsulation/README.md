# Đóng gói
*Kiến thức cần biết:* [class](../../terminology.md#class)

#### Đóng gói là gì?

Đóng gói ([encapsulation](../../terminology.md#encapsulation)) là nguyên tắc gộp những trường và phương thức liên quan vào chung một lớp đồng thời giấu dữ liệu, chi tiết cài đặt của một đối tượng khỏi các đối tượng khác. Các đối tượng khác chỉ có thể thao tác với đối tượng đó thông qua những gì đối tượng đó cho phép.

#### Sao mà cần tính đóng gói?

Để giảm bớt sự phức tạp cho người dùng. Những gì đối tượng cho phép sử dụng ([public interface](../../terminology.md#public-interface)) đại diện cho khả năng của đối tượng đó, người dùng chỉ cần quan tâm đối tượng làm được gì chứ không cần biết làm như thế nào cũng có thể sử dụng. Ví dụ sạc máy tính có public interface là một chân cắm vào máy tính và một chân cắm vào ổ điện, người sử dụng không biết cấu tạo bên trong thế nào. Hay trong Java, một đối tượng `String` có thể lưu giữ một chuỗi các kí tự nhưng một đối tượng `String` sử dụng trường gì, kiểu dữ liệu gì để lưu chuỗi đó thì người dùng không cần biết.

Người lập trình cũng dễ dàng thay đổi, tối ưu đối tượng của mình mà không ảnh hưởng đến người sử dụng nếu không làm thay đổi public interface. Ví dụ sạc máy tính thay đổi loại dây điện bên trong nhưng hai đầu cắm không thay đổi thì không ảnh hưởng đến người dùng.

#### Làm sao chương trình Java của mình có tính đóng gói?
Java có 4 [access modifier](../../terminology.md#access-modifier) là các từ khoá thêm vào trước các lệnh khai báo để kiểm soát quyền truy cập đến các trường và phương thức của đối tượng:
- `default`: các đối tượng của lớp trong cùng package có thể truy cập.
- `public`: mọi đối tượng đều có thể truy cập.
- `private`: chỉ các đối tượng trong cùng lớp mới có thể truy cập.
- `protected`: các đối tượng trong cùng lớp hoặc của lớp con (bài sau) có thể truy cập.

Khi khai báo trường hay phương thức cho một lớp thì thêm vào đầu câu lệnh khai báo một trong các access modifier trên sao cho hợp lý. Nếu không thêm thì mặc định là sử dụng `default`.

#### Vẫn không biết khi nào dùng cái access modifier nào?

Ví dụ có 3 lớp `Person`, `Cat` và `Program`:

```java
public class Person {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public void feed(Cat cat) {
        cat.eat();
    }

    public void namePet(Cat cat, String name) {
        cat.setName(name);
    }
}
```

```java
public class Cat {
    private String name;

    public String getName() {
        return this.name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void eat() {
        System.out.println(this.name + " is eating.");
        this.meow();
    }

    private void meow() {
        System.out.println("Meow.");
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Person person = new Person("A");
        Cat cat = new Cat();

        person.setName(cat, "B");
        person.feed(cat);
    }
}
```

Ở ví dụ trên, một đối tượng `Person` có một trường là `name`. Trường `name` khi đã tạo không muốn các đối tượng hay lớp khác thay đổi nên để là `private` (ví dụ phương thức `main` gọi `person.name` sẽ bị lỗi biên dịch). Các phương thức của đối tượng `Person` có thể truy cập từ bất cứ đâu (ví dụ phương thức `main` gọi `person.setName` hay `person.feed`). Đối tượng `Cat` cũng có trường `name` nhưng không được phép truy cập trực tiếp mà cần sử dụng thông qua 2 phương thức `setName` và `getName`. Một người có thể bảo mèo ăn nên để phương thức `eat` là `public`. Người không bảo mèo kêu meo được, việc kêu hay không tuỳ mèo quyết định nên phương thức `meow` để `private`.

Việc dùng access modifier nào tuỳ vào đặc điểm của bài toán. Nếu không có gì đặc biệt thì các trường nên để là `private` và các phương thức nên để là `public`.

#### Dùng setName và getName thì khác gì để name là public đâu?

Xét ví dụ như sau:

```java
public class Person {
    private int age;

    public void setAge(int age) {
        if (age > 0)
            this.age = age;
    }

    public int getAge() {
        return this.age;
    }
}
```

Phương thức `setAge` chỉ thay đổi trường `age` khi giá trị muốn cập nhật lớn hơn `0`. Sử dụng các phương thức `setAge` và `getAge` giúp giới hạn quá trình truy cập và thay đổi các trường, đảm bảo giá trị các trường luôn hợp lệ. Các phương thức này gọi là các [setter](../../terminology.md#setter) và [getter](../../terminology.md#getter). Ngay cả khi các getter và setter không làm thêm nhiệm vụ gì thì vẫn nên được sử dụng, để về sau nếu muốn kiểm soát việc truy cập các trường thì không cần thay đổi [public interface](../..terminology.md#public-interface) của đối tượng.

#### Lớp có dùng được các access modifier khác ngoài public không?
Lớp ngoài cùng (lớp không nằm trong khối lệnh nào, [outer class](../../terminology.md#outer-class)) chỉ có thể sử dụng 2 access modifier là `public` và `default`. Trong một file có thể có nhiều lớp ở ngoài cùng, tuy nhiên chỉ có một lớp được để là `public` và phải trùng với tên file.

#### Thế có lớp không ngoài cùng à?
Có thể có lớp bên trong lớp ([inner class](../../terminology.md#)), ví dụ:

```java

```

.  
.  
.  

*Từ khoá:* [encapsulation](../../terminology.md#encapsulation), [public interface](../../terminology.md#public-interface), [access modifier](../../terminology.md#access-modifier), [setter](../../terminology.md#setter), [getter](../../terminology.md#getter)

[Bài tập](exercise.md)

[Quay lại: Lập trình hướng đối tượng với Java](..)
