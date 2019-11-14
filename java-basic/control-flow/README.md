# Câu lệnh điều khiển luồng
*Kiến thức cần biết:* [statement](../../terminology.md#statement), [variable](../../terminology.md#variable), [expression](../../terminology.md#expression)

#### Câu lệnh điều khiển luồng là gì?
Bình thường các câu lệnh trong một phương thức sẽ được thực hiện lần lượt và đầy đủ từ trên xuống dưới. Các câu lệnh điều khiển luồng (control flow statement) cho phép bỏ qua các lệnh hay lặp lại các lệnh tuỳ thuộc vào trạng thái của chương trình.

#### Có những câu lệnh điều khiển luồng nào?
Có những nhóm sau:
- Câu lệnh điều kiện (decision making statement)
- Câu lệnh lặp (looping statement)
- Câu lệnh nhảy (branching statement)

#### Câu lệnh điều kiện là gì?
Câu lệnh điều kiện chia một hay nhiều phần của chương trình thành các trường hợp. Với mỗi trường hợp, chương trình sẽ thực hiện một khối lệnh riêng, một lần chạy chương trình sẽ chỉ thực hiện khối lệnh của một trường hợp. Java hỗ trợ các câu lệnh điều kiện sau: `if`, `if-else`, `switch`.

#### Khối lệnh là gì?
Khối lệnh (block) là một hay nhiều lệnh liên tiếp nhau. Nếu có nhiều lệnh trong khối lệnh, các lệnh phải đặt trong một cặp dấu ngoặc nhọn `{ }` để thể hiện là cùng nằm trong một khối.

#### Câu lệnh if dùng như nào?
Câu lệnh điều kiện đơn giản nhất là câu lệnh `if` với cú pháp như sau:
```
if<mở ngoặc đơn><biểu thức điều kiện><đóng ngoặc đơn><khối lệnh>
```

trong đó, biểu thức điều kiện là một biểu thức mà khi thực hiện sẽ đưa ra `true` hoặc `false`. Khi gặp câu lệnh `if`, chương trình sẽ chỉ thực hiện khối lệnh của lệnh `if` nếu biểu thức điều kiện là `true`.

#### Ví dụ về câu lệnh if đi!

Giả sử có một biến `age` lưu một số nguyên
```java
if (age > 25) {
    System.out.println("Chào cô");
}
System.out.println("Tạm biệt");
```

Nếu `age` đang có giá trị lớn hơn `25` chương trình sẽ in ra 2 dòng chữ, nếu không sẽ chỉ in ra một dòng chữ `Tạm biệt`.

Ngoài ra, vì khối lệnh chỉ có một lệnh nên có thể bỏ đi dấu ngoặc nhọn (các dấu cách, xuống dòng, thụt đầu dòng chỉ để cho người lập trình dễ đọc):

```java
if (age > 25)
    System.out.println("Chào cô");
System.out.println("Tạm biệt");
```

#### Câu lệnh if-else dùng như nào?

Cú pháp như sau:
```
if <mở ngoặc đơn><biểu thức điều kiện><đóng ngoặc đơn>
    <khối lệnh 1>
else
    <khối lệnh 2>
```

Nếu biểu thức điều kiện là `true`, chương trình thực hiện khối lệnh 1, nếu không thì thực hiện khối lệnh 2. Ví dụ:

```java
if (age > 25) {
    System.out.println("Chào cô");
} else {
    System.out.println("Chào bạn");
}
```

Nếu biến `age` có giá trị lớn hơn `25`, chương trình in ra dòng chữ `Chào cô`, nếu không thì in ra `Chào bạn`.

Câu lệnh trên tương đương với 2 câu lệnh `if`:

```java
if (age > 25) {
    System.out.println("Chào cô");
} 
if (!(age > 25)) {
    System.out.println("Chào bạn");
}
```

#### Nếu có nhiều hơn 2 trường hợp thì sao?
Có thể dùng lệnh `if-else` lồng nhau:
```java
if (age > 25) {
    if (laNam == true)
        System.out.println("Chào chú");
    else
        System.out.println("Chào cô");
} else {
    System.out.println("Chào bạn");
}
```

hoặc dùng lệnh `if-else` nối tiếp nhau:
```java
if (age > 60)
    System.out.println("Chào bà");
else if (age > 25) 
    System.out.println("Chào cô");
else
    System.out.println("Chào bạn");
```

Nếu dùng đầy đủ dấu ngoặc nhọn, lệnh trên sẽ thành:

```java
if (age > 60) {
    System.out.println("Chào bà");
} else {
    if (age > 25) {
        System.out.println("Chào cô");
    } else {
        System.out.println("Chào bạn");
    }
}
```

#### Thế còn lệnh switch?
Lệnh `switch` cũng dùng để chia nhiều trường hợp với cú pháp như sau:
```
switch <mở ngoặc đơn><biểu thức><đóng ngoặc đơn><mở ngoặc nhọn>
    case <giá trị 1><dấu hai chấm>
        <câu lệnh 1.1>
        <câu lệnh 1.2>
        ...
        break;
    case <giá trị 2><dấu hai chấm>
        <câu lệnh 2.1>
        <câu lệnh 2.2>
        ...
        break;
    case <giá trị 3><dấu hai chấm>
    ...
    default<dấu hai chấm>
        <câu lệnh ...>
        <câu lệnh ...>
        break;
<đóng ngoặc nhọn>
```
Nếu biểu thức có giá trị là `giá trị 1`, các câu lệnh sau `giá trị 1` sẽ được thực hiện đến khi gặp lệnh `break` thì kết thúc lệnh `switch`, tương tự với `giá trị 2`, `giá trị 3`... Nếu kết quả biểu thức không bằng giá trị nào trong các giá trị sau từ khoá `case` thì các lệnh sau từ khoá `default` sẽ được thực hiện. Câu lệnh `switch` có thể không dùng từ khoá `default`.

Ví dụ:
```java
int season = 4;
switch (season) {
    case 1:
        System.out.println("Mùa xuân");
        break;
    case 2:
        System.out.println("Mùa hè");
        break;
    case 3:
        System.out.println("Mùa thu");
        break;
    case 4:
        System.out.println("Mùa đông");
        break;
    default:
        System.out.println("Không có mùa này");
        break;
}
```

Nếu giá trị trong biến `season` là `1` thì ỉn ra `Mùa xuân`, nếu là `2` in ra `Mùa hè`, là `3` in ra `Mùa thu`, là `4` in ra `Mùa đông`, các trường hợp khác in ra `Không có mùa này`. Ví dụ trên sẽ in ra `Mùa đông`.

#### Nếu không có lệnh break thì sao?
Nếu một trường hợp không có `break` thì các lệnh ở trường hợp phía sau trường hợp đó cũng sẽ được chạy đến khi gặp lệnh `break` mới thôi. Ví dụ:
```java
int month = 7;
switch (month) {
    case 1:
    case 3:
    case 5:
    case 7:
    case 8:
    case 10:
    case 12:
        System.out.println("Tháng " + month + " có 31 ngày.");
        break;
    case 2:
        System.out.println("Tháng " + month + " có 28 hoặc 29 ngày.");
        break;
    case 4: 
    case 6:
    case 9:
    case 11:
        System.out.println("Tháng " + month + " có 30 ngày.");
        break;
}
```
Câu lệnh `switch` ở trên sẽ in ra màn hình dòng chữ `Tháng 7 có 31 ngày.`.

#### Nếu có nhiều trường hợp thì nên dùng if-else hay switch?
Bất cứ cái gì `switch` làm được thì `if-else` cũng làm được, còn ngược lại thì không đúng nên có thể chỉ cần dùng lệnh `if-else` thôi. Nếu thích dùng `switch` thì cứ dùng cũng không ai cấm.

#### Câu lệnh lặp là gì?
Câu lệnh lặp dùng để thực hiện một khối lệnh nhiều lần. Có 3 cách viết câu lệnh lặp trong Java: `while`, `do-while` và `for`.

#### Câu lệnh while dùng như nào?
Cú pháp lệnh `while` như sau:
```
while <mở ngoặc đơn><biểu thức điều kiện><đóng ngoặc đơn><khối lệnh>
```

Khi chương trình chạy đến lệnh `while`, nếu biểu thức điều kiện có giá trị `false` thì kết thúc lệnh `while`. Nếu có giá trị là `true` thì thực hiện khối lệnh, sau đó kiểm tra lại điều kiện, nếu điều kiện vẫn đúng thì lại thực hiện khối lệnh lần nữa, lặp lại như vậy đến khi biểu thức điều kiện có kết quả là `false`.

Ví dụ:

```java
int soLan = 0;
while (solan < 10) {
    System.out.println("Hello World");
    soLan++;
}
```
Ban đầu khởi tạo `soLan` là `0`, vì điều kiện `soLan < 10` là `true` nên thực hiện việc in ra màn hình và tăng biến `soLan` lên một đơn vị thành `1`. Điều kiện `soLan < 10` vẫn ra kết quả là `true` nên vẫn tiếp tục in ra màn hình, đến khi `soLan` là `9` in ra lần cuối cùng, tăng `soLan` lên thành `10`, không thoả mãn điều kiện `soLan < 10` nên kết thúc lệnh `while`. Kết quả in ra `10` lần dòng chữ `Hello World` (tương ứng với `soLan = 0, 1, 2, 3, 4, 5, 6, 7, 8, 9`).

#### Câu lệnh do-while thì sao?
Cú pháp lệnh `do-while` như sau:
```
do 
    <khối lệnh>
while <mở ngoặc đơn><biểu thức điều kiện><đóng ngoặc đơn><dấu chấm phẩy>
```

Câu lệnh `do-while` tương tự lệnh `while` chỉ khác là khối lệnh được thực hiện trước sau đó mới kiểm tra biểu thức điều kiện. Nếu biểu thức điều kiện là `true` thì thực hiện lại khối lệnh, nếu là `false` thì kết thúc khối lệnh. Vì thế, khối lệnh của câu lệnh `do-while` luôn luôn được thực hiện ít nhất một lần.

#### Câu lệnh for?
Câu lệnh `for` và câu lệnh `while` tương đương nhau. Rất nhiều lệnh lặp có 3 thành phần: câu lệnh khởi tạo, biểu thức điều kiện và câu lệnh để thay đổi điều kiện. Với câu lệnh `for`, 3 thành phần đó có thể để cùng một chỗ với cú pháp như sau:
```
for<mở ngoặc đơn><câu lệnh khởi tạo><dấu chấm phẩy><biểu thức điều kiện><dấu chấm phẩy><câu lệnh thay đổi điều kiện><đóng ngoặc đơn><khối lệnh>
```

Ví dụ:
```java
for (int soLan = 0; soLan < 10; soLan ++) {
    System.out.println("Hello World");
}
```
Lệnh ở trên có tác dụng tương tự ví dụ của câu lệnh `while`.

Ngoài ra có thể có nhiều lệnh khởi tạo cách nhau bởi dấu phảy, nhiều lệnh thay đổi vòng lặp cách nhau bởi dấu phảy.

#### Các câu lệnh lặp có thể lồng trong nhau không?
Có, câu lệnh lặp cũng giống một câu lệnh bình thường nên có thể nằm trong khối lệnh của câu lệnh lặp khác. Ví dụ:

```java
for (int i = 0; i < 10; i ++) {
    for (int j = 0; j < 3; j ++) {
        System.out.println(i);
    }
}
```

Câu lệnh lặp bên trên in ra màn hình 3 lần số `0`, sau đó in ra 3 lần số `1`, ..., 3 lần số `9`.

#### Thế khi nào dùng for khi nào dùng while?
Nhìn vào dòng đầu tiên của câu lệnh `for` ta có thể thấy được vòng lặp sẽ thực hiện bao nhiêu lần. Với câu lệnh `while`, 3 thành phần ảnh hưởng đến số lần lặp nằm ở các vị trí xa nhau nên khó biết hơn. Vì thế nếu số lần lặp là xác định thì thường dùng lệnh `for`, nếu không xác định thì thường dùng `while`.

Khi có nhiều lệnh khởi tạo cho vòng lặp hoặc có nhiều lệnh thay đổi biểu thức điều kiện của vòng lặp thì nên dùng `while` hơn cho đỡ rối mắt.

Hoặc dùng tuỳ theo sở thích.

#### Câu lệnh nhảy là gì?
Câu lệnh nhảy là câu lệnh để nhảy đến câu lệnh khác, được sử dụng với các [từ khoá](../../terminology.md#keyword) sau:
- `break`: dùng trong vòng lặp hoặc trong câu lệnh `switch`, nếu chương trình gặp lệnh này thì thoát khỏi vòng lặp luôn (dù biểu thức điều kiện vẫn đúng) hoặc thoát khỏi lệnh `switch`.
- `continue`: dùng trong vòng lặp, nếu chương trình gặp lệnh này thì thoát khỏi lần lặp hiện tại và sang lần lặp tiếp theo.
- `return`: dùng trong phương thức, nếu chương trình gặp lệnh này thì kết thúc phương thức hiện tại và quay lại phương thức trước đó.

Ví dụ:
```java
for (int i = 99; i >= 0; i --) {
    if (i % 13 == 0) {
        System.out.println("Số lớn nhất nhỏ hơn 100 và chia hết cho 13 là: " + i);
        break;
    }
}
```

Chương trình trên lặp lần lượt với các giá trị của biến `i` từ `100` đến `91`. Đến khi `i` có giá trị bằng `91` (thoả mãn điều kiện chia hết cho `13`), chương trình in ra màn hình dòng chữ như trên và kết thúc câu lệnh lặp luôn (do lệnh `break`). Nếu không có lệnh `break` thì chương trình sẽ kiểm tra `i` từ `100` đến `0` và in ra tất cả các số chia hết cho `13`.

```java
System.out.println("Các số nhỏ hơn 100 vừa không chia hết cho 2 vừa không chia hết cho 5 là:");
for (int i = 0; i < 100; i ++) {
    if (i % 2 == 0)
        continue;
    if (i % 5 == 0)
        continue;
    System.out.println(i);
}
```
Chương trình trên sẽ không in ra màn hình các số chia hết cho `2` hoặc chia hết cho `5` do khi gặp lệnh `continue` thì lệnh `System.out.println` phía sau sẽ không được thực hiện.

Lệnh `return` sẽ tìm hiểu ở bài sau.

#### Ví dụ cuối không dùng continue cũng được mà?
Ừ, thường thì một vấn đề đều có nhiều cách làm, dùng như thế nào tuỳ thói quen từng người thôi. Ví dụ bên trên có thể làm cách khác:

```java
System.out.println("Các số nhỏ hơn 100 vừa không chia hết cho 2 vừa không chia hết cho 5 là:");
for (int i = 0; i < 100; i ++) {
    if (i % 2 != 0 !! i % 5 != 0)
        System.out.println(i);
}
```

#### Sao hay đặt tên biến là i thế?
`i` là viết tắt của `iteration`, người ta hay đặt tên biến là `i` trong vòng lặp để đại diện cho hiện tại đang ở vòng lặp thứ bao nhiêu.

#### Hết chưa?
Còn một chú ý nữa về phong cách lập trình (programming convention) là các lệnh trong một khối lệnh nên viết thẳng hàng nhau. Khối lệnh thuộc về một lệnh khác (ví dụ `if`, `for`) thì các lệnh trong đó thụt vào một dấu tab (dấu tab trên bàn phím, NetBeans thường tự động thụt) so với lệnh bên ngoài. Viết như vậy chương trình sẽ đẹp và dễ đọc. Các ví dụ bên trên đều viết theo phong cách như vậy.

.  
.  
.  

[Bài tập](exercise.md)
