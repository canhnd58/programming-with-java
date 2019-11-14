# Các bước lập trình

#### Lập trình Java có những bước nào?
Để lập trình Java, cần làm đầy đủ các bước sau:

1. Tìm một vấn đề có thể giải quyết bằng lập trình.
2. Cảm thấy hứng thú, nếu không &#8594; quay lại bước 1.
3. Tìm hướng giải quyết, thiết kế chương trình.
4. Cảm thấy khả thi, nếu không &#8594; quay lại bước 3.
5. Cài đặt ý tưởng bằng Java và biên dịch.
6. Bị lỗi biên dịch, cảm thấy khó chịu &#8594; quay lại bước 5 **hoặc** chương trình chạy thành công, cảm thấy vui sướng.
7. Kiểm thử chương trình.
8. Thấy chương trình chạy không đúng, cảm thấy khó hiểu &#8594; quay lại bước 3 **hoặc** chương trình chạy đúng, cảm thấy thoả mãn.
9. Viết tài liệu về chương trình và bảo trì.
10. Cảm thấy chán &#8594; quay lại bước 1.

Hoặc bỏ qua vài bước cũng được.

#### Vấn đề gì lập trình giải quyết được?
Bất cứ vấn đề gì giải quyết bằng việc chia nhỏ thành từng bước cụ thể, chia nhỏ đến mức một bước máy tính có thể làm được luôn.
Ví dụ một số thao tác có thể coi là máy tính làm được luôn:
- Cộng 2 số.
- Đổi tên file.
- Kiểm tra mấy giờ rồi.
- Hiển thị cái gì đó lên màn hình.
- Gửi thông tin qua mạng.
- In một file (nếu kết nối với máy in).

Hướng dẫn máy tính chia trường hợp (nếu cái này thì làm cái này, nếu không làm cái khác), lặp đi lặp lại các việc và kết hợp linh hoạt các thao tác sẽ tạo ra các chương trình giải quyết được rất nhiều vấn đề.

#### Ví dụ một vài cái xem nào.
Ví dụ:
- Ý nghĩa cuộc sống là gì? &#8594; không biết mô tả thành các bước như nào &#8594; không lập trình được.
- Có những số nào nhỏ hơn 10 tạo thành 3 cạnh tam giác vuông? &#8594; kiểm tra lần lượt tất cả các bộ ba số (1, 1, 1), (1, 1, 2), (1, 1, 3) ... (1, 1, 9), (1, 2, 1) ... (9, 9, 9) thấy bộ ba nào thoả mãn điều kiện tổng bình phương của 2 số đầu bằng bình phương của số thứ 3 thì tạo thành 3 cạnh tam giác được &#8594; lập trình được.
- Có 1 file lưu tên và email của 1000 người, giờ làm sao gửi email cho từng người nhưng dòng chữ "Kính gửi ..." có tên người tương ứng? &#8594; mở file, đọc lần lượt tên và email của người đầu tiên, thay dấu "..." trong dòng chữ "Kính gửi ..." thành tên người đó rồi gửi mail, tiếp tục như vậy với người thứ hai, người thứ 3 đến hết file &#8594; lập trình được.
- Bài hát vừa ra hay hay không để còn nghe? &#8594; chưa mô tả được cụ thể thế nào là hay thì chưa lập trình được.
- Vẽ cái ảnh này lên màn hình, nếu ấn lên thì ảnh dịch lên, nếu ấn xuống thì ảnh dịch xuống &#8594; vừa tự mô tả các bước rồi đó &#8594; lập trình được.

#### Có vấn đề mà không hứng thú làm thì có làm không?
Nếu không bị bắt làm thì tìm cái khác.

#### Lập trình mô tả được thành các bước mà, không lập trình cho máy tính tự lập trình được à?
Các bước phải cụ thể hơn nữa. Chưa biết cách mô tả một bài toán để máy tính hiểu đúng ý mình thì chưa lập trình cho máy tính tự lập trình được.

*Giờ người ta đang nghiên cứu cách máy tính tự lập trình rồi, lập trình viên sắp thất nghiệp rồi .-.*

