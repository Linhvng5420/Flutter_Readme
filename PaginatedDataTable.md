# 1. Giới Thiệu PaginatedDataTable
`PaginatedDataTable` là một widget trong Flutter, được thiết kế để hiển thị dữ liệu dưới dạng bảng có thể phân trang. Nó đặc biệt hữu ích khi bạn cần hiển thị một tập dữ liệu lớn mà không muốn làm lộn xộn giao diện người dùng. Dưới đây là các chi tiết quan trọng về `PaginatedDataTable`:
## **Cấu trúc cơ bản**
`PaginatedDataTable` hoạt động cùng với một lớp dữ liệu gọi là `DataTableSource`. Lớp này chịu trách nhiệm cung cấp dữ liệu cho bảng.

## **Các thuộc tính chính**
1. **`header`**  
   Dùng để hiển thị tiêu đề hoặc một đoạn mô tả trên đầu bảng.
   ```dart
   header: Text('Danh sách người dùng'),
   ```

2. **`columns`**  
   Danh sách các cột của bảng, được định nghĩa bằng `DataColumn`.
   ```dart
   columns: [
     DataColumn(label: Text('Tên')),
     DataColumn(label: Text('Tuổi')),
     DataColumn(label: Text('Email')),
   ],
   ```

3. **`source`**  
   Đối tượng của lớp `DataTableSource`, chịu trách nhiệm cung cấp dữ liệu và xử lý các hành động như phân trang.

4. **`rowsPerPage`**  
   Số lượng hàng hiển thị trên mỗi trang. Có thể điều chỉnh để phù hợp với ứng dụng của bạn.

5. **`onRowsPerPageChanged`**  
   Hàm callback được gọi khi người dùng thay đổi số lượng hàng hiển thị trên mỗi trang.

6. **`actions`**  
   Danh sách các widget (như nút hoặc menu) được hiển thị ở góc phải phía trên bảng.

## **Tạo một ví dụ cơ bản**
Dưới đây là ví dụ đơn giản về cách sử dụng `PaginatedDataTable`:

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('PaginatedDataTable Example')),
        body: PaginatedDataTableExample(),
      ),
    );
  }
}

class PaginatedDataTableExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return SingleChildScrollView(
      child: PaginatedDataTable(
        header: Text('Danh sách sản phẩm'),
        columns: [
          DataColumn(label: Text('Tên')),
          DataColumn(label: Text('Số lượng')),
          DataColumn(label: Text('Giá')),
        ],
        source: ProductDataSource(),
        rowsPerPage: 5,
      ),
    );
  }
}

class ProductDataSource extends DataTableSource {
  final List<Map<String, dynamic>> _products = [
    {'name': 'Sản phẩm 1', 'quantity': 10, 'price': 1000},
    {'name': 'Sản phẩm 2', 'quantity': 20, 'price': 2000},
    {'name': 'Sản phẩm 3', 'quantity': 30, 'price': 3000},
    {'name': 'Sản phẩm 4', 'quantity': 40, 'price': 4000},
    {'name': 'Sản phẩm 5', 'quantity': 50, 'price': 5000},
    {'name': 'Sản phẩm 6', 'quantity': 60, 'price': 6000},
  ];

  @override
  DataRow getRow(int index) {
    final product = _products[index];
    return DataRow(cells: [
      DataCell(Text(product['name'])),
      DataCell(Text(product['quantity'].toString())),
      DataCell(Text(product['price'].toString())),
    ]);
  }

  @override
  bool get isRowCountApproximate => false;

  @override
  int get rowCount => _products.length;

