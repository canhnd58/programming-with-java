# Khai báo lớp và khởi tạo đối tượng
*Kiến thức cần biết:* [method](../../terminology.md#method)

#### Lớp chỉ là chỗ để gộp các phương thức lại thôi đúng không?
Đó là một tác dụng của lớp.

Trong Java đã có sẵn lớp tên là `Math` trong đó có các phương thức đã được khai báo ([declaration](../../terminology.md#declaration)) từ trước để thực hiện các việc tính toán toán học, mình chỉ cần gọi phương thức là dùng được. Ví dụ gọi `Math.sqrt(4)` mình sẽ thu được kết quả là `2` (căn 4) hay `Math.pow(2, 3)` mình sẽ thu được kết quả là `8` (2 mũ 3). Cũng có nhiều lớp khác đã có sẵn khi cài [JDK](../../terminology.md#jdk), hoặc mình có thể tải thêm trên mạng về dùng. Một số lớp quan trọng sẽ giới thiệu ở các phần sau.

Mình cũng có thể tạo ra một lớp như vậy chứa các phương thức mình hay dùng (hoặc cho người khác dùng), ví dụ:
```java
// File src/mypackage/MyUtils.java
package mypackage;

public class MyUtils {
    static void greet(String name, int age) {
        System.out.println("Chào " + (age > 25 ? "cô " : "bạn ") + name);
    } 
    static void drawLine() {
        System.out.println("------------------");
    }
}
```

Tất cả các file khác cùng thư mục (cùng package) đều có thể sử dụng các phương thức trong lớp vừa tạo (dùng giống như dùng lớp `Math`).

Ví dụ:
```java
// File src/mypackage/MyProgram.java
package mypackage;

public class MyProgram {
    public static void main(String[] args) {
        MyUtils.drawLine();
        greet("A", 20);
        MyUtils.drawLine();
    }
}
```

Nhưng có một tác dụng khác quan trọng hơn của lớp là để tạo ra các đối tượng.

#### Đối tượng là gì?
Đối tượng ([object](../../terminology.md#object)) nếu nhìn dưới góc nhìn của máy tính thì giống như biến, là các vùng nhớ lưu giữ trạng thái của chương trình. Tuy nhiên, một đối tượng gồm các biến và phương thức. Thay vì việc chỉ lưu trữ các giá trị cụ thể, một đối tượng có các phương thức để thay đổi các giá trị của nó và tương tác với các đối tượng khác.

Nhìn dưới góc độ người lập trình, một đối tượng đại diện cho một sự vật, một thực thể. Ví dụ một người tên `A` là một đối tượng, khi nói đến `A` giả sử mình chỉ quan tâm đến cân nặng và chiều cao của `A` thì đối tượng `A` sẽ gồm 2 biến là `chieuCao` và `canNang` và có thể có các phương thức như `tinhChiSoBMICuaMinh` hay `tangChieuCaoCuaMinhLenMotDonVi`.

#### Vẫn không hiểu vì sao cần dùng đối tượng?

Không nhất thiết cần dùng.

Để giải quyết một vấn đề ta cần xác định các *bước* cụ thể mà nếu làm theo lần lượt thì vấn đề sẽ được giải quyết. Trong lập trình, các bước như thế chính là các câu lệnh ([statement](../../terminology.md#statement)). Lập trình có thể chỉ cần viết các câu lệnh liên tiếp nhau mà không cần tạo ra phương thức hay lớp mới. Thực tế thì một số chương trình nhỏ dùng một lần (thường gọi là các [script](../../terminology.md#script)) ít khi viết thêm lớp mới hay thậm chí cả phương thức mới. Ví dụ để tính chỉ số BMI của một người sẽ có các bước là lấy bình phương chiều cao, sau đó lấy cân nặng chia bình phương chiều cao là được chỉ số BMI.

Với các bài toán lớn hơn có quá nhiều các bước, người ta thường chia thuật toán thành các *công việc*. Sau đó, việc giải quyết các bài toán là giải quyết lần lượt các công việc. Trong lập trình, các công việc chính là các phương thức ([method](../../terminology.md#method)), hay còn gọi là hàm hoặc thủ tục. Cách lập trình như vậy gọi là lập trình thủ tục ([procedural programming](../../terminology.md#procedural-programming)), tức việc thiết kế chương trình xoay quanh việc nghĩ giờ cần phương thức nào, các phương thức làm việc gì. Ví dụ để tìm ra người béo nhất trong 3 người ta sẽ cần các phương thức như: tính chỉ số BMI khi biết cân nặng và chiều cao, tìm số lớn nhất trong ba số.

Với bài toán có quá nhiều công việc, người ta tìm các *sự vật* có trong bài toán, mỗi *sự vật* phụ trách một số công việc của nó. Trong lập trình, các sự vật được gọi là các đối tượng ([object](../../terminology.md#object) (hay còn gọi là các thực thể ([instance](../../terminology.md#instance))). Các đối tượng có thuộc tính (biến) và các phương thức của chúng, tương tác với nhau qua các phương thức để thay đổi thuộc tính của mình rồi giải quyết bài toán ban đầu. Cách lập trình như vậy gọi là lập trình hướng đối tượng ([object-oriented programming](../../terminology.md#object-oriented-programming), tức việc thiết kế chương trình xoay quanh việc thiết kế các đối tượng. Với cùng ví dụ tìm người béo nhất trong 3 người như trên, sẽ cần 3 đối tượng mỗi đối tượng đại diện cho một người, mỗi đối tượng có thuộc tính chiều cao và cân nặng, mỗi đối tượng có phương thức tính chỉ số BMI của mình.

Với một vấn đề ta có thể chọn cách lập trình nào cũng được.

#### Thế không cần học lập trình hướng đối tượng được không?
Được, nhưng có sẵn rất nhiều lớp trong Java viết theo kiểu hướng đối tượng, không biết hướng đối tượng là gì thì sao dùng được.

#### Lớp với đối tượng có quan hệ gì?
Giống như để gọi phương thức ([method invocation](../../terminology.md#method-invocation)) thì trước đó cần tạo ra một phương thức (khai báo phương thức), để tạo ra một đối tượng thì trước đó cần tạo ra một lớp ([class](../../terminology.md)) (khai báo lớp). Tạo ra một lớp giống như mình mô tả cho máy tính một khái niệm mới, khi máy tính đã biết đến khái niệm đó rồi mình có thể yêu cầu máy tính tạo ra một thực thể của khái niệm đó (hay đối tượng của lớp đó). Ví dụ: con người là một khái niệm (một lớp), bạn "Nguyễn Đức Cảnh" là một thực thể (một đối tượng) con người.

#### Tạo ra lớp mới như thế nào?
Cú pháp tạo một lớp mới như thế này:
```
class <tên lớp><khối lệnh>
```

Một lớp gồm các trường ([field](../../terminology.md#field)) và các phương thức ([method](../../terminology.md#method)). Trường là các thuộc tính của 1 đối tượng của lớp đó. Phương thức là các hành vi của 1 đối tượng của lớp đó. Ví dụ để mô tả một người nhưng chỉ quan tâm đến tên, chiều cao, cân nặng, một người có khả năng tự tính được chỉ số BMI của mình thì có thể khai báo một lớp `Person` như sau:

```java
package example;

public class Person {
    String name;
    double weight, height;

    double getBMI() {
        return this.weight / (this.height * this.height);
    }
}
```

#### this là cái gì thế?
Các biến thuộc một phương thức được gọi là [local variable](../../terminology.md#local-variable), các biến khác gọi là [member variable](../../terminology.md#member-variable) hay có tên khác là thuộc tính ([attribute](../../terminology.md#attribute)) hoặc trường ([field](../../terminology.md#field)). Ví dụ `name`, `weight` và `height` là member variable.

Tại một thời điểm có thể có một local variable cùng tên với một member variable, lúc đó muốn truy cập đến member variable ta phải dùng từ khoá `this`.

`this` là từ khoá dùng trong phương thức của một đối tượng để truy cập đến thuộc tính hoặc phương thức khác của đối tượng đó. Từ khoá `this` dùng để phân biệt thuộc tính cuả đối tượng với biến trong phương thức. Trong phương thức `getBMI` trên có thể tạo ra thêm các biến tên là `name`, `weight`, `height`. Nếu phương thức không có các biến cùng tên với thuộc tính thì ta có thể viết tắt bằng cách bỏ đi từ khoá `this`.

```java
    double getBMI() {
        return weight / (height * height);
    }
```

#### Rồi dùng lớp đó như thế nào?
Ta dùng [toán tử](../../terminology.md#operator) `new` để tạo ra một đối tượng của một lớp như sau:

```java
new Person();
```

Câu lệnh trên sẽ yêu cầu máy tính cấp cho chương trình vùng nhớ để lưu một đối tượng `Person` (gồm các biến và phương thức của lớp `Person`). Việc tạo ra một đối tượng như vậy gọi là khởi tạo đối tượng ([object initialization](../../terminology.md#object-initialization)). Toán tử `new` sau khi tạo đối tượng sẽ trả về tham chiếu ([reference](../../terminology.md#reference)) đến đối tượng đó. Tham chiếu có thể hiểu là vị trí của đối tượng đó trong bộ nhớ, mình sẽ thao tác với đối tượng thông qua tham chiếu của nó. Có thể tạo ra một biến lưu tham chiếu như sau:

```java
Person canh;
```

Có thể gán tham chiếu của đối tượng mới tạo ra vào biến tham chiếu `canh` như sau:

```java
canh = new Person();
```

Như vậy có thể coi `Person` là kiểu dữ liệu mới, các biến thuộc kiểu dữ liệu `Person` lưu các tham chiếu đến các đối tượng thuộc lớp `Person`. Trong một phương thức của một đối tượng, từ khoá `this` chính là tham chiếu đến đối tượng đang xét.

Biến tham chiếu còn có thể lưu giá trị đặc biệt là `null` để thể hiện đang không chứa tham chiếu đến đối tượng nào. Ví dụ:

```java
Person noone = null;
```

#### Tạo đối tượng rồi dùng nó thế nào?
Có thể truy cập đến các thuộc tính và phương thức của đối tượng thông qua toán tử `.`. Ví dụ chương trình sau tính chỉ số BMI của một người sử dụng lớp `Person` như đã khai báo ở trên:


```java
// File này nằm cùng thư mục với file Person.java
package example;

public class Program {
    public static void main(String[] args) {
        Person canh = new Person();
        canh.weight = 50;
        canh.height = 1.7;
        canh.name = "Canh";
        System.out.println("Chỉ số BMI của " + canh.name + " là " + canh.getBMI());
    }
}
```

#### Chương trình trên không dùng lớp viết ngắn hơn mà?
Ừa, không dùng thì như thế này:

```java
public class Program {
    public static void main(String[] args) {
        double weight = 50;
        double height = 1.7;
        double name = "Canh";
        System.out.println("Chỉ số BMI của " + name + " là " + (weight/(height*height)));
    }
}
```

Đúng là chương trình ngắn hơn, tuy nhiên phương thức `main` lại cần quan tâm đến việc tính chỉ số BMI thế nào. Nếu không dùng đối tượng thì phương thức `main` sẽ cần quan tâm đến rất nhiều thứ, người lập trình phải quan tâm đến tất cả ngóc ngách của chương trình khi viết phương thức `main`. Ngược lại nếu dùng đối tượng, phương thức `main` biết là một đối tượng của lớp `Person` có khả năng tự tính được chỉ số BMI của nó nên chỉ cần gọi đến phương thức `getBMI` chứ không quan tâm phương thức đó tính như thế nào.

#### Tạo ra nhiều đối tượng được không?
Có, mỗi khi tạo đối tượng máy tính sẽ cấp cho chương trình một vùng nhớ mới, vì thế các thuộc tính của các đối tượng sẽ không liên quan đến nhau (do là các vùng nhớ khác nhau). Ví dụ:

```java
public static void main(String[] args) {
    Person canh = new Person();
    Person thanh = new Person();

    canh.weight = 50;
    thanh.weight = 78;
}
```

Ở ví dụ trên, đối tượng có tham chiếu trong biến `canh` (gọi tắt là đối tượng `canh`) có thuộc tính `weight` là `50` trong khi đối tượng `thanh` có thuộc tính `weight` là `78`.

#### Sao chỗ tạo đối tượng mới có cái ngoặc đơn ở cuối giống lời gọi phương thức thế?
Khi viết `Person()` thực ra là đang gọi đến phương thức khởi tạo của lớp `Person`.

#### Phương thức khởi tạo là gì? @@
Một lớp luôn có một phương thức đặc biệt được gọi mỗi khi tạo ra một đối tượng mới gọi là phương thức khởi tạo ([constructor](../../terminology.md#constructor)). Nếu không viết phương thức này thì [trình biên dịch](../../terminology.md#compiler) tự tạo một phương thức khởi tạo có khối lệnh rỗng. Lớp `Person` ở trên đầy đủ sẽ như sau:

```java
package example;

public class Person {
    String name;
    double weight, height;

    // Đây là phương thức khởi tạo - constructor
    Person() {
    }

    double getBMI() {
        return this.weight / (this.height * this.height);
    }
}
```

Chú ý là phương thức khởi tạo không có kiểu dữ liệu đầu ra (không có cả từ khoá `void`) và tên của phương thức phải trùng với tên lớp.

#### Vậy phương thức khởi tạo dùng để làm gì?
Nếu muốn làm gì đó khi tạo đối tượng mới thì mình viết trong phương thức khởi tạo. Ví dụ:

```java
package example;

public class Person {
    String name;
    double weight, height;

    // Đây là phương thức khởi tạo - constructor
    Person() {
        name = "Không có tên";
        weight = 50;
        height = 1.7;
    }

    double getBMI() {
        return this.weight / (this.height * this.height);
    }
}
```

Nếu dùng lớp `Person` như trên thì đối tượng mới luôn có `weight` là `50`, `height` là `1.7`, `name` là `Không có tên` vì phương thức khởi tạo tự động được gọi khi tạo đối tượng. Nếu mình viết hàm khởi tạo thì trình biên dịch sẽ không tạo ra hàm khởi tạo mặc định nữa.

#### Phương thức khởi tạo có thể nhận đầu vào được không?
Có, ví dụ:

```java
package example;

public class Person {
    string name;
    double weight, height;

    Person(string name, double weight, double height) {
        this.name = name;
        this.weight = weight;
        this.height = height;
    }

    double getBMI() {
        return this.weight / (this.height * this.height);
    }

    void speak() {
        System.out.println("Chỉ số BMI của " + this.name + " là " + this.getBMI());
    }
}
```

thì có thể được dùng như này:

```java
// File này nằm cùng thư mục với file Person.java
package example;

public class Program {
    public static void main(String[] args) {
        Person canh = new Person("Cảnh", 50, 1.7);
        Person thanh = new Person("Thành", 78, 1.7);

        canh.speak();
        thanh.speak();
    }
}
```

Khi gặp lệnh `new Person("Cảnh", 50, 1.7)`, chương trình tạo ra đối tượng mới đồng thời gán các thuộc tính của đối tượng đó `name` là `"Cảnh"`, `weight` là `50`, `height` là `1.7`, sau đó gán tham chiếu vào `canh`. Biến `thanh` cũng tương tự như vậy nên sẽ in ra màn hình:

```
Chỉ số BMI của Cảnh là 17.301038062283737
Chỉ số BMI của Thành là 26.989619377162633 
```

#### Ơ mà sao phương thức getBMI và speak không có chữ static nhỉ?
Từ khoá `static` làm thay đổi ý nghĩa của phương thức mình khai báo. Nếu không có `static`, phương thức đó sẽ thuộc vào một đối tượng, có thể truy cập được đến các thuộc tính của đối tượng đó, cũng truy cập được đến các phương thức khác của đối tượng đó (dùng `this` hoặc không đều được). Phương thức như vậy gọi là [instance method](../../terminology.md#instance-method). Nếu có `static` thì phương thức đó thuộc về một lớp, không cần tạo đối tượng cũng gọi được và cũng không thể truy cập được đến thuộc tính hay instance method thông qua từ khoá `this` (vì không tạo đối tượng thì biết `this` là cái gì). Phương thức như vậy gọi là [class method](../../terminology.md#class-method).

#### Một lớp vừa có instance method vừa có class method được không?
Được, ví dụ:


```java
package example;

public class Person {
    ... // Giống hệt ở trên

    // Phương thức đưa ra chỉ số BMI tối đa được coi là gầy
    static double getMaxBMIForUnderweight() {
        return 18.5;
    }
}
```

Gọi phương thức `getMaxBMIForUnderweight` như sau:
```java
double underWeightBMI = Person.getMaxBMIForUnderweight();
```

Còn gọi phương thức `getBMI` như sau:
```java
Person canh = new Person("Cảnh", 50, 1.7);
double BMI = canh.getBMI();
```

#### Từ khoá static còn làm gì nữa không?
Từ khoá `static` còn có để đặt trước câu lệnh khai báo một [member variable](../../terminology.md#member-variable) để thể hiện rằng biến đó thuộc về lớp ([class variable](../../terminology.md#class-variable)) chứ không thuộc về đối tượng ([instance variable](../../terminology.md#instance-variable)). Ví dụ:

```java
package example;

public class Person {
    static int totalPerson = 0;
    double weight;

    ... // Giống hệt ở trên
}
```

Có thể truy cập đến biến `totalPerson` như sau:
```java
Person.totalPerson
```

#### Vậy một cái thuộc lớp một cái thuộc đối tượng thì không liên quan gì đến nhau à?
Vì đối tượng thuộc 1 lớp, nên lớp đó có gì đối tượng cũng biết và dùng được. Ví dụ câu lệnh như sau chạy bình thường:

```java
Person canh = new Person("Cảnh", 50, 1.7);
canh.totalPerson ++;
```

Còn ngược lại thì không, ví dụ lệnh sau có lỗi:
```java
Person.weight = 40;
```

Ngoài ra, các đối tượng đều dùng chung [class variable](../../terminology.md#class-variable). Ví dụ:

```java
public static void main(String[] args) {
    Person canh = new Person("Cảnh", 50, 1.7);
    canh.totalPerson ++;
    Person thanh = new Person("Thành", 89, 1.7);
    thanh.totalPerson ++;
    System.out.println(Person.totalPerson);
}
```

Ví dụ trên sẽ in ra `2`.

Ở cùng ví dụ trên, sẽ tốt hơn nếu đưa thao tác `canh.totalPerson ++;` vào trong lớp `Person`:

```java
// File Person.java
package example;

public class Person {
    // Đây là class variable
    static int totalPerson = 0;

    // Còn đây là instance variable
    string name;
    double weight, height;

    // Đây là instance method
    Person(string name, double weight, double height) {
        this.name = name;
        this.weight = weight;
        this.height = height;

        Person.totalPerson ++; // hoặc this.totalPerson++ hoặc totalPerson++ đều được
    }

    double getBMI() {
        return this.weight / (this.height * this.height);
    }

    boolean isUnderweight() {
        // Instance method truy cập được đến cả class variable và instance variable
        // Lệnh dưới bỏ this và Person đi cũng được
        return this.getBMI() < Person.getMaxBMIForUnderweight();
    }

    // Còn đây là class method
    static double getMaxBMIForUnderweight() {
        // Lệnh này thì không truy cập `this.weight` được nhưng truy cập `Person.totalPerson` được
        return 18.5;
    }
}
```

```java
// File Program.java
package example;

public class Program {
    public static void main(String[] args) {
        Person canh = new Person("Cảnh", 50, 1.7);
        Person thanh = new Person("Thành", 78, 1.7);

        System.out.print("Trên thế giới có " + Person.totalPerson + " người");

        int underweightCount = 0;
        if (canh.isUnderweight())
            underweightCount ++;
        if (thanh.isUnderweight())
            underweightCount ++;

        System.out.println(" và có " + underweightCount + " người bị gầy");
    }
}
```

Chương trình như trên sẽ in ra màn hình:
```
Trên thế giới có 2 người và có 1 người bị gầy.
```

#### Khi nào nên dùng static?
Các phương thức mà không cần quan tâm đến thuộc tính của đối tượng thì dùng `static`. Các thuộc tính dùng chung giữa tất cả các đối tượng của lớp thì cũng dùng `static`.

#### Đặt tên lớp có quy tắc gì không?
Cách đặt tên giống đặt tên biến. Tuy nhiên nên để chữ cái đầu tiên viết hoa.

#### Mà thấy chữ public nhiều lắm rồi nhá nhưng vẫn không hiểu nó làm gì?
Đợi xíu bài sau.

.  
.  
.  

[Bài tập](exercise.md)

[Quay lại: Java căn bản](..)
