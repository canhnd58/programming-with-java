# Bài tập: Cấu trúc chương trình Java

### Bài 1
Chương trình có cấu trúc thư mục như sau gồm những package nào?
```
Exercise
|---build
|   |---classes
|       |---ex1
|       |   |---HelloWorld.class
|       |
|       |---ex2
|           |---ByeWorld.class
|           |---ByeYou.class
|
|---src
|   |---ex1
|   |   |---HelloWorld.java
|   |
|   |---ex2
|       |---ByeWorld.java
|       |---ByeYou.java
|
|---build.xml
```

### Bài 2
Khi chương trình gồm 2 file sau được chạy, các lệnh nào sẽ được thực hiện và theo thứ tự nào?

File `ByeWorld.java`:
```java
package ex2;
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
package ex2;
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
Chương trình với cấu trúc thư mục và nội dung file `Exercise.java` như sau có chạy được không?

```
Exercise3
|---src
    |---ex3
        |---Exercise.java
```

File `Exercise.java`:
```
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

#### Bài 4:
Viết chương trình Java in ra các dòng chữ như sau:
> Chào mọi người.  
> Mình tên là \<tự điền tên vào đây\>.  
> Đây là chương trình đầu tiên mình tự viết.  
