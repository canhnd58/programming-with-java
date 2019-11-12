# Bài tập: Biểu thức và câu lệnh biểu thức

### Bài 1:

Giả sử đã có biến `a` và `b` thuộc kiểu `int` và có giá trị lần lượt là `10`, `15`. Kết quả của phương thức `Math.pow` là luỹ thừa của 2 đối số (`Math.pow(2, 3)` là `8`). Kết quả của các biểu thức sau là gì?

1. `5 + 7 / 2 + 20`
1. `5 > 6 || 6 > 5 && 3 >= 2`
1. `!(3 * 5 == 1 * 6)`
1. `20.2 / 2 + 7`
1. `a / (double) b`
1. `a <= 10 && a + 5 <= b`
1. `28 / (int) Math.pow(1 + 2, 2)`
1. `b % 4 + "xau"`

### Bài 2:

Kết thúc biểu thức sau, biến `a` có giá trị là bao nhiêu?

```java
int a;
a = 2 >= 2 ? 2 : 3;
a ++;
a = a + 3;
a *= 5 / 2;
```

### Bài 3:

Viết chương trình làm các thao tác sau:
- Tạo 2 biến thuộc kiểu `int` tên là `number` và `yearOfBirth`.
- Gán cho biến `number` một số nguyên bất kì, biến `yearOfBirth` là năm sinh của mình.
- Chia biến `number` cho `22`, lấy phần dư nhân với `10` và gán lại vào `number`.
- Tăng biến `number` lên `50` đơn vị.
- Nhân `number` với `20` và gán lại vào `number`.
- Tăng biến `number` lên `1019` đơn vị.
- In ra màn hình dòng chữ `Tuổi của mình là: ` kèm theo kết quả biểu thức `(number - yearOfBirth) % 100`.

