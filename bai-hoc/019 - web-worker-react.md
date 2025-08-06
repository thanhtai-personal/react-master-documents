
# 📘 Ngày 19 – Web Worker trong React

## I. Web Worker là gì?

- JavaScript chạy ở thread riêng, không block UI
- Dùng cho tính toán nặng, xử lý ảnh, parsing lớn

---

## II. Tạo Web Worker

```js
// worker.js
self.onmessage = (e) => {
  self.postMessage(e.data * 2);
};
```

```js
// main.js
const worker = new Worker('./worker.js');
worker.onmessage = (e) => console.log(e.data);
worker.postMessage(5);
```

---

## III. Kết hợp React + Web Worker

- Dùng `useEffect` tạo worker
- Giao tiếp qua message
- Cleanup khi unmount

---

## IV. Thư viện hỗ trợ

- `comlink`: truyền function giữa threads
- `use-worker`: hook wrapper cho React

---

## V. Thực hành

1. Tạo filter list lớn bằng Web Worker
2. Giao tiếp worker + component qua message
3. Dùng `use-worker` đơn giản hóa

---
