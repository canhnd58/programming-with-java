# Trừu tượng

*Kiến thức cần biết:* [class](../../terminology.md#class), [inheritance](../../terminology.md#inheritance), [polymorphism](../../terminology.md#polymorphism)

#### Trừu tượng là gì?

Trừu tượng ([abstraction](../../terminology.md#abstraction)) là nguyên tắc mô tả các đối tượng thông qua những gì đối tượng có thể thực hiện thay vì cách thức các đối tượng thực hiện. Ngoài ra, trừu tượng cũng là việc bỏ qua những chi tiết không cần thiết của đối tượng.

#### Sao mà cần trừu tượng?

Trừu tượng cho phép thiết kế chương trình tập trung vào những gì đối tượng có thể làm.

#### Làm sao để chương trình mình có tính trừu tượng?

Thực ra khi viết các lớp mình chỉ chọn một vài trường thì cũng là có tính trừu tượng rồi. Ví dụ một người có tên, tuổi, nghề nghiệp, sở thích ... nhưng bài toán chỉ liên quan đến tuổi thì khi viết các lớp không cần đến các trường khác. Ngoài ra, tính trừu tượng trong Java cũng được thể hiện qua:

- [abstract class](../../terminology.md#abstract-class)
- [interface](../../terminology.md#interface)

#### Abstract class là gì?

Lớp trừu tượng ([abstract class](../../terminology.md#abstract-class)) là lớp có thể có một hay nhiều phương thức trừu tượng ([abstract method](../../terminology.md#abstract-method)) và được khai báo thông qua từ khoá `abstract` .-.

#### Thế phương thức trừu tượng là gì? @@

Phương thức trừu tượng là phương thức không có nội dung. Ví dụ:

```java
public abstract class Pet {
    public abstract void makeSound();
}
```

Không thể tạo một đối tượng thuộc lớp `Pet`, các lớp con có thể thừa kế từ lớp trừu tượng nhưng bắt buộc phải ghi đè ([override](../../terminology.md#overide)) tất cả các phương thức trừu tượng của lớp cha hoặc lớp con tiếp tục khai báo là lớp trừu tượng.

```java
public class Cat extends Pet {
    @Override
    public void makeSound() {
        System.out.println("meow meow");
    }
}
```

```java
public abstract Poultry extends Pet {
}
```

```java
public class Chicken extends Poultry {
    @Override
    public void makeSound() {
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        // Pet pet = new Pet(); bị lỗi
        Pet cat = new Cat();
        Pet chicken = new Chicken();

        cat.makeSound(); // in ra "meow meow"
        chicken.makeSound(); // in ra "chip chip"
    }
}
```

#### Sao mà phải làm như thế?
 
Khi mình muốn một thú nuôi bắt buộc phải là một con vật cụ thể như chó hoặc mèo hoặc gà, việc tạo một đối tượng `Pet` không có ý nghĩa lắm với cả một con `Pet` chung chung không biết kêu như thế nào nên để phương thức `makeSound` là `abstract`.

#### Những cái gì có thể để là abstract?

Chỉ lớp với [instance method](../../terminology.md#instance-method) mới có thể để là `abstract`. Tuy nhiên lớp trừu tượng vẫn có thể có các trường hay phương thức khác như bình thường.

#### Thế interface là gì?

[Interface](../../terminology.md#interface) có thể coi là một lớp hoàn toàn trừu tượng. Interface là tập hợp các phương thức trừu tượng và được khai báo với từ khoá `interface`.

```java
// File flyable.java
public interface Flyable {
    void fly();
}
```

Các phương thức trong `interface` mặc định là `public abstract` (tự viết thêm vào cũng được). Interface `Flyable` có thể dùng như một lớp trừu tượng bình thường (làm kiểu dữ liệu cho biến nhưng không thể khởi tạo đối tượng) nhưng khi thừa kế phải sử dụng từ khoá `implements`. Một lớp có thể vừa thừa kế một lớp khác và thừa kế nhiều `interface` một lúc.

```java
public class Chicken extends Poultry implements Flyable {
    @Override
    public void makeSound() {
        System.out.println("chip chip");
    }

    @Override
    public void fly() {
        System.out.println("flap flap");
    }
}
```

public class Plane implements Flyable {
    @Override
    public void fly() {
        System.out.println("umm umm");
    }
}

```java
public class Program {
    public static void main(String[] args) {
       Flyable object1 = new Chicken();
       Flyable object2 = new Plane();

        object1.fly(); // flap flap
        object2.fly(); // umm umm
    }
}
```

Nếu thừa kế nhiều interface thì các interface cách nhau dấu phẩy. Ví dụ: `public class Chicken implements Flyable, Cookable { ... }`.

#### Sao mà không dùng abstract class thay cho interface luôn?
Cũng được, nhưng nếu thế thì lớp con chỉ thừa kế được một lớp cha thôi.

#### Sao lớp chỉ thừa kế được một mà interface lại được nhiều?
Ví dụ có lớp `A` có phương thức `void say()` in ra màn hình chữ "A", là cha của lớp `B` và `C` ghi đè phương thức `say` và in ra lần lượt là "B" và "C". Nếu thừa kế được nhiều lớp một lúc, giả sử lớp `D` thừa kế cả lớp `B` và `C` nhưng không ghi đè phương thức `say` thì các câu lệnh có kết quả không xác định:

```java
   A obj = new D();
   obj.say(); // Không biết phải gọi phương thức trong lớp nào
```

Do tất cả các phương thức trong interface đều là trừu tượng, lớp con bắt buộc phải ghi đè nên không bị tình trạng như trên.

#### Interface chắc ít được dùng nhỉ?
Interface được dùng rất nhiều trong các package có sẵn. Ví dụ có interface `Comparable` trong package `java.lang` chỉ có một phương thức `int compareTo(Object obj)`, phương thức `sort` trong lớp `Arrays` gọi đến phương thức `compareTo` khi sắp xếp các phần tử trong mảng cho nên bất cứ lớp nào thừa kế interface `Comparable` thì mảng các đối tượng của lớp đó đều có thể được sắp xếp bằng phướng thức `sort`. Phương thức `compareTo` trả về một số âm nếu đối tượng đang xét đứng trước đối tượng `obj` khi sắp xếp. Lớp `String` cũng thừa kế từ interface `Comparable`.

```java
public class Pet implements Comparable {
    private int age;

    public Pet(int age) {
        this.age = age;
    }

    public int getAge() {
        return age;
    }

    @Override
    public int compareTo(Object obj) {
        Pet pet = (Pet) obj;
        return age < obj.getAge() ? -1 : (age == obj.getAge() ? 0 : 1);
    }

    @Override
    public String toString() {
        return "Pet[" + age + "]";
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Pet[] pets = new Pet[3];
        pets[0] = new Pet(10);
        pets[1] = new Pet(3);
        pets[2] = new Pet(5);

        Arrays.sort(pets);
        System.out.println(pets[0]); // In ra "Pet[3]"
    }
}
```

.  
.  
.  

*Từ khoá:* [abstract class](../../terminology.md#abstract-class), [abstract-method](../../terminology.md#abstract-method), [interface](../../terminology.md#interface)

[Bài tập](exercise.md)

[Quay lại: Lập trình hướng đối tượng với Java](..)
