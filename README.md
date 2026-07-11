# Sample Tracker — Cat Dang Handicraft

Công cụ theo dõi mẫu phát triển (development sample tracker), dùng chung cho sales team, nhiều brand, nhiều thành viên. Dữ liệu đồng bộ real-time giữa mọi người dùng.

## Kiến trúc

- **Frontend**: `index.html` — một file tĩnh duy nhất (HTML + CSS + JS gộp chung), host miễn phí trên GitHub Pages.
- **Backend/dữ liệu**: [Firebase Firestore](https://console.firebase.google.com/project/catdang-sample-tracker) — database thật, cập nhật real-time cho tất cả người dùng đang mở trang.
- **Đăng nhập**: Firebase Authentication (Email/Password), dùng chung 1 tài khoản cho cả team, passcode do bạn tự đặt là "mật khẩu" của tài khoản đó.

## Truy cập

Mở trang GitHub Pages (link sẽ được cung cấp sau khi bật Pages), nhập:
1. **Passcode chung** của team.
2. **Tên của bạn** — dùng để hiển thị trong lịch sử cập nhật của từng mẫu, không phải mật khẩu.

Sau lần đầu đăng nhập thành công, trình duyệt sẽ nhớ phiên đăng nhập (không cần nhập lại passcode mỗi lần mở, trừ khi xoá dữ liệu trình duyệt).

## Quản lý dữ liệu / Firebase

- Firebase project: `catdang-sample-tracker`
- Firestore collection chứa toàn bộ mẫu: `samples`
- Đổi passcode: vào Firebase Console → Authentication → Users → chọn user `team@catdang-sample-tracker.app` → Reset password.
- Xem/sửa dữ liệu thô: Firebase Console → Firestore Database → collection `samples`.

## Giới hạn hiện tại (biết trước để tránh bất ngờ)

- **Ảnh mẫu**: được nén và lưu trực tiếp trong Firestore document dạng base64 (không dùng Firebase Storage riêng). Đủ dùng cho quy mô hiện tại; nếu sau này nhiều ảnh/mẫu hơn, nên chuyển sang Firebase Storage.
- **Phân quyền**: tất cả người đăng nhập bằng passcode chung đều có quyền thêm/sửa/xoá mọi mẫu — chưa phân quyền theo brand hoặc theo người phụ trách.
- **Gói Firebase**: đang dùng gói miễn phí (Spark) — đủ dùng cho quy mô nội bộ team, không phát sinh chi phí trừ khi lưu lượng tăng rất lớn.

## Phát triển thêm

Toàn bộ code nằm trong `index.html`, không cần build tool/npm install để chỉnh sửa — mở file, sửa trực tiếp, commit lên GitHub là Pages tự cập nhật.
