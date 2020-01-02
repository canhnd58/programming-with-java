# Enum

#### Enum là gì?

Enum là một loại lớp đặc biệt trong Java để định nghĩa ra các hằng ([constant](../../terminology.md#constant)). Ví dụ enum thường dùng để đại diện cho 7 ngày trong tuần, 12 tháng trong năm, 4 phương ...

#### Dùng enum như thế nào?

Mình dùng từ khoá `enum` (thay vì dùng `class` hoặc `interface`) để tạo ra một kiểu dữ liệu enum. Ví dụ:

```java
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY,
    SUNDAY
}
```

Nếu được khai báo như trên, kiểu dữ liệu `Day` có 7 giá trị khác nhau lần lượt là `Day.MONDAY`, `Day.TUESDAY` ... `Day.SUNDAY` (thực ra `Day` là một lớp thừa kế từ lớp có sẵn tên là `Enum`, mỗi giá trị `MONDAY`, `TUESDAY` ... là một đối tượng của lớp `Day`). Sau khi khai báo như trên, có thể dùng enum `Day` như sau:

```java
public class Program {
    public static void main(String[] args) {
        Day today = Day.TUESDAY;
        if (today == Day.SATURDAY || today == Day.SUNDAY)
            System.out.println("Hôm nay là cuối tuần");
        else
            System.out.println("Hôm nay không phải cuối tuần");
    }
}
```

Khi kiểu dữ liệu enum dùng trong câu lệnh `switch` thì các giá trị có thể bỏ đi tên lớp:

```java
public class Program {
    public static void main(String[] args) {
        Day today = Day.TUESDAY;
        switch (today) {
            case MONDAY:
                System.out.println("Đầu tuần");
                break;
            case SATURDAY:
            case SUNDAY:
                System.out.println("Cuối tuần");
                break;
            default:
                System.out.println("Giữa tuần");
                break;
        }
    }
}
```

#### Kiểu dữ liệu enum có sẵn phương thức nào không?

Kiểu dữ liệu enum có các phương thức của lớp `Object` và ghi đè phương thức `String toString()` để trả về một xâu tên trùng với tên của giá trị trong enum

```java
System.out.println(Day.TUESDAY); // in ra TUESDAY
```

Ngoài ra, enum `Day` có sẵn hai phương thức static sau:
- `static Day[] values()`: trả về mảng chứa tất cả các giá trị có thể có của `Day`.
- `static Day valueOf(String name)`: trả về tham chiếu đến một giá trị có tên là `name`

```java
Day d = Day.valueOf("TUESDAY"); // d sẽ tham chiếu đến Day.TUESDAY
```

#### Có thể thêm phương thức cho enum không?

Có thể thêm các thuộc tính và phương thức cho enum nhưng phải đặt sau danh sách các giá trị, danh sách các giá trị phải kết thúc bằng dấu chấm phẩy. Tuy nhiên, mục đích của enum là để đại diện cho các hằng nên không nên có các phương thức thay đổi các thuộc tính của các đối tượng enum, các thuộc tính nên được khởi tạo từ constructor và không thay đổi trong suốt quá trình chạy chương trình.

```java
public enum Day {
    MONDAY (1),
    TUESDAY (2),
    WEDNESDAY (3),
    THURSDAY (4),
    FRIDAY (5),
    SATURDAY (6),
    SUNDAY (0);

    private final int value;

    private Day(int value) {
        this.value = value;
    }

    public int getValue() {
        return value;
    }
}
```

Với cách viết như trên, các giá trị của kiểu enum `Day` (các đối tượng lớp `Day`) khi được tạo sẽ truyền các giá trị sau dấu ngoặc đơn vào phương thức khởi tạo. Vì thế giá trị `Day.MONDAY` sẽ có thuộc tính `value` là `1`, `Day.TUESDAY` sẽ có thuộc tính `value` là `2`.

```java
System.out.println(Day.MONDAY.getValue()); // In ra 1
```

#### Hình như viết nhầm, phương thức khởi tạo phải để là public chứ?

Với enum thì giới hạn truy cập của phương thức khởi tạo bắt buộc phải là `private` hoặc `default` (không ghi gì) do enum là lớp đặc biệt chỉ có một số hữu hạn đối tượng được tạo ra (`Day` chỉ có 7 đối tượng), mình không được phép tạo thêm đối tượng nên phải để là `private`.

#### Phương thức khởi tạo nhiều hơn một tham số thì sao?

Thì thêm nhiều giá trị cách nhau bởi dấu phẩy trong cặp dấu ngoặc đơn sau tên giá trị:

```java
public enum Day {
    MONDAY (1, "chán"),
    TUESDAY (2, "chán"),
    WEDNESDAY (3, "chán"),
    THURSDAY (4, "chán"),
    FRIDAY (5, "chán"),
    SATURDAY (6, "chán"),
    SUNDAY (0, "vui");

    private final int value;
    private final String feeling;

    private Day(int v, String f) {
        value = v;
        feeling = f;
    }
}
```

#### Enum thừa kế được lớp khác không?

Dù không viết cụ thể những enum đã thừa kế từ lớp có tên `Enum` mà Java không cho phép thừa kế nhiều lớp nên không thể thừa kế thêm lớp khác. Tuy nhiên vẫn có thể thừa kế từ nhiều `interface` được (bằng từ khoá `implements`).

.  
.  
.  

[Quay lại: Java nâng cao](..)
