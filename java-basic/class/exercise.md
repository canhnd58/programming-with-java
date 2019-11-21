# Bài tập: Khai báo lớp và khởi tạo đối tượng

### Bài 1:
Chương trình sau in ra kết quả là bao nhiêu?

```java
public class Person {
    String name;
    Person() {
        name = "No name";
    }

    public static void main(String[] args) {
        Person p;
        System.out.println(p.name);
    }
}
```

### Bài 2:
Cho lớp `Person` như sau:
```java
public class Person {
    static int total = 0;
    int id;

    Person() {
        total ++;
        id = total;
    }
}
```

Các câu lệnh bên dưới in ra kết quả gì?
```java
Person p1 = new Person();
Person p2 = new Person();
Person p3 = p1;

System.out.println(p1.id);
System.out.println(p2.id);
System.out.println(p3.id);
System.out.println((new Person()).id);

p1.id ++;
p2.id ++;
p3.id ++;

System.out.println(p1.id);
System.out.println(p2.id);
System.out.println(p3.id);
System.out.println((new Person()).id);
```

### Bài 3:
Đang nghĩ
