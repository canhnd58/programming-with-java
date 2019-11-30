# Đa hình

*Kiến thức cần biết:* [class](../../terminology.md#class), [inheritance](../../terminology.md#inheritance), [public interface](../../terminology.md#public-interface)

#### Đa hình là gì?

Đa hình ([polymorphism](../../terminology.md#polymorphism)) là nguyên tắc viết chương trình sao cho một hành động có thể thực hiện theo nhiều cách, tuỳ thuộc vào đối tượng nào đang thực hiện hành động hoặc hành động được thực hiện với các đối tượng nào.

#### Sao mà cần đa hình?

Đa hình giúp chương trình tự nhiên hơn .-. Chắc thế .-.

#### Làm sao để chương trình mình có tính đa hình?

Tính đa hình được thực hiện qua 2 cách:
- [method overriding](../../terminology#method-overriding)
- [method overloading](../../terminology#method-overloading)

#### Method overriding là gì? @@

Khi một lớp con thừa kế một lớp cha, lớp con đó có thể khai báo thêm phương thức cùng tên cùng tham số với lớp cha (ghi đè). Cách viết như vậy gọi là [method overiding](../../terminology.md#method-overriding). Một biến tham chiếu của lớp cha có thể tham chiếu tới một đối tượng thuộc lớp con bằng việc ép kiểu ([type casting](../../terminology.md#type-casting)). Khi biến đó gọi phương thức thì tuỳ thuộc đối tượng đang tham chiếu thuộc lớp nào mà gọi phương thức của lớp đó. Ví dụ:

```java
public class Pet {
    public void makeSound() {
        System.out.println("pet pet");
    }
}
```

```java
public class Cat extends Pet {
    @Override
    public void makeSound() {
        System.out.println("meow meow");
    }
}
```

```java
public class Dog extends Pet {
    @Override
    public void makeSound() {
        System.out.println("woof woof");
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Pet pet1 = (Pet) new Cat();
        Pet pet2 = (Pet) new Dog();
        pet1.makeSound(); // meow meow
        pet2.makeSound(); // woof woof
    }
}
```

Việc ép kiểu từ lớp con sang lớp cha ([upcasting](../../terminology.md#upcasting)) sẽ tự động được thêm nếu trình biên dịch thấy cần. Do đó lớp `Program` có thể viết ngắn gọn hơn như sau:

```java
public class Program {
    public static void main(String[] args) {
        Pet pet1 = new Cat();
        Pet pet2 = new Dog();
        pet1.makeSound(); // meow meow
        pet2.makeSound(); // woof woof
    }
}
```

Việc phương thức nào được sử dụng được quyết định khi chạy chương trình ([dynamic binding](../../terminology.md#dynamic-binding)), đối tượng hiện tại thực sự là của lớp nào thì chạy phương thức trong lớp tương ứng, cho nên cách viết như trên còn được gọi là dynamic polymorphism hay runtime polymorphism.

#### Dòng @Override là cái gì vậy?

Dòng đó gọi là [annotation](../../terminology.md#annotation) là các dòng để thông báo với trình biên dịch là mình đang ghi đè phương thức, cũng để người đọc biết là đang ghi đè. Bất cứ khi nào muốn ghi đè phương thức thì nên viết `@Override` lên trên phương thức đó. Khi biên dịch, trình biên dịch sẽ kiểm tra nếu không phải đang ghi đè thì trình biên dịch sẽ báo lỗi cho mình biết. Không có dòng `@Override` vẫn chạy được. Các annotation chỉ có tác dụng yêu cầu trình biên dịch kiểm tra thêm cho chương trình của mình.


#### Sao không để là pet1 là Cat với pet2 là Dog luôn đi?

Cũng được, nhưng khi mình muốn đối xử với `Cat` và `Dog` như nhau thì nên để kiểu dữ liệu là `Pet`.

```java
public class Person {
    public void feed(Pet pet) {
        pet.makeSound();
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Pet pet1 = new Cat();
        Pet pet2 = new Dog();
        Person person = new Person();
        person.feed(pet1); // meow meow
        person.feed(pet2); // woof woof
    }
}
```

Ở ví dụ trên, phương thức `feed` trong lớp `Person` chỉ nhận vào một tham số thuộc kiểu `Pet` nhưng ta vẫn có thể truyền các đối tượng thuộc lớp `Cat` và `Dog` vào được do hai biến `pet1` và `pet2` được khai báo là biến tham chiếu kiểu `Pet`. Tuy nhiên do [upcasting](../../terminology.md#upcasting) tự động được thực hiện nên để kiểu dữ liệu biến `pet` là `Cat`, biến `pet2` là `Dog` vẫn được.


```java
public class Program {
    public static void main(String[] args) {
        Cat cat = new Cat();
        Dog dog = new Dog();
        Person person = new Person();
        person.feed(cat); // meow meow
        person.feed(dog); // woof woof
    }
}
```

Hai câu lệnh cuối thực ra là:

```java
        person.feed((Pet) cat);
        person.feed((Pet) dog);
```

#### Vậy biến nên để kiểu dữ liệu là lớp cha hay lớp con?

Không biết .-. thấy cái nào hợp lý thì dùng thôi .-. Thường thì khi mình muốn đối xử với các đối tượng của lớp con như nhau thì để kiểu dữ liệu là lớp cha vì [public interface](../../terminology.md#public-interface) của lớp cha đơn giản hơn lớp con. Tuy nhiên cần chú ý là khi ép sang kiểu của lớp cha thì những phương thức chỉ có trong lớp con sẽ không gọi được. Ví dụ:

```java
public class GuardDog extends Dog {
    public void guard() {
        System.out.println("Guarding");
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Pet pet = new GuardDog();
        pet.makeSound(); // woof woof
        pet.guard(); // Lỗi biên dịch
    }
}
```

Câu lệnh `pet.makeSound()` in ra `woof woof` do thừa kế từ lớp `Dog` và do tính đa hình (nên không in ra `pet pet`). Câu lệnh `pet.guard()` bị lỗi biên dịch do biến thuộc kiểu `Pet` không biết đến phương thức `guard`. Nếu muốn gọi đến phương thức `guard` thì ta cần ép kiểu cho biến `pet` sang kiểu `GuardDog` như sau:

```java
        ((GuardDog) pet).guard();
```

hay thêm một biến:

```java
        GuardDog gdog = (GuardDog) pet;
        gdog.guard(); // In ra "Guarding"
```

Việc ép từ lớp cha sang lớp con được gọi là [downcasting](../../terminology.md#downcasting). Vì downcasting không phải lúc nào cũng làm được (chỉ khi đối tượng đó thực sự thuộc lớp con) nên trình biên dịch không tự động thêm mà mình phải ghi cụ thể như ở trên.

#### Khi sử dụng method overriding thì không sử dụng được phương thức đã bị ghi đè à?
Một đối tượng vẫn có thể truy cập được đến phương thức đã bị ghi đè bằng từ khoá `super`:

```java
public class AnnoyingPet extends Pet {
    @Override
    public void makeSound() {
        super.makeSound();
        super.makeSound();
        super.makeSound();
    }
}
```

#### Ghi đè được trường của lớp cha không?
Có, và cũng có thể dùng từ khoá `super` để truy cập đến trường bị ghi đè.

#### Có phương thức nào không ghi đè được không?
Phương thức ở lớp cha được khi báo với từ khoá `final` thì không thể ghi đè được.

#### Có thể ghi đè được các phương thức nào của lớp Object?
Có một vài phương thức hay dùng của lớp `Object` mà bất cứ lớp nào cũng có thể ghi đè hoặc sử dụng luôn:

- `int hashCode()`: trả về một số độc nhất đại diện cho đối tượng hiện tại.

- `String toString()`: trả về một xâu biểu diễn cho đối tượng hiện tại theo định dạng `<tên lớp>@<hashCode ở cơ số 16>`. Ví dụ phương thức `void println(Object obj)` của đối tượng `System.out` gọi đến `obj.toString()` để in ra màn hình nên ta có thể ghi đè phương thức `toString` để in ra theo cách mình muốn. Ví dụ câu lệnh `System.out.println(new Pet("Meo", 3));` sẽ in ra `[Meo]: 3` với lớp `Pet` như sau:

```java
public class Pet {
    private String name;
    private int age;

    public Pet(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public void toString() {
        return "[" + name + "]: " + age;
    }
}
```

- `boolean equals(Object obj)`: trả về `true` nếu đối tượng đang xét và `obj` cùng là một object.

#### Thế method overloading là gì?

Trong một lớp có thể có nhiều phương thức cùng tên nhưng khác tham số như sau:

```java
public class Pet {
    private int age;

    public Pet() {
        age = 0;
    }

    public int getAge() {
        return age;
    }

    public void growUp() {
        age ++;
    }

    public void growUp(int numYear) {
        age += numYear;
    }
}
```

```java
public class Program {
    public static void main(String[] args) {
        Pet pet = new Pet();
        pet.growUp();
        pet.growUp(10);
        System.out.println(pet.getAge()); // In ra 11
    }
}
```

Ở ví dụ trên, tuy hai phương thức `growUp` có cùng tên nhưng nhận các tham số khác nhau nên trình biên dịch coi 2 phương thức đó là hai phương thức khác nhau. Tuỳ vào tham số mà phương thức phù hợp được gọi. Khi chạy chương trình các phương này đã được phân biệt từ trước rồi (trình biên dịch sinh ra hai phương thức khác nhau rồi - [static binding](../../terminology.md#static-binding)) nên cách viết này còn được gọi là `static polymorphism`.

#### Có nhiều phương thức khởi tạo cùng tên được không?
Được. Và phương thức khởi tạo này còn có thể gọi đến phương thức khởi tạo khác thông qua từ khoá `this`.

```java
public class Pet {
    private int age;
    private String name;

    public Pet(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Pet(String name) {
        this(name, 0);
    }

    public Pet() {
        this("", 0);
    }
}
```

Lớp `Pet` như ở trên cho phép tạo đối tượng `Pet` bằng 3 cách: không tham số, một tham số `String` và hai tham số `String` và `int`. Lệnh `new Pet()` sẽ gọi đến phương thức khởi tạo không tham số, phương thức đó lại gọi đến phương thức khởi tạo hai tham số nên sẽ tạo một đối tượng có `name` là xâu rỗng và `age` là `0`.

#### Có thể có bao nhiêu phương thức cùng một tên?
Bao nhiêu cũng được.

.  
.  
.  

*Từ khoá:* [polymorphism](../../terminology.md#polymorphism), [method overriding](../../terminology.md#method-overriding), [method-overloading](../../terminology.md#method-overloading), [upcasting](../../terminology.md#upcasting), [downcasting](../../terminology.md#downcasting)

[Bài tập](exercise.md)

[Quay lại: Lập trình hướng đối tượng với Java](..)
