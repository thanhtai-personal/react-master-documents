
# 📘 Ngày 8 – Forms & Events trong React

## I. Synthetic Events

```jsx
function handleClick(e) {
  console.log(e.type); // synthetic event
}
```

- React dùng hệ thống sự kiện riêng → nhất quán giữa trình duyệt

---

## II. Controlled vs Uncontrolled

```jsx
// Controlled
<input value={value} onChange={e => setValue(e.target.value)} />

// Uncontrolled
<input defaultValue="hello" ref={ref} />
```

---

## III. Form Libraries

### React Hook Form (đề xuất):
- Hiệu năng cao, dễ dùng
- Validation mạnh
- Hỗ trợ async schema (zod, yup)

```jsx
const { register, handleSubmit } = useForm();
<input {...register("email")} />
```

---

## IV. Formik (thay thế cũ)

```jsx
<Formik initialValues={{ name: '' }} onSubmit={...}>
  ...
</Formik>
```

---

## V. Validation Tools

- yup: Schema-based
- zod: Typescript-first

---

## VI. Thực hành

1. Viết form đăng ký có validate email và password
2. Dùng React Hook Form + yup để validate

---
