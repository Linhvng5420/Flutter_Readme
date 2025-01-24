# Hướng dẫn sử dụng BoxFit trong Flutter

`BoxFit` là một enum trong Flutter giúp định nghĩa cách thức hiển thị một widget con bên trong một widget cha. Dưới đây là các giá trị của `BoxFit` và cách chúng hoạt động:

- `BoxFit.fill`: Kéo giãn hình ảnh hoặc widget để lấp đầy toàn bộ không gian của widget cha mà không giữ tỉ lệ ban đầu.
- `BoxFit.contain`: Co giãn hình ảnh hoặc widget để vừa vặn trong widget cha và giữ nguyên tỉ lệ ban đầu. Có thể để lại khoảng trống nếu tỉ lệ không khớp.
- `BoxFit.cover`: Kéo giãn hình ảnh hoặc widget để bao phủ toàn bộ không gian của widget cha và giữ nguyên tỉ lệ ban đầu. Phần hình ảnh hoặc widget nằm ngoài khung sẽ bị cắt bỏ.
- `BoxFit.fitWidth`: Co giãn hình ảnh hoặc widget để vừa vặn theo chiều rộng của widget cha và giữ nguyên tỉ lệ ban đầu. Có thể để lại khoảng trống theo chiều cao nếu tỉ lệ không khớp.
- `BoxFit.fitHeight`: Co giãn hình ảnh hoặc widget để vừa vặn theo chiều cao của widget cha và giữ nguyên tỉ lệ ban đầu. Có thể để lại khoảng trống theo chiều rộng nếu tỉ lệ không khớp.
- `BoxFit.none`: Hiển thị hình ảnh hoặc widget theo kích thước gốc của nó. Nếu kích thước lớn hơn widget cha, phần vượt quá sẽ bị cắt bỏ.
- `BoxFit.scaleDown`: Giống như `contain`, nhưng chỉ co giãn hình ảnh hoặc widget nếu nó lớn hơn kích thước của widget cha.

## Ví dụ sử dụng

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('BoxFit Example'),
        ),
        body: Center(
          child: Container(
            width: 200,
            height: 200,
            color: Colors.blue,
            child: FittedBox(
              fit: BoxFit.cover,
              child: Image.network('https://flutter.dev/assets/homepage/carousel/slide_1-layer_0-2d11187e4b34ef196a8e4d9e5ce8b5f4d47d8f9f8d3c1c1e6f0e3f3d1c4a9c61.png'),
            ),
          ),
        ),
      ),
    );
  }
}
