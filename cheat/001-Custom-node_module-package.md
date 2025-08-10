
# Hướng dẫn sử dụng patch-package để tùy biến package trong node_modules

## 1. Cài đặt & chuẩn bị
```bash
# Cài patch-package và postinstall-postinstall
npm i -D patch-package postinstall-postinstall

# Thêm script vào package.json
{
  "scripts": {
    "postinstall": "patch-package"
  }
}
```

> Luôn commit thư mục `patches/` vào git.

---

## 2. Quy trình chuẩn 5 bước

1. **Cài đúng phiên bản** package cần vá (ví dụ: `react-native-track-player@4.1.0`).
2. **Chỉnh sửa trực tiếp** file trong `node_modules/<package>/...` (vào đúng file build app đang dùng).
3. **Tạo patch**:
```bash
npx patch-package react-native-track-player
```
→ Sinh file `patches/react-native-track-player+4.1.0.patch`.
4. **Hoàn nguyên node_modules** (nếu muốn test patch):
```bash
rm -rf node_modules package-lock.json
npm i
```
5. **Kiểm tra**: build/chạy lại. Nếu OK → commit `patches/`.

---

## 3. Ví dụ vá: Guard import khi chạy trong Node
**Mục tiêu:** Tránh EAS/Expo import module native khi đọc config.

- Sửa `node_modules/react-native-track-player/lib/index.js`:
```js
let TrackPlayer;
try {
  if (typeof navigator !== 'undefined' && navigator.product === 'ReactNative') {
    const mod = require('./trackPlayer');
    TrackPlayer = mod?.default ?? mod;
  } else {
    TrackPlayer = {};
  }
} catch {
  TrackPlayer = {};
}

module.exports = TrackPlayer;
module.exports.default = TrackPlayer;
```

- Tạo patch:
```bash
npx patch-package react-native-track-player
```

---

## 4. Mẹo & lưu ý quan trọng

- **Đúng phiên bản**: Patch gắn với version cụ thể. Nâng version → patch có thể không áp dụng.
- **Vá ở file build**, không phải source TS.
- **Line endings (Windows)**: Lỗi CRLF/LF có thể làm patch fail.
- **Nhiều file/nhiều package**: Tạo patch riêng cho từng package.
- **Monorepo**: Tạo patch ở root workspace.
- **Gỡ patch**: Xóa file `.patch` trong `patches/` rồi cài lại deps.
- **Kiểm tra patch**: Xóa `node_modules` + cài lại.

---

## 5. Quy trình chuẩn cho CI/CD

- Commit `patches/` + `package.json` (có script postinstall).
- Trên CI:
```bash
npm ci  # hoặc npm i
```
- Postinstall sẽ tự áp patch.

---

## 6. Checklist nhanh

- [ ] Cài patch-package + postinstall-postinstall
- [ ] Sửa file trong node_modules
- [ ] Tạo patch
- [ ] Commit patches/
- [ ] Test xóa node_modules + cài lại
- [ ] Khi nâng version → tạo patch mới
