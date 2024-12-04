Flutter hỗ trợ nhiều loại button tích hợp sẵn và các widget tùy chỉnh để tạo ra các kiểu nút khác nhau. Dưới đây là các loại nút phổ biến và cách sử dụng chúng:

---

### 1. **ElevatedButton**
- **Mô tả**: Nút nâng lên, thường dùng để làm nổi bật hành động chính.
- **Code**:
  ```dart
  ElevatedButton(
    onPressed: () {
      print('ElevatedButton pressed');
    },
    style: ElevatedButton.styleFrom(
      backgroundColor: Colors.teal,
      padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
    ),
    child: Text('Elevated Button'),
  )
  ```

---

### 2. **TextButton**
- **Mô tả**: Nút dạng phẳng, không có nền, phù hợp với các hành động ít quan trọng.
- **Code**:
  ```dart
  TextButton(
    onPressed: () {
      print('TextButton pressed');
    },
    style: TextButton.styleFrom(
      foregroundColor: Colors.blue,
    ),
    child: Text('Text Button'),
  )
  ```

---

### 3. **OutlinedButton**
- **Mô tả**: Nút có viền nhưng không có nền, dùng khi cần phân biệt nhẹ so với nền.
- **Code**:
  ```dart
  OutlinedButton(
    onPressed: () {
      print('OutlinedButton pressed');
    },
    style: OutlinedButton.styleFrom(
      side: BorderSide(color: Colors.blue),
    ),
    child: Text('Outlined Button'),
  )
  ```

---

### 4. **IconButton**
- **Mô tả**: Nút chỉ có icon, thường dùng để thực hiện các hành động nhanh.
- **Code**:
  ```dart
  IconButton(
    icon: Icon(Icons.thumb_up),
    color: Colors.blue,
    onPressed: () {
      print('IconButton pressed');
    },
  )
  ```

---

### 5. **FloatingActionButton**
- **Mô tả**: Nút nổi, thường dùng để thực hiện hành động chính trong một màn hình.
- **Code**:
  ```dart
  FloatingActionButton(
    onPressed: () {
      print('FloatingActionButton pressed');
    },
    backgroundColor: Colors.red,
    child: Icon(Icons.add),
  )
  ```

---

### 6. **DropdownButton**
- **Mô tả**: Nút hiển thị menu xổ xuống để chọn giá trị.
- **Code**:
  ```dart
  DropdownButton<String>(
    value: 'Option 1',
    items: [
      DropdownMenuItem(value: 'Option 1', child: Text('Option 1')),
      DropdownMenuItem(value: 'Option 2', child: Text('Option 2')),
    ],
    onChanged: (value) {
      print('Selected: $value');
    },
  )
  ```

---

### 7. **PopupMenuButton**
- **Mô tả**: Nút hiển thị một menu dạng pop-up.
- **Code**:
  ```dart
  PopupMenuButton<String>(
    onSelected: (value) {
      print('Selected: $value');
    },
    itemBuilder: (BuildContext context) {
      return [
        PopupMenuItem(value: 'Option 1', child: Text('Option 1')),
        PopupMenuItem(value: 'Option 2', child: Text('Option 2')),
      ];
    },
  )
  ```

---

### 8. **Custom Button (Tùy chỉnh)**
- **Mô tả**: Tạo nút theo ý thích với `InkWell` hoặc `GestureDetector`.
- **Code**:
  ```dart
  InkWell(
    onTap: () {
      print('Custom button pressed');
    },
    borderRadius: BorderRadius.circular(10),
    child: Container(
      padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
      decoration: BoxDecoration(
        color: Colors.green,
        borderRadius: BorderRadius.circular(10),
      ),
      child: Text('Custom Button', style: TextStyle(color: Colors.white)),
    ),
  )
  ```

---

### 9. **ToggleButton**
- **Mô tả**: Một nhóm nút có thể bật/tắt, thường dùng để chọn một hoặc nhiều giá trị.
- **Code**:
  ```dart
  ToggleButtons(
    isSelected: [true, false, false],
    onPressed: (index) {
      print('Toggled: $index');
    },
    children: [
      Icon(Icons.format_bold),
      Icon(Icons.format_italic),
      Icon(Icons.format_underline),
    ],
  )
  ```

---

### 10. **Switch**
- **Mô tả**: Nút dạng công tắc bật/tắt.
- **Code**:
  ```dart
  Switch(
    value: true,
    onChanged: (value) {
      print('Switch toggled: $value');
    },
  )
  ```

---

### 11. **GestureDetector for Custom Button**
- **Mô tả**: Dùng `GestureDetector` để tạo nút hoàn toàn tuỳ chỉnh.
- **Code**:
  ```dart
  GestureDetector(
    onTap: () {
      print('Custom GestureDetector button pressed');
    },
    child: Container(
      padding: EdgeInsets.all(16),
      decoration: BoxDecoration(
        color: Colors.blue,
        borderRadius: BorderRadius.circular(10),
      ),
      child: Text(
        'Gesture Button',
        style: TextStyle(color: Colors.white),
      ),
    ),
  )
  ```

---

### Kết luận
Mỗi loại nút phù hợp với một trường hợp sử dụng cụ thể. Bạn có thể tùy chỉnh màu sắc, kích thước, và hình dạng của nút bằng các thuộc tính của chúng. Nếu cần sự độc đáo hơn, bạn luôn có thể tự tạo một nút tùy chỉnh. 🚀
