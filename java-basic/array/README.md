# Mảng

#### Mảng là cái gì?

Mảng (array) là một tập hợp các phần tử có cùng kiểu dữ liệu (data type) nằm cạnh nhau trong bộ nhớ máy tính.

#### Sao mà cần dùng mảng?

Nằm cạnh nhau trông gọn .-. Thỉnh thoảng mình cũng cần tạo ra rất nhiều biến thuộc cùng một kiểu dữ liệu, ví dụ:
- lưu một dãy số.
- lưu nhiều xâu kí tự (String).
- quản lý nhiều quyển sách.

#### Tạo ra một mảng như nào?

Mảng là một đối tượng (object) có thể tạo ra bằng toán tử `new` như sau:

```
new<dấu cách><kiểu dữ liệu của một phần tử><mở ngoặc vuông><số lượng phần tử><đóng ngoặc vuông>
```

Ví dụ tạo ra 10 số nguyên:
```java
new int[10];
```

Giống như tạo ra các đối tượng khác, toán tử `new` trả lại một tham chiếu (reference) đến đối tượng vừa được tạo ra. Tham chiếu đó có thể gán vào một biến, các lệnh tiếp theo dùng biến đó để truy cập đến mảng. Kiểu dữ liệu của biến tham chiếu là kiểu dữ liệu của một phần tử kèm thêm cặp dấu ngoặc vuông ở cuối để thể hiện đó là một mảng, ví dụ:

```java
int[] arr = new int[10];
```

là lệnh tạo ra 10 số nguyên và lưu tham chiếu đến 10 số đó vào biến `arr`.

Dấu ngoặc vuông cũng có thể để ở cuối của biến:
```java
int arr[] = new int[10];
```

#### Sao 10 số mà có mỗi một biến?

Các phần tử trong mảng được đánh thứ tự từ `0`. Thứ tự của phần tử trong mảng gọi là chỉ số (index) của phần tử. Phần tử thứ nhất có chỉ số là `0`, phần tử cuối cùng của mảng có `10` phần tử có chỉ số là `9`.

Mình truy cập đến một phần tử trong mảng bằng cú pháp:

```
<tên biến tham chiếu><mở ngoặc vuông><chỉ số của phần tử><đóng ngoặc vuông>
```

Ví dụ:
```java
int[] arr = new int[10];
arr[0] = 3;
arr[1] = arr[0] + 4;
```

Lệnh đầu tiên tạo ra mảng 10 phần tử (mặc định các phần tử của mảng khi tạo ra sẽ bằng `0`). Lệnh thứ 2 gán cho phần tử đầu tiên của mảng số `3`. Lệnh thứ 3 lấy giá trị trong phần tử đầu tiên cộng thêm `4` được kết quả là `7` rồi gán cho phần tử thứ 2. Kết thúc 3 lệnh trên, phần tử đầu tiên có giá trị là `3`, phần tử thứ 2 có giá trị là `7`, các phần tử khác có giá trị là `0`.

*Chú ý: Nếu truy cập đến một phần tử có chỉ số nằm ngoài mảng sẽ khiến chương trình bị lỗi.*

#### Có thể tạo ra mảng của các kiểu dữ liệu nào?
Bất cứ kiểu dữ liệu nào (primitive và reference data types) đều được.

#### Mảng còn gì đặc biệt không?

Một đối tượng mảng có một thuộc tính (field hay member variable) tên là `length`. Thuộc tính `length` lưu số lượng phần tử của mảng. Ví dụ:

```java
int[] arr = new int[10];
System.out.println(arr.length);
```

sẽ in ra màn hình số `10`.

#### Hết chưa?

Giống như `String`, mảng cũng có cách khởi tạo đặc biệt. Ngoài cách khởi tạo dùng `new` như trên còn có cách sau:

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

Lệnh trên tạo ra mảng 10 phần tử, phần tử đầu có giá trị là `1`, phần tử thứ 2 có giá trị là `2`, ...

#### Ví dụ một bài cần dùng mảng xem nào!

Nhập vào 5 số nguyên, in ra màn hình theo thứ tự ngược lại.

#### Dùng 5 biến a, b, c, d, e rồi in e, d, c, b, a không được à?

Vậy thì nhập 100 số nguyên, in ra màn hình theo thứ tự ngược lại.

#### Dùng 100 biến a1, a2, a3, ..., a100?

:\|

#### Thế bài kia dùng mảng như nào?
Như này nè:

```java
import java.util.Scanner;

public class ArrayExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] arr = new int[100];

        // Nhập các phần tử với chỉ số tăng dần 0, 1, ..., 98, 99
        for (int i = 0; i < 100; i ++)
            arr[i] = sc.nextInt();

        // In các phần tử với chỉ số giảm dần 99, 98 ..., 1, 0
        for (int i = 99; i >= 0; i --)
            System.out.println(arr[i]);
    }
}
```

#### Có thế thôi phải không?

Những cái trên gọi là mảng 1 chiều, còn có mảng nhiều chiều nữa.

#### Không học được không?

Không :\|

#### Mảng nhiều chiều là cái gì?

Mảng 2 chiều là một mảng các mảng, mảng 3 chiều là mảng của mảng của mảng, các mảng nhiều chiều hơn tương tự.

#### Là sao ko hiểu? :'(

Tưởng tượng mảng một chiều là một dãy các ô nhớ nằm cạnh nhau tạo thành một hàng thì mảng 2 chiều là 1 bảng nhiều hàng, mảng 3 chiều là nhiều bảng nằm đè lên nhau thành một khối, mảng 4 chiều ... ko biết tưởng tượng.

#### Thế dùng mảng nhiều chiều như nào?

Ví dụ tạo ra mảng 2 chiều là một bảng 5 hàng 6 cột (có 30 ô) như sau:
```java
int[][] table = new int[5][6];
```

Nếu dùng như trên, `table` là tham chiếu đến mảng `5` phần tử, mỗi phần tử là một tham chiếu đến một mảng `6` số nguyên.

Truy cập đến phần tử hàng thứ 3 cột thứ 2 như sau:
```java
table[2][1]
```

Lấy ra số lượng các hàng:
```java
table.length
```

Lấy ra số lượng các cột:
```java
table[0].length // Không dùng được nếu mảng rỗng (không có phần tử chỉ số 0)
```

Khởi tạo luôn giá trị của mảng 2 chiều:

```java
int[][] table = {
    {1, 2, 3},
    {4, 5, 6}
};
System.out.println(table[1][1]);        // 5
System.out.println(table.length);       // 2
System.out.println(table[0].length);    // 3
```

#### Còn gì nữa không?

Có package `java.util.Arrays` chứa một số phương thức static (static method) để làm việc với mảng. Ví dụ với mảng số nguyên có:
- `static void sort(int[] a)`: sắp xếp các phần tử của mảng `a` tăng dần.

```java
int[] arr = {3, 1, 4, 2};
Arrays.sort(arr); // Mảng thành {1, 2, 3, 4}
```

- `static void fill(int[] a, int value)`: gán tất cả các phần tử của mảng `a` thành `value`.

```java
int[] arr = new arr[5];
Arrays.fill(arr, 4); // Mảng thành {4, 4, 4, 4, 4}
```

#### Vẫn chưa hết à?

Hết rồi.

#### Yê!

[Bài tập](exercise.md)
