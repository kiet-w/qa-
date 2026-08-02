# 04 — Manual Testing Workflow: Quy Trình Manual Test

## Mục tiêu
Thành thạo kỹ năng viết Test Plan, viết Test Case chuẩn atomic, viết Bug Report chuyên nghiệp mà Developer đọc xong có thể reproduce được ngay, và xây dựng Requirement Traceability Matrix (RTM).

---

## 📊 Sơ đồ trực quan (Diagrams & Lifecycles)

### Quy trình Manual Test Cycle
![Quy trình Manual Test Cycle](diagrams/manual-test-cycle.svg)

### Vòng đời Defect trong Quy trình Test
![Vòng đời Defect trong Quy trình Test](diagrams/defect-lifecycle.svg)

### Requirement Traceability Matrix (RTM)
![Requirement Traceability Matrix (RTM)](diagrams/rtm-matrix.svg)



## 1. Cấu trúc Test Case chuẩn

| Field | Description | Example |
|---|---|---|
| **Test Case ID** | Mã định danh duy nhất | `TC_AUTH_001` |
| **Title** | Tên mô tả ngắn gọn action & expected | Verify login with valid email and password |
| **Precondition** | Điều kiện cần có trước khi test | User account `user@test.com` exists and is active |
| **Test Data** | Dữ liệu cụ thể dùng để test | Email: `user@test.com`, Password: `Password123!` |
| **Steps** | Các bước chi tiết (Atomic & Clear) | 1. Open `/login`<br>2. Enter Email & Password<br>3. Click "Login" |
| **Expected Result** | Kết quả kỳ vọng chuẩn xác | Redirect to `/dashboard`, toast "Welcome back" appears |
| **Priority** | High / Medium / Low | High |

---

## 2. Quy chuẩn viết Bug Report chuyên nghiệp

Một Bug Report tốt giúp dev sửa lỗi nhanh chóng mà không cần hỏi lại.

```markdown
### [Auth] Error 500 khi đăng nhập bằng Google OAuth với email có dấu '+'

**Environment:** Chrome 126 / macOS 15.2 / Staging
**Severity:** Major | **Priority:** High

**Precondition:** Tài khoản Google có email format `user+test@gmail.com`

**Steps to Reproduce:**
1. Mở trang `/login`
2. Click nút "Login with Google"
3. Chọn tài khoản Google `user+test@gmail.com`

**Expected Result:** Đăng nhập thành công, điều hướng về `/dashboard`
**Actual Result:** Trang trắng, Console hiện `Error 500: Internal Server Error`. Network log đính kèm.

**Attachments:**
- screenshot_error.png
- network_payload.json
```

---

## 3. Test Plan cơ bản (Kế hoạch kiểm thử)

Nội dung chính của một Test Plan:
1. **Scope:** In-scope (tính năng test) và Out-of-scope (tính năng chưa test).
2. **Strategy:** Manual test cho new feature, Automation cho regression test.
3. **Entry Criteria:** Điều kiện bắt đầu test (Code deployed staging, Smoke test PASS).
4. **Exit Criteria:** Điều kiện kết thúc test (100% Critical cases PASS, 0 open Critical bugs).
5. **Resource & Schedule:** Phân công nhân sự và mốc thời gian.

---

## 4. Requirement Traceability Matrix (RTM)

Bảng ma trận truy xuất nguồn gốc giúp đảm bảo **100% Requirement đều có Test Case bao phủ**:

| Requirement ID | Description | Test Case IDs | Execution Status | Defect ID |
|---|---|---|---|---|
| `REQ_AUTH_01` | Đăng nhập bằng Email | `TC_AUTH_001`, `TC_AUTH_002` | PASS | - |
| `REQ_AUTH_02` | Quên mật khẩu qua Email | `TC_AUTH_010` | FAIL | `BUG_045` |

---

## Checklist & Bài tập
- [ ] Chọn 1 feature trong ứng dụng của bạn, viết 10 Test Cases chuẩn format.
- [ ] Tự tạo 1 Bug Report mẫu cho lỗi bạn tìm được trên webapp.
- [ ] Lập bảng RTM cho module User Profile.
