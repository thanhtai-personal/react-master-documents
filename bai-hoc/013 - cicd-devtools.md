
# 📘 Ngày 13 – DevTools, Debug & CI/CD

## I. React DevTools

- Tab Component: xem props, state
- Tab Profiler: đo thời gian render

## II. Debug UI

- Dùng breakpoint (VS Code)
- `console.log`, `debugger`
- Check render lại bằng `why-did-you-render`

---

## III. CI/CD với Vercel

### Tự động build khi push:

- Connect GitHub → Vercel
- Push branch → deploy preview
- Merge vào main → deploy production

---

## IV. ESLint + Prettier

- Giữ code format thống nhất
- Bắt lỗi sớm

```bash
npm install eslint prettier eslint-plugin-react
```

---

## V. Bundle Analyzer

```ts
const withBundleAnalyzer = require("@next/bundle-analyzer")({ enabled: true });
```

---

## VI. Monitoring & Analytics

- Google Analytics, Vercel Analytics
- Sentry, LogRocket để bắt bug production

---

## VII. Thực hành

1. Bật React DevTools, đo lại hiệu năng
2. Thêm ESLint + Prettier vào project
3. Deploy CI/CD lên Vercel từ GitHub

---
