### **So sánh MVVM và MVC**

| **Tiêu chí**          | **MVC (Model-View-Controller)**                                    | **MVVM (Model-View-ViewModel)**                             |
|-----------------------|--------------------------------------------------------------------|------------------------------------------------------------|
| **Cấu trúc**          | - Bao gồm 3 thành phần chính: `Model`, `View`, `Controller`.      | - Bao gồm 3 thành phần chính: `Model`, `View`, `ViewModel`. |
| **Nhiệm vụ**          | - `Controller`: Điều phối giữa `Model` và `View`. Xử lý logic ứng dụng. <br> - `View`: Chỉ hiển thị giao diện người dùng. <br> - `Model`: Lưu trữ và quản lý dữ liệu. | - `ViewModel`: Xử lý logic giao diện và cung cấp dữ liệu cho `View`. <br> - `View`: Chỉ hiển thị giao diện. <br> - `Model`: Lưu trữ và quản lý dữ liệu. |
| **Mối quan hệ giữa các thành phần** | - `View` phụ thuộc vào `Controller`. <br> - `Controller` giao tiếp trực tiếp với `Model` và `View`. | - `View` liên kết với `ViewModel` thông qua cơ chế **data binding**. <br> - `ViewModel` giao tiếp với `Model`. |
| **Sự phụ thuộc**      | - `View` và `Controller` thường bị ràng buộc chặt chẽ (tight coupling). | - `View` và `ViewModel` được tách biệt rõ ràng (loose coupling). |
| **Data Binding**      | Không hỗ trợ data binding trực tiếp. Dữ liệu phải được chuyển thủ công qua `Controller`. | Hỗ trợ **data binding** (thường tự động đồng bộ dữ liệu giữa `View` và `ViewModel`). |
| **Độ phức tạp**       | Thích hợp cho các ứng dụng nhỏ hoặc đơn giản.                     | Tốt hơn cho các ứng dụng lớn hoặc phức tạp.                 |
| **Testability**       | Khó kiểm thử `View` và `Controller` do sự phụ thuộc chặt chẽ.      | `ViewModel` dễ kiểm thử vì độc lập với `View`.              |
| **Framework phổ biến**| - ASP.NET MVC, Ruby on Rails, Laravel, iOS UIKit.                 | - Flutter, WPF (Windows Presentation Foundation), Angular. |

---

### **Phân tích chi tiết**

#### **MVC (Model-View-Controller):**
- **Model**: 
  - Quản lý trạng thái và dữ liệu của ứng dụng.
  - Không biết gì về `View` hoặc `Controller`.
- **View**: 
  - Hiển thị dữ liệu từ `Model`.
  - Không chứa logic phức tạp, phụ thuộc vào `Controller`.
- **Controller**: 
  - Nhận yêu cầu từ `View` và điều phối công việc giữa `Model` và `View`.

**Nhược điểm**:
1. `Controller` có thể trở nên quá tải (God Object) khi ứng dụng lớn.
2. Tách biệt không hoàn toàn giữa `View` và `Controller`.

---

#### **MVVM (Model-View-ViewModel):**
- **Model**:
  - Tương tự trong MVC: Quản lý dữ liệu và trạng thái.
- **View**:
  - Hiển thị dữ liệu từ `ViewModel`.
  - Kết nối với `ViewModel` qua **data binding** (khi dữ liệu thay đổi, giao diện sẽ tự động cập nhật).
- **ViewModel**:
  - Trung gian giữa `Model` và `View`.
  - Chứa logic giao diện, biến đổi dữ liệu từ `Model` để phù hợp với `View`.

**Ưu điểm**:
1. Dễ kiểm thử vì `ViewModel` tách biệt hoàn toàn với giao diện.
2. Data binding giúp giảm code xử lý thủ công.

**Nhược điểm**:
1. Cần học và thiết lập data binding (có thể phức tạp hơn).
2. Có thể tăng độ phức tạp trong ứng dụng nhỏ.

---

### **Khi nào sử dụng?**
- **MVC**:
  - Ứng dụng nhỏ hoặc khi không cần phức tạp.
  - Dễ dàng hiểu và triển khai nhanh.
- **MVVM**:
  - Ứng dụng lớn, giao diện phức tạp, nhiều trạng thái cần cập nhật.
  - Khi cần tách biệt hoàn toàn giữa logic giao diện và giao diện.
