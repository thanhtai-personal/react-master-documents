
# 📘 Ngày 21 – Server Component trong Next.js 13+

## I. Giới thiệu

- Chạy **trên server**, không gửi JS xuống client
- Bảo mật hơn, tối ưu hơn, render sớm hơn
- Hỗ trợ streaming UI (React 18)

---

## II. use client vs server component

```tsx
// server by default
export default function Page() {}

// client bắt buộc
'use client';
import { useState } from 'react';
```

---

## III. Ưu điểm server component

- Không tải JS không cần thiết
- Truy cập trực tiếp database
- Không expose logic cho client

---

## IV. Giới hạn

- Không dùng state/hook client
- Không dùng browser API
- Không có `onClick`, `useEffect`...

---

## V. Kết hợp streaming + Suspense

```tsx
<Suspense fallback={<Loading />}>
  <Comments />
</Suspense>
```

---

## VI. Thực hành

1. Tạo page hiển thị bài viết từ DB bằng server component
2. Tách phần tương tác sang client (nút Like)
3. Dùng Suspense + loading.tsx

---
