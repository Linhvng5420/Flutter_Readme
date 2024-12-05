# Thứ 5

Dưới đây là tổng hợp kiến thức Flutter mà bạn đã học hôm nay qua các trao đổi:

---

### 1. **Điều chỉnh kích thước giao diện theo màn hình**  
- **Text tự động điều chỉnh kích thước:**  
  - Sử dụng `FittedBox` với `fit: BoxFit.scaleDown` trong `Text` để chữ tự thu nhỏ theo kích thước container hoặc màn hình.
  - Ví dụ:
    ```dart
    FittedBox(
      fit: BoxFit.scaleDown,
      child: Text(
        "Nội dung",
        style: TextStyle(fontSize: 14),
      ),
    )
    ```

- **Icon tự động điều chỉnh kích thước:**  
  - Lấy kích thước màn hình bằng `MediaQuery` và tính kích thước icon dựa trên tỷ lệ.
  - Ví dụ:
    ```dart
    double iconSize = MediaQuery.of(context).size.width * 0.08; // 8% chiều rộng màn hình
    Icon(Icons.home, size: iconSize);
    ```

---

### 2. **Bố cục linh hoạt với `Row` và `Column`**  
- Sử dụng `Spacer` để định vị các phần trong `Column`.  
  - Ví dụ: Phần 1 luôn ở đầu, phần 2 ở giữa, phần 3 ở cuối.
    ```dart
    Column(
      children: [
        // Phần 1
        Container(child: Text("Phần 1")),
        Spacer(), // Đẩy phần 2 xuống giữa
        // Phần 2
        Container(child: Text("Phần 2")),
        Spacer(), // Đẩy phần 3 xuống cuối
        // Phần 3
        Container(child: Text("Phần 3")),
      ],
    );
    ```

- Sử dụng `Expanded` trong `Row` để các nút hoặc widget chia sẻ không gian đồng đều và tự động co giãn.
  - Ví dụ:
    ```dart
    Row(
      children: [
        Expanded(
          child: ElevatedButton(onPressed: () {}, child: Text("Nút 1")),
        ),
        SizedBox(width: 10), // Khoảng cách giữa các nút
        Expanded(
          child: ElevatedButton(onPressed: () {}, child: Text("Nút 2")),
        ),
      ],
    );
    ```

---

### 3. **Tùy chỉnh Button**  
- **Thêm margin, border, và padding:**  
  - Sử dụng `Container` để bọc `ElevatedButton` cho margin và border.
  - Ví dụ:
    ```dart
    Container(
      margin: EdgeInsets.all(8.0), // Khoảng cách xung quanh
      decoration: BoxDecoration(
        borderRadius: BorderRadius.circular(10),
      ),
      child: ElevatedButton(
        onPressed: () {},
        style: ElevatedButton.styleFrom(
          padding: EdgeInsets.symmetric(vertical: 12, horizontal: 16), // Padding
          backgroundColor: Colors.blue,
        ),
        child: FittedBox(child: Text("Button Text")),
      ),
    );
    ```

---

### 4. **GridView hiển thị danh sách**  
- Dùng `GridView.builder` để hiển thị danh sách các phòng với cột cố định:
  ```dart
  GridView.builder(
    gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
      crossAxisCount: 2, // Số cột
      crossAxisSpacing: 10, // Khoảng cách giữa các cột
      mainAxisSpacing: 10, // Khoảng cách giữa các hàng
      childAspectRatio: 3 / 4, // Tỷ lệ khung
    ),
    itemCount: rooms.length, // Số lượng item
    itemBuilder: (context, index) {
      return RoomCard(
        roomName: rooms[index].name,
        customerName: rooms[index].customerName,
        price: rooms[index].price,
      );
    },
  );
  ```

---

### 5. **Custom Icon Button**  
- Tạo một nút icon với viền, màu nền, và kích thước tùy chỉnh:
  ```dart
  class CustomIconButton extends StatelessWidget {
    final Color? borderColor;
    final double borderRadius;
    final double buttonSize;
    final Color? fillColor;
    final Widget icon;
    final VoidCallback? onPressed;

    const CustomIconButton({
      required this.borderRadius,
      required this.buttonSize,
      this.borderColor,
      this.fillColor,
      required this.icon,
      this.onPressed,
    });

    @override
    Widget build(BuildContext context) {
      return Material(
        color: Colors.transparent,
        borderRadius: BorderRadius.circular(borderRadius),
        child: InkWell(
          onTap: onPressed,
          borderRadius: BorderRadius.circular(borderRadius),
          child: Container(
            width: buttonSize,
            height: buttonSize,
            decoration: BoxDecoration(
              color: fillColor ?? Colors.transparent,
              borderRadius: BorderRadius.circular(borderRadius),
              border: Border.all(
                color: borderColor ?? Colors.transparent,
                width: 1,
              ),
            ),
            child: Center(child: icon),
          ),
        ),
      );
    }
  }
  ```

---

### 6. **Tổ chức UI với các widget tùy chỉnh**
- Sử dụng widget như `RoomCard`, `RoomTabButtons`, và `StatisticCard` để chia nhỏ giao diện và dễ quản lý.
- Áp dụng `Expanded`, `Padding`, và `MediaQuery` trong các widget để đảm bảo giao diện linh hoạt trên mọi kích thước màn hình.

---

