# Biểu thức và câu lệnh biểu thức
*Kiến thức cần biết:* [statement](../../terminology.md#statement), [variable](../../terminology.md#variable), [data type](../..terminology.md#data-type)

#### Câu lệnh biểu thức là gì?
Tìm hiểu biểu thức là gì đã.

#### Thế biểu thức là gì?
Biểu thức ([expression](../../terminology.md#expression)) là sự kết hợp giữa các toán tử ([operator](../../terminology.md#operator)) và toán hạng ([operand](../../terminology.md#operand)) theo quy tắc mà ngôn ngữ cho phép. Chỉ 1 toán hạng thôi cũng gọi là biểu thức.
Khi chương trình chạy gặp biểu thức, biểu thức luôn được tính thành một giá trị cụ thể ([literal](../../terminology.md#literal)). Như vậy, bất cứ chỗ nào trong chương trình có thể để một giá trị cụ thể thì cũng có thể để một biểu thức.

Giữa các toán tử và toán hạng còn có thể thêm các khoảng trắng để dễ đọc.

#### Toán tử là gì?
Toán tử ([operator](../../terminology.md#operator)) là các phép toán như `+`, `-`, `*`, `/`, dùng để thực hiện một phép tính với các toán hạng sau đó đưa ra một giá trị cụ thể.

#### Toán hạng là gì?
Toán hạng ([operand](../../terminology.md#operand)) là các vế của một phép toán. Toán hạng có thể là giá trị cụ thể ([literal](../../terminology.md#literal)), biến ([variable](../../terminology.md#variable)), lời gọi đến phương thức ([method invocation](../../terminology.md#method-invocation)) hay biểu thức ([expression](../../terminology.md#expression)) khác.
Tuỳ thuộc các toán hạng thuộc kiểu dữ liệu nào mà các toán tử có thể có ý nghĩa khác nhau.

#### Có những giá trị cụ thể nào trong Java?
Java có những giá trị cụ thể ([literal](../../terminology.md#literal)) sau:
- Các số nguyên như: `0`, `1`, `100`, `-100`.
- Các số thực như: `0.1`, `-10.25`, `10.0`.
- Các kí tự như: `'a'`, `'B'`, `'%'`, `'3'` (trong file mã nguồn, các kí tự luôn đặt trong cặp dấu nháy đơn `'` để phân biệt với số, toán tử, tên biến...).
- Các xâu (hay còn gọi là chuỗi) kí tự như: `"xin chao"`, `"hello world!"`, `"a"` (trong file mã nguồn, các chuỗi kí tự luôn nằm trong cặp dấu nháy kép `"` để phân biệt với từ khoá, tên biến...).
- Hai giá trị boolean: `true` và `false` (chú ý không có dấu nháy kép).
- Giá trị tham chiếu (có thể hiểu là vị trí của một vùng nhớ trong bộ nhớ máy tính).
- Giá trị đặc biệt thể hiện việc không có giá trị: `null`.

#### 10 với 10.0 không phải là một à?
Không, `10` được coi là một số nguyên còn `10.0` được coi là một số thực. Cụ thể hơn, `10` thuộc [kiểu dữ liệu](../../terminology.md#data-type) `int` còn `10.0` thuộc kiểu dữ liệu `double`.

#### Giá trị tham chiếu là gì?
Sẽ nói sau ở bài về lớp ([class](../../terminology.md#class)).

#### Giá trị null là gì?
Cũng nói ở bài lớp (class).

#### Có những toán tử nào?

- Toán tử gán([assignment](../../terminology.md#assignment)): `=`, thay đổi giá trị trong biến ở vế trái thành giá trị của biểu thức vế phải. Ví dụ `a = 5` lưu số `5` vào trong biến `a`.

- Toán tử toán học:

|Toán tử|Kết quả|Ví dụ|Kết quả ví dụ|
|-------|-------|-----|-------------|
|`+`|Tổng, (cũng dùng để nối xâu)|`5 + 2`|`7`|
|`-`|Hiệu|`5 - 2`|`3`|
|`*`|Tích|`5 * 2`|`10`|
|`/`|Thương|`5 / 2`|`2`|
|`%`|Lấy phần dư|`5 % 2`|`1`|

Các phép toán sẽ khác nhau nếu toán hạng có kiểu dữ liệu khác nhau. Ví dụ: `5 + 6` có kết quả là `11`, `5 + " nguoi"` sẽ có kết quả là `"5 nguoi"`. Nếu toán tử `/` dùng để chia 2 số nguyên thì kết quả luôn là số nguyên (bỏ đi phần thập phân). Ví dụ: `5 / 2` kết quả là `2`, còn `5 / 2.0` kết quả là `2.5`.

- Toán tử so sánh:

|Toán tử|Kết quả|Ví dụ|Kết quả ví dụ|
|-------|-------|-----|-------------|
|`==`|`true` nếu hai vế bằng nhau, ngược lại `false`|`1 == 2`|`false`|
|`!=`|`true` nếu hai vế khác nhau, ngược lại `false`|`1 != 2`|`true`|
|`>`|`true` nếu vế trái lớn hơn vế phải, ngược lại `false`|`1 > 2`|`false`|
|`>=`|`true` nếu vế trái lớn hơn hoặc bằng vế phải, ngược lại `false`|`1 >= 2`|`false`|
|`<`|`true` nếu vế trái nhỏ hơn vế phải, ngược lại `false`|`1 < 2`|`true`|
|`<=`|`true` nếu vế trái nhỏ hơn hoặc bằng vế phải, ngược lại `false`|`1 <= 2`|`true`|

- Toán tử điều kiện:

|Toán tử|Kết quả|Ví dụ|Kết quả ví dụ|
|-------|-------|-----|-------------|
|`&&`|`true` nếu cả hai vế đều là `true`, ngược lại `false`|`true && false`|`false`|
|`||`|`true` nếu một trong hai vế là `true`, ngược lại `false`|`true || false`|`true`|

- Toán tử đơn ngôi:

|Toán tử|Kết quả|Ví dụ|Kết quả ví dụ|
|-------|-------|-----|-------------|
|`-`|Đảo dấu biểu thức|`-(2 - 3)`|`1`|
|`!`|Đổi `true` thành `false` và ngược lại|`!true`|`false`|

- Toán tử tam ngôi: `? :`, nếu kết quả biểu thức trước dấu `?` là `true` thì kết quả biểu thức tam ngôi là kết quả biểu thức sau dấu `?`, nếu không thì là kết quả biểu thức sau dấu `:`. Ví dụ: `2 > 1 ? 2 : 1` kết quả là `2`.

- Toán tử `++` và `--` để tăng hoặc giảm biến một đơn vị. Giả sử giá trị trong biến `a` đang là `5` thì `a++` sẽ tăng giá trị trong biến `a` lên thành `6`.

Ngoài ra, còn một số toán tử khác là kết hợp các toán tử trên như: `+=` (cộng rồi gán, `a += 5` tương đương với `a = a + 5`), `-=`, `*=`, `\=`, `%=`, hay các toán tử làm việc với bit như toán tử đảo bit: `~`, các toán tử dịch bit: `<<`, `>>`, `>>>`, các toán tử so sánh bit:  `&`, `|`, `^`. Một số toán tử liên quan đến lớp như `new`, `instanceof`, `.` sẽ nói ở phần sau.

#### Sử dụng biến trong biểu thức như thế nào?
Nếu toán hạng là biến thì giá trị mà biến đang lưu sẽ được sử dụng làm toán hạng. Trừ trường hợp biến nằm ở vế trái của toán tử gán, lúc này chương trình làm việc với vùng nhớ chứ không quan tâm đến giá trị trong biến.

Ví dụ:
```java
int number, sum;
number = 4;
sum = number + 5;
sum = sum + 6;
```
Khi gặp lệnh `number = 4`, chương trình lưu số `4` vào biến `number` (lưu số `4` vào vùng nhớ được đặt tên là `number`). Khi gặp lệnh `sum = number + 5`, chương trình lấy giá trị đang có trong biến `number` cộng với `5` thu được kết quả là `9` và gán `9` vào trong biến `sum`. Khi gặp lệnh `sum = sum + 6`, chương trình lấy giá trị trong biến `sum` cộng với `6` thu được kết quả là `15` và gán `15` vào trong biến `sum`. Kết thúc 4 lệnh trên, biến `number` có giá trị là `4` và biến `sum` có giá trị là `15`.

Phép toán gán và lệnh khai báo biến còn có thể gộp chung thành 1 lệnh:
```java
int a = 5;
```
Lệnh trên tương đương với 2 lệnh:
```java
int a;
a = 5;
```

Chú ý trước khi thực hiện việc tính toán cần gán giá trị cho biến trước:
```java
int a;
int b = a + 1;
```

Lệnh trên sẽ bị lỗi biên dịch vì `a` chưa có giá trị nên không thể cộng thêm `1`.


#### Có thể gán giá trị của kiểu dữ liệu này sang biến thuộc kiểu dữ liệu khác không?
Muốn gán giá trị thuộc kiểu dữ liệu này sang biến kiểu dữ liệu khác cần thực hiện thao tác ép kiểu (type casting) bằng cách đặt trước giá trị cần ép kiểu kiểu dữ liệu muốn chuyển sang như sau:

```java
int a = 1000;
short b = (short) a;
```

Ở ví dụ trên, giá trị trong biến `a` thuộc kiểu `int` được chuyển sang kiểu dữ liệu `short`, sau đó lưu vào biến `b` thuộc kiểu dữ liệu `short`.

Khi gán từ kiểu dữ liệu nhỏ sang kiểu dữ liệu lớn thì không cần thiết phải ghi rõ là đang ép kiểu. Ví dụ:

```java
short a = 1000;
int b = a;
```

Ngược lại thì sẽ cần ghi rõ, nếu không sẽ bị lỗi biên dịch. Cần chú ý trường hợp giá trị lưu vào biến vượt quá giới hạn biến có thể lưu, kết quả tính toán có thể sai hoặc khi gán giá trị số thực vào một biến số nguyên thì phần thập phân sau dấu phẩy sẽ bị mất.

Thao tác ép kiểu cũng có thể dùng trong biểu thức để thay đổi ý nghĩa của toán tử. Ví dụ:
```java
double a = 1 + 9 / 2;
double b = 1 + (double) 9 / 2;
```

Biến `a` sẽ lưu giá trị `5` do toán tử `/` là phép chia lấy phần nguyên. Biến `b` sẽ lưu giá trị `5.5` do số `9` được chuyển sang kiểu `double` nên phép chia sẽ là phép chia một số thực với một số nguyên.

#### Một biểu thức có nhiều toán tử thì thứ tự thực hiện như thế nào?
Độ ưu tiên của các toán tử như sau (các toán tử ở dòng càng trên càng được thực hiện trước):

&#8594; Toán tử đơn ngôi, `++`, `--`  
&#8594; Các toán tử `*`, `/`, `%`  
&#8594; Các toán tử `+`, `-`  
&#8594; Các toán tử `>`, `>=`, `<`, `<=`  
&#8594; Các toán tử `==`, `!=`  
&#8594; Toán tử `&&`  
&#8594; Toán tử `||`  
&#8594; Toán tử tam ngôi  
&#8594; Toán tử gán.

Nếu các toán tử có độ ưu tiên như nhau thì các toán tử đó thực hiện từ trái sang phải.
Có thể dùng thêm cặp dấu ngoặc đơn để chỉ định phần sẽ được thực hiện trước.
Ví dụ:

|Biểu thức|Kết quả|
|---------|-------|
|`2 + 3 * 4`|`14`|
|`5 * 2 + 3 > 11 && 2 * 2 <= 4`|`true`|
|`(3 + 2) * (4 + 1 - (3 * 2))`|`-6`|
|`a = 2 + 3 > 7`| `false`, và giá trị biến `a` chuyển thành `false`|

#### Lời gọi đến phương thức là gì?
Một [phương thức](../../terminology.md#method) là một chuỗi các [câu lệnh](../../terminology.md#statement) cùng nhau thực hiện một nhiệm vụ nào đó với một đầu vào cho trước. Một phương thức có thể đưa ra một kết quả hoặc không. Nếu phương thức đưa ra một kết quả, có thể dùng phương thức như một toán hạng trong biểu thức. Như đã biết, một chương trình chỉ chạy các câu lệnh trong phương thức `main` nếu phương thức `main` không gọi đến các phương thức khác. Cú pháp để gọi một phương thức như sau:

```
<tên phương thức><dấu ngoặc mở><các đối số cách nhau dấu phẩy><dấu ngoặc đóng>
```

Ví dụ:
```java
Math.pow(2, 3)
```
là một lời gọi đến phương thức `Math.pow` với đầu vào là hai số `2` và `3`, phương thức này làm nhiệm vụ tính `2` mũ `3` và đưa ra kết quả là `8`.

Có thể dùng phương thức trên trong một biểu thức như sau:
```java
int a;
a = 1 + Math.pow(2, 3) + 4;
```

Biểu thức `1 + Math.pow(2, 3) + 4` có kết quả là `13`, được gán vào biến `a`. Sau 2 câu lệnh trên, biến `a` lưu số `13`.

Nếu phương thức không đưa ra giá trị gì thì không thể làm toán hạng trong biểu thức. Ví dụ phương thức `System.out.println` làm nhiệm vụ in ra màn hình và không đưa ra kết quả gì. Câu lệnh sau không thực hiện được:

```java
int a;
a = System.out.println("Dong nay se bi loi");
```

#### Thế cuối cùng câu lệnh biểu thức là gì?
Các biểu thức sau thêm dấu `;` ở cuối thì thành câu lệnh biểu thức:
- Biểu thức gán.
- Biểu thức dùng toán tử `++` hay `--`. 
- Lời gọi phương thức.
- Biểu thức dùng toán tử `new` (bài class).

Những biểu thức khác không thể đứng một mình thành một lệnh (bị lỗi biên dịch).

Ví dụ:
- `a = 10 + 7 + b;`
- `System.out.println("abc");`
- `a++;`

.  
.  
.  

[Còn nữa, mà dài lắm đừng đọc](TLDR.md)

[Bài tập](exercise.md)
