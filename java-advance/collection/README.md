# Collection

#### Collection là gì?

Java cung cấp rất nhiều lớp và interface để làm việc với tập hợp nhiều phần tử (giống như mảng).

#### Như nào?
Để làm việc với nhiều phần tử, Java có 2 interface chính là `java.util.Collection` và `java.util.Map`:

```
Collection<E>
|---List<E>
|   |---ArrayList<E>
|   |---LinkedList<E>
|   |---...
|
|---Set<E>
|   |---HashSet<E>
|   |---TreeSet<E>
|
|---...

Map<K,V>
|---HashMap<K,V>
|---TreeMap<K,V>

```

Các lớp và interface trên đều là generic. Chú ý sơ đồ trên không thể hiện quan hệ cha con trực tiếp giữa các lớp và interface. Ví dụ `LinkedList` thừa kế nhưng không trực tiếp từ `List`.

#### Dùng List như thế nào?

`List<E>` là interface đại diện cho danh sách gồm nhiều phần tử (`E` là kiểu dữ liệu của một phần tử), có một số phương thức hay dùng như sau:

- `boolean add(E e)`: thêm phần tử `e` vào cuối danh sách.
- `void add(int index, E element)`: thêm phần tử `e` vào vị trí `index`.
- `E set(int index, E element)`: thay phần tử ở vị trí `index` thành `element`.
- `E get(int index)`: trả về phần tử tại vị trí `index`.
- `int size()`: trả về số lượng phần tử trong danh sách.
- `boolean isEmpty()`: kiểm tra danh sách có rỗng hay không.
- `E remove(int index)`: xoá phần tử tại vị trí `index`.
- `boolean remove(Object element)`: xoá phần tử đầu tiên mà giống với `element` trong danh sách (sử dụng phương thức `equals`).
- `boolean contains(Object element)`: kiểm tra có chứa phần tử `element` không.
- `Object[] toArray()`: trả về mảng đại diện cho danh sách.

Lớp `ArrayList<E>` là lớp cụ thể thừa kế từ interface `List<E>` nên có các phương thức trên. Lớp `ArrayList` lưu các phần tử nằm cạnh nhau trong bộ nhớ (giống mảng) và có thể thay đổi kích thước trong lúc chạy chương trình (không cần phải khởi tạo với số lượng phần tử cố định).

```java
ArrayList<Book> books = new ArrayList<>();
books.add(new Book("Book1"));
books.add(new Book("Book2"));

Book book = books.get(1); // Book2
```

#### Dùng Set như thế nào?

`Set<E>` là interface đại diện cho tập hợp của nhiều phần tử, các phần tử trong `Set` không được giống nhau (thông qua phương thức `equals`) và tối đa một phần tử `null`. `Set` có các phương thức hay dùng sau:

- `boolean add(E e)`: thêm phần tử `e` vào tập hợp nếu tập hợp chưa có `e`.
- `int size()`: trả về số lượng phần tử trong tập hợp.
- `boolean isEmpty()`: kiểm tra tập hợp có rỗng hay không.
- `boolean remove(Object element)`: xoá phần tử giống với `element` trong tập hợp (sử dụng `equals`).
- `boolean contains(Object element)`: kiểm tra có chứa phần tử `element` không.
- `Object[] toArray()`: trả về mảng đại diện cho danh sách.

Phương thức `contains` của `Set` thực hiện nhanh hơn rất nhiều của `List` nên nếu thao tác kiểm tra một phần tử có trong tập hợp được dùng nhiều lần thì nên dùng `Set` hơn là `List`. Cụ thể hơn, nếu số lượng phần tử trong tập hợp là `n` thì phương thức `contains` của `HashSet` có độ phức tạp là O(1) (có nghĩa là thời gian chạy phương thức không phụ thuộc vào `n`, nhiều hay ít phần tử không ảnh hưởng đến tốc độ của phương thức), còn phương thức `contains` của `ArrayList` có độ phức tạp là O(n) (có nghĩa là thời gian chạy phương thức phụ thuộc tuyến tính vào `n`, `n` tăng gấp đôi thì thời gian chạy phương thức tăng gấp đôi). 

Có 2 lớp hay dùng thừa kế interface `Set<E>` là:
- `TreeSet<E>`: các phần tử trong tập hợp được sắp xếp tăng dần.
- `HashSet<E>`: các phần tử có thứ tự không xác định, nhưng phương thức `contains` thực hiện nhanh hơn của `TreeSet<E>`.

Giả sử hai quyển sách có tên giống nhau được coi là giống nhau (do ghi đè phương thức `equals`) thì

```java
HashSet<Book> books = new HashSet<>();
books.add(new Book("Book1"));
books.add(new Book("Book2"));
books.add(new Book("Book3"));
books.add(new Book("Book1"));

System.out.println(books.size());
```
Sẽ in ra 3 do quyển sách `Book1` lần thứ 2 sẽ không được thêm.

#### Dùng Map như thế nào?

`Map<K,V>` là interface đại diện cho một bảng gồm các khoá (`K`) và giá trị tương ứng của khoá (`V`). Ví dụ như quyển từ điển có thể coi là một `Map` có các khóa là các từ, giá trị là giải thích nghĩa của các từ; hay một `Map` các sinh viên trong lớp học có các khoá là mã sinh viên và giá trị là đối tượng sinh viên tương ứng. Các khoá trong `Map` không được trùng nhau, `Map` có các phương thức hay dùng sau:

