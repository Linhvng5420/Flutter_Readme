Trong Flutter, cả `FutureBuilder` và `StreamBuilder` đều được sử dụng để xây dựng UI dựa trên dữ liệu không đồng bộ, nhưng chúng có những điểm khác nhau về cách xử lý dữ liệu và trường hợp sử dụng.

---

### **1. FutureBuilder**

#### **Khái niệm**
- Dùng để xử lý **Future**.
- `Future` là một tác vụ không đồng bộ mà chỉ trả về **một giá trị duy nhất** hoặc một lỗi sau khi hoàn thành.

#### **Cách sử dụng**
Sử dụng `FutureBuilder` khi bạn muốn lấy dữ liệu từ một API, đọc dữ liệu từ file, hoặc bất kỳ tác vụ nào chỉ thực hiện **một lần**.

#### **Ví dụ**
```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2)); // Giả lập độ trễ
  return "Dữ liệu từ Future";
}

class FutureExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('FutureBuilder Example')),
      body: FutureBuilder<String>(
        future: fetchData(),
        builder: (context, snapshot) {
          if (snapshot.connectionState == ConnectionState.waiting) {
            return Center(child: CircularProgressIndicator());
          } else if (snapshot.hasError) {
            return Center(child: Text('Error: ${snapshot.error}'));
          } else if (snapshot.hasData) {
            return Center(child: Text('Data: ${snapshot.data}'));
          } else {
            return Center(child: Text('No data available.'));
          }
        },
      ),
    );
  }
}
```

---

### **2. StreamBuilder**

#### **Khái niệm**
- Dùng để xử lý **Stream**.
- `Stream` là một luồng dữ liệu không đồng bộ, có thể phát ra **nhiều giá trị** theo thời gian (hoặc không có giá trị nào).

#### **Cách sử dụng**
Sử dụng `StreamBuilder` khi bạn cần xử lý các luồng dữ liệu liên tục như:
- Lắng nghe sự thay đổi trạng thái của ứng dụng.
- Nhận dữ liệu từ WebSocket.
- Cập nhật thời gian thực từ cơ sở dữ liệu.

#### **Ví dụ**
```dart
Stream<int> generateNumbers() async* {
  for (int i = 0; i < 10; i++) {
    await Future.delayed(Duration(seconds: 1)); // Giả lập độ trễ
    yield i;
  }
}

class StreamExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('StreamBuilder Example')),
      body: StreamBuilder<int>(
        stream: generateNumbers(),
        builder: (context, snapshot) {
          if (snapshot.connectionState == ConnectionState.waiting) {
            return Center(child: Text('Waiting for data...'));
          } else if (snapshot.hasError) {
            return Center(child: Text('Error: ${snapshot.error}'));
          } else if (snapshot.hasData) {
            return Center(child: Text('Current number: ${snapshot.data}'));
          } else {
            return Center(child: Text('Stream closed.'));
          }
        },
      ),
    );
  }
}
```

---

### **So sánh FutureBuilder và StreamBuilder**

| **Đặc điểm**         | **FutureBuilder**                          | **StreamBuilder**                          |
|----------------------|--------------------------------------------|--------------------------------------------|
| **Loại dữ liệu**     | `Future` - chỉ trả về một giá trị.         | `Stream` - trả về nhiều giá trị.           |
| **Sử dụng cho**      | Các tác vụ không đồng bộ chỉ chạy một lần. | Các luồng dữ liệu liên tục, thời gian thực. |
| **Ví dụ sử dụng**    | Lấy dữ liệu từ API, đọc file JSON.         | Lắng nghe WebSocket, thay đổi trạng thái.  |
| **Cập nhật UI**      | Chỉ cập nhật UI khi `Future` hoàn thành.  | Cập nhật UI mỗi khi `Stream` phát ra giá trị mới. |

---

### Khi nào nên dùng?
1. **FutureBuilder**:
   - Khi chỉ cần tải dữ liệu một lần duy nhất.
   - Ví dụ: Lấy thông tin người dùng từ API, đọc file.

2. **StreamBuilder**:
   - Khi cần xử lý dữ liệu liên tục thay đổi.
   - Ví dụ: Cập nhật tin nhắn trong chat app, nhận dữ liệu thời gian thực từ WebSocket.

---

Hy vọng bạn đã hiểu rõ sự khác biệt giữa `FutureBuilder` và `StreamBuilder`. Nếu bạn có câu hỏi cụ thể, mình rất sẵn lòng hỗ trợ! 😊
