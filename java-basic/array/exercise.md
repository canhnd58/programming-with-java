# Bài tập: Mảng

### Bài 1:

Viết chương trình nhập vào một số `n`, sau đó nhập vào `n` số nguyên, in ra màn hình `n` số đó theo thứ tự ngược lại.

### Bài 2:

Viết một phương thức tên `doubleOdd` nhận vào một mảng các số nguyên và tăng giá trị trong các phần tử có giá trị lẻ lên gấp đôi.

Ví dụ:
```java
int[] a = {1, 2, 3, 7, 7, 4};
doubleOdd(a);
for (int i = 0; i < a.length; i ++)
    System.out.println(a[i]); // in ra 2 2 6 14 14 4
```

### Bài 3:

Viết một phương thức tên `isSorted` nhận vào một mảng các số nguyên, đưa ra `true` nếu mảng đang sắp xếp tăng dần, các số sau lớn hơn (không được bằng) các số trước, nếu không đưa ra `false`.

Ví dụ:
```java
int[] a = {1, 4, 7};
System.out.println(isSorted(a)); // true
```

```java
int[] a = {1, 4, 4};
System.out.println(isSorted(a)); // false
```

```java
int[] a = {2, 3, 1};
System.out.println(isSorted(a)); // false
```

### Bài 4:
Viết chương trình tự tạo một mảng các số nguyên với các giá trị trong khoảng từ `0` đến `9`. Sau đó in ra màn hình số lượng các số `0` trong mảng, số lượng các số `1`, ..., số lượng các số `9`.

### Bài 5:

Tạo một lớp (class) tên là `Book` đại diện cho một quyển sách với các thuộc tính sau:
- `String name`: tên quyển sách.
- `String author`: tên tác giả.

có hàm khởi tạo:
- `Book(String name, String author)` tạo một quyển sách mới với tên `name` và tác giả `author`.

có hàm thành viên:
- `String toString()` đưa ra biểu diễn dạng xâu kí tự của quyển sách. Ví dụ sách tên `Mat Biec` của tác giả `Nguyen Nhat Anh` thì phương thức sẽ đưa ra xâu `Mat biec [Nguyen Nhat Anh]`.

Trong phương thức `main` tạo một mảng các quyển sách như sau:
```java
books[0] = new Book("Mat biec", "Nguyen Nhat Anh");
books[1] = new Book("Lao Hac", "Nam Cao");
books[2] = new Book("Cho toi xin mot ve di tuoi tho", "Nguyen Nhat Anh");
books[3] = new Book("Tat den", "Ngo Tat To");
```

Sử dụng vòng lặp để tìm trong mảng và in ra biểu diễn dạng xâu kí tự của các quyển sách của tác giả `Nguyen Nhat Anh`.

Chương trình cần hiện lên màn hình như sau:
```java
Mat biec [Nguyen Nhat Anh]
Cho toi xin mot ve di tuoi tho [Nguyen Nhat Anh]
```

### Bài 6:
Một bức ảnh đen trắng có thể lưu bằng một mảng 2 chiều với giá trị `0` thể hiện màu đen, giá trị `1` thể hiện màu trắng. Viết một lớp `Image` có các phương thức:
- `Image(int n, int m)` tạo một ảnh toàn màu đen kích thước `n x m`.
- `void addWhite(int i, int j)` đổi màu tại hàng `i` cột `j` (tính từ `0`) thành màu trắng.
- `void invert()` đổi các điểm ảnh màu trắng thành màu đen và ngược lại.
- `void show()` in ra các giá trị điểm ảnh của ảnh dưới dạng bảng.

Ví dụ:
```java
Image img = new Image(4, 5);
img.addWhite(3, 3);
img.addWhite(1, 2);
img.invert();
img.show();
```

thì kết quả như sau:

```
11111
11011
11111
11101
```

### Bài 7:

