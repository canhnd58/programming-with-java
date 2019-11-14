# Bài tập: Các câu lệnh điều khiển luồng

### Bài 1:

Chỉ số BMI (Body Mass Index) dùng để đánh giá mức độ gầy hay béo của một người thông qua các chỉ số về cân nặng và chiều cao của cơ thể. Chỉ số BMI được tính bằng cân nặng của người đó (kg) chia cho bình phương chiều cao (m).

Viết chương trình tạo hai biến `weight` và `height` để lưu chiều cao và cân nặng của bản thân, sau đó sử dụng câu lệnh `if-else` in ra một trong các dòng chữ sau tuỳ theo chỉ số BMI:
- `Thiếu cân`: BMI nhỏ hơn `18.5`
- `Bình thường`: BMI từ `18.5` đến `25.0`
- `Thừa cân`: BMI từ `25.0` đến `30.0`
- `Béo phì`: BMI từ `30.0` trở lên

### Bài 2:

Một năm dương lịch (thời gian Trái Đất quay một vòng quanh Mặt Trời) dài khoảng 365 ngày 6 giờ cho nên thông thường cứ 3 năm có 365 ngày sẽ đến một năm có 366 ngày. Năm có 366 ngày gọi là năm nhuận, người ta coi những năm chia hết cho 4 là năm nhuận. Ví dụ năm 2004, 2008 là năm nhuận trong khi năm 2005, 2006 không phải. Thực tế thì một năm dương lịch ngắn hơn 365 ngày 6 giờ một chút nên người ta điều chỉnh lịch sao cho những năm chia hết cho 100 thì phải chia hết cho 400 nữa mới gọi là năm nhuận. Ví dụ năm 1600, 2000 là các năm nhuận nhưng năm 1700, 1800, 1900 không được gọi là năm nhuận.

Viết chương trình tạo một biến `year` để lưu một năm và sử dụng câu lệnh `if-else` kiểm tra năm đó là năm nhuận hay không. Khi thay đổi giá trị biến `year` thì kết quả phải giống như sau:

|Giá trị biến `year`|Kết quả in ra màn hình|
|---|---|
|1996|1996 là năm nhuận|
|1997|1997 không phải năm nhuận|
|1998|1998 không phải năm nhuận|
|1999|1999 không phải năm nhuận|
|2000|2000 là năm nhuận|
|2100|2100 không phải năm nhuận|

### Bài 3:

Viết chương trình tạo một biến `letter` để lưu một kí tự và kiểm tra kí tự đó có phải là một nguyên âm trong tiếng Anh không, sử dụng câu lệnh `switch`.

|Giá trị biến `letter`|Kết quả in ra màn hình|
|---|---|
|a|a là nguyên âm|
|0|0 không phải nguyên âm|
|e|e là nguyên âm|
|i|i là nguyên âm|
|m|m không phải nguyên âm|
|o|o là nguyên âm|
|u|u là nguyên âm|
|z|z không phải nguyên âm|

### Bài 4:

Viết chương trình tạo một biến `times` lưu một số nguyên dương bất kì, sau đó sử dụng câu lệnh `for` in ra màn hình `times` lần dòng chữ `alo`.

### Bài 5:

Sử dụng câu lệnh lặp in ra màn hình 100 số nguyên dương đầu tiên chia hết cho 7.

### Bài 6:

Sử dụng câu lệnh `while` in ra màn hình tổng các chữ số của một số nguyên dương. Gợi ý: chia lấy phần dư với 10 để lấy ra chữ số cuối, chia lấy phần nguyên với 10 để xoá chữ số cuối.

|Số cần kiểm tra|Kết quả in ra màn hình|
|---|---|
|123|6|
|4|4|
|21980|20|

### Bài 7:

Sử dụng câu lệnh lặp kiểm tra một số có phải là số nguyên tố hay không, số nguyên tố là số chỉ chia hết cho 1 và chính nó. Gợi ý: cần tạo thêm một biến phụ.

|Số cần kiểm tra|Kết quả in ra màn hình|
|---|---|
|2|2 là nguyên tố|
|5|5 là nguyên tố|
|9|9 không phải nguyên tố|
|11|11 là nguyên tố|
|16|16 không phải nguyên tố|
|3189|3189 không phải nguyên tố|
|3191| 3191 là nguyên tố|

### Bài 8:

Biết câu lệnh `System.out.print("a");` sẽ in ra màn hình chữ `a` và không xuống dòng. Câu lệnh `System.out.println();` sẽ chỉ xuống dòng và không in ra gì. Viết chương trình tạo một biến `size` và in ra màn hình hình vuông có kích thước `size x size` như sau(ví dụ `size = 5`):

```
*****
*****
*****
*****
*****
```

### Bài 9:
Câu lệnh `do-while` chưa nghĩ ra bài nào.
