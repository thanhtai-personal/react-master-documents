
# 📘 Ngày 2 – Component Patterns & Hook Engine chuyên sâu

## I. Kiến trúc Component trong React

### 1. Component là gì?
- Hàm hoặc class nhận props và trả về UI (React Element).
- Có thể tái sử dụng, độc lập, dễ kiểm thử.

### 2. Functional vs Class Component

| So sánh | Functional Component | Class Component |
|---------|----------------------|------------------|
| Khai báo | `function App() {}` | `class App extends React.Component {}` |
| Lifecycle | Hooks | Lifecycle methods |
| State | `useState`, `useReducer` | `this.state`, `this.setState` |
| Gọn nhẹ | ✅ | ❌ |
| Dùng phổ biến | ✅ | Gần như không còn dùng mới |

### 3. Pure Component & Memo

- `React.memo(Component)` giúp tránh re-render không cần thiết.
- Sử dụng khi component phụ thuộc props "tĩnh".

---

## II. 6 Component Pattern phổ biến

### 1. Presentational vs Container
```jsx
// Presentational
const Button = ({ label }) => <button>{label}</button>;

// Container
const LoginButton = () => <Button label="Login" />;
```

### 2. Controlled vs Uncontrolled
```jsx
// Controlled Input
<input value={value} onChange={e => setValue(e.target.value)} />
// Uncontrolled Input
<input defaultValue="abc" ref={inputRef} />
```

### 3. Compound Components
```jsx
<Tabs>
  <Tabs.Tab label="1">Nội dung 1</Tabs.Tab>
  <Tabs.Tab label="2">Nội dung 2</Tabs.Tab>
</Tabs>
```

### 4. Render Props
```jsx
<DataProvider render={(data) => <Chart data={data} />} />
```

### 5. HOC – Higher Order Component
```jsx
const withLogger = (Component) => (props) => {
  console.log("Props", props);
  return <Component {...props} />;
};
```

### 6. Custom Hook Pattern
```jsx
function useCounter() {
  const [count, setCount] = useState(0);
  const inc = () => setCount(c => c + 1);
  return { count, inc };
}
```

---

## III. Hook Engine – Cách Hooks hoạt động bên trong

### 1. Hooks lưu state ở đâu?
React lưu các hook vào một danh sách liên kết (linked list) trong Fiber node.

```jsx
function App() {
  const [a, setA] = useState(0);
  const [b, setB] = useState(1);
}
```
→ React ghi nhớ `a` ở vị trí gọi `useState` đầu tiên, `b` ở vị trí thứ hai.

### 2. Quy tắc bắt buộc khi dùng Hook:
- Chỉ gọi hook ở **cấp cao nhất** của function component.
- Không gọi trong điều kiện (`if/else`, loop, ...).
- Hook phải **theo đúng thứ tự** ở mỗi lần render.

### 3. Vì sao useEffect bị gọi lại?
- Vì dependencies thay đổi (dù là reference object, array…).
- Cần `useMemo`, `useCallback` để tránh.

---

## IV. Thực hành

1. Viết `useCounter`, `useLocalStorage`, `useDebounce` hook.
2. Viết Tabs component dạng Compound Component.
3. Viết `withLoadingSpinner(Component)` HOC.

---

## V. Quiz ôn tập

1. `React.memo` dùng để...?  
2. Khác biệt chính giữa Controlled & Uncontrolled components?  
3. Tại sao không được gọi `useState` trong vòng lặp?
4. `Render Props` khác gì HOC? Ưu nhược điểm?
5. `React` lưu state hook theo thứ tự nào?

---

**Tổng kết:** Ngày 2 giúp bạn nắm chắc toàn bộ các pattern component hiện đại, hiểu rõ cách hoạt động của Hook và nguyên lý cập nhật state trong React – nền tảng để viết code sạch, tái sử dụng tốt và dễ test.