Hôm nay bạn đã học được khá nhiều kiến thức về Flutter qua các trao đổi. Dưới đây là một số nội dung bổ sung mà bạn đã thực hành hoặc áp dụng:

---

### 7. **`Wrap` cho giao diện nhiều dòng**  
- Khi các button hoặc widget trong `Row` không đủ không gian, bạn có thể sử dụng `Wrap` để tự động xuống dòng:
  ```dart
  Wrap(
    spacing: 10, // Khoảng cách ngang giữa các widget
    runSpacing: 10, // Khoảng cách dọc giữa các dòng
    children: [
      RoomTabButtons(label: "Tất Cả", color: Colors.blue),
      RoomTabButtons(label: "Đã Cho Thuê", color: Colors.green),
      RoomTabButtons(label: "Còn Trống", color: Colors.orange),
    ],
  );
  ```
- **Ứng dụng:** Hiển thị các nhóm button lọc trong giao diện.

---

### 8. **`MediaQuery` cho mọi thành phần UI**  
- **Điều chỉnh kích thước dựa trên màn hình:**  
  - Bạn đã áp dụng `MediaQuery` không chỉ cho icon mà còn cho:
    - Kích thước button.
    - Padding và margin của các widget.
    - Tỷ lệ kích thước `childAspectRatio` trong `GridView`.
  - Cách tính kích thước theo phần trăm màn hình:
    ```dart
    double screenWidth = MediaQuery.of(context).size.width;
    double screenHeight = MediaQuery.of(context).size.height;
    double iconSize = screenWidth * 0.08; // Ví dụ: 8% chiều rộng
    ```

---

### 9. **`Card` và giao diện linh hoạt**  
- **Tổ chức thông tin trong `RoomCard`:**
  - Phân chia bố cục rõ ràng:  
    - Phần 1: Tên phòng.
    - Phần 2: Thông tin khách hàng (nếu có) hoặc nút "Thêm Khách Hàng".
    - Phần 3: Nút "Chỉnh Sửa" và "Xóa".
  - Sử dụng `Spacer` để đẩy các phần lên/xuống linh hoạt:
    ```dart
    Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        // Phần 1
        Text("Tên Phòng", style: TextStyle(fontWeight: FontWeight.bold)),
        Spacer(),
        // Phần 2
        customerName != null
            ? Text("Khách Hàng: $customerName")
            : ElevatedButton(onPressed: () {}, child: Text("Thêm Khách Hàng")),
        Spacer(),
        // Phần 3
        Row(
          children: [
            TextButton(onPressed: () {}, child: Text("Chỉnh Sửa")),
            TextButton(onPressed: () {}, child: Text("Xóa")),
          ],
        ),
      ],
    );
    ```

---

### 10. **Tạo nút chức năng linh hoạt (`FunctionButtons`)**
- Bạn đã tạo nút với các biểu tượng động (thay đổi dựa trên danh sách icon).  
- Các bước:
  - Sử dụng `List` chứa danh sách icon.
  - Lặp qua danh sách và tạo widget nút từ `CustomIconButton`.
  - Ví dụ:
    ```dart
    Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: [
        for (var iconData in [
          Icons.replay,
          Icons.repeat_outlined,
          Icons.remove_red_eye_outlined,
          Icons.edit_note
        ])
          Expanded(
            child: CustomIconButton(
              borderRadius: 8,
              buttonSize: MediaQuery.of(context).size.width * 0.1,
              fillColor: Colors.blueAccent,
              icon: Icon(iconData, color: Colors.white),
              onPressed: () => print('${iconData.codePoint} pressed'),
            ),
          ),
      ],
    );
    ```

---

### 11. **Phân chia code rõ ràng**
- Bạn đã học cách tạo các **widget riêng biệt** cho từng thành phần, giúp tái sử dụng và quản lý dễ dàng:
  - `RoomTabButtons`: Button với border, padding, và tự điều chỉnh kích thước chữ.
  - `RoomCard`: Hiển thị thông tin phòng với bố cục 3 phần rõ ràng.
  - `FunctionButtons`: Nút chức năng có danh sách biểu tượng động.
  - `RoomGrid`: Hiển thị danh sách phòng dạng lưới.

---

### 12. **Divider và khoảng cách giữa các phần**  
- Sử dụng `Divider` để phân tách nội dung:
  ```dart
  Divider(
    thickness: 3, // Độ dày
    color: Color(0x6F000000), // Màu sắc
  );
  ```
- Tạo khoảng cách bằng `SizedBox`:
  ```dart
  SizedBox(height: 10); // Khoảng cách dọc 10 pixel
  ```

---

### Tổng hợp các kỹ năng chính:
- **Điều chỉnh giao diện:** Tự động co giãn kích thước (text, icon, button) theo màn hình.
- **Bố cục động:** Sử dụng `Spacer`, `Wrap`, `Expanded` để bố trí widget linh hoạt.
- **Tái sử dụng widget:** Tạo các widget tùy chỉnh giúp quản lý dễ dàng hơn.
- **GridView:** Tối ưu hóa việc hiển thị danh sách phòng dưới dạng lưới.
- **Widget nâng cao:** Tạo các thành phần giao diện tùy chỉnh như `CustomIconButton` và `FunctionButtons`.

---

Nếu bạn có yêu cầu hoặc cần mở rộng thêm phần nào, hãy cho mình biết nhé! 😊
