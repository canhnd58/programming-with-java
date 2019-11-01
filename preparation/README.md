# Cài đặt môi trường lập trình Java

#### Bắt đầu lập trình thôi!
Chưa, phải cài đặt một số thứ cần thiết đã mới lập trình được.

#### Cần cài đặt những gì?
Tối thiểu cần cài đặt công cụ phát triển Java ([JDK](../terminology.md#JDK) - Java Development Kit). JDK bao gồm các [trình biên dịch](../terminology.md#compiler), [trình gỡ lỗi](../terminology.md#debugger), [máy ảo Java](../terminology.md#JVM) và một số thành phần khác[\*](TLDR.md#JDK-gồm-những-gì) giúp cho việc tạo và chạy các chương trình Java. Có thể download JDK ở [đây](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Tuỳ thuộc máy mình là Windows, Linux hay MacOS mà tải về bản phù hợp (nếu không biết thì chắc là Windows x64) rồi cài đặt.

Nếu sử dụng [giao diện dòng lệnh](../terminology.md#CLI), giờ ta đã có lệnh:
- `javac`: để biên dịch một file `.java`. Ví dụ có file program.java thì biên dịch như sau: `javac program.java` sẽ sinh ra file program.class.
- `java`: để chạy một file `.class`. Ví dụ có file program.class thì chạy như sau: `java program`.
- Và một số lệnh nữa như `javadoc` để sinh tài liệu hay `javadb` để gỡ lỗi.

Nếu không biết sử dụng giao diện dòng lệnh, cần tải về một [IDE](../terminology.md#IDE) nào đó. Ví dụ có thể tải NetBeans ở [đây](https://netbeans.org/downloads/8.2/) về cài đặt(nhớ chọn phiên bản Java SE[\*](TLDR.md#java-se-là-gì)). Trong IDE sẽ có các nút để biên dịch và chạy chương trình (thực ra khi IDE biên dịch và chạy là gọi đến các lệnh `javac` với `java` ở trên).

#### Làm sao biết đã cài đặt được hay chưa?
Nếu sử dụng [giao diện dòng lệnh](../terminology.md#CLI), gõ lệnh như sau `javac -version`. Nếu hiện ra dòng chữ gần gần như này là được:
> javac 1.8.0\_231

Nếu sử dụng IDE thì tạo project mới, sau đó sửa các dòng sau trong file `.java` IDE vừa tạo ra:
```
public static void main(String[] args) {
    // TODO code application logic here
}
```
thành
```
public static void main(String[] args) {
    System.out.println("Xin chao moi nguoi");
}
```

Tìm và bấm nút **Run Project** hay nút gì đó giống giống. Nếu màn hình hiện ra dòng chữ **Xin chao moi nguoi** tức là đã cài đặt thành công.

Ví dụ với NetBeans thì làm như sau:
1. Bấm chuột vào **File** &#8594; **New Project**
2. Chọn loại project là **Java Application** &#8594; **Next**
3. Đặt tên cho project viết liền không dấu &#8594; Tick chọn **Create Main Class** &#8594; **Finish**
4. Sửa các dòng trong file `.java` như mô tả ở trên
5. Bấm chuột vào **Run** &#8594; **Run Project**


[Còn nữa, mà dài lắm đừng đọc.](TLDR.md)

