# 📘 Ngày 1 – React Core: Tư duy, JSX, Virtual DOM và Fiber

## I. Tại sao React ra đời?
React được sinh ra để giải quyết các vấn đề phổ biến trong frontend như:
- Thao tác DOM trực tiếp gây chậm và khó quản lý.
- Quản lý UI phức tạp và khó kiểm soát khi state thay đổi.
- Không có mô hình component hóa rõ ràng (trước React: jQuery, Backbone, ...).

React giới thiệu:
- UI theo hướng **declarative** (khai báo theo state).
- **One-way data flow**: dễ predict, dễ debug.
- **Virtual DOM**: giúp render nhanh và hiệu quả hơn.
- **Component-based**: chia nhỏ và tái sử dụng logic UI.

---

## II. JSX & `React.createElement`

### JSX là gì?
JSX là cú pháp mở rộng của JavaScript được compile thành `React.createElement()`.

**Ví dụ:**
```jsx
const el = <h1>Hello</h1>;
// Tương đương:
const el = React.createElement("h1", null, "Hello");
```

### Compilation Flow:
```
JSX → Babel → AST → React.createElement → React Element Tree
```

**Lưu ý khi dùng JSX:**
- Không dùng `if/else` trực tiếp → dùng ternary / function.
- Không dùng loop trực tiếp → dùng `array.map()`.
- `class` → `className`, `for` → `htmlFor`.

---

## III. Virtual DOM & Fiber Architecture

### 1. Virtual DOM
Virtual DOM là bản sao lightweight của DOM thật. React:
- So sánh virtual DOM mới & cũ (diffing).
- Chỉ cập nhật DOM thật khi cần thiết.

### 2. React Render Flow (React 18+)
```
JSX → React Element → Fiber Tree → Reconciliation → Commit DOM
```

### 3. Fiber Architecture
- Thay thế kiến trúc Stack cũ bằng mô hình **Fiber Tree**.
- Giúp **chia nhỏ công việc**, **hoãn hoặc tạm dừng render** khi cần thiết.
- Cho phép **concurrent rendering** và hỗ trợ `Suspense`, `startTransition`...

---

## IV. Thực hành

### Viết JSX và `createElement` tương đương:
```jsx
const Comp = () => <div className="box">Hello</div>;
// Viết lại:
const Comp = () => React.createElement('div', { className: 'box' }, 'Hello');
```

### Diffing demo:
```jsx
function Demo() {
  const [count, setCount] = useState(0);
  return <h1>{count}</h1>; // chỉ textNode bị cập nhật
}
```

---

## V. Quiz ôn tập

**Ví dụ 3 câu đầu tiên:**
1. React là gì? → `B. UI Library`
2. JSX thực chất là gì? → `C. Được compile thành React.createElement`
3. Virtual DOM dùng để? → `A. Tránh thao tác DOM thật không cần thiết`

(... bạn có thể thêm tiếp các câu còn lại)

---

## VI. Bài tập code
1. Viết 1 component dùng JSX và viết lại bằng `React.createElement`.
2. Demo danh sách không có `key` vs có `key` → dùng React DevTools để so sánh quá trình cập nhật.

---

**Tổng kết:** Bài học này giúp bạn hiểu rõ nguồn gốc, nguyên lý hoạt động của React từ mức độ low-level, chuẩn bị cho việc học sâu hơn về Hook Engine, Component Patterns trong các ngày tới.
