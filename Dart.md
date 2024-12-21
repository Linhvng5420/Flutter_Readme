# Phân Tích Code
```dart
const Object i = 3; // Where i is a const Object with an int value...
const list = [i as int]; // Use a typecast.
const map = {if (i is int) i: 'int'}; // Use is and collection if.
const set = {if (list is List<int>) ...list}; // ...and a spread.
```

*Cách sử dụng: `const`, ép kiểu (`typecast`), kiểm tra kiểu (`is`), `collection if` và `spread operator` (`...`) để làm việc với các giá trị hằng số (`const`).*
- `const list` chứa danh sách `[3]`.
- `const map` chứa bản đồ `{3: 'int'}`.
- `const set` chứa tập hợp `{3}`.
---

# **Spread Operator (`...`)**

**Spread Operator (`...`)** trong Dart được sử dụng để "trải" các phần tử của một tập hợp dữ liệu (như `List`, `Set`, hoặc `Map`) vào một tập hợp mới. Nó giúp hợp nhất, sao chép, hoặc thêm các phần tử từ một tập hợp vào một tập hợp khác một cách gọn gàng và hiệu quả.

 **1. Trong danh sách (`List`)**
Spread Operator được dùng để thêm tất cả các phần tử của một danh sách vào một danh sách khác.

```dart
void main() {
  var list1 = [1, 2, 3];
  var list2 = [0, ...list1, 4, 5];

  print(list2); // Output: [0, 1, 2, 3, 4, 5]
}
```

- **Giải thích**:
  - `...list1` sẽ "trải" các phần tử của `list1` vào `list2`.
  - `list2` chứa các phần tử của `list1` và các giá trị khác.

 **2. Trong tập hợp (`Set`)**
Tương tự như danh sách, Spread Operator có thể được sử dụng với `Set`.

```dart
void main() {
  var set1 = {1, 2, 3};
  var set2 = {0, ...set1, 4, 5};

  print(set2); // Output: {0, 1, 2, 3, 4, 5}
}
```

- **Lưu ý**: Trong `Set`, các phần tử trùng lặp sẽ tự động bị loại bỏ.

 **3. Trong bản đồ (`Map`)**
Spread Operator cũng có thể "trải" các cặp key-value từ một `Map` sang một `Map` khác.

```dart
void main() {
  var map1 = {'a': 1, 'b': 2};
  var map2 = {'c': 3, ...map1};

  print(map2); // Output: {c: 3, a: 1, b: 2}
}
```

- **Giải thích**:
  - `...map1` sẽ sao chép tất cả các cặp key-value từ `map1` sang `map2`.
  - Nếu key bị trùng lặp, giá trị mới sẽ ghi đè giá trị cũ.


 **4. Null-aware Spread Operator (`...?`)**

Trong trường hợp một tập hợp có thể `null`, bạn có thể sử dụng **Null-aware Spread Operator (`...?`)** để tránh lỗi khi "trải" một tập hợp `null`.

```dart
void main() {
  var list1 = null;
  var list2 = [0, ...?list1, 4, 5];

  print(list2); // Output: [0, 4, 5]
}
```

- **Giải thích**:
  - `...?list1` đảm bảo rằng nếu `list1` là `null`, thì nó sẽ không gây lỗi và không thêm gì vào `list2`.
---

# **So sánh giữa List, Set và Map trong Dart**

| **Tiêu chí**            | **List**                                           | **Set**                                         | **Map**                                         |
|-------------------------|---------------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Khái niệm**           | Danh sách các phần tử được sắp xếp theo thứ tự.   | Tập hợp các phần tử **duy nhất** (không trùng lặp). | Tập hợp các cặp **key-value** để lưu trữ dữ liệu. |
| **Thứ tự**              | Giữ nguyên thứ tự các phần tử khi thêm vào.       | Không đảm bảo thứ tự (trừ `LinkedHashSet`).   | Không đảm bảo thứ tự (trừ `LinkedHashMap`).   |
| **Truy cập**            | Truy cập bằng chỉ số (index), bắt đầu từ 0.       | Không hỗ trợ chỉ số, chỉ duyệt qua iterator.  | Truy cập bằng **key**.                        |
| **Dữ liệu trùng lặp**   | Cho phép các phần tử trùng lặp.                   | Không cho phép phần tử trùng lặp.             | Key phải duy nhất, nhưng value có thể trùng.  |
| **Cú pháp khởi tạo**    | `List<int> list = [1, 2, 3];`                     | `Set<int> set = {1, 2, 3};`                   | `Map<int, String> map = {1: 'one', 2: 'two'};`|
| **Khi nào dùng?**       | Khi cần lưu danh sách có thứ tự.                  | Khi cần tập hợp các giá trị không trùng lặp.  | Khi cần lưu trữ dữ liệu dạng key-value.       |

 **1. List**
