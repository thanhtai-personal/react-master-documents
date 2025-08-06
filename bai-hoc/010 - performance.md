
# 📘 Ngày 10 – Performance Optimization trong React

## I. React re-render là gì?

- Mỗi khi state/props thay đổi → component render lại
- Cần hạn chế re-render không cần thiết

---

## II. useMemo, useCallback (ôn lại)

- `useMemo`: tránh tính toán lại
- `useCallback`: giữ function ổn định

---

## III. React.memo

```jsx
const MemoComp = React.memo(Component);
```

- Chỉ render lại nếu props thay đổi

---

## IV. Lazy Load & Code Splitting

```jsx
const LazyPage = React.lazy(() => import("./Page"));
```

- Kết hợp `Suspense` để tải theo nhu cầu

---

## V. Bundle Analyzer

- Phân tích bundle Webpack/Vite để giảm kích thước
- Loại bỏ dependency thừa

---

## VI. DevTools & Profiler

- React DevTools tab “Profiler”: đo time render, cây component
- Chrome Lighthouse: đo TTI, TBT, FCP...

---

## VII. Thực hành

1. Tối ưu table hiển thị 5000 dòng
2. Dùng React.memo và useMemo
3. Phân tích bundle bằng `@next/bundle-analyzer` hoặc `source-map-explorer`

---
