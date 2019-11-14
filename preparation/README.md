# Cài đặt môi trường lập trình Java
*Kiến thức cần nhớ:* [compiler](../terminology.md#compiler), [JVM](../terminology.md#jvm)

#### Bắt đầu lập trình thôi!
Chưa, phải cài đặt một số thứ cần thiết đã mới lập trình được.

#### Cần cài đặt những gì để bắt đầu lập trình Java?
Ít nhất cần cài đặt công cụ phát triển Java ([JDK](../terminology.md#JDK) - Java Development Kit). JDK bao gồm [trình biên dịch](../terminology.md#compiler), [máy ảo Java](../terminology.md#JVM) và một số thành phần khác[\*](TLDR.md#JDK-gồm-những-gì) giúp cho việc tạo và chạy các chương trình Java. Có thể download JDK ở [đây](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Tuỳ thuộc máy mình là Windows, Linux hay MacOS mà tải về bản phù hợp (nếu không biết thì chắc là Windows x64) rồi cài đặt.

Sau đó tải về một [IDE](../terminology.md#IDE). Ví dụ có thể tải NetBeans ở [đây](https://netbeans.org/downloads/8.2/) về cài đặt (chọn phiên bản Java SE[\*](TLDR.md#java-se-là-gì)). Trong IDE sẽ có các nút để biên dịch và chạy chương trình (thực ra khi IDE biên dịch và chạy là gọi đến các chương trình có trong JDK).

#### Làm sao biết đã cài đặt được hay chưa?
Sử dụng IDE tạo project mới, sau đó sửa các dòng sau trong file `.java` IDE vừa tạo ra:
```java
public static void main(String[] args) {
    // TODO code application logic here
}
```
thành
```java
public static void main(String[] args) {
    System.out.println("Hello World!");
}
```

Tìm và bấm nút **Run Project** hay nút gì đó giống giống. Nếu màn hình hiện ra dòng chữ **Hello World!** tức là đã cài đặt thành công.

Ví dụ với NetBeans thì làm như sau:
1. Bấm chuột vào **File** &#8594; **New Project**
2. Chọn loại project là **Java Application** &#8594; **Next**
3. Đặt tên cho project viết liền không dấu &#8594; Tick chọn **Create Main Class** &#8594; **Finish**
4. Sửa các dòng trong file `.java` như mô tả ở trên
5. Bấm chuột vào **Run** &#8594; **Run Project**

.  
.  
.  

[Còn nữa, mà dài lắm đừng đọc](TLDR.md)

[Quay lại: Lập trình Java](..)