```dart
void main() {
  List<int> list = [1, 2, 3, 2];
  
  print(list);      // Output: [1, 2, 3, 2]
  print(list[1]);   // Truy cập phần tử thứ hai: Output: 2
}
```
- **Đặc điểm**:
  - Cho phép phần tử trùng lặp (ví dụ: `2` xuất hiện hai lần).
  - Truy cập phần tử bằng chỉ số (`index`).
 **2. Set**
```dart
void main() {
  Set<int> set = {1, 2, 3, 2};
  
  print(set); // Output: {1, 2, 3}
}
```
- **Đặc điểm**:
  - Không cho phép phần tử trùng lặp (phần tử `2` chỉ xuất hiện một lần).
  - Thứ tự không được đảm bảo (trừ khi dùng `LinkedHashSet`).

 **3. Map**
```dart
void main() {
  Map<int, String> map = {1: 'one', 2: 'two', 3: 'three'};
  
  print(map);      // Output: {1: one, 2: two, 3: three}
  print(map[2]);   // Truy cập giá trị với key = 2: Output: two
}
```
- **Đặc điểm**:
  - Dữ liệu được lưu dưới dạng cặp key-value.
  - Key phải duy nhất, nhưng value có thể trùng lặp.

 **Khi nào sử dụng?**
1. **Sử dụng List**:
   - Khi cần một danh sách giá trị có thứ tự.
   - Ví dụ: Danh sách sản phẩm, danh sách người dùng.

2. **Sử dụng Set**:
   - Khi cần một tập hợp các giá trị không trùng lặp.
   - Ví dụ: Danh sách email duy nhất, ID không trùng.

3. **Sử dụng Map**:
   - Khi cần lưu trữ dữ liệu dạng cặp key-value để tra cứu nhanh.
   - Ví dụ: Thông tin người dùng với `ID` là key và `Tên` là value.

 **Tóm tắt**
- **List**: Thích hợp để lưu trữ danh sách có thứ tự, cho phép phần tử trùng lặp.
- **Set**: Dùng khi cần tập hợp các giá trị không trùng lặp, không cần thứ tự.
- **Map**: Thích hợp cho dữ liệu dạng key-value, key phải duy nhất, hỗ trợ tra cứu nhanh.
---

# **So sánh `const`, `final`, và `late` trong Dart**

| **Tiêu chí**             | **Const**                                              | **Final**                                              | **Late**                                               |
|--------------------------|-------------------------------------------------------|-------------------------------------------------------|-------------------------------------------------------|
| **Khái niệm**            | Hằng số bất biến được xác định tại **compile time**.   | Biến chỉ được gán một lần, giá trị có thể xác định tại **runtime**. | Biến được khởi tạo khi cần (lazy initialization).     |
| **Thời điểm khởi tạo**    | Tại thời điểm biên dịch (compile time).                | Tại thời điểm chạy chương trình (runtime).            | Chỉ khởi tạo khi biến được sử dụng lần đầu tiên.      |
| **Có thể thay đổi giá trị?**| Không, giá trị cố định và không thể thay đổi.          | Không, chỉ được gán giá trị một lần duy nhất.         | Không, sau khi khởi tạo không thể thay đổi.           |
| **Sử dụng cho đối tượng** | Chỉ với các đối tượng bất biến (immutable).            | Được dùng với cả đối tượng mutable và immutable.       | Tương tự như `final`, nhưng chỉ khởi tạo khi cần.      |
| **Thích hợp dùng khi**    | Giá trị được biết trước và không thay đổi (hằng số compile time). | Giá trị chỉ được gán một lần và có thể được xác định tại runtime. | Khi muốn trì hoãn khởi tạo cho hiệu suất.             |

 **1. `const`**
- Giá trị phải được biết trước tại thời điểm biên dịch (compile time).
- Không thể gán lại hoặc thay đổi sau khi đã khởi tạo.

