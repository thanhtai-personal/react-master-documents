
# 📘 Ngày 15 – useLayoutEffect, forwardRef & useImperativeHandle

## I. useLayoutEffect vs useEffect

| useEffect | useLayoutEffect |
|-----------|-----------------|
| Gọi sau khi DOM đã được paint | Gọi **ngay sau DOM mutation**, trước khi browser vẽ |
| Không chặn hiển thị | Có thể block UI nếu code nặng |

### Khi nào dùng useLayoutEffect?
- Đo kích thước DOM (`getBoundingClientRect`)
- Đặt scroll, animation cần tính toán layout
- Đồng bộ layout critical (drag, dropdown)

---

## II. forwardRef

```jsx
const Input = forwardRef((props, ref) => (
  <input ref={ref} {...props} />
));
```

→ Cho phép truyền `ref` từ cha xuống component con functional

---

## III. useImperativeHandle

```jsx
useImperativeHandle(ref, () => ({
  focus: () => inputRef.current.focus()
}));
```

- Dùng với `forwardRef`
- Giúp expose public API của component

---

## IV. useId

```jsx
const id = useId();
<label htmlFor={id}>Email</label>
<input id={id} />
```

- Tránh đụng id khi render nhiều lần (SSR)

---

## V. Thực hành

1. Tạo input dùng `forwardRef` + focus từ bên ngoài
2. Dùng `useLayoutEffect` đo chiều cao box
3. Dùng `useImperativeHandle` tạo API scrollTo()

---
