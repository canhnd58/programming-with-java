# Thread

#### Thread là gì?

Thread là một luồng chạy của chương trình, từ trước đến giờ các chương trình của mình chỉ có một luồng chạy (chạy các lệnh tuần tự từ trên xuống dưới của phương thức `main`) nhưng các chương trình còn có thể có nhiều luồng chạy đồng thời với nhau. Chương trình như vậy gọi là chương trình đa luồng (multi-threading).

#### Như nào cơ?

Có 2 cách để dùng thread trong Java là interface `Runnable` hoặc lớp `Thread`, cả hai đều có phương thức `run` cần ghi đè để chứa các lệnh mà luồng đó thực hiện. Ví dụ:

```java
class CountThread extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 100; i ++) {
            System.out.println(i);
        }
    }
}

public class CountThreadTest {
    public static void main(String[] args) {
        Thread t1 = new CountThread();
        t1.start();
        Thread t2 = new CountThread();
        t2.start();
    }
}
```

Để bắt đầu luồng chạy mình dùng phương thức `start` của `Thread`. Chương trình trên sẽ in ra các số từ 0 đến 99 mỗi số hai lần nhưng do hai thread chạy đồng thời nên không đảm bảo thứ tự in ra các số. Chương trình trên có thể in ra một phần của thread 1 sau đó in một phần của thread 2 rồi quay lại in thread 1.

Nếu dùng interface `Runnable` thì làm như sau:

```java
class CountThread implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i ++) {
            System.out.println(i);
        }
    }
}

public class CountThreadTest {
    public static void main(String[] args) {
        Thread t1 = new Thread(new CountThread());
        t1.start();
        Thread t2 = new Thread(new CountThread());
        t2.start();
    }
}
```

#### Thread có cần thiết không?

Rất nhiều ứng dụng thực thế là đa luồng, ví dụ chương trình chạy video phải có một luồng hiển thị hình ảnh một luồng chạy âm thanh; hay những ứng dụng giao diện đồ hoạ làm gì đó mất thời gian sẽ chạy ở một thread khác và vẫn có thread để người dùng tương tác được với ứng dụng.

#### Các thread có liên quan gì đến nhau không?

Các thread chạy độc lập với nhau nhưng có thể dùng chung dữ liệu, ví dụ:

```java
class Account { // Tài khoản ngân hàng
    private int balance;

    public void display() {
        System.out.println(balance);
    }

    public void withdraw(int amount) {
        balance -= amount;
        display();
    }

    public void deposit(int amount) {
        balance += amount;
        display();
    }
}

class TransactionDeposit implements Runnable { // Giao dịch nạp tiền
    private int amount;
    private Account acc;

    public TransactionDeposit(Account acc, int amount) {
        this.amount = amount;
        this.acc = acc;
    }

    @Override
    public void run() {
        acc.deposit(amount);
    }
}

class TransactionWithdraw implements Runnable { // Giao dịch rút tiền
    private int amount;
    private Account acc;

    public TransactionWithdraw(Account acc, int amount) {
        this.amount = amount;
        this.acc = acc;
    }

    @Override
    public void run() {
        acc.withdraw(amount);
    }
}

public class Test {
    public static void main(String[] args) {
        Account acc = new Account();
        new Thread(new TransactionDeposit(acc, 250000)).start();
        new Thread(new TransactionWithdraw(acc, 70000)).start();
    }
}
```

Ví dụ trên sử dụng 2 thread nạp tiền và rút tiền chạy đồng thời và dùng chung đối tượng `acc`, bình thường sẽ in ra màn hình:

```
250000
180000
```

Tuy nhiên cần lưu ý là thao tác rút tiền có thể được thực hiện trước thao tác nạp tiền (thread 2 tạo ra sau nhưng có thể chạy nhanh hơn thread 1) nên cũng có lúc sẽ in ra `-700000 180000`. Hơn nữa phương thức `deposit` của thread 1 vừa chạy xong lệnh `balance += amount` chưa kịp chạy `display()` mà thread 2 chạy lệnh `balance -= amount` và `display()` giữa lúc đó, chương trình có thể in ra `180000 180000`. Để đảm bảo một phương thức của một thread đang chạy thread khác không được phép xen vào mình phải sử dụng từ khoá `synchronized` khi khai báo phương thức:

```java
    public synchronized void withdraw(int amount) { ... }
    ...
    public synchronized void deposit(int amount) { ... }
```

Một phương thức đánh dấu là `synchronized` thì khi phương thức đó đang thực hiện những thread khác sẽ phải đợi phương thức đó thực hiện xong mới thực hiện phương thức `synchronized` (nếu có) của mình.

#### Vậy làm sao để nạp tiền rồi mới rút tiền?

Các đối tượng trong Java đều có phương thức `wait` có tác dụng dừng thread của mình đến khi nào thread khác gọi phương thức `notify` thì mới chạy tiếp, phương thức `withdraw` và `deposit` có thể viết lại như sau:

```java
    public synchronized void withdraw(int amount) {
        while (balance <= 0) {
            try {
                wait();
            } catch (InterruptedException e) {
                System.out.println("Interrupted");
                throw new RuntimeException(e);
            }
        }
        balance -= amount;
        display();
    }

    public synchronized void deposit(int amount) {
        balance += amount;
        display();
        notify();
    }
```

Phương thức `withdraw` dù chạy trước nhưng nếu `balance` không lớn hơn 0 thì sẽ đợi đến khi có lệnh `notify` được gọi mới chạy tiếp nên chương trình luôn in ra màn hình `25000 18000` (dù mình có đổi lệnh `start` của `TransactionWithdraw` lên trước). Phương thức `wait` có ngoại lệ cần xử lý là `InterruptedException` xảy ra khi có vấn đề gì đó không cho thread đợi tiếp.

.  
.  
.  

[Quay lại: Java nâng cao](..)

