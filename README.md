# Bougie frontend

Website marketing frontend-only cho Bougie. Không cần cài package hay backend. Có sẵn GitHub Actions workflow để triển khai GitHub Pages khi push lên nhánh `main` hoặc `master`.

## Chạy tại máy

Mở `index.html` trong trình duyệt, hoặc chạy một static server từ thư mục này:

```powershell
py -m http.server 8000
```

Sau đó mở `http://localhost:8000`. Các section có thể mở trực tiếp qua `/#collection`, `/#seasonal`, `/#customize`, `/#workshop`, `/#story` và `/#contact`. Chi tiết sản phẩm dùng query URL (`?product=vanilla-chivas#collection`) để tương thích với GitHub Pages ở cả project site lẫn user site.

## Đưa website lên GitHub Pages

1. Đưa thư mục này lên repository GitHub của bạn, trên nhánh `main` hoặc `master`.
2. Trong repository, mở **Settings → Pages** và đặt **Source** thành **GitHub Actions**.
3. Mỗi lần push lên `main` hoặc `master`, workflow `.github/workflows/pages.yml` sẽ tự triển khai website. Có thể chạy thủ công từ tab **Actions**.

Workflow chỉ đưa các tệp website và ảnh cần dùng trong `img/originals/` lên Pages; các tài liệu nguồn và ảnh tài chính không được đóng gói.

## Nội dung và ảnh

- Ảnh gốc độ phân giải cao lấy từ file Word nằm trong `img/originals/` và được dùng cho Mood Collection, Seasonal, Customization, Workshop và Our Story.
- Nút `VIEW IMAGE` mở ảnh tham khảo ở kích thước lớn để xem rõ chữ và chi tiết.
- Ảnh tham khảo Seasonal được ghi là concept; giá Mood Collection hiển thị theo khoảng 520.000–550.000đ.
- Nút liên hệ sao chép nội dung hỏi để người dùng tự gửi qua kênh của họ. Chưa có liên kết chính thức nào được cung cấp.
- Các ảnh tài chính và ảnh chụp trang mạng xã hội trong thư mục `img` không được dùng làm nội dung website.
- Chữ hiển thị đang ưu tiên tiếng Anh theo đặc tả. Google Fonts có font dự phòng nếu không có kết nối mạng.
