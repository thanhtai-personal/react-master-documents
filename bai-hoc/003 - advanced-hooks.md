
# 📘 Ngày 3 – Hooks nâng cao: useEffect sâu, useMemo, useCallback thực chiến

## I. useEffect – hiểu thật sâu

### 1. Cấu trúc cơ bản
```jsx
useEffect(() => {
  // effect logic
  return () => {
    // cleanup logic
  };
}, [deps]);
```

- **Không deps**: gọi sau mỗi render
- **Deps rỗng `[]`**: chỉ gọi sau render lần đầu (componentDidMount)
- **Có deps**: gọi lại khi deps thay đổi

### 2. Vấn đề thường gặp
- Gọi API lặp nhiều lần nếu không set đúng deps
- Cleanup không đúng → memory leak (ex: socket, timer...)
- Vấn đề closure trap – biến trong scope cũ

### 3. Ví dụ closure trap:
```jsx
useEffect(() => {
  const interval = setInterval(() => {
    console.log(count); // count không cập nhật
  }, 1000);
  return () => clearInterval(interval);
}, []); // thiếu deps!
```

**Cách fix:** dùng ref hoặc thêm deps đúng

---

## II. useMemo – tối ưu tính toán

### 1. Công dụng:
- Tránh tính toán lại những biểu thức nặng nếu deps không đổi

```jsx
const result = useMemo(() => heavyCompute(a, b), [a, b]);
```

### 2. Khi nào dùng?
- Khi render lag do tính toán nặng
- Khi cần giữ reference ổn định để tránh re-render

> **Không nên dùng quá mức – chỉ khi cần thiết.**

---

## III. useCallback – giữ function ổn định

### 1. Cách dùng:
```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

- Trả về **function mới chỉ khi deps thay đổi**
- Tránh props callback bị thay đổi → gây re-render

### 2. So sánh:
| Hook | Trả về | Dùng cho |
|------|--------|---------|
| useMemo | Giá trị | Memoize kết quả tính toán |
| useCallback | Hàm | Giữ function reference ổn định |

---

## IV. useRef – giá trị không re-render

```jsx
const countRef = useRef(0);
countRef.current++;
```

- Không làm component re-render
- Giữ giá trị qua các lần render

**Dùng tốt cho:** scroll, DOM node, previous state

---

## V. Thực hành

1. Tạo component có setInterval → fix bằng ref để tránh closure trap.
2. Dùng useMemo để tối ưu hàm filter dữ liệu lớn.
3. Dùng useCallback để truyền function callback vào component con mà không bị re-render.

---

## VI. Quiz ôn tập

1. `useEffect(() => {...})` có deps rỗng nghĩa là gì?
2. Tại sao `useEffect` có thể bị gọi lại nhiều lần không mong muốn?
3. Khi nào dùng `useMemo`?
4. `useCallback` khác gì `useMemo`?
5. Tại sao `useRef` không làm re-render?

---

**Tổng kết:** Ngày 3 giúp bạn xử lý các hook quan trọng nhất trong thực tế với tư duy sâu sắc: tránh lỗi useEffect, hiểu tối ưu với useMemo, và giữ performance mượt mà với useCallback – nền tảng thiết yếu cho các app React lớn.
