
# 📘 Ngày 23 – Bảo mật trong React App

## I. Lỗ hổng phổ biến

- XSS (Cross Site Scripting)
- CSRF (Cross Site Request Forgery)
- Token/session leak

---

## II. Tránh XSS

```jsx
<div dangerouslySetInnerHTML={{ __html: data }} />
```

- ⚠️ Chỉ dùng khi thật sự cần
- Luôn sanitize HTML (DOMPurify, sanitize-html)

---

## III. Input Validation

- Không tin input từ user
- Dùng zod/yup/schema để validate

---

## IV. Secure Auth Flow

- Không lưu token trong localStorage
- Ưu tiên httpOnly cookie
- Bảo vệ route theo role (RBAC)

---

## V. Headers & CSP

- Dùng `helmet`, `next-secure-headers`
- CSP: chỉ cho phép script đáng tin

---

## VI. Thực hành

1. Demo XSS + cách fix
2. Bảo vệ route `/admin` chỉ cho `isAdmin`
3. Dùng `sanitize-html` + schema validate

---
