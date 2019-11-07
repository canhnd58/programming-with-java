# Biểu thức và câu lệnh biểu thức

#### Biểu thức là gì?
Biểu thức (expression) là sự kết hợp giữa các toán tử (operator) và toán hạng (operand) theo quy tắc mà ngôn ngữ cho phép.
Khi chạy chương trình, biểu thức luôn được tính thành một giá trị cụ thể.

#### Toán tử là gì?
Toán tử là các phép toán như `+`, `-`, `*`, `/`, dùng để thực hiện một phép tính với các toán hạng sau đó đưa ra một kết quả.

#### Toán hạng là gì?
Toán hạng có thể là giá trị cụ thể (literal), biến (variable), lời gọi đến phương thức (method invocation) hay biểu thức con.
Tuỳ thuộc các toán hạng thuộc kiểu dữ liệu nào mà các toán tử có thể có ý nghĩa khác nhau.

#### Biểu thức trông như thế nào?
Một số ví dụ về biểu thức:
- `100`
- `100 + 20`
- `(3 + 4) * 5 + 6 / 2`
- `number * 10`
- `"Toi ten la: " + hoVaTen`
- `number++`
- `20 + tinhTrungBinh(2, 4, 3)`

#### Câu lệnh biểu thức là gì?
Biểu thức thêm dấu `;` ở cuối thì thành câu lệnh biểu thức thôi.

#### Có những giá trị cụ thể nào trong Java?
Java có những giá trị cụ thể sau:
- Các số nguyên như: `0`, `1`, `100`, `-100`.
- Các số thực như: `0.1`, `-10.25`.
- Các kí tự như: `'a'`, `'B'`, `'%'`, `'3'` (các kí tự luôn đặt trong cặp dấu nháy đơn `'` để phân biệt với số, toán tử, và tên biến).
- Các xâu (hay còn gọi là chuỗi) kí tự như: `"xin chao"`, `"hello world!"`, `"a"` (các chuỗi kí tự luôn nằm trong cặp dấu nháy kép `"` để phân biệt với tên biến).
- Hai giá trị boolean: `true` và `false` (chú ý không có dấu nháy kép).
- Giá trị đặc biệt thể hiện việc không có giá trị: `null`.

#### Có những toán tử nào?
- Toán tử gán:

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`=`| lưu một giá trị hoặc kết quả của một biểu thức ở <br>vế phải của toán tử vào biến ở vế trái | `a = 5` | `5`, đồng thời biến `a` lưu giá trị `5` |

- Toán tử toán học: các toán tử sau làm việc với 2 toán hạng (một toán hạng bên trái, một toán hạng bên phải)

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`+`| lấy tổng 2 số, hoặc nối 2 xâu. Nếu một toán hạng là<br> xâu một toán hạng là số thì là phép toán nối xâu | `2 + 3`<br> `"hello " + "world"`<br> `"hello" + 1` | `5`<br>`"hello world"`<br>`"hello1"` |
|`-`| lấy hiệu 2 số | `2 - 3` | `-1` |
|`*`| lấy tích 2 số | `2.2 * 3` | `6.6` |
|`/`| lấy thương 2 số nếu một trong 2 số là số thực,<br> nếu cả 2 đều là số nguyên thì lấy phần nguyên của thương 2 số | `9.0 / 2`<br>`9 / 2` | `4.5`<br>`4` |
|`%`| chỉ áp dụng với số nguyên, lấy phần dư khi chia 2 số | `9 / 2` | `1` |

- Toán tử so sánh: kết quả của các toán tử sau luôn là `true` hoặc `false`:

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`==`| Kiểm tra 2 toán hạng bằng nhau không | `1 == 2` | `false` |
|`!=`| Kiểm tra 2 toán hạng khác nhau không | `1 != 2` | `true` |
|`<`| Kiểm tra toán hạng bên trái bé hơn toán hạng bên phải không | `1 < 2` | `true` |
|`<=`| Kiểm tra toán hạng bên trái bé hơn hoặc bằng toán hạng bên phải không | `1 <= 2` | `true` |
|`>`| Kiểm tra toán hạng bên trái lớn hơn toán hạng bên phải không | `1 > 2` | `false` |
|`>=`| Kiểm tra toán hạng bên trái lớn hơn hoặc bằng toán hạng bên phải không | `1 >= 2` | `false` |

- Toán tử điều kiện: kết quả của các toán tử sau luôn là `true` hoặc `false` và các toán hạng phải có giá trị thuộc kiểu boolean

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`&&`| Chỉ trả kết quả `true` nếu cả 2 toán hạng ở 2 bên đều là `true`,<br> nếu không kết quả là `false` | `(1 > 2) && (1 > 0)` | `false` |
|`||`| Chỉ trả kết quả `false` nếu cả 2 toán hạng ở 2 bên đều là `false`,<br> nếu không kết quả là `true` | `(1 > 2) || (1 > 0)` | `true` |

