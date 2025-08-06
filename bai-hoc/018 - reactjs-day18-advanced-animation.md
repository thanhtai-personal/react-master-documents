
# 📘 Ngày 18 – Animation nâng cao với React

## I. Thư viện animation phổ biến

- `framer-motion` – declarative, mạnh mẽ, dễ dùng
- `react-spring` – vật lý, motion tự nhiên
- `GSAP` – phức tạp, dùng khi animation nâng cao

---

## II. Framer Motion cơ bản

```jsx
<motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} />
```

- `initial`, `animate`, `exit`, `transition`
- Animate layout: `layout` prop

---

## III. Animate presence

```jsx
<AnimatePresence>
  {isOpen && <motion.div exit={{ opacity: 0 }} />}
</AnimatePresence>
```

- Dùng cho component mount/unmount

---

## IV. UI animation thực tế

- Modal open/close
- Drag & drop card
- Expand/collapse
- Skeleton loader

---

## V. Thực hành

1. Làm Modal với AnimatePresence
2. Drag drop đơn giản
3. Motion tab chuyển động mượt

---
