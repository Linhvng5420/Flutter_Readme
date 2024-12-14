**`mobx_codegen`** là một thư viện **code generator** dành cho **MobX** trong Flutter/Dart. Nó được sử dụng để tự động tạo ra các phần code boilerplate khi bạn sử dụng **MobX** để quản lý trạng thái trong ứng dụng Flutter. 

---

### **Công dụng của `mobx_codegen`**
1. **Tự động sinh mã boilerplate**:  
   - Khi bạn sử dụng các decorator như `@observable`, `@action`, và `@computed`, thư viện này sẽ tạo ra các getter, setter, và các phương thức cần thiết phía sau.

2. **Tiết kiệm thời gian**:  
   - Thay vì viết thủ công, bạn chỉ cần định nghĩa trạng thái hoặc logic, phần còn lại sẽ do **`mobx_codegen`** đảm nhận.

3. **Dễ dàng quản lý và mở rộng**:  
   - Tự động sinh mã đảm bảo bạn không cần lo lắng về lỗi liên quan đến code lặp lại hoặc thiếu sót.

---

### **Cách sử dụng `mobx_codegen`**

1. **Thêm thư viện vào `pubspec.yaml`**:
   ```yaml
   dependencies:
     mobx: ^2.1.3+1
     flutter_mobx: ^2.0.6+5

   dev_dependencies:
     mobx_codegen: ^2.0.6
     build_runner: ^2.4.6
   ```

2. **Đánh dấu các thuộc tính với decorator MobX**:
   Sử dụng các annotation như `@observable`, `@action`, hoặc `@computed` trong lớp store:
   ```dart
   import 'package:mobx/mobx.dart';

   part 'counter.g.dart';

   class Counter = _Counter with _$Counter;

   abstract class _Counter with Store {
     @observable
     int count = 0;

     @action
     void increment() {
       count++;
     }
   }
   ```

3. **Chạy `build_runner` để sinh mã**:
   Chạy lệnh sau trong terminal:
   ```bash
   flutter pub run build_runner build
   ```
   Hoặc nếu muốn chạy liên tục khi có thay đổi:
   ```bash
   flutter pub run build_runner watch
   ```

   Sau khi chạy, tệp `counter.g.dart` sẽ được tạo tự động.

4. **Sử dụng store trong ứng dụng Flutter**:
   ```dart
   final counter = Counter();

   Observer(
     builder: (_) => Text('${counter.count}'),
   );

   ElevatedButton(
     onPressed: counter.increment,
     child: Text('Increment'),
   );
   ```

---

### **Lưu ý khi sử dụng `mobx_codegen`**
- Phải luôn đảm bảo bạn chạy lệnh **`build_runner`** sau khi chỉnh sửa các lớp `Store`.
- Tệp `*.g.dart` được tạo tự động, không nên chỉnh sửa thủ công.
- Cần khai báo `part 'filename.g.dart';` trong tệp chính của store.