**Ví dụ:**
```dart
void main() {
  const int number = 5;
  const double pi = 3.14;

  // Sử dụng hằng số compile time
  print(number); // Output: 5
  print(pi);     // Output: 3.14
}
```

**Lưu ý:**
- `const` có thể sử dụng cho các giá trị bất biến như chuỗi, số, hoặc danh sách không thay đổi.
- Không thể dùng `const` nếu giá trị cần khởi tạo tại runtime.

 **2. `final`**
- Chỉ có thể gán giá trị một lần và không thể thay đổi sau khi đã gán.
- Giá trị có thể được xác định tại thời điểm runtime.

**Ví dụ:**
```dart
void main() {
  final DateTime now = DateTime.now();

  print(now); // Output: Thời điểm hiện tại tại runtime
}
```

**Lưu ý:**
- `final` linh hoạt hơn `const` vì giá trị có thể được xác định trong quá trình chạy chương trình.

 **3. `late`**
- Được sử dụng để trì hoãn việc khởi tạo biến cho đến khi nó được sử dụng lần đầu tiên.
- Thường được dùng với `final` hoặc các biến không muốn khởi tạo ngay lập tức.

**Ví dụ:**
```dart
void main() {
  late String greeting;

  // Khởi tạo giá trị khi cần
  greeting = 'Hello, Dart!';
  print(greeting); // Output: Hello, Dart!
}
```

**Lưu ý:**
- Nếu truy cập biến `late` mà chưa khởi tạo, chương trình sẽ báo lỗi.
- Kết hợp tốt với các biến tốn tài nguyên hoặc cần khởi tạo muộn.

 **Khi nào sử dụng?**

| **Tình huống**                               | **Nên dùng**          |
|---------------------------------------------|-----------------------|
| Giá trị không thay đổi, có thể xác định trước. | `const`              |
| Giá trị chỉ gán một lần, xác định tại runtime. | `final`              |
| Khởi tạo muộn để tối ưu hiệu suất hoặc tránh lãng phí tài nguyên. | `late`               |

 **Tóm tắt**
- **`const`**: Hằng số bất biến, xác định tại **compile time**.
- **`final`**: Gán một lần, xác định tại **runtime**.
- **`late`**: Trì hoãn khởi tạo, chỉ khởi tạo khi cần.
---

# **Mutable và Immutable là gì?**
 **1. Khái niệm**
- **Mutable**: 
  - Đối tượng có thể **thay đổi trạng thái** hoặc giá trị sau khi đã được khởi tạo.
  - Ví dụ: Danh sách có thể thêm, xóa, hoặc sửa phần tử.

- **Immutable**:
  - Đối tượng không thể thay đổi sau khi đã được khởi tạo.
  - Mọi thao tác chỉnh sửa trên một đối tượng immutable sẽ tạo ra một bản sao mới thay vì thay đổi chính đối tượng ban đầu.

 **So sánh Mutable và Immutable**

| **Tiêu chí**          | **Mutable**                               | **Immutable**                              |
|-----------------------|-------------------------------------------|-------------------------------------------|
| **Khả năng thay đổi**  | Có thể thay đổi giá trị hoặc trạng thái.   | Không thể thay đổi giá trị sau khi khởi tạo. |
| **Hiệu suất**          | Hiệu quả khi thay đổi dữ liệu nhiều lần.   | Hiệu quả hơn trong các ứng dụng bất biến (cần nhiều bản sao dữ liệu). |
| **An toàn dữ liệu**    | Dễ gặp lỗi nếu nhiều tham chiếu thay đổi đối tượng cùng lúc. | An toàn hơn, vì dữ liệu không thay đổi.    |
| **Ví dụ trong Dart**   | `List`, `Map` khi không được gán là `final` hoặc `const`. | Các đối tượng được khai báo với `const`.   |


 **1. Đối tượng Mutable**
```dart
void main() {
  List<int> mutableList = [1, 2, 3];

  // Thay đổi giá trị của danh sách
  mutableList.add(4);
  print(mutableList); // Output: [1, 2, 3, 4]
}
```
- **Đặc điểm**:
  - `mutableList` có thể được sửa đổi, ví dụ: thêm, xóa phần tử.

 **2. Đối tượng Immutable**
```dart
void main() {
  const List<int> immutableList = [1, 2, 3];

  // immutableList.add(4); // Lỗi: Không thể thay đổi danh sách
  print(immutableList); // Output: [1, 2, 3]
}
```
- **Đặc điểm**:
  - `immutableList` không thể thay đổi sau khi được khởi tạo do sử dụng `const`.

 **Khi nào sử dụng Mutable và Immutable?**
