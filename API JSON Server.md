# **JSON Server**
Dưới đây là hướng dẫn chi tiết cách cài đặt và sử dụng **JSON Server** để tạo API RESTful từ file JSON:

### **1. Cài đặt Node.js**
JSON Server yêu cầu Node.js. Nếu chưa cài đặt Node.js, làm theo các bước sau:
- Tải Node.js tại [https://nodejs.org/](https://nodejs.org/).
- Chọn phiên bản LTS (dài hạn) để cài đặt.
- Sau khi cài đặt xong, mở terminal (hoặc cmd) và kiểm tra bằng lệnh:
  ```bash
  node -v
  npm -v
  ```
  Nếu hiển thị phiên bản, Node.js đã được cài đặt thành công.

### **2. Cài đặt JSON Server**
Mở terminal hoặc cmd và chạy lệnh sau:
```bash
npm install -g json-server
```
- Lệnh này sẽ cài đặt JSON Server toàn cục, cho phép bạn chạy từ bất kỳ thư mục nào.

### **3. Tạo file JSON**
Tạo một file JSON để làm nguồn dữ liệu cho API. Ví dụ, file `db.json` có nội dung sau:
```json
{
  "products": [
    { "id": 1, "name": "Gạch xây", "price": 5000 },
    { "id": 2, "name": "Xi măng", "price": 70000 },
    { "id": 3, "name": "Sắt thép", "price": 200000 }
  ],
  "categories": [
    { "id": 1, "name": "Vật liệu xây dựng" },
    { "id": 2, "name": "Dụng cụ" }
  ]
}
```
Lưu file này vào thư mục làm việc của bạn.

### **4. Chạy JSON Server**
Trong terminal, di chuyển đến thư mục chứa file `db.json`, sau đó chạy lệnh:
```bash
json-server --watch db.json
```

### **5. Truy cập API**
Sau khi chạy lệnh trên, JSON Server sẽ khởi động API RESTful. Bạn có thể truy cập tại:
- URL chính: [http://localhost:3000](http://localhost:3000)
- Endpoint ví dụ:
  - Lấy danh sách sản phẩm: [http://localhost:3000/products](http://localhost:3000/products)
  - Lấy danh mục: [http://localhost:3000/categories](http://localhost:3000/categories)

### **6. Sử dụng JSON Server với cổng khác (tuỳ chọn)**
Nếu muốn đổi cổng, bạn có thể dùng tham số `--port`:
```bash
json-server --watch db.json --port 4000
```
API sẽ chạy tại [http://localhost:4000](http://localhost:4000).

### **7. Các lệnh API RESTful hỗ trợ**
JSON Server hỗ trợ đầy đủ các lệnh CRUD:
- **GET**: Lấy dữ liệu (`/products`)
- **POST**: Thêm mới dữ liệu
- **PUT**: Cập nhật dữ liệu
- **DELETE**: Xoá dữ liệu

Ví dụ sử dụng với `POST` để thêm sản phẩm mới:
- URL: `http://localhost:3000/products`
- Body (JSON):
  ```json
  { "name": "Sơn nước", "price": 120000 }
  ```

### **8. Dừng JSON Server**
Để dừng server, nhấn **Ctrl + C** trong terminal.



# Truy cập API chạy trên máy thật từ máy ảo Android
Dưới đây là hướng dẫn chi tiết cách sử dụng địa chỉ **`10.0.2.2`** để truy cập API chạy trên máy thật từ máy ảo Android (emulator):

### **1. Hiểu `10.0.2.2`**
- Máy ảo Android (Android Emulator) không thể trực tiếp truy cập địa chỉ **`localhost`** hoặc **`127.0.0.1`** của máy tính thật vì hai hệ thống tách biệt nhau.
- Địa chỉ **`10.0.2.2`** được Android Emulator ánh xạ để đại diện cho **`localhost`** trên máy tính thật.
### **2. Thiết lập API trên máy thật**
Dưới đây là ví dụ chạy một API trên máy tính thật bằng **`json-server`**.

#### **Cài đặt `json-server`**
1. **Cài đặt Node.js**:
   - Tải từ [Node.js](https://nodejs.org/) và cài đặt.
2. **Cài đặt `json-server`**:
   Mở terminal và chạy:
   ```bash
   npm install -g json-server
   ```

#### **Tạo file API mẫu**
1. Tạo file **`db.json`** trong một thư mục, nội dung như sau:
   ```json
   {
     "posts": [
       { "id": 1, "title": "Hello World", "author": "User" },
       { "id": 2, "title": "Second Post", "author": "Admin" }
     ]
   }
   ```

2. Chạy **json-server** với lệnh:
   ```bash
   json-server --watch db.json --port 3000
   ```
   - API sẽ hoạt động tại **`http://localhost:3000`**.

### **3. Truy cập API từ máy ảo**
Khi máy ảo Android chạy, thực hiện như sau:

1. **Truy cập từ trình duyệt máy ảo:**
   - Mở trình duyệt trong Android Emulator và nhập:
     ```plaintext
     http://10.0.2.2:3000/posts
     ```
   - Bạn sẽ thấy danh sách dữ liệu JSON từ API.

2. **Tích hợp vào Flutter**
   Trong code Flutter, sử dụng **HTTP client** để kết nối API:
   ```dart
   import 'package:flutter/material.dart';
   import 'package:http/http.dart' as http;
   import 'dart:convert';

   class MyApp extends StatelessWidget {
     @override
     Widget build(BuildContext context) {
       return MaterialApp(
         home: Scaffold(
           appBar: AppBar(title: Text('Fake API Example')),
           body: Center(
             child: ElevatedButton(
               onPressed: fetchPosts,
               child: Text('Fetch Posts'),
             ),
           ),
         ),
       );
     }

     void fetchPosts() async {
       final response = await http.get(Uri.parse('http://10.0.2.2:3000/posts'));

       if (response.statusCode == 200) {
         print('Response: ${json.decode(response.body)}');
       } else {
         print('Failed to fetch posts');
       }
     }
   }

   void main() => runApp(MyApp());
   ```

3. **Chạy ứng dụng trên máy ảo:**
   - Chạy lệnh:
     ```bash
     flutter run
     ```
   - Nhấn nút "Fetch Posts", dữ liệu sẽ được in trong **debug console** hoặc hiển thị trên ứng dụng tùy thiết kế.

### **4. Xử lý lỗi phổ biến**
#### **Lỗi 1: Không truy cập được API từ máy ảo**
- **Nguyên nhân**: API có thể không chạy đúng hoặc firewall chặn.
- **Cách xử lý**:
  - Đảm bảo **json-server** đang chạy (kiểm tra với **http://localhost:3000** trên trình duyệt máy thật).
  - Thêm **json-server** vào danh sách ngoại lệ của firewall.

#### **Lỗi 2: Máy ảo không kết nối mạng**
- Kiểm tra kết nối mạng của máy ảo:
  - Vào **Settings** → **Network & Internet** → Bật **Wi-Fi**.

### **5. Kết hợp với `ngrok` (nếu cần truy cập từ bên ngoài)**
Nếu bạn cần API hoạt động trên cả thiết bị thật hoặc ngoài mạng cục bộ:
1. **Cài đặt `ngrok`:**
   - Tải từ [ngrok](https://ngrok.com/).
2. **Public API bằng `ngrok`:**
   - Chạy lệnh:
     ```bash
     ngrok http 3000
     ```
   - Ngrok sẽ cung cấp URL công khai, ví dụ:
     ```plaintext
     https://abcd-1234.ngrok.io
     ```
   - Truy cập từ máy ảo hoặc thiết bị thật với URL này.

Hãy thử và cho mình biết nếu gặp vấn đề hoặc cần thêm hướng dẫn! 😊
