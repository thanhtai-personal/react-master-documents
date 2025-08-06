
# 📘 Ngày 9 – Styling React App

## I. Các phương pháp styling

| Cách | Ví dụ | Ưu điểm |
|------|-------|---------|
| CSS Modules | `style.module.css` | Scope cục bộ |
| Tailwind CSS | `class="bg-red-500"` | Utility-first |
| Styled Components | `styled.div` | CSS-in-JS, dynamic |
| Emotion | `css\`\`` | Linh hoạt, typed |
| Inline Style | `style={{ color: 'red' }}` | Không khuyến khích |

---

## II. Tailwind CSS

```html
<button class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2">Click</button>
```

- Dễ responsive
- Class nhiều nhưng gọn code logic

---

## III. Styled Components

```jsx
const Button = styled.button`
  background: red;
  color: white;
`;
```

- Hỗ trợ theming
- Có thể dùng prop để đổi style

---

## IV. Responsive & Dark Mode

- Tailwind: `md:flex`, `dark:bg-gray-800`
- Emotion/SC: dùng media queries trong template literal

---

## V. Thực hành

1. So sánh styled-component vs tailwind trên cùng UI
2. Cài Tailwind vào Next.js project
3. Thêm Dark Mode toggle

---
