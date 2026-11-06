# MY EARN — Website triển khai GitHub Pages

## Cấu trúc
- `index.html`: trang chủ hợp nhất, điều hướng đến hai khu vực.
- `member.html`: trang thành viên.
- `admin.html`: trung tâm quản trị (yêu cầu Firebase custom claim `admin: true`).

## Đưa website lên GitHub Pages
1. Tạo một repository GitHub mới, ví dụ `my-earn`.
2. Tải lên **toàn bộ 3 tệp HTML** này và tệp `README.md` ở thư mục gốc repository.
3. Mở **Settings → Pages**.
4. Trong **Build and deployment**, chọn **Deploy from a branch**.
5. Chọn nhánh `main`, thư mục `/ (root)`, rồi nhấn **Save**.
6. Chờ GitHub triển khai. Địa chỉ thường có dạng `https://TEN-GITHUB.github.io/my-earn/`.

## Cấu hình Firebase bắt buộc
- Trong Firebase Authentication, thêm domain GitHub Pages vào danh sách Authorized domains.
- Bật phương thức đăng nhập đang được website sử dụng và bật Firestore.
- Cấp quyền quản trị bằng Firebase Admin SDK ở môi trường máy chủ đáng tin cậy; không tự đặt `admin: true` từ trình duyệt.
- Thiết lập Firestore Security Rules chặt chẽ cho từng collection.
- Kiểm tra lại cấu hình Firebase trong `member.html` và `admin.html`, chỉ dùng dự án bạn sở hữu hoặc được phép quản lý.

## Tùy chỉnh thương hiệu
Tên hiển thị hiện được đổi tạm thành **MY EARN**. Có thể tìm và thay `MY EARN` trong ba tệp HTML bằng tên thương hiệu chính thức sau này. Không đổi tên collection, trường dữ liệu hoặc hàm Firebase nếu chưa rà soát tương thích.

## Giới hạn và an toàn
GitHub Pages chỉ lưu trữ website tĩnh, không chạy máy chủ riêng. Các thao tác số dư, phần thưởng, mã quà tặng và thanh toán phải được xác minh và thực hiện ở Cloud Functions/server API; không tin dữ liệu do trình duyệt gửi lên. Giao diện không phải bằng chứng rằng hệ thống đã kết nối hoặc giao dịch an toàn. Kiểm thử trên dữ liệu giả trước khi sử dụng thực tế.
