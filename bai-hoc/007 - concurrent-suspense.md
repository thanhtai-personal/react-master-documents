
# 📘 Ngày 7 – Concurrent Rendering & Suspense (React 18+)

## I. Concurrent Rendering là gì?

- Cho phép React **tạm dừng render**, **ưu tiên công việc quan trọng**, **tránh block UI**
- React 18 dùng Fiber để scheduling thông minh hơn

### So sánh:
| Legacy Render | Concurrent Render |
|---------------|-------------------|
| Đồng bộ, blocking | Chia nhỏ, interruptible |
| Mọi thứ chạy tới cùng | Có thể pause/resume/cancel |

---

## II. startTransition & useTransition

```jsx
const [isPending, startTransition] = useTransition();

startTransition(() => {
  setSearch(input);
});
```

- Dùng cho UI update **không khẩn cấp** (như filter, search...)
- `isPending` cho biết UI đang chờ → hiển thị loading hợp lý

---

## III. useDeferredValue

```jsx
const deferredValue = useDeferredValue(searchTerm);
```

- Trì hoãn render UI phụ thuộc vào state → tránh lag khi typing

---

## IV. Suspense & Lazy Loading

```jsx
<Suspense fallback={<Loading />}>
  <LazyComponent />
</Suspense>
```

- `fallback` hiển thị trong lúc chờ component tải
- Kết hợp với `React.lazy(() => import(...))`

---

## V. SuspenseList (hiếm dùng)

```jsx
<SuspenseList revealOrder="forwards">
  <Suspense fallback="Loading A"><A /></Suspense>
  <Suspense fallback="Loading B"><B /></Suspense>
</SuspenseList>
```

---

## VI. Thực hành

1. Dùng `startTransition` để search list lớn không bị lag
2. Dùng `useDeferredValue` để tối ưu filter
3. Kết hợp Suspense + lazy load component

---
