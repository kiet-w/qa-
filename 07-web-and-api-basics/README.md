# 07 — Web & API Fundamentals: Kiến Thức Web & API cho QA

## Mục tiêu
Nắm vững cơ chế Web (SSR vs CSR, Hydration, Caching), HTTP Methods, Status Codes, và danh sách kiểm tra (Checklist) khi test API.

---

## 1. Web Architecture: SSR vs CSR & Caching

- **SSR (Server-Side Rendering - Next.js):** HTML được render từ server. QA cần chú ý lỗi **Hydration Mismatch** (HTML server trả về khác với client render).
- **CSR (Client-Side Rendering - React):** HTML rỗng, JS render UI. QA cần chú ý các trạng thái **Loading/Skeleton** và các lỗi async timing.
- **Cache Bugs:** Dữ liệu đã update trong DB nhưng UI vẫn hiển thị cũ do Browser/CDN Cache. (Test bằng Incognito / Hard Refresh Ctrl+Shift+R).

---

## 2. HTTP Methods & Status Codes

### HTTP Methods
- `GET`: Lấy dữ liệu (Safe, Idempotent).
- `POST`: Tạo mới dữ liệu.
- `PUT`: Cập nhật toàn bộ object.
- `PATCH`: Cập nhật 1 phần object.
- `DELETE`: Xóa dữ liệu.

### Status Codes chuẩn QA
- `200 OK` / `201 Created` / `204 No Content` ➔ Success.
- `400 Bad Request` ➔ Input invalid / Thiếu field.
- `401 Unauthorized` ➔ Chưa đăng nhập / Token hết hạn.
- `403 Forbidden` ➔ Đã đăng nhập nhưng không có quyền.
- `404 Not Found` ➔ Resource không tồn tại.
- `422 Unprocessable Entity` ➔ Validation fail.
- `429 Too Many Requests` ➔ Quá tải rate limit.
- `500 Internal Server Error` ➔ Server crash / Unhandled exception (**Luôn là Bug**).

---

## 3. API Testing Checklist (Postman / cURL)

- [ ] Verify Response Status Code khớp với scenario (Happy path & Error path).
- [ ] Verify JSON Response Schema (đúng kiểu dữ liệu string, number, boolean, array).
- [ ] Verify Authentication & Authorization (Thử bỏ Token ➔ Phải nhận 401).
- [ ] Verify Validation error messages (Báo rõ ràng field nào bị lỗi).
- [ ] Verify Response Time (< 200ms cho API thường).
