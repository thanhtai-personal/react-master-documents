
# 📘 Ngày 12 – Next.js Fullstack: App Router, SSR, SEO

## I. Giới thiệu Next.js

- Framework React fullstack hiện đại
- Tích hợp routing, API, SSR/SSG, SEO, image optimization

---

## II. File-based Routing

```bash
app/
  page.tsx         => "/"
  about/page.tsx   => "/about"
  blog/[slug]/page.tsx => "/blog/:slug"
```

---

## III. SSR, SSG, ISR

| Cách | Hàm | Khi nào dùng |
|------|-----|--------------|
| SSR | `getServerSideProps` | Cập nhật theo request |
| SSG | `getStaticProps` | Tạo sẵn khi build |
| ISR | `revalidate` | SSG + cập nhật định kỳ |

---

## IV. Metadata & SEO

```tsx
export const metadata = {
  title: "Trang chủ",
  description: "SEO tốt cho Google",
};
```

---

## V. API Routes

```ts
export async function GET(req) {
  return NextResponse.json({ hello: "world" });
}
```

---

## VI. Image & Fonts

- `next/image`: tối ưu lazy load
- `next/font/google`: nhúng font nhanh hơn

---

## VII. Thực hành

1. Tạo blog page dùng dynamic route + fetch data từ API
2. Tạo SSR page với query string
3. Viết API đơn giản trả về JSON

---
