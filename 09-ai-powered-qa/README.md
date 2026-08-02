# 09 — AI-Powered QA: Ứng Dụng AI Trong Kiểm Thử (Trọng Tâm)

## Mục tiêu
Làm chủ việc ứng dụng AI/LLM trong quy trình QA: Prompt Engineering (Framework RCFCO), AI sinh Test Cases & Automation Code, sử dụng Microsoft Playwright MCP server, xây dựng mô hình Agentic Testing (Planner-Generator-Healer), và nắm rõ giới hạn của AI.

---

## 📊 Sơ đồ trực quan (Diagrams & Lifecycles)

### Kiến trúc 3-Agent Agentic Testing (Playwright MCP)
![Kiến trúc 3-Agent Agentic Testing (Playwright MCP)](diagrams/agentic-architecture.svg)

### Vòng lặp Review & Kiểm chứng AI Output
![Vòng lặp Review & Kiểm chứng AI Output](diagrams/ai-qa-review-loop.svg)

## 1. Prompt Engineering Framework cho QA (RCFCO)

Để AI cho ra Test Cases / Code chất lượng, dùng công thức **RCFCO**:
- **Role:** Vai trò của AI (Senior QA Engineer).
- **Context:** Ngữ cảnh feature, User story, Acceptance Criteria, Business rules.
- **Format:** Định dạng output (Bảng Markdown, JSON, Gherkin, Code TypeScript).
- **Constraint:** Ràng buộc (Platform, Browser, Data limits).
- **Output:** Phạm vi (Focus on Edge cases, Security, Boundary values).

```markdown
**Prompt Mẫu:**
Role: Senior QA Engineer chuyên về Web E-commerce.
Context: Feature "Áp dụng mã giảm giá tại Checkout". Giá trị đơn hàng tối thiểu 200k. Mã hết hạn hoặc hết lượt sẽ bị từ chối.
Task: Sinh 10 test cases bao gồm Happy path, Negative cases, Boundary values.
Format: Bảng Markdown gồm (Test ID | Title | Type | Steps | Expected Result | Priority).
Constraint: Cung cấp ít nhất 3 security edge cases (SQL injection, Tampered payload).
```

---

## 2. Playwright MCP (Model Context Protocol) Server

Microsoft cung cấp **Playwright MCP Server** cho phép các AI Agent (Claude Code, Cursor, Gemini CLI) trực tiếp điều khiển trình duyệt thật thông qua **Accessibility Tree** (dạng Role/Name/State) thay vì Screenshot.

### Setup MCP Config:
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

---

## 3. Mô hình 3-Agentic Testing Architecture

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   PLANNER   │ ──▶ │  GENERATOR   │ ──▶ │   HEALER    │
│ (Lên KH Test)│     │(Sinh Code UI)│     │(Tự Sửa Test)│
└─────────────┘     └──────────────┘     └─────────────┘
```

1. **Planner Agent:** Đọc PRD/Requirement ➔ Sinh ra Test Strategy & Matrix scenarios.
2. **Generator Agent:** Đọc Accessibility Tree của App ➔ Sinh Playwright Test Code chuẩn POM.
3. **Healer Agent (Self-Healing):** Chạy test, khi Selector bị lỗi do UI đổi ➔ Tự đọc DOM snapshot mới và cập nhật lại Code.

---

## 4. Review Checklist cho AI-Generated Code & AI Limitations

### Review Checklist:
- [ ] Selector AI chọn có thực sự tồn tại và stable không?
- [ ] Assertion có đúng logic nghiệp vụ không?
- [ ] AI có lỡ dùng `waitForTimeout` (anti-pattern) không?

### Giới hạn của AI trong QA:
- AI không hiểu business logic ngầm của công ty ➔ Cần Human QA cung cấp context đầy đủ.
- AI có thể hallucinate API endpoints / Selectors ➔ **Bắt buộc phải chạy test thật để kiểm chứng**.
- Exploratory Testing (Trực giác & Khám phá lỗi ngoài kịch bản) vẫn là thế mạnh tuyệt đối của con người.
