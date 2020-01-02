# Kiểm thử tự động

#### Gì đây?
Bình thường kiểm tra chương trình chạy đúng không mình luôn phải thay đổi giá trị của biến hoặc nhập từ bàn phím để thử các trường hợp rồi in kết quả ra màn hình. Còn có cách kiểm tra khác là viết test (lập trình để kiểm thử chương trình khác).

#### Viết chương trình chính đã mệt mà lại còn phải viết chương trình để kiểm tra chương trình chính nữa à? .-.
Lần đầu viết test có thể mất thời gian nhưng khi chương trình chính phải sửa đổi mình không cần phải tự kiểm tra bằng tay lại từng trường hợp nữa, chỉ cần chạy các test là xong.

#### Không học đâu :|
Các test sẽ được viết trong các lớp nằm trong thư mục `test`:

```
Calculator
|---src
|   |---calculator
|       |---Calculator.java
|
|---test
    |---calculator
        |---CalculatorTest.java
```

Dùng NetBeans thì thư mục `test` hiện ra là `Test Packages`. Mỗi file test nên ứng với một lớp muốn kiểm tra và thêm chữ `Test` ở cuối, project trên có một file test tên là `CalculatorTest.java`. Dùng NetBeans có thể chạy tất cả các test trong project bằng cách ấn `Run -> Test Project` hoặc `Ctrl F6`.

#### File CalculatorTest.java trông như thế nào?
Ví dụ file `Calculator.java` như sau:

```java
public class Calculator {
    private int result;

    public Calculator() {
        result = 0;
    }

    public int getResult() {
        return result;
    }

    public Calculator add(int num) {
        result += num;
        return this;
    }

    public Calculator subtract(int num) {
        result -= num;
        return this;
    }
}
```

File `CalculatorTest.java` sử dụng package `org.junit` để kiểm thử tự động như sau:

```java
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class CalculatorTest {

    @Test
    public void testAdd() {
        Calculator cal = new Calculator();

        cal.add(10);
        assertEquals(10, cal.getResult());

        cal.add(15);
        assertEquals(25, cal.getResult());

        cal.add(3).add(6).add(1); // Viết thế này được do phương thức add có lệnh return this
        assertEquals(35, cal.getResult());
    }

    @Test
    public void testSubtract() {
        Calculator cal = new Calculator();
        cal.subtract(2);
        assertEquals(-2, cal.getResult());
    }

    @Test
    public void testAddAndSubtract() {
        Calculator cal = new Calculator();
        cal.add(10).subtract(2);
        assertEquals(8, cal.getResult());
    }
}
```

Lớp `CalculatorTest` ở trên có 3 phương thức được đánh dấu với [annotation](../../terminology.md#annotation) `@Test`, các phương thức này gọi là các [testcase](../../terminology.md#testcase). Mỗi lần ấn test chương trình, tất cả các phương thức đánh dấu bằng `@Test` đều được chạy. Trong mỗi testcase có sử dụng phương thức `assertEquals` là phương thức nhận vào hai tham số và kiểm tra hai tham số có bằng nhau hay không, nếu không bằng nhau thì sẽ đưa ra ngoại lệ `AssertionFailError`, kết thúc phương thức đó và testcase đó được tính là sai (`fail`).

Do package `org.junit` không nằm trong [JDK](../../terminology.md#jdk) nên khi sử dụng ta phải thêm package này vào project của mình. Trong NetBeans click chuột phải vào `Test Libraries` (ở cửa số bên trái), chọn `Add Library` rồi tìm và chọn `JUnit`. Khi đã thêm `JUnit` ta có thể test project bằng cách ấn `Ctrl F6`. Màn hình hiện lên màu xanh là tất cả các test đều thành công, màu đỏ là có test sai, mình có thể click vào để xem chi tiết các lỗi sai rồi sửa.

#### JUnit chỉ có thế thôi phải không?
Ngoài annotation `@Test` còn có các annotation khác như:

- `@Before`: chạy một lần trước khi chạy mỗi phương thức `@Test` trong lớp hiện tại
- `@After`: chạy một lần sau khi chạy mỗi phương thức `@Test` trong lớp hiện tại
- `@BeforeClass`: chạy một lần duy nhất trước khi chạy các phương thức `@Test` trong lớp hiện tại
- `@AfterClass`: chạy một lần duy nhất sau khi chạy hết các phương thức `@Test` trong lớp hiện tại

Ví dụ:


```java
import org.junit.Test;
import org.junit.Before;
import static org.junit.Assert.assertEquals;

public class CalculatorTest {
    private Calculator cal;

    @Before
    public void setUp() {
        cal = new Calculator();
    }

    @Test
    public void testAdd() {
        cal.add(10);
        assertEquals(10, cal.getResult());

        cal.add(15);
        assertEquals(25, cal.getResult());

        cal.add(3).add(6).add(1); // Viết thế này được do phương thức add có lệnh return this
        assertEquals(35, cal.getResult());
    }

    @Test
    public void testSubtract() {
        cal.subtract(2);
        assertEquals(-2, cal.getResult());
    }

    @Test
    public void testAddAndSubtract() {
        cal.add(10).subtract(2);
        assertEquals(8, cal.getResult());
    }
}
```

Phương thức `setUp` được chạy trước khi chạy mỗi phương thức `testAdd`, `testSubtract` và `testAddAndSubtract`. 3 phương thức kia dùng chung biến `cal` nhưng mỗi lần đều tạo đối tượng mới do phương thức `setUp` được gọi trước.

Lớp `Assert` ngoài phương thức `assertEquals` còn có các phương thức khác như: `assertTrue`, `assertFalse`, `assertNull`, `assertNotNull`, `assertArrayEquals` ... tự tìm hiểu.

#### Làm sao để kiểm tra phương thức có ngoại lệ hay không?
Có thể dùng phương thức `static fail()` (hoặc `static fail(String message)`). Khi một testcase gặp một lời gọi đến phương thức `fail` thì testcase đó sẽ kết thúc và tính là sai. Ví dụ:

```java
public class MyException extends Exception{
    @Override
    public String getMessage() {
        return "Lỗi rồi";
    }
}
```

```java
import org.junit.Test;
import static org.junit.Assert.fail;

public class SomeTest {
    @Test
    public void testMethodThrowException() {
        try {
            someMethod();
            fail("Should throw exception");
        }
        catch (Exception e) {
            assertEquals("Lỗi rồi", e.getMessage());
        }
    }
```

Nếu phương thức `someMethod` không gây ra ngoại lệ thì câu lệnh `fail` sẽ được chạy và testcase này tính là sai. Nếu có ngoại lệ nhưng phương phức `getMessage` không trả về đúng xâu kí tự mình muốn thì testcase cũng tính là sai.

.  
.  
.  

[Quay lại: Java nâng cao](..)

