
# 📘 Ngày 5 – State Management chuyên sâu: Context, Redux Toolkit, Zustand, Jotai

## I. Tại sao cần State Management toàn cục?
- React state (`useState`) chỉ dùng trong 1 component hoặc truyền xuống qua props.
- Khi app lớn: nhiều component cần chia sẻ state → "prop drilling", khó quản lý.
- Giải pháp: Context API, Redux Toolkit, Zustand, Jotai...

---

## II. Context API (built-in)

### 1. Tạo Context
```jsx
const ThemeContext = createContext();
```

### 2. Provider
```jsx
<ThemeContext.Provider value={{ theme: 'dark' }}>
  <App />
</ThemeContext.Provider>
```

### 3. Consumer (Hook)
```jsx
const { theme } = useContext(ThemeContext);
```

### ✅ Ưu điểm:
- Đơn giản, không cần lib ngoài
- Tốt cho config, theme, auth

### ⚠️ Hạn chế:
- Không tối ưu cho state thay đổi thường xuyên
- Không có middlewares, async, devtools

---

## III. Redux Toolkit

### 1. Setup Store
```js
const store = configureStore({ reducer: { counter: counterReducer } });
```

### 2. Slice
```js
const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: (state) => state + 1
  }
});
```

### 3. Dùng trong React
```jsx
const count = useSelector(state => state.counter);
const dispatch = useDispatch();
dispatch(increment());
```

✅ Ưu điểm:
- DevTools mạnh mẽ
- Dễ kiểm soát logic
- Middleware, async logic (`createAsyncThunk`)

---

## IV. Zustand (lightweight & reactive)

### 1. Tạo store
```js
const useStore = create((set) => ({
  count: 0,
  inc: () => set(state => ({ count: state.count + 1 }))
}));
```

### 2. Dùng trong component
```jsx
const count = useStore(state => state.count);
const inc = useStore(state => state.inc);
```

✅ Ưu điểm:
- Rất nhẹ (1kb), không cần Provider
- Có DevTools, persist, middleware

---

## V. Jotai (atomic state)

### 1. Khởi tạo atom
```js
const countAtom = atom(0);
```

### 2. Sử dụng trong component
```jsx
const [count, setCount] = useAtom(countAtom);
```

✅ Ưu điểm:
- Cách tiếp cận functional, giống Recoil
- Dễ phân tách state nhỏ

---

## VI. So sánh nhanh các giải pháp

| Tiêu chí | Context | Redux Toolkit | Zustand | Jotai |
|----------|---------|----------------|--------|-------|
| Built-in | ✅ | ❌ | ❌ | ❌ |
| Boilerplate | Thấp | Vừa | Rất thấp | Thấp |
| DevTools | ❌ | ✅ | ✅ | ✅ (plugin) |
| Async support | ❌ | ✅ | ✅ | ✅ |
| Performance | Trung bình | Tốt | Rất tốt | Tốt |
| Use case | Theme, Auth | App lớn | App nhỏ-vừa | App functional-reactive |

---

## VII. Thực hành

1. Dùng Context cho theme toggle (light/dark).
2. Dùng Redux Toolkit để quản lý counter + async fetch API.
3. Dùng Zustand làm todo list đơn giản.
4. Dùng Jotai để tạo form state logic phân tách.

---

## VIII. Quiz ôn tập

1. Khi nào nên dùng Context thay vì Redux?
2. Ưu điểm chính của Zustand là gì?
3. Jotai khác Redux Toolkit ở điểm nào?
4. useSelector trong Redux dùng để làm gì?
5. Middleware trong Redux Toolkit dùng để làm gì?

---

**Tổng kết:** Ngày 5 giúp bạn nắm được các giải pháp quản lý state toàn cục – từ đơn giản (Context) đến chuyên nghiệp (Redux), hiện đại (Zustand, Jotai) – để bạn linh hoạt chọn đúng công cụ phù hợp với dự án.
