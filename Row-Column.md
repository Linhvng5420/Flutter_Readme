## **1 - AxisAlignment**
**So sánh `mainAxisAlignment` và `crossAxisAlignment`**

| Thuộc tính           | **`mainAxisAlignment`**                        | **`crossAxisAlignment`**                  |
|----------------------|-----------------------------------------------|------------------------------------------|
| **Ý nghĩa**          | Định vị các widget con dọc theo **trục chính** (main axis) của `Row` hoặc `Column`. | Định vị các widget con dọc theo **trục chéo** (cross axis) của `Row` hoặc `Column`. |
| **Trục áp dụng**     | Trục chính: <br>- Với `Row`: theo chiều ngang.<br> - Với `Column`: theo chiều dọc. | Trục chéo: <br>- Với `Row`: theo chiều dọc. <br>- Với `Column`: theo chiều ngang. |
| **Ảnh hưởng đến UI** | Điều chỉnh cách phân bổ **khoảng cách** hoặc căn chỉnh các widget con trên trục chính. | Điều chỉnh **căn chỉnh** vị trí của các widget con trên trục chéo. |
| **Thường dùng khi**  | Cần phân bố đều, căn giữa hoặc điều chỉnh khoảng cách giữa các widget con trên trục chính. | Cần căn chỉnh vị trí các widget con (trái, phải, giữa, kéo dài). |

**Các giá trị (thuộc tính) của `mainAxisAlignment`**
`mainAxisAlignment` (trục chính) có các giá trị sau:

1. **`MainAxisAlignment.start`**  
   - Đẩy các widget con về **đầu** trục chính.
   - Mặc định của `Column`.

2. **`MainAxisAlignment.end`**  
   - Đẩy các widget con về **cuối** trục chính.

3. **`MainAxisAlignment.center`**  
   - Căn giữa các widget con trên trục chính.

4. **`MainAxisAlignment.spaceBetween`**  
   - Phân bố khoảng cách giữa các widget con sao cho **khoảng cách đầu và cuối là 0**.

5. **`MainAxisAlignment.spaceAround`**  
   - Phân bố khoảng cách giữa các widget con với khoảng cách ở đầu và cuối **bằng một nửa** khoảng cách giữa hai widget.

6. **`MainAxisAlignment.spaceEvenly`**  
   - Phân bố khoảng cách giữa các widget con **đều nhau**, bao gồm cả khoảng cách ở đầu và cuối.

**Các giá trị (thuộc tính) của `crossAxisAlignment`**
`crossAxisAlignment` (trục chéo) có các giá trị sau:

1. **`CrossAxisAlignment.start`**  
   - Căn các widget con về **đầu** trục chéo.

2. **`CrossAxisAlignment.end`**  
   - Căn các widget con về **cuối** trục chéo.

3. **`CrossAxisAlignment.center`**  
   - Căn các widget con theo **trung tâm** trục chéo.

4. **`CrossAxisAlignment.stretch`**  
   - Kéo dài các widget con để **lấp đầy trục chéo** (nếu kích thước con có thể thay đổi).

5. **`CrossAxisAlignment.baseline`** *(Chỉ dành cho `Row`)*  
   - Căn chỉnh các widget con dựa trên đường **baseline** của văn bản (nếu có).  

   **Lưu ý**: Để dùng giá trị này, cần đặt `textBaseline` (ví dụ: `TextBaseline.alphabetic`).

**Ví dụ minh họa**
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  crossAxisAlignment: CrossAxisAlignment.start,
  children: [
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
),
```

- `mainAxisAlignment.spaceEvenly`: Các `Text` sẽ phân bố đều trên trục ngang.  
- `crossAxisAlignment.start`: Các `Text` được căn về phía trên (đầu trục dọc).

## **2 - **
