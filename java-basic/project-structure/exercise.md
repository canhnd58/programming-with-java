# Bài tập: Cấu trúc chương trình Java

### Bài 1
Chương trình có cấu trúc thư mục như sau gồm những package nào?
```
BaiTap
|---build
|   |---classes
|       |---bai1
|       |   |---HelloWorld.class
|       |
|       |---bai2
|           |---ByeWorld.class
|           |---ByeYou.class
|
|---src
|   |---bai1
|   |   |---HelloWorld.java
|   |
|   |---bai2
|       |---ByeWorld.java
|       |---ByeYou.java
|
|---build.xml
```

### Bài 2
Khi chương trình gồm 2 file sau được chạy, các lệnh nào sẽ được thực hiện và theo thứ tự nào?

File `ByeWorld.java`:
```java
package bai2;
public class ByeWorld {
    public static void bye(String[] args) {
        System.out.println("vinh");
        System.out.println("biet");
        System.out.println("the");
        System.out.println("gioi");
    }
}
```

File `ByeYou.java`:
```java
package bai2;
public class ByeYou {
    public static void main(String[] args) {
        System.out.println("biet");
        System.out.println("cac");
        System.out.println("ban");
        System.out.println("tam");
    }
}
```

### Bài 3:
Chương trình với cấu trúc thư mục và nội dung file `Bai3.java` như sau có chạy được không?

```
Bai3
|---src
    |---bai3
        |---Bai3.java
```

File `Bai3.java`:
```
public class Hello {
    public static void main(String[] args) {
        System.out.println("Xin chao cac ban");
    }
}
```

#### Bài 4:
Viết chương trình Java in ra các dòng chữ như sau:
> Chào mọi người.  
> Mình tên là \<tự điền tên vào đây\>.  
> Đây là chương trình đầu tiên mình tự viết.  
