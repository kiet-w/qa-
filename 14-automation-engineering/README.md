# 14 — Automation Engineering: Xây Dựng Framework Nâng Cao

## Mục tiêu
Làm chủ mô hình Page Object Model (POM), Quản lý Fixtures, Xử lý Flaky Tests, và Tích hợp CI/CD với GitHub Actions & Allure Report.

---

## 📊 Sơ đồ trực quan (Diagrams & Lifecycles)

### Kiến trúc Page Object Model (POM) Pattern
![Kiến trúc Page Object Model (POM) Pattern](diagrams/pom-architecture.svg)

### Workflow Tự động hóa CI/CD với GitHub Actions
![Workflow Tự động hóa CI/CD với GitHub Actions](diagrams/cicd-pipeline.svg)

## 1. Page Object Model (POM) Pattern

```typescript
// pages/login.page.ts
export class LoginPage {
  constructor(private page: Page) {}
  readonly emailInput = this.page.getByLabel('Email');
  readonly loginBtn = this.page.getByRole('button', { name: 'Login' });

  async login(email: string, pass: string) {
    await this.emailInput.fill(email);
    await this.page.getByLabel('Password').fill(pass);
    await this.loginBtn.click();
  }
}
```

---

## 2. CI/CD GitHub Actions Workflow

```yaml
name: Playwright Tests
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
      - run: npm ci
      - run: npx playwright install --with-deps
      - run: npx playwright test
```
