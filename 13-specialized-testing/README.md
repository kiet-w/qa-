# 13 — Mobile, Performance, Security & Accessibility

## Mục tiêu

Khám phá các nhánh chuyên môn sau nền tảng, sau đó chọn một hoặc hai nhánh để học sâu thay vì học dàn trải.

## Backlog theo nhánh

### Mobile testing

- Android/iOS lifecycle, install/update/uninstall, permissions, offline/online, notification, orientation.
- Device/OS matrix, real device vs emulator, screen sizes, battery/network conditions.

### Performance testing

- Metric cơ bản: response time, throughput, error rate, concurrent users.
- Load, stress, spike, soak; đọc kết quả và xác định bottleneck hypothesis.
- Bắt đầu bằng k6 hoặc JMeter trên môi trường demo/staging có cho phép; không load test production tùy ý.

### Security testing cho QA

- OWASP Top 10 ở mức nhận biết: broken access control, injection, auth/session issues, security misconfiguration, data exposure.
- Test permission theo role, validate input, error message, session expiry; báo evidence, không tự khai thác vượt scope.

### Accessibility testing

- Keyboard-only navigation, focus order, semantic labels, alt text, contrast, zoom/reflow, screen reader basics.
- Dùng Lighthouse/axe như công cụ gợi ý; vẫn manual verify user experience.

## Definition of done

- [ ] Chọn một nhánh ưu tiên phù hợp mục tiêu nghề nghiệp.
- [ ] Có checklist thực hành an toàn trên app demo/staging được phép.
- [ ] Nêu được giới hạn quyền hạn khi thực hiện performance/security test.
