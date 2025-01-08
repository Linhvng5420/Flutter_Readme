# 1 - ```LayoutBuilder```
Dưới đây là tóm tắt các thuộc tính và thông tin liên quan đến widget `LayoutBuilder` trong Flutter:

### **`LayoutBuilder` là gì?**
`LayoutBuilder` là một widget xây dựng giao diện dựa trên các ràng buộc bố cục (layout constraints) được cung cấp bởi cha của nó. Nó giúp bạn thiết kế giao diện linh hoạt và thích ứng với các kích thước màn hình khác nhau.

### **Thuộc tính của `LayoutBuilder`**
| **Thuộc tính**       | **Ý nghĩa**                                                                                         |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| `builder`            | Hàm callback (function) được gọi để xây dựng giao diện. Hàm nhận hai tham số:                       |
|                       | - `BuildContext context`: Ngữ cảnh của widget.                                                     |
|                       | - `BoxConstraints constraints`: Các ràng buộc bố cục từ cha của widget (bao gồm `minWidth`, `maxWidth`, `minHeight`, `maxHeight`). |

### **Các thành phần liên quan**
#### **`BoxConstraints`** (cung cấp cho `LayoutBuilder`)
| **Thuộc tính**       | **Ý nghĩa**                                                                                         |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| `minWidth`           | Chiều rộng tối thiểu mà cha cung cấp.                                                               |
| `maxWidth`           | Chiều rộng tối đa mà cha cung cấp.                                                                  |
| `minHeight`          | Chiều cao tối thiểu mà cha cung cấp.                                                                |
| `maxHeight`          | Chiều cao tối đa mà cha cung cấp.                                                                   |
| `hasBoundedWidth`    | Trả về `true` nếu chiều rộng bị giới hạn (`minWidth != double.infinity && maxWidth != double.infinity`). |
| `hasBoundedHeight`   | Trả về `true` nếu chiều cao bị giới hạn (`minHeight != double.infinity && maxHeight != double.infinity`). |
| `hasInfiniteWidth`   | Trả về `true` nếu chiều rộng không bị giới hạn (`maxWidth == double.infinity`).                     |
| `hasInfiniteHeight`  | Trả về `true` nếu chiều cao không bị giới hạn (`maxHeight == double.infinity`).                     |

### **Ví dụ sử dụng `LayoutBuilder`**
#### **Ví dụ cơ bản**
```dart
import 'package:flutter/material.dart';

class LayoutBuilderExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('LayoutBuilder Example')),
      body: LayoutBuilder(
        builder: (BuildContext context, BoxConstraints constraints) {
          // Kiểm tra chiều rộng để thay đổi giao diện
          if (constraints.maxWidth < 600) {
            return Center(child: Text('Giao diện nhỏ'));
          } else {
            return Center(child: Text('Giao diện lớn'));
          }
        },
      ),
    );
  }
}
```

### **Các thuộc tính và widget liên quan khác**
#### **`MediaQuery`**
| **Mục đích**         | Lấy thông tin kích thước màn hình và các ràng buộc bố cục.                                          |
| **Ví dụ**            | `MediaQuery.of(context).size.width` để lấy chiều rộng màn hình.                                      |

#### **`FittedBox`**
| **Mục đích**         | Thay đổi kích thước widget con để phù hợp với bố cục cha.                                           |

#### **`Flexible` và `Expanded`**
| **Mục đích**         | Được sử dụng trong `Row`, `Column` để kiểm soát kích thước của các widget con trong bố cục.         |

### **Khi nào nên sử dụng `LayoutBuilder`?**
1. Khi bạn cần tùy chỉnh giao diện dựa trên kích thước hoặc ràng buộc từ cha.
2. Để tạo giao diện thích ứng cho nhiều kích thước màn hình (như responsive design).
3. Khi bạn muốn kiểm tra hoặc thao tác với các ràng buộc bố cục cụ thể.
 ---