Viết lớp `Permutation` trong package `permutation` để in ra các hoán vị của các số. Hoán vị của các số từ `0` đến `3` có thể là `0, 1, 2, 3` hay `1, 3, 0, 2`. Với `n` số khác nhau thì có `n!` hoán vị. Lớp `Permutation` gồm các phương thức:

- constructor `Permutation(int n)` tạo ra một đối tượng chứa một mảng các số từ `0` đến `n-1`.
- instance method `String getText()` đưa ra biểu diễn dạng xâu kí tự cho hoán vị hiện tại, giữa các số thêm dấu gạch ngang `-`. Ví dụ `(new Permutation(6)).getText()` sẽ đưa ra xâu `0-1-2-3-4-5`.
- instance method `boolean nextPermutation()` tính toán hoán vị tiếp theo của hoán vị hiện tại, nếu có. Nếu hoán vị hiện tại là hoán vị cuối cùng, đưa ra `false`, nếu không đưa ra `true`. Thứ tự các hoán vị như sau:

```
0-1-2-3-4-5-6-7-8-9
0-1-2-3-4-5-6-7-9-8
0-1-2-3-4-5-6-8-7-9
0-1-2-3-4-5-6-8-9-7
...
2-9-0-3-6-5-8-7-4-1 (X)
2-9-0-3-6-7-1-4-5-8 (X)
...
7-8-3-9-6-5-4-2-1-0
7-8-4-0-1-2-3-5-6-9
...
9-8-7-6-5-4-3-2-1-0
```

Trong package `permutation`, tạo thêm một lớp `PermutationTest` để kiểm tra lớp `Permutation` với hàm `main` như sau:

|Bước|Thao tác|Kết quả|
|----|--------|-------|
|1|Tạo một đối tượng của lớp `Permutation`||
|2|Hiển thị đối tượng dưới dạng xâu (gọi đến phương thức `getText`)|`0-1-2-3-4-5-6-7-8-9`|
|3|Tính hoán vị tiếp theo (gọi đến phương thức `nextPermutation` và lấy kết quả)|`true`|
|4|Hiển thị đối tượng dưới dạng xâu|`0-1-2-3-4-5-6-7-9-8`|
|5|Tính 362878 hoán vị tiếp theo||
|6|Hiển thị đối tượng dưới dạng xâu|`0-9-8-7-6-5-4-3-2-1`|
|7|Tính toán vị tiếp theo|`true`|
|8|Hiển thị đối tượng dưới dạng xâu|`1-0-2-3-4-5-6-7-8-9`|
|9|Tính 3265918 hoán vị tiếp theo||
|10|Hiển thị đối tượng dưới dạng xâu|`9-8-7-6-5-4-3-2-0-1`|
|11|Tính hoán vị tiếp theo|`true`|
|12|Hiển thị đối tượng dưới dạng xâu|`9-8-7-6-5-4-3-2-1-0`|
|13|Tính hoán vị tiếp theo|`false`|
|14|Hiển thị đối tượng dưới dạng xâu|`9-8-7-6-5-4-3-2-1-0`|

Gợi ý:
Trước khi lập trình cần phải tìm ra thuật toán để tính hoán vị tiếp theo từ hoán vị hiện tại. Phân tích các hoán vị được đánh dấu là (X) trong ví dụ bên trên:
- Từ một hoán vị đến một hoán vị tiếp theo, cần giữ nguyên các số vế bên trái nhiều nhất có thể. Ví dụ từ hoán vị `2-9-0-3-6-5-8-7-4-1` tới hoán vị `2-9-0-3-6-7-1-4-5-8`, 5 số đầu `2-9-0-3-6` giữ nguyên. Nói cách khác, hoán vị được thực hiện trên càng ít số bên phải càng tốt (trong ví dụ là thực hiện hoán vị với 5 số cuối `5-8-7-4-1`).
- Tìm hiểu vì sao không thể tính hoán vị tiếp theo bằng cách đổi chỗ ít số bên phải hơn (ví dụ 4 số cuối `8-7-4-1`).