- Toán tử đơn ngôi: là toán tử làm việc với một toán hạng

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`-`| Đảo dấu của một biểu thức | `-(4+5)` | `-9`|
|`!`| Đổi `true` thành `false`, `false` thành `true` | `!true` | `false` |
|`++`| Tăng giá trị của biến lên một đơn vị. Nếu biến ở trước toán tử, kết quả của biểu thức là giá trị trước khi tăng. Nếu biến ở sau toán tử, kết quả của biểu thức là giá trị sau khi tăng | (Giả sử biến `a` đang lưu số `4`) <br> `a++` <br> `++a` | (Cả hai trường hợp giá trị biến `a` đến tăng lên thành `5`)<br> `4` <br> `5` |
|`--`| Giảm giá trị của biến xuống một đơn vị. Nếu biến ở trước toán tử, kết quả của biểu thức là giá trị trước khi giảm. Nếu biến ở sau toán tử, kết quả của biểu thức là giá trị sau khi giảm | (Giả sử biến `a` đang lưu số `4`) <br> `a++` <br> `++a` | (Cả hai trường hợp giá trị biến `a` đến giảm xuống thành `3`)<br> `4` <br> `3` |

- Toán tử tam ngôi:

| Toán tử | Ý nghĩa | Ví dụ | Kết quả biểu thức |
|---------|---------|-------|-------------------|
|`? :`| Kiểm tra biểu thức trước dấu `?`, nếu kết quả là `true`,<br> đưa ra kết quả là kết quả của biểu thức sau dấu `?`,<br> nếu không, đưa ra kết quả là kết quả biểu thức sau dấu `:`| `(1 > 2) ? 4 : 5` | `5` |

Ngoài ra, còn một số toán tử khác là kết hợp các toán tử trên như: `+=` (cộng rồi gán, `a += 5` tương đương với `a = a + 5`), `-=`, `*=`, `\=`, `%=`, hay các toán tử làm việc với bit như toán tử đảo bit: `~`, các toán tử dịch bit: `<<`, `>>`, `>>>`, các toán tử so sánh bit:  `&`, `|`, `^`.

Còn có toán tử `new` và toán tử `instanceof` liên quan đến lớp (class) và đối tượng (object) sẽ bàn ở các phần sau.

#### Sử dụng biến trong biểu thức như thế nào?
Nếu toán hạng là biến thì giá trị mà biến đang lưu sẽ được sử dụng để tính toán. Trừ trường hợp biến nằm ở vế trái của toán tử gán, lúc này chương trình làm việc với vùng nhớ của biến chứ không quan tâm đến giá trị trong biến.

Ví dụ:
```
int number, sum;
number = 4;
sum = a + 5;
sum = sum + 6;
```
Khi gặp lệnh `number = 4`, chương trình lưu số `4` vào vùng nhớ của biến `number`. Khi gặp lệnh `sum = number + 5`, chương trình lấy giá trị đang có trong biến `number` cộng với `5` thu được kết quả là `9` và gán `9` vào trong vùng nhớ của biến `sum`. Khi gặp lệnh `sum = sum + 6`, chương trình lấy giá trị trong biến `sum` cộng với `6` thu được kết quả là `15` và gán `15` vào trong vùng nhớ của biến `sum`. Kết thúc 4 lệnh trên, biến `number` có giá trị là `4` và biến `sum` có giá trị là `15`.

Phép toán gán và lệnh khai báo biến còn có thể gộp chung thành 1 lệnh:
```java
int a = 5;
```
Lệnh trên tương đương với 2 lệnh:
```java
int a;
a = 5;
```

#### Một biểu thức có nhiều toán tử thì thứ tự thực hiện như thế nào?
Độ ưu tiên của các toán tử như sau (các toán tử ở dòng càng trên càng được thực hiện trước):

&#8594; Toán tử đơn ngôi  
&#8594; Các toán tử `*`, `/` và `%`  
&#8594; Các toán tử `+` và `-`  
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

#### Làm sao để nhớ thứ tự thực hiện các phép toán?
Dùng nhiều thì nhớ thôi, nếu không nhớ thì cứ dùng dấu ngoặc đơn cho chắc.

#### Lời gọi đến phương thức là gì?
Một phương thức là một chuỗi các câu lệnh cùng nhau thực hiện một nhiệm vụ nào đó với một đầu vào cho trước. Một phương thức có thể đưa ra một kết quả hoặc không. Nếu phương thức đưa ra một kết quả, có thể dùng phương thức như một toán hạng trong biểu thức. Như đã biết, một chương trình chỉ chạy các câu lệnh trong phương thức `main` nếu phương thức `main` không gọi đến các phương thức khác. Cú pháp để gọi một phương thức như sau:

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

Nếu phương thức không đưa ra giá trị gì thì không thể làm toán hạng trong biểu thức. Ví dụ phương thức `System.out.println` làm nhiệm vụ in ra màn hình và không đưa ra kết quả gì nên phải đứng một mình. Ví dụ câu lệnh sau không thực hiện được:

```java
int a;
a = System.out.println("Dong nay se bi loi");
```

#### Làm sao biết phương thức nào làm gì và có đưa ra kết quả hay không?
Google là bạn thân nhất của lập trình viên.
