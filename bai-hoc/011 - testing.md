
# 📘 Ngày 11 – Testing React Components

## I. Tại sao cần test?
- Bảo vệ logic trước khi refactor
- Bắt bug sớm
- Tăng độ tin cậy khi làm việc nhóm

---

## II. Các loại test

| Loại | Mục đích |
|------|---------|
| Unit Test | Kiểm tra logic nhỏ |
| Integration Test | Kiểm tra tương tác giữa component |
| E2E Test | Giả lập người dùng thao tác trên UI |

---

## III. React Testing Library (RTL)

```bash
npm install @testing-library/react @testing-library/jest-dom
```

```jsx
render(<Counter />);
fireEvent.click(screen.getByText("Increment"));
expect(screen.getByText("1")).toBeInTheDocument();
```

- RTL ưu tiên test như người dùng thật nhìn thấy

---

## IV. Playwright – Test E2E

```bash
npx playwright test
```

```ts
await page.goto("/login");
await page.getByLabel("Email").fill("abc@test.com");
await page.getByRole("button", { name: "Login" }).click();
```

---

## V. Mock API & async test

```jsx
jest.mock("./api");
await waitFor(() => expect(screen.getByText("Success")).toBeInTheDocument());
```

---

## VI. Thực hành

1. Test counter có tăng khi click
2. Test form có validate
3. Test login flow bằng Playwright

---
