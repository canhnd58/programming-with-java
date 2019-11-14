# Cấu trúc chương trình Java

*Kiến thức cần biết:* [compiler](../../terminology.md#compiler), [JVM](../../terminology.md#JVM), [JDK](../../terminology.md#JDK)

#### Chạy được chương trình in ra chữ Hello World rồi nhưng không hiểu nó làm gì!
Vậy bây giờ tìm hiểu cấu trúc của một chương trình Java.

#### Một chương trình Java gồm những gì?
Một chương trình Java là một project, một project (có thể) gồm nhiều package, một package (có thể) gồm nhiều class, một class (có thể) gồm nhiều method, một method (có thể) gồm nhiều statement .-.

project &#8594; package &#8594; class &#8594; method &#8594; statement

#### Là sao? @@
Một lệnh hay câu lệnh ([statement](../../terminology.md#statement)) là đơn vị nhỏ nhất mang một mục đích mình muốn máy tính thực hiện. Các câu lệnh cùng nhau thực hiện một nhiệm vụ tạo thành 1 phương thức ([method](../terminology.md#statement)). Các phương thức thực hiện các nhiệm vụ của một sự vật được gộp chung vào một lớp ([class](../../terminology.md#class)). Các lớp liên quan đến nhau được nhóm vào thành một [package](../../terminology.md#package) (cái package này chẳng ai dịch). Các package gộp lại thành một chương trình. Đây là góc nhìn của người lập trình và của [trình biên dịch](../../terminology.md#compiler). Khi biên dịch xong, chương trình sẽ chuyển thành chuỗi các chỉ thị (instruction) để [JVM](../../terminology.md#jvm) thực hiện lần lượt thôi.

Ví dụ dùng NetBeans tạo một project tên HelloWorld sẽ ra cấu trúc thư mục sau:
```
HelloWorld
|---src
    |---helloworld
        |---HelloWorld.java
```

Sửa nội dung của file `HelloWorld.java` như sau:
```java
package helloworld;

public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}
```

Ở ví dụ trên, thư mục `src` chứa các package mình tạo ra cho chương trình, ở đây có một package tên là `helloworld`. Trong package `helloworld` có một lớp `HelloWorld` nằm trong file `HelloWorld.java`. Trong lớp `HelloWorld` có một phương thức tên là `main`. Trong phương thức `main` có một lệnh `System.out.println("Hello World!");` là lệnh yêu cầu máy tính in ra màn hình dòng chữ `Hello World!` và xuống dòng mới.

Trong Java, mỗi file `.java` tương ứng với 1 lớp và tên file phải trùng với tên lớp, một câu lệnh luôn kết thúc bằng dấu `;`, nếu không sẽ bị lỗi biên dịch. Các câu lệnh có thể viết trên cùng một dòng hoặc mỗi dòng một lệnh. Cả file `HelloWorld.java` như trên có thể viết thành còn một dòng cũng được.

Ngoài ra trong file mã nguồn còn có thể có các dòng [comment](../../terminology.md#comment) có tác dụng giải thích thêm ý nghĩa các phần của chương trình. Comment chỉ để người lập trình đọc, trình biên dịch bỏ qua hết các phần comment khi biên dịch.

#### Comment viết như thế nào?
Có 2 cách viết comment: nếu comment trên 1 dòng thì đặt 2 dấu `//` trước phần muốn comment, nếu comment trên nhiều dòng thì đặt các dòng đó trong cặp `/*` và `*/`.
Ví dụ:

```java
package helloworld;

/*
    Đây là chương trình Hello World.
    Chương trình này in ra màn hình dòng chữ "Hello World!".
*/
public class HelloWorld {

    // Đây là hàm main
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Lệnh in ở đây
    }

}
```

#### Giờ có nhiều lớp, nhiều phương thức, nhiều lệnh thì câu lệnh nào được thực hiện trước?
Một chương trình Java luôn phải có một lớp có chứa phương thức `main`. Khi biên dịch xong và chạy chương trình, các lệnh trong phương thức `main` được thực hiện từ trên xuống dưới, xong lệnh trước mới thực hiện lệnh sau. Kết thúc phương thức `main` cũng là kết thúc chương trình.

#### Vậy các lệnh khác ở trong phương thức khác không dùng à?
Sẽ có các câu lệnh có nhiệm vụ gọi đến phương thức khác. Giả sử trong `main` có câu lệnh đó, khi gặp, chương trình sẽ chuyển quyền điều khiển cho phương thức được gọi và thực hiện các lệnh trong đó, khi thực hiện hết sẽ quay lại `main` và thực hiện nốt các lệnh chưa thực hiện trong `main`.

#### Thế mấy từ khác như public, static, void ... để làm gì?
Đó gọi là các từ khoá (keyword). Mỗi từ khoá có một ý nghĩa riêng biệt mà mình sẽ phải nhớ, giống như học từ vựng tiếng Anh vậy. Các câu lệnh, phương thức hay lớp đều có các quy tắc viết phải tuân theo, nếu không trình biên dịch sẽ không hiểu và không dịch được. Các quy tắc như thế gọi là cú pháp (syntax), giống như ngữ pháp trong ngôn ngữ thường ngày.

Các từ khoá và ý nghĩa từng từ khoá sẽ nói rõ hơn khi học cú pháp viết câu lệnh, phương thức và lớp. 

#### Sao không gọi là từ vựng với ngữ pháp luôn?
Để những đứa khác sẽ không hiểu gì và thấy bọn học lập trình toàn học những thứ cao siêu.

#### Java có bao nhiêu từ khoá?
Có [51 từ khoá](https://en.wikipedia.org/wiki/List_of_Java_keywords)

#### Java có những câu lệnh nào?
Các câu lệnh trong Java chia làm 3 loại:
- Câu lệnh khai báo (declaration statement)
- Câu lệnh biểu thức (expression statement)
- Câu lệnh điều khiển luồng (control flow statement)

Các câu lệnh này làm gì bài sau sẽ rõ.

.  
.  
.  

[Bài tập](exercise.md)