#### Thế nào gọi là tìm thấy hướng giải quyết?
Các bước cụ thể giải quyết một vấn đề gọi là thuật toán ([algorithm](../terminology.md#algorithm)). Tìm ra thuật toán có vẻ khả thi (nghĩ máy tính làm theo được) là có thể bắt tay vào bước tiếp theo.

#### Mãi không thấy khả thi thì sao?
Nhảy vào lập trình luôn rồi có thể sẽ ra, hoặc nghĩ tiếp, hoặc đọc thêm sách, hoặc search google, hoặc hỏi người khác giỏi hơn, hoặc bỏ làm cái khác.

#### Thiết kế chương trình là làm gì?
Với chương trình to, cần thiết kế làm sao cho chương trình dễ quản lý. Chia nhỏ chương trình thành vài bước chính, mỗi bước chính tạo thành một bài toán con. Sau đó tập trung giải quyết từng bài toán con độc lập. Bài toán con vẫn to thì chia nhỏ tiếp. Một phần chương trình tập trung giải quyết bước này, phần khác tập trung giải quyết bước khác, sau đó các phần trao đổi với nhau để giải được bài toán ban đầu. Việc chia nhỏ chương trình thành các thành phần độc lập nhưng có thể giao tiếp với nhau gọi là thiết kế chương trình.

Hoặc thiết kế kiểu khác cũng được.

#### Cài đặt là làm gì?
Để máy tính làm theo thuật toán của mình, cần tạo ra một file có đuôi là `.java`. File này sẽ chứa các lệnh thể hiện từng bước từng bước máy tính cần làm theo để ra kết quả mình muốn.

File như vậy gọi là file mã nguồn ([source code](../terminology.md#source-code)). Việc gõ ra file mã nguồn gọi là cài đặt thuật toán, hay còn gọi là [code](../terminology.md#code).

#### Biên dịch là gì?
Thực ra thì máy tính chỉ hiểu ngôn ngữ của nó thôi, muốn giao tiếp với nó mình phải học ngôn ngữ của nó. Một số người rảnh rỗi đã ngồi học ngôn ngữ của nó rồi và viết ra một chương trình gọi là trình biên dịch ([compiler](../terminology.md#compiler)) để dịch lệnh ở ngôn ngữ Java sang ngôn ngữ máy, hay mã máy ([machine code](../terminology.md#machine-code)). Java dễ học hơn nên mình học ngôn ngữ Java, sau đó dùng trình biên dịch để dịch sang ngôn ngữ máy. Từ file mã nguồn đuôi `.java` sau khi biên dịch sẽ ra một file mã máy đuôi `.class` (thực ra với Java là mã máy ảo[\*](TLDR.md#mã-máy-ảo-là-sao)). Sau đó sử dụng file `.class` để chạy chương trình.

#### Làm thế nào để chạy chương trình?
Một máy tính muốn chạy chương trình Java phải cài sẵn máy ảo Java[\*](TLDR.md#máy-ảo-java-là-gì) ([JVM](../terminology.md#jvm) - Java Virtual Machine). Khi chạy chương trình, máy ảo Java đọc các lệnh trong file `.class` và thực thi lần lượt. Để sử dụng máy ảo Java, có thể cài đặt các phần mềm như [NetBeans](https://netbeans.org/), [Eclipse](https://www.eclipse.org/) hay [IntelliJ IDEA](https://www.jetbrains.com/idea/). Các phần mềm này được gọi là môi trường phát triển tích hợp ([IDE](../terminology.md#ide) - Integrated Development Environment), vừa có vùng để soạn thảo, vừa có nút để biên dịch và chạy. Ấn nút là chạy. Với NetBeans, có thể dùng phím F6 để chạy chương trình. Các ví dụ ở các phần sau sẽ dùng NetBeans để minh hoạ.

#### Cài đặt xong không chạy chương trình được luôn à?
Mỗi ngôn ngữ lập trình đều có các nguyên tắc phải tuân theo thì trình biên dịch mới hiểu rồi dịch. Tưởng mình viết đúng nhưng nhiều lúc không đúng, trình biên dịch sẽ báo lỗi là "không hiểu mày viết gì không dịch được", thì sẽ không chạy chương trình được.

#### Làm thế nào để sửa lỗi?
Mỗi khi có chỗ không hiểu, trình biên dịch sẽ báo cho mình biết nó không hiểu ở dòng số bao nhiêu và cố đoán xem mình thiếu cái gì. Nếu dùng NetBeans, các dòng mà trình biên dịch không hiểu sẽ bị gạch chân màu đỏ, trỏ chuột vào đó để xem lỗi và chỉnh sửa lại mã nguồn của mình.

#### Bị lỗi biên dịch không thấy khó chịu thì sao?
:|

#### Sửa hết lỗi không thấy vui thì sao?
Sẽ thấy vui .-.

#### Kiểm thử là gì?
Chương trình đã chạy được không có nghĩa là chạy đúng. Kiểm thử là kiểm tra chương trình với nhiều trường hợp khác nhau để đảm bảo không có trường hợp chương trình chạy sai.

#### Chương trình chạy sai nhưng không biết do đâu thì phải làm sao?
TODO

#### Sao phải viết tài liệu?
Lâu không động vào mình sẽ không nhớ chương trình mình viết từ đời nào có tác dụng gì, hoặc không nhớ đoạn này trong chương trình đang làm gì, hoặc đưa người khác làm tiếp người ta không hiểu gì nên cần viết tài liệu. Tài liệu mô tả chương trình làm gì, các thành phần trong chương trình làm gì.

#### Bảo trì là gì?
Bảo trì là đảm bảo chương trình vẫn còn chạy đúng theo thời gian. Trong quá trình sử dụng chương trình có thể xuất hiện thêm lỗi thì cần sửa hay một số thứ mà chương trình mình phụ thuộc vừa được nâng cấp thì chương trình mình cũng cần nâng cấp theo.

#### Chương trình nào cùng cần viết tài liệu với bảo trì à?
Chương trình nào dùng một lần rồi vứt thì không cần.

.  
.  
.  

[Còn nữa, mà dài lắm đừng đọc](TLDR.md)

[Quay lại: Lập trình Java](..)
