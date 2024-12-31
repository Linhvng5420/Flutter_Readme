Trong Flutter, các thuộc tính **`mainAxisAlignment`** và **`crossAxisAlignment`** được sử dụng để định vị và sắp xếp các phần tử con trong một widget bố trí như **`Row`** và **`Column`**. 

Dưới đây là tất cả các giá trị mà hai thuộc tính này hỗ trợ:

---

### **`mainAxisAlignment`**
Thuộc tính này được dùng để sắp xếp các phần tử con dọc theo **trục chính (main axis)**.  
- Trong **`Row`**, trục chính là **ngang (horizontal)**.  
- Trong **`Column`**, trục chính là **dọc (vertical)**.

#### Các giá trị:
1. **`MainAxisAlignment.start`**
   - Sắp xếp các phần tử con ở đầu trục chính.
2. **`MainAxisAlignment.end`**
   - Sắp xếp các phần tử con ở cuối trục chính.
3. **`MainAxisAlignment.center`**
   - Sắp xếp các phần tử con ở giữa trục chính.
4. **`MainAxisAlignment.spaceBetween`**
   - Khoảng cách giữa các phần tử con được chia đều, không có khoảng cách ở đầu và cuối.
5. **`MainAxisAlignment.spaceAround`**
   - Khoảng cách giữa các phần tử con được chia đều, với khoảng cách ở đầu và cuối bằng **một nửa** khoảng cách giữa các phần tử.
6. **`MainAxisAlignment.spaceEvenly`**
   - Khoảng cách giữa các phần tử con và khoảng cách từ phần tử đầu/cuối đến mép đều nhau.

---

### **`crossAxisAlignment`**
Thuộc tính này được dùng để sắp xếp các phần tử con dọc theo **trục chéo (cross axis)**.  
- Trong **`Row`**, trục chéo là **dọc (vertical)**.  
- Trong **`Column`**, trục chéo là **ngang (horizontal)**.

#### Các giá trị:
1. **`CrossAxisAlignment.start`**
   - Căn các phần tử con về đầu trục chéo.
2. **`CrossAxisAlignment.end`**
   - Căn các phần tử con về cuối trục chéo.
3. **`CrossAxisAlignment.center`**
   - Căn các phần tử con ở giữa trục chéo.
4. **`CrossAxisAlignment.stretch`**
   - Kéo dãn các phần tử con để lấp đầy trục chéo.
5. **`CrossAxisAlignment.baseline`** (chỉ dùng cho `Row`)
   - Căn các phần tử con theo đường cơ sở (baseline) của văn bản. Phải đặt **`textBaseline`** để hoạt động.

---

### Ví dụ sử dụng:
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Text('A'),
    Text('B'),
    Text('C'),
  ],
)
```

Trong ví dụ trên:
- **`mainAxisAlignment.spaceBetween`**: Chia đều khoảng cách giữa các phần tử trên trục ngang.  
- **`crossAxisAlignment.center`**: Căn giữa các phần tử trên trục dọc.  

Hãy cho biết nếu bạn cần thêm ví dụ hoặc giải thích chi tiết hơn! 😊