- `V put(K key, V value)`: thêm một cặp khoá và giá trị vào bảng, nếu khoá `key` đã có trong bảng thì giá trị `value` sẽ ghi đè vào giá trị đang có của khoá `key`.
- `V get(Object key)`: trả về giá trị tại khoá `key`, hoặc `null` nếu không có khoá `key` trong bảng.
- `boolean isEmpty()`: kiểm tra bảng có rỗng hay không.
- `int size()`: trả về kích thước của bảng.
- `void clear()`: xoá hết các khoá và giá trị khỏi bảng.
- `boolean containsKey(Object key)`: kiểm tra có khoá `key` trong bảng hay không.
- `boolean containsValue(Object value)`: kiểm tra có giá trị `value` trong bảng hay không.
- `V remove(Object key)`: xoá khoá `key` và giá trị tương ứng khỏi bảng.
- `Set<K> keySet()`: trả về tập hợp chứa các khoá.
- `Collection<V> values()`: trả về các giá trị.

Giống như `Set`, có 2 lớp hay được sử dụng thừa kế từ `Map`:

- `TreeMap<K,V>`: các khoá được sắp xếp tăng dần.
- `HashMap<K,V>`: các khoá có thứ tự không xác định, nhưng phương thức `containsKey(Object key)` và `get(Object key) thực hiện nhanh hơn của `TreeMap<K,V>`.

`Map` hay được sử dụng khi một đối tượng có thể được đại diện bởi một khoá và thao tác tìm kiếm theo khoá được sử dụng nhiều.

```java
HashMap<String, Student> students = new HashMap<>();
students.put("13020203", new Student("13020203", "Nguyễn Văn A"));
students.put("13020204", new Student("13020204", "Nguyễn Văn B"));

System.out.println(students.get("13020203").getName()); // Nguyễn Văn A
```

#### List, Set với Map có dùng chỉ số để truy cập các phần tử giống như mảng không?

Không phải lớp nào trong `Collection` cũng sử dụng chỉ số như mảng nên để duyệt hết các phần tử thì thường dùng vòng lặp `for` như sau:

```java
Collection<Book> books = new ...

// Thêm vào books
// ...

for (Book book : books) {
    System.out.println(book);
}
```

Khi đó, với mỗi lần lặp của vòng lặp `for`, biến `book` sẽ tham chiếu đến một phần tử của `books`. Có thể dùng biến `book` để thay đổi các thuộc tính của các đối tượng trong `books` (ví dụ `book.setTitle`) nhưng không thể dùng `book` để thay thế một đối tượng trong `books` thành đối tượng khác. Ví dụ:

```java
for (Book book : books) {
    if (book.getName().equals("Book1")) {
        book.setName("BookA");
    }

    if (book.getName().equals("Book2")) {
        book = new Book("BookB");
    }
}
```

Các quyển sách có tên là `Book1` sẽ được đổi tên là `BookA` nhưng các quyển có tên `Book2` vẫn giữa nguyên do tham chiếu `book` trỏ tới đối tượng `Book` khác nhưng tham chiếu mà `books` đang giữ không thay đổi.

Để duyệt một `Map<String, Book> bookMap` thì có thể dùng như sau:

```java
for (String key : bookMap.keySet()) {
    System.out.println(bookMap.get(key)); 
}
```

#### Mảng có duyệt như vậy được không?

Mảng cũng làm vậy được, nhưng cũng có lưu ý giống như duyệt một `Collection`:

```java
int[] arr = {2, 3, 1};
for (int e : arr) {
    if (e == 3)
        e = 4;
}
```

Mảng trên sẽ không thay đổi do ở lần lặp thứ 2, `e` và `arr[1]` dù có cùng giá trị là `3` nhưng là 2 biến khác nhau.

```java
int[] arr = {2, 3, 1};
for (int i = 0; i < arr.length; i ++) {
    if (arr[i] == 3)
        arr[i] = 4;
}
```

Mảng trên sẽ đổi thành `{2, 4, 1}`.

#### Còn có gì khác duyệt được như thế?

Mảng và các lớp thừa kế interface `Iterable<T>` đều duyệt được bằng vòng lặp `for` như trên. Interface `Collection` thừa kế `Iterable` nên tất cả các lớp con đều duyệt được như vậy. Ngoài ra `Iterable<T>` còn có phương thức `Iterator<T> iterator()` trả về một đối tượng `Iterator` để duyệt hết các phần tử. Một đối tượng `Iterator` có các phương thức:

- `boolean hasNext()`: kiểm tra có phần tử tiếp theo không.
- `T next()`: lấy ra phần tử tiếp theo.
- `void remove()`: xoá khỏi danh sách phần tử cuối cùng lấy ra từ `iterator` này.

Ví dụ:

```java
List<Book> books = new ArrayList<>();
...
Iterator<Book> it = books.iterator();

while (it.hasNext()) {
    Book book = it.next();
    if (book.getName().equals("Book1")) {
        it.remove();
    }
}
```

.  
.  
.  

[Quay lại: Java nâng cao](..)
