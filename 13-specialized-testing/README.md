# 13 — Specialized Testing: Performance, Security & Accessibility

## Mục tiêu
Nắm vững khái niệm và thực hành cơ bản với k6 (Load Testing), OWASP Top 10 (Security Testing), AXE (Accessibility Testing), và Mobile Testing.

---

## 1. Performance / Load Testing với k6

```javascript
import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  vus: 50, // 50 Virtual Users
  duration: '30s',
  thresholds: { http_req_duration: ['p(95)<500'] }, // 95% request < 500ms
};

export default function () {
  const res = http.get('http://localhost:3000/api/products');
  check(res, { 'status is 200': (r) => r.status === 200 });
  sleep(1);
}
```

---

## 2. Security Testing (OWASP Top 10 Basics)

- **IDOR (Insecure Direct Object Reference):** Sửa ID trên URL `/api/orders/1` thành `/api/orders/2` ➔ Phải nhận 403 Forbidden nếu không phải owner.
- **XSS (Cross-Site Scripting):** Nhập `<script>alert('xss')</script>` ➔ Verify input được escape an toàn.

---

## 3. Accessibility Testing (a11y) với AXE

Thực thi kiểm tra chuẩn WCAG trực tiếp trong Playwright:
```typescript
import AxeBuilder from '@axe-core/playwright';

test('a11y check', async ({ page }) => {
  await page.goto('/');
  const results = await new AxeBuilder({ page }).analyze();
  expect(results.violations).toEqual([]);
});
```
