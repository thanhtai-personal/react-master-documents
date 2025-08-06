
# 📘 Ngày 17 – Accessibility (A11y) trong React

## I. Tại sao cần A11y?

- Đáp ứng tiêu chuẩn WCAG (Web Content Accessibility Guidelines)
- Giúp người khiếm thị, dùng bàn phím, screen reader

---

## II. ARIA roles cơ bản

```jsx
<button aria-label="Đóng menu">❌</button>
<nav role="navigation">...</nav>
```

---

## III. Keyboard navigation

- `tabIndex={0}`: focusable
- `onKeyDown`: bắt sự kiện phím
- `aria-pressed`, `aria-expanded`: thông báo trạng thái

---

## IV. Công cụ hỗ trợ

- `axe-core`, `eslint-plugin-jsx-a11y`
- Chrome Lighthouse A11y
- NVDA / VoiceOver screen reader test

---

## V. Dùng thư viện hỗ trợ

- `@react-aria`, `radix-ui`, `headlessui`

---

## VI. Thực hành

1. Làm menu dropdown dùng keyboard
2. Thêm aria-label cho icon
3. Chạy lighthouse và sửa lỗi A11y

---
