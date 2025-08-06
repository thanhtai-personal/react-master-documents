
# 📘 Ngày 22 – Micro Frontends & Module Federation

## I. Microfrontend là gì?

- Chia nhỏ app thành các phần riêng biệt
- Mỗi phần có thể deploy, update độc lập
- Tăng khả năng scale team

---

## II. Module Federation (Webpack 5)

```js
// expose
exposes: {
  './Header': './src/Header',
}
// remote
remotes: {
  navbar: 'navbar@http://localhost:3001/remoteEntry.js',
}
```

---

## III. Host – Remote architecture

- Host: app chính
- Remote: app con (có component, pages riêng)

---

## IV. Tích hợp trong React

- Dùng `ModuleFederationPlugin`
- Tải component động: `import('navbar/Header')`

---

## V. Turborepo + Next.js

- Chia workspace theo feature
- Cùng deploy hoặc CI riêng biệt

---

## VI. Thực hành

1. Tách app Navbar và App chính
2. Tích hợp remote component từ app khác
3. Build monorepo React + deploy

---