  @override
  int get selectedRowCount => 0;
}
```

## **Mô tả hoạt động**
1. **Lớp `ProductDataSource`**  
   Cung cấp dữ liệu cho bảng và định nghĩa cách dữ liệu được hiển thị trong từng hàng.

2. **Các thuộc tính của `DataTableSource`**  
   - `getRow`: Tạo một hàng với dữ liệu tại chỉ số `index`.
   - `rowCount`: Tổng số hàng dữ liệu.
   - `isRowCountApproximate`: Xác định liệu số hàng có chính xác không.
   - `selectedRowCount`: Số hàng đang được chọn.

## **Tính năng nâng cao**
- **Sắp xếp cột**: Có thể sắp xếp dữ liệu trong cột bằng cách thiết lập thuộc tính `onSort` trong `DataColumn`.
- **Tùy chỉnh hàng**: Bạn có thể thêm các nút hoặc hình ảnh vào từng hàng bằng `DataCell`.

---

# 2. Tất cả thuộc tính
Dưới đây là bảng tóm tắt các thuộc tính của `PaginatedDataTable` và các thành phần liên quan:

---

### **Thuộc tính của `PaginatedDataTable`**
| **Thuộc tính**            | **Ý nghĩa**                                                                                      |
|----------------------------|--------------------------------------------------------------------------------------------------|
| `header`                  | Tiêu đề hoặc mô tả xuất hiện trên bảng.                                                          |
| `actions`                 | Danh sách các widget (ví dụ: nút) hiển thị ở góc phải trên bảng.                                |
| `columns`                 | Danh sách các cột được định nghĩa bằng `DataColumn`.                                            |
| `source`                  | Đối tượng `DataTableSource` cung cấp dữ liệu cho bảng.                                           |
| `rowsPerPage`             | Số lượng hàng hiển thị trên mỗi trang.                                                          |
| `onRowsPerPageChanged`    | Hàm callback khi người dùng thay đổi số hàng trên mỗi trang.                                    |
| `availableRowsPerPage`    | Danh sách các giá trị số hàng có thể chọn hiển thị trên mỗi trang.                              |
| `sortColumnIndex`         | Chỉ số của cột đang được sắp xếp.                                                               |
| `sortAscending`           | Xác định hướng sắp xếp là tăng (`true`) hoặc giảm (`false`).                                    |
| `showCheckboxColumn`      | Hiển thị cột checkbox để chọn hàng nếu `true`.                                                  |
| `showFirstLastButtons`    | Hiển thị các nút "Trang đầu" và "Trang cuối" nếu `true`.                                        |

---

### **Thuộc tính của `DataColumn`**
| **Thuộc tính**     | **Ý nghĩa**                                                                                      |
|---------------------|--------------------------------------------------------------------------------------------------|
| `label`            | Widget hiển thị tên cột.                                                                         |
| `tooltip`          | Văn bản hiển thị khi giữ hoặc di chuột vào tiêu đề cột.                                           |
| `numeric`          | Đặt `true` nếu cột hiển thị giá trị số.                                                          |
| `onSort`           | Hàm callback được gọi khi người dùng nhấn vào tiêu đề cột để sắp xếp.                            |

---

### **Phương thức và thuộc tính của `DataTableSource`**
| **Phương thức/Thuộc tính**  | **Ý nghĩa**                                                                                      |
|-----------------------------|--------------------------------------------------------------------------------------------------|
| `getRow(int index)`         | Trả về một hàng (`DataRow`) tại chỉ số được chỉ định.                                            |
| `rowCount`                  | Tổng số hàng dữ liệu.                                                                           |
| `isRowCountApproximate`     | Xác định xem số hàng có phải là ước tính (`true`) hay không (`false`).                          |
| `selectedRowCount`          | Số lượng hàng đang được chọn.                                                                  |

---

### **Thuộc tính của `DataRow`**
| **Thuộc tính**     | **Ý nghĩa**                                                                                      |
|---------------------|--------------------------------------------------------------------------------------------------|
| `cells`            | Danh sách các ô (`DataCell`) trong hàng.                                                         |
| `selected`         | Xác định xem hàng có đang được chọn không.                                                       |
| `onSelectChanged`  | Hàm callback được gọi khi trạng thái chọn của hàng thay đổi.                                     |

---

### **Thuộc tính của `DataCell`**
| **Thuộc tính**     | **Ý nghĩa**                                                                                      |
|---------------------|--------------------------------------------------------------------------------------------------|
| `child`            | Widget hiển thị nội dung trong ô.                                                                |
| `onTap`            | Hàm callback được gọi khi người dùng nhấn vào ô.                                                 |
| `placeholder`      | Đặt `true` nếu ô đang trong trạng thái chờ dữ liệu.                                              |
| `showEditIcon`     | Hiển thị biểu tượng chỉnh sửa trong ô nếu `true`.                                                |

---

### **Sử dụng chính**
- **Hiển thị dữ liệu lớn**: `PaginatedDataTable` chia dữ liệu thành nhiều trang để dễ quản lý.
- **Tùy chỉnh hiển thị**: Dễ dàng tùy chỉnh số hàng, cột, và các hành động liên quan.
- **Hỗ trợ sắp xếp**: Sắp xếp dữ liệu theo cột với thuộc tính `onSort`.

# 3. Sử dụng ```LayoutBuilder```: Tự động điều chỉnh kích thước.
Table tự động điều chỉnh kích thước phù hợp với màn hình trước khi build.
