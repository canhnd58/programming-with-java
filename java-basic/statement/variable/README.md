# Biến và khai báo biến

#### Câu lệnh khai báo là gì?
Có một khái niệm quan trọng trong lập trình, đó là biến (variable). Các biến là các vùng nhớ trong bộ nhớ máy tính (memory) lưu giữ tạm thời trạng thái của một chương trình. Khi chương trình chạy đến một lệnh khai báo biến, máy tính sẽ cấp cho chương trình một vùng nhớ và đảm bảo không chương trình nào khác được đụng vào. Chương trình kết thúc thì tất cả các biến được cấp sẽ được giải phóng. Đây là một trong những lý do máy tính bị đơ, có chương trình nào đó xin cấp phát nhiều vùng nhớ quá không còn bộ nhớ cho chương trình khác chạy.

Một biến gồm kiểu dữ liệu (data type) và tên biến. Kiểu dữ liệu là loại dữ liệu biến có thể lưu, một biến sau khi đã khai báo chỉ lưu được 1 loại dữ liệu. Biến cần được đặt tên để các lệnh sau đó có thể dùng.

Cú pháp của lệnh khai báo biến như sau:
```
<kiểu_dữ_liệu><dấu_cách><tên_biến><dấu_chấm_phẩy>
```

Ví dụ:
```
int number;
```
Lệnh trên yêu cầu máy tính cấp phát cho chương trình một vùng nhớ để lưu các số nguyên, và đặt tên vùng nhớ đó là `number`.

Cũng có thể khai báo nhiều biến một lúc như sau:
```
int number1, number2, number3;
```

Câu lệnh trên tương đương với 3 câu lệnh:
```
int number1;
int number2;
int number3;
```

#### Có các kiểu dữ liệu nào?

Có 8 kiểu dữ liệu cơ sở (primitive data types), được khai báo bằng 8 từ khoá như sau:
- 4 kiểu dữ liệu lưu số nguyên:
    - `byte`: chiếm 1 byte trong bộ nhớ, lưu được các số từ `-128` đến `127`.
    - `short`: chiếm 2 byte trong bộ nhớ, lưu được các số từ `-32,768` đến `32,767`.
    - `int`: chiếm 4 byte trong bộ nhớ, lưu được các số từ `2,147,483,648` đến `2,147,483,647`.
    - `long`: chiếm 8 byte trong bộ nhớ, lưu được các số từ `-9,223,372,036,854,775,808` đến `9,223,372,036,854,775,807`
- 2 kiểu dữ liệu lưu số thực, giới hạn tuỳ thuộc vào phần nguyên và phần thực, phần nguyên càng nhiều thì phần thực càng ít và ngược lại:
    - `float`: chiếm 4 byte.
    - `double`: chiếm 8 byte.
- 1 kiểu dữ liệu lưu một kí tự:
    - `char`: chiếm 2 byte.
- 1 kiểu dữ liệu chỉ lưu một trong hai giá trị `true` (đúng) hoặc `false` (sai):
    - `boolean`: kích thước không xác định (<= 1 byte), tuỳ thuộc vào JVM.

Ngoài ra còn có kiểu dữ liệu đặc biệt nữa là `String` dùng để lưu một chuỗi các kí tự.

#### Làm sao để nhớ số 9,223,372,036,854,775,807?
Không ai nhớ cả, tự tính lại:
- 1 bit là `0` hoặc `1` lưu được 2 số khác nhau.
- 2 bit lưu được 4 số khác nhau: `00`, `01`, `10`, `11`. 4 = 2^2.
- 3 bit lưu được 8 số khác nhau: `000`, `001`, `010`, `011`, `100`, `101`, `110`, `111`. 8 = 2^3.
- 1 byte là 8 bit lưu được 2^8 các số khác nhau.
- Kiểu dữ liệu `long` là 8 byte lưu được 2^32 số khác nhau, chia đôi 1 nửa lưu số âm (2^31 số âm), 1 nửa lưu số dương và số 0 (2^31 - 1 số dương và 1 số 0), nên sẽ lưu được các số từ -2^31 đến 2^31 - 1.

9,223,372,036,854,775,807 = 2^31 - 1

#### Đặt tên biến như thế nào cũng được à?

Tại một thời điểm không được phép có 2 biến cùng tên. Tên biến đặt theo quy tắc sau, nếu không trình biên dịch sẽ báo lỗi:
- Không được trùng với từ khoá.
- Bắt đầu bằng một kí tự chữ cái `a-z` hoặc `A-Z`, hoặc kí tự `$`, hoặc kí tự `_`.
- Sau đó có thể có nhiều kí tự chữ cái, chữ số, `$`, `_`.

Ngoài ra, cũng cần đặt theo quy ước đặt tên (naming convention) giữa cộng đồng những người lập trình, nếu không sẽ bị người khác chửi:
- Không dùng kí tự `$`.
- Không bắt đầu tên biến bằng kí tự `_`.
- Tên biến viết thường, nếu tên gồm nhiều từ thì viết hoa chữ cái đầu tiên của các từ thứ 2 trở đi.
- Nếu mục đích của biến chỉ để đại diện cho 1 giá trị cố định, thì viết hoa tất cả chữ cái, các từ cách nhau bởi kí tự `_`.
- Tên biến phải có ý nghĩa, thể hiện được biến lưu cái gì, nhưng cũng đừng dài quá.

Ví dụ đặt tên biến như sau sẽ hợp lệ, không ai phàn nàn:
- `ten`, `hoVaTen`, `tenNguoiThu3`, `soLuong`.
- `name`, `fullName`, `name3`, `numberOfPeople`.
- `SO_PI`, `SO_E`, `MOT`, `HAI`.

Ví dụ đặt tên biến như sau trình biên dịch báo lỗi:
- `int`, `float`, `public`.
- `3people`, `ho va ten`, `abc#def`.

Ví dụ đặt tên biến như sau không bị lỗi nhưng bị chửi:
- `padfafwerdv`
- `TEnCUAtoi`
- `$1234alo`

#### Biến được dùng như thế nào?
Biến dùng trong biểu thức, hỏi biểu thức là gì đi.

#### Biểu thức là gì?
[Bài sau](../expression) sẽ rõ.
