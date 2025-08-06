
# 📘 Ngày 20 – Internationalization (i18n) trong React

## I. Tại sao cần i18n?

- Hỗ trợ nhiều ngôn ngữ (global users)
- Thân thiện với SEO
- Bắt buộc nếu làm app cho thị trường quốc tế

---

## II. Thư viện phổ biến

- `i18next` + `react-i18next`
- `react-intl`
- `next-intl` (Next.js)

---

## III. Cấu trúc i18n cơ bản

```js
const resources = {
  en: { translation: { welcome: "Welcome" } },
  vi: { translation: { welcome: "Chào bạn" } },
};
```

```jsx
const { t } = useTranslation();
<h1>{t("welcome")}</h1>
```

---

## IV. Lazy load locale + fallback

- Tách file `en.json`, `vi.json`
- Tự động đổi theo browser hoặc chọn

---

## V. i18n trong Next.js

- Tích hợp router locale
- Middleware định hướng theo geo/IP
- Server Component hỗ trợ `next-intl`

---

## VI. Thực hành

1. Setup i18n chuyển đổi English ⇄ Vietnamese
2. Lazy load ngôn ngữ
3. Tối ưu SEO với `lang`, `html[lang]`

---