- **Mutable**:
  - Khi cần thay đổi dữ liệu liên tục trong cùng một đối tượng.
  - Ví dụ: Thay đổi danh sách sản phẩm, cập nhật cấu hình.

- **Immutable**:
  - Khi cần đảm bảo dữ liệu không thay đổi để tránh lỗi hoặc giữ nguyên trạng thái.
  - Ví dụ: Hằng số, cấu hình ứng dụng, hoặc dữ liệu không cần chỉnh sửa.

**Tóm lại**
- **Mutable**: Đối tượng có thể thay đổi.
- **Immutable**: Đối tượng không thể thay đổi, an toàn hơn trong nhiều trường hợp lập trình.

 **Tại sao `final` được sử dụng cho cả mutable và immutable trong Dart?**

 **1. `final` trong Dart**
- `final` chỉ định rằng một biến **chỉ được gán giá trị một lần duy nhất** sau khi nó được khởi tạo.
- Tuy nhiên, điều này không có nghĩa là giá trị của đối tượng được tham chiếu bởi `final` là bất biến (**immutable**). Nếu đối tượng là kiểu dữ liệu **mutable**, bạn vẫn có thể thay đổi trạng thái bên trong của nó.

 **Cách hoạt động của `final` với Mutable và Immutable**
 **1. Với Mutable Object**
`final` đảm bảo rằng biến không thể tham chiếu đến một đối tượng khác, nhưng trạng thái của đối tượng được tham chiếu có thể thay đổi.

**Ví dụ:**
```dart
void main() {
  final List<int> numbers = [1, 2, 3];

  // Không thể gán numbers sang danh sách khác
  // numbers = [4, 5, 6]; // Lỗi: Không thể gán giá trị mới cho biến final

  // Nhưng có thể thay đổi nội dung của danh sách
  numbers.add(4);
  print(numbers); // Output: [1, 2, 3, 4]
}
```

- **Giải thích**:
  - Biến `numbers` luôn tham chiếu đến cùng một danh sách.
  - Tuy nhiên, bạn có thể thay đổi nội dung của danh sách (vì danh sách là một đối tượng **mutable**).

 **2. Với Immutable Object**
`final` kết hợp với đối tượng immutable đảm bảo rằng cả biến và nội dung của nó đều không thể thay đổi.

**Ví dụ:**
```dart
void main() {
  final List<int> numbers = const [1, 2, 3];

  // Không thể gán lại
  // numbers = const [4, 5, 6]; // Lỗi

  // Không thể thay đổi nội dung
  // numbers.add(4); // Lỗi
}
```

- **Giải thích**:
  - `const` biến danh sách thành một đối tượng bất biến (**immutable**), vì vậy nội dung bên trong danh sách không thể thay đổi.
  - Kết hợp với `final`, bạn không thể thay đổi cả tham chiếu và trạng thái của đối tượng.

 **Vì sao `final` được sử dụng cho cả mutable và immutable?**

1. **Kiểm soát tham chiếu:**
   - `final` đảm bảo rằng một biến không thể thay đổi tham chiếu sang một đối tượng khác sau khi được khởi tạo.
   - Điều này hữu ích trong việc giữ tính nhất quán của biến.

2. **Phân biệt mutable và immutable phụ thuộc vào đối tượng:**
   - Nếu đối tượng là **mutable**, bạn có thể thay đổi trạng thái của nó ngay cả khi nó được khai báo là `final`.
   - Nếu đối tượng là **immutable** (như sử dụng `const`), trạng thái của nó không thể thay đổi bất kể `final` hay không.

3. **Tăng tính an toàn và dễ đọc mã nguồn:**
   - Sử dụng `final` giúp đảm bảo rằng biến không thể bị gán lại giá trị mới, điều này tránh được các lỗi lập trình không mong muốn.

 **Tóm lại**
- `final` chỉ đảm bảo **tham chiếu** của biến không thay đổi, không liên quan đến trạng thái bên trong của đối tượng.
- Đối với đối tượng mutable, bạn vẫn có thể thay đổi nội dung bên trong.
- Đối với đối tượng immutable, `final` kết hợp với `const` sẽ đảm bảo cả tham chiếu và trạng thái đều không thay đổi.
