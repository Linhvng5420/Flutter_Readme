### 1 - So Sánh
```double fontSize = widget.screenWidth * 0.04;```

```dart
  @override
  void initState() {
    super.initState();
    fontSize = widget.screenWidth * 0.04;
  }
```

**- Phạm vi:** 
Trong initState, fontSize có thể là một biến thành viên của lớp.
Trong phương thức build, fontSize là một biến cục bộ, chỉ tồn tại trong phạm vi của phương thức build.

**- Tính toán lại:** 
initState chỉ được gọi một lần khi widget được khởi tạo.
build có thể được gọi nhiều lần, mỗi khi widget cần được xây dựng lại, do đó fontSize sẽ được tính toán lại mỗi lần build được gọi.

**-Nếu screenWidth không thay đổi thường xuyên và bạn muốn tối ưu hóa hiệu suất, hãy sử dụng initState. <br>-Nếu screenWidth có thể thay đổi và bạn cần cập nhật fontSize tương ứng, hãy sử dụng trong phương thức build.**

