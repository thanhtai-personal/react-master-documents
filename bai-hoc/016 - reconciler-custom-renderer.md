
# 📘 Ngày 16 – React Reconciler & Custom Renderer

## I. React hoạt động thế nào bên trong?

- JSX → React Element → Fiber Tree
- Fiber chứa thông tin render unit
- Scheduler quyết định khi nào render gì

---

## II. React-Reconciler là gì?

- Low-level API để custom renderer (non-DOM)
- Các renderer như: `react-three-fiber`, `react-pdf`, `ink`

```ts
import Reconciler from 'react-reconciler';
```

---

## III. Viết custom renderer đơn giản

- Khởi tạo hostConfig
- Dùng `Reconciler.createContainer()`, `updateContainer()`
- Tạo tree bằng API riêng (VD: canvas, terminal)

---

## IV. Khi nào nên viết custom renderer?

- Giao diện không phải DOM: canvas, GL, terminal
- Cần xử lý render theo platform riêng

---

## V. Thực hành

1. Tìm hiểu `react-pdf`, `react-three-fiber`
2. Viết demo render text terminal với `ink`
3. Viết Hello World renderer với console.log()

---
