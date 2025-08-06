
# 📘 Ngày 4 – Custom Hooks & Patterns tái sử dụng logic

## I. Custom Hook là gì?
Custom Hook là function bắt đầu bằng `use`, có thể sử dụng các hook khác bên trong để tái sử dụng logic giữa các component.

### Mục đích:
- DRY code – không lặp lại logic giống nhau
- Trừu tượng hóa logic phức tạp
- Dễ test và bảo trì

---

## II. Cách viết Custom Hook

### Cấu trúc cơ bản:
```jsx
function useCounter(initial = 0) {
  const [count, setCount] = useState(initial);
  const inc = () => setCount(c => c + 1);
  const dec = () => setCount(c => c - 1);
  return { count, inc, dec };
}
```

### Cách sử dụng:
```jsx
const { count, inc } = useCounter(5);
```

---

## III. Các loại custom hook thực tế

### 1. useDebounce
```jsx
function useDebounce(value, delay) {
  const [debounced, setDebounced] = useState(value);
  useEffect(() => {
    const handler = setTimeout(() => setDebounced(value), delay);
    return () => clearTimeout(handler);
  }, [value, delay]);
  return debounced;
}
```

### 2. useLocalStorage
```jsx
function useLocalStorage(key, defaultValue) {
  const [value, setValue] = useState(() => {
    const json = localStorage.getItem(key);
    return json ? JSON.parse(json) : defaultValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}
```

### 3. usePrevious
```jsx
function usePrevious(value) {
  const ref = useRef();
  useEffect(() => {
    ref.current = value;
  }, [value]);
  return ref.current;
}
```

---

## IV. Tư duy kiến trúc tái sử dụng logic

| Pattern | Ưu điểm | Khi nào dùng |
|--------|--------|--------------|
| Custom Hook | Dễ đọc, tách biệt rõ logic | Khi có logic state tái sử dụng |
| Render Props | Linh hoạt truyền logic vào UI khác | Khi muốn truyền dữ liệu xuống sâu |
| HOC | Thêm logic bao quanh component | Khi dùng nhiều component có logic chung |

> Hiện tại, **Custom Hook** là cách phổ biến và được khuyên dùng trong React hiện đại.

---

## V. Thực hành

1. Viết `useDebounce`, `useLocalStorage`, `usePrevious`
2. Viết `useIsOnline` – kiểm tra kết nối internet bằng `navigator.onLine`
3. Kết hợp nhiều hook: `useFormInput` (dùng debounce + localStorage)

---

## VI. Quiz ôn tập

1. Tại sao custom hook phải bắt đầu bằng `use`?
2. So sánh custom hook với HOC và render props?
3. Cách lưu state vào localStorage bằng hook?
4. Cách ghi nhớ giá trị trước đó trong render?
5. Hook nào dùng để debounce dữ liệu nhập vào?

---

**Tổng kết:** Ngày 4 giúp bạn tự tay viết và tổ chức các custom hook chuẩn production, đồng thời hiểu được tư duy thiết kế reusable logic – kỹ năng cốt lõi cho các dự án lớn và team codebase chia sẻ.
