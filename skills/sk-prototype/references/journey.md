# User Journey & Workflow — hướng dẫn khai thác

Đây là phần TRỌNG TÂM của prototype. Không hiểu journey → prototype rời rạc.

## Cách hỏi

- **User journey:** người dùng đi qua những bước nào từ lúc vào đến lúc đạt mục tiêu?
  (dùng `textarea`). VD: "Đăng ký → onboarding → tạo dự án → mời thành viên → xem báo cáo".
- **Workflow / tác vụ chính:** các việc người dùng cần hoàn thành trong sản phẩm?
  VD: "Tạo hoá đơn, theo dõi thanh toán, xuất báo cáo".

## Nếu user không rõ → CHỦ ĐỘNG đề xuất journey mẫu theo loại hệ thống

| Loại hệ thống | Journey mẫu đề xuất |
|---|---|
| **SaaS dashboard** | Landing → Signup → Onboarding → Dashboard → Tạo/quản lý item → Settings |
| **Thương mại điện tử** | Home → Danh mục → Chi tiết sản phẩm → Giỏ hàng → Checkout → Xác nhận |
| **Booking / dịch vụ** | Landing → Chọn dịch vụ → Chọn lịch → Nhập thông tin → Thanh toán → Xác nhận |
| **Admin / nội bộ** | Login → Dashboard tổng → Danh sách bản ghi → Chi tiết/sửa → Báo cáo |
| **Marketplace** | Home → Tìm kiếm → Kết quả → Chi tiết → Liên hệ/đặt → Quản lý đơn |

→ Đề xuất → **xin xác nhận** trước khi dựng. Điều chỉnh theo phản hồi user.

## Nguyên tắc chuyển journey → trang

- Mỗi **bước journey** = ít nhất 1 trang bấm được.
- Các trang liên kết đúng thứ tự luồng (nút "Tiếp tục" / breadcrumb / nav).
- Tác vụ lặp (CRUD) → gộp thành pattern chung (list → detail → form).
- Ưu tiên đường "happy path" trước; thêm empty/error state ở mức Standard+.
