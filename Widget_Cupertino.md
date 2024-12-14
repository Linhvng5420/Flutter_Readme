**`Cupertino`** trong Flutter là một bộ widget mang phong cách thiết kế của iOS. Nó được sử dụng để tạo giao diện người dùng trông giống các ứng dụng trên iOS, đảm bảo tính nhất quán về thiết kế khi phát triển ứng dụng đa nền tảng. Flutter cung cấp `Cupertino` widgets nằm trong thư viện `flutter/cupertino.dart`.

---

### **Cách sử dụng `Cupertino`**

1. **Thêm thư viện Cupertino:**
   - Không cần cài đặt thêm package vì `Cupertino` đã tích hợp trong Flutter.
   - Import thư viện:
     ```dart
     import 'package:flutter/cupertino.dart';
     ```

2. **Tạo ứng dụng cơ bản với CupertinoApp:**
   ```dart
   import 'package:flutter/cupertino.dart';

   void main() {
     runApp(const MyCupertinoApp());
   }

   class MyCupertinoApp extends StatelessWidget {
     const MyCupertinoApp({Key? key}) : super(key: key);

     @override
     Widget build(BuildContext context) {
       return CupertinoApp(
         home: CupertinoPageScaffold(
           navigationBar: const CupertinoNavigationBar(
             middle: Text('Cupertino App'),
           ),
           child: Center(
             child: CupertinoButton(
               child: const Text('Click Me'),
               onPressed: () {
                 print('Button Pressed');
               },
             ),
           ),
         ),
       );
     }
   }
   ```

---

### **Các widget phổ biến trong Cupertino**

#### 1. **CupertinoApp**
- Được dùng thay thế `MaterialApp` trong các ứng dụng iOS.
- Cung cấp cấu trúc chính, định nghĩa theme, và quản lý các route.
- Ví dụ:
  ```dart
  CupertinoApp(
    theme: const CupertinoThemeData(
      brightness: Brightness.light,
      primaryColor: CupertinoColors.activeBlue,
    ),
  );
  ```

#### 2. **CupertinoPageScaffold**
- Tạo cấu trúc trang đơn giản bao gồm thanh điều hướng (Navigation Bar) và phần thân (body).
- Ví dụ:
  ```dart
  CupertinoPageScaffold(
    navigationBar: const CupertinoNavigationBar(
      middle: Text('My Page'),
    ),
    child: Center(
      child: Text('Hello iOS'),
    ),
  );
  ```

#### 3. **CupertinoNavigationBar**
- Thanh điều hướng giống iOS.
- Hỗ trợ các thuộc tính như `middle`, `leading`, và `trailing`.
- Ví dụ:
  ```dart
  const CupertinoNavigationBar(
    middle: Text('Navigation Bar'),
    leading: Icon(CupertinoIcons.back),
    trailing: Icon(CupertinoIcons.search),
  );
  ```

#### 4. **CupertinoButton**
- Nút bấm có giao diện giống với iOS.
- Ví dụ:
  ```dart
  CupertinoButton(
    child: const Text('Press Me'),
    onPressed: () {
      print('Button Pressed');
    },
  );
  ```

#### 5. **CupertinoTextField**
- TextField có giao diện giống iOS.
- Ví dụ:
  ```dart
  CupertinoTextField(
    placeholder: 'Enter text',
    onChanged: (value) {
      print(value);
    },
  );
  ```

#### 6. **CupertinoActivityIndicator**
- Hiển thị vòng tròn tải giống iOS.
- Ví dụ:
  ```dart
  CupertinoActivityIndicator(
    radius: 15.0, // Đường kính vòng tròn
  );
  ```

#### 7. **CupertinoAlertDialog**
- Hiển thị hộp thoại cảnh báo với thiết kế iOS.
- Ví dụ:
  ```dart
  CupertinoAlertDialog(
    title: const Text('Alert'),
    content: const Text('This is an alert dialog.'),
    actions: [
      CupertinoDialogAction(
        child: const Text('Cancel'),
        onPressed: () {
          print('Cancel Pressed');
        },
      ),
      CupertinoDialogAction(
        child: const Text('OK'),
        onPressed: () {
          print('OK Pressed');
        },
      ),
    ],
  );
  ```

---

### **Các đặc điểm chính của Cupertino**

1. **Hỗ trợ trải nghiệm iOS:**
   - Widget Cupertino được thiết kế để hoạt động giống với giao diện chuẩn trên iOS.

2. **Tích hợp tốt với Material:**
   - Bạn có thể kết hợp `Cupertino` và `Material` widgets trong một ứng dụng nếu cần.
   - Ví dụ:
     ```dart
     CupertinoButton(
       child: const Icon(Icons.add), // Dùng biểu tượng của Material
       onPressed: () {},
     );
     ```

3. **Hiệu suất cao:**
   - Cupertino widget được tối ưu hóa để chạy mượt mà trên cả Android và iOS.

---

### **Lưu ý khi sử dụng Cupertino**
- Nên dùng `CupertinoApp` thay cho `MaterialApp` nếu bạn muốn thiết kế giao diện hoàn toàn theo phong cách iOS.
- Khi kết hợp `Cupertino` và `Material`, hãy cẩn thận để tránh mâu thuẫn về giao diện.
- Nếu cần tích hợp với các tính năng chỉ có trên iOS (như `CupertinoDatePicker`), hãy kiểm tra môi trường bằng `Platform.isIOS`.

---

Nếu bạn cần hỗ trợ thêm ví dụ cụ thể hoặc tính năng nào khác của Cupertino, hãy cho mình biết nhé! 😊
