
# 📘 Ngày 24 – Kiến trúc Codebase lớn trong React

## I. Vì sao cần kiến trúc tốt?

- Dễ bảo trì và mở rộng
- Dễ scale đội ngũ
- Giảm bug khi refactor
- Tối ưu performance & DX

---

## II. Tư duy tổ chức thư mục

### 1. Theo domain (Domain-driven folder)

```
/features
  /auth
    /components
    /hooks
    /services
  /dashboard
  /posts
```

→ Mỗi domain tự quản lý state, UI, API riêng

---

### 2. Atomic Design (UI theo mức độ)

```
/components
  /atoms     (Button, Input)
  /molecules (Form, Card)
  /organisms (Layout, PageSection)
```

→ Dễ tái sử dụng UI theo cấp độ

---

### 3. Hybrid (kết hợp cả 2)

```
/features
  /auth
    /ui (atoms/molecules)
    /hooks
    /api
```

---

## III. Monorepo cho frontend

- Dùng `Turborepo`, `Nx`, `Lage`
- Quản lý nhiều packages trong 1 repo
- Dùng khi có nhiều app hoặc module độc lập

---

## IV. Tối ưu hiệu năng codebase

- `react.lazy` + `Suspense` cho component lớn
- `dynamic import()` khi routing hoặc tương tác
- Prefetch bằng `next/link` hoặc Intersection Observer

---

## V. Coding convention

- ESLint + Prettier + EditorConfig
- Commitlint + Husky (pre-commit)
- Folder naming thống nhất (kebab-case, PascalCase)

---

## VI. Thực hành

1. Thiết kế lại cấu trúc folder cho app blog
2. Thêm lazy loading cho page lớn
3. Tạo folder `features`, chia domain rõ ràng

---
