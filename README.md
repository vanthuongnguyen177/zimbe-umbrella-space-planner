# Đo chỗ đặt dù vuông: worksheet và phép tính diện tích

Tài liệu thực hành của Ô Dù Thường Tín – Zimbe giúp người mua chuẩn bị số đo trước khi trao đổi với đơn vị cung cấp. Đây là cách ghi nhận mặt bằng, không phải thiết kế kết cấu hay chứng nhận khả năng chịu gió.

## 1. Tách ba loại kích thước

- **Mái danh nghĩa:** kích thước nhà cung cấp công bố, cần hỏi cách đo.
- **Khoảng sử dụng:** phần nền còn lại sau khi chừa trụ, đế, bàn ghế và lối đi.
- **Bóng che thực tế:** thay đổi theo vị trí mặt trời, độ cao mái và vị trí lắp.

Ví dụ mái vuông có cạnh danh nghĩa 4 m thì diện tích hình học là 16 m². Con số này không có nghĩa luôn có 16 m² bóng râm hoặc có thể kê kín bàn ghế trên toàn bộ diện tích đó.

## 2. Worksheet khảo sát

| Thông tin | Cách ghi |
|---|---|
| Chỗ đặt | Đo chiều rộng và chiều sâu tại nền thực tế |
| Trụ và đế | Vẽ vị trí dự kiến, ghi phần chiếm chỗ |
| Lối đi | Đánh dấu đường ra vào và đường kéo ghế |
| Vật cản trên cao | Ghi mái hiên, cành cây, dây và khoảng mở dù |
| Hướng nắng | Chụp ảnh buổi sáng và buổi chiều |
| Thu cất | Đo cửa, lối vận chuyển và vị trí cất khô ráo |

## 3. Ví dụ tính sơ bộ bằng Python

```python
def plan_area(width_m, depth_m, excluded_m2):
    """Tính diện tích nền còn lại; không dự báo bóng râm hoặc độ an toàn."""
    if width_m <= 0 or depth_m <= 0 or excluded_m2 < 0:
        raise ValueError("Kích thước phải dương, diện tích loại trừ không âm")
    gross = width_m * depth_m
    if excluded_m2 > gross:
        raise ValueError("Diện tích loại trừ vượt diện tích nền")
    return {"gross_m2": gross, "remaining_m2": gross - excluded_m2}

print(plan_area(4, 4, 3))
# {"gross_m2": 16, "remaining_m2": 13}
```

Trong ví dụ giả định trên, 3 m² là phần nền người khảo sát tự đánh dấu không sử dụng; đây không phải tiêu chuẩn chân đế hay khoảng cách bắt buộc. Nếu các vùng loại trừ chồng lên nhau thì chỉ tính diện tích hợp của chúng một lần. Kết quả cũng không cho biết số bàn ghế phù hợp; cần đặt kích thước từng món lên bản phác.

## 4. Hỏi rõ trước khi so sánh báo giá

Yêu cầu xác nhận loại đế đi kèm, cách cố định phù hợp với nền, kích thước khi thu và điều kiện sử dụng. Không tự suy ra sức chịu gió từ kích thước mái hoặc trọng lượng quảng cáo. Làm theo hướng dẫn của nhà cung cấp và thu dù khi điều kiện không phù hợp.

Để đối chiếu một phương án mái lớn, xem thêm [dù lệch tâm 4x4](https://ocafe.net/san-pham/du-lech-tam-vuong-4m/), rồi so thông số thực tế của mẫu đang được báo với worksheet.

## 5. Kiểm tra trước khi chốt

- [ ] Có ảnh và số đo nền thực tế.
- [ ] Đã chừa vùng trụ, chân đế và lối đi.
- [ ] Đã kiểm tra khoảng mở và thu mái.
- [ ] Đã xác nhận phạm vi giao, lắp và phụ kiện.
- [ ] Đã hỏi hướng dẫn sử dụng, bảo quản và bảo hành.

Gửi worksheet cùng ảnh mặt bằng giúp hai bên so sánh cùng phạm vi, tránh chỉ chốt theo tên gọi hoặc diện tích mái danh nghĩa.