# 2 - MediaQuery - FittedBox - Flexible - Expanded
#### **`MediaQuery`**  
- **Mục đích**: Lấy thông tin kích thước và ràng buộc của màn hình.  
- **Ví dụ**:  
  ```dart
  MediaQuery.of(context).size.width; // Lấy chiều rộng màn hình
  ```

#### **`FittedBox`**  
- **Mục đích**: Điều chỉnh kích thước widget con để phù hợp với bố cục cha.  

#### **`Flexible` và `Expanded`**  
- **Mục đích**: Kiểm soát kích thước của các widget con trong `Row` và `Column`.  
- **Ví dụ**:  
  ```dart
  Flexible(child: Text('Nội dung'), flex: 1);
  Expanded(child: Text('Nội dung'));
  ```
 ---

# 3 - Tương tự
Dưới đây là danh sách các widget và thuộc tính có chức năng tương tự hoặc hỗ trợ trong việc tạo giao diện linh hoạt, giống như `LayoutBuilder`:

### **1. MediaQuery**
- **Chức năng**: Cung cấp thông tin về kích thước màn hình, độ phân giải, và các ràng buộc bố cục.  
- **Ví dụ**: 
  ```dart
  MediaQuery.of(context).size.width; // Lấy chiều rộng màn hình
  MediaQuery.of(context).orientation; // Lấy hướng màn hình (Portrait/Landscape)
  ```

### **2. ConstrainedBox**
- **Chức năng**: Đặt các ràng buộc về chiều rộng và chiều cao cho một widget con.  
- **Ví dụ**: 
  ```dart
  ConstrainedBox(
    constraints: BoxConstraints(
      minWidth: 100,
      maxWidth: 200,
      minHeight: 50,
      maxHeight: 100,
    ),
    child: Text('Nội dung'),
  );
  ```

### **3. FittedBox**
- **Chức năng**: Thay đổi kích thước widget con để vừa với không gian có sẵn.  
- **Ví dụ**: 
  ```dart
  FittedBox(
    child: Text('Nội dung quá dài'),
  );
  ```

### **4. FractionallySizedBox**
- **Chức năng**: Đặt kích thước của widget con theo tỷ lệ phần trăm so với kích thước cha.  
- **Ví dụ**: 
  ```dart
  FractionallySizedBox(
    widthFactor: 0.5, // Chiếm 50% chiều rộng của cha
    heightFactor: 0.3, // Chiếm 30% chiều cao của cha
    child: Container(color: Colors.blue),
  );
  ```

### **5. Flexible**
- **Chức năng**: Kiểm soát cách một widget con chiếm không gian trong `Row` hoặc `Column`.  
- **Ví dụ**: 
  ```dart
  Flexible(
    flex: 2,
    child: Container(color: Colors.green),
  );
  ```

### **6. Expanded**
- **Chức năng**: Mở rộng widget con để chiếm hết không gian còn lại trong `Row` hoặc `Column`.  
- **Ví dụ**: 
  ```dart
  Expanded(
    child: Container(color: Colors.red),
  );
  ```

### **7. CustomSingleChildLayout**
- **Chức năng**: Tùy chỉnh cách bố trí widget con dựa trên logic bạn tự định nghĩa.  
- **Ví dụ**: Dùng khi cần xây dựng bố cục phức tạp không phù hợp với các widget tiêu chuẩn.

### **8. Stack với Align**
- **Chức năng**: Bố trí widget con dựa trên các vị trí cụ thể (top, bottom, center, v.v.).  
- **Ví dụ**: 
  ```dart
  Stack(
    children: [
      Align(
        alignment: Alignment.topLeft,
        child: Text('Góc trên bên trái'),
      ),
    ],
  );
  ```

### **Tóm lại**  
- **`LayoutBuilder`**: Linh hoạt với bố cục dựa trên ràng buộc.  
- **Tương tự**: `MediaQuery`, `ConstrainedBox`, `Flexible`, `Expanded`.  
- **Bố cục nâng cao**: `CustomSingleChildLayout`, `Stack` với `Align`.

