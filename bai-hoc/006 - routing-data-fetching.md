
# 📘 Ngày 6 – Routing & Data Fetching với React Router v6.4+

## I. Giới thiệu về React Router

React Router là thư viện routing phổ biến nhất cho SPA (Single Page App) trong React.

- Quản lý URL → component mapping
- Hỗ trợ nested route, dynamic route, lazy loading, loader, error boundary...

---

## II. Cài đặt và setup cơ bản

```bash
npm install react-router-dom
```

### Cấu trúc router cơ bản:
```jsx
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

const router = createBrowserRouter([
  { path: "/", element: <Home /> },
  { path: "/about", element: <About /> },
]);

<RouterProvider router={router} />
```

---

## III. Nested Route & Layouts

### Nested Route:
```jsx
const router = createBrowserRouter([
  {
    path: "/dashboard",
    element: <DashboardLayout />,
    children: [
      { path: "profile", element: <Profile /> },
      { path: "settings", element: <Settings /> },
    ]
  }
]);
```

- `DashboardLayout` sẽ hiển thị phần `outlet` cho các trang con.

```jsx
import { Outlet } from 'react-router-dom';
const DashboardLayout = () => (
  <div>
    <Sidebar />
    <Outlet />
  </div>
);
```

---

## IV. Data Fetching – Loader & useLoaderData

### Route có loader:
```js
{
  path: "/posts",
  element: <PostList />,
  loader: async () => fetch("/api/posts").then(res => res.json())
}
```

### Trong component:
```jsx
const posts = useLoaderData();
```

> Loader giúp fetch dữ liệu **trước khi render**, hỗ trợ SSR/SSG dễ dàng hơn.

---

## V. Lazy Loading Components

```jsx
const Post = lazy(() => import("./Post"));
<Route path="post" element={<Suspense fallback={<Loading />}><Post /></Suspense>} />
```

- Giúp **tối ưu hiệu suất**, chỉ tải code khi cần.

---

## VI. useNavigate, useParams

```jsx
const navigate = useNavigate();
navigate("/profile");

const { id } = useParams();
```

- `useNavigate`: điều hướng bằng code.
- `useParams`: lấy biến từ URL (ví dụ `/post/:id`)

---

## VII. Error Boundary

```js
{
  path: "/admin",
  element: <AdminPage />,
  errorElement: <ErrorPage />
}
```

> Khi có lỗi trong loader hoặc rendering → tự động render `errorElement`.

---

## VIII. Thực hành

1. Tạo routing có layout `MainLayout` và nested routes: Home, Blog, Contact.
2. Thêm loader vào route Blog để fetch danh sách bài viết từ API.
3. Dùng useNavigate để chuyển trang sau khi form submit.

---

## IX. Quiz ôn tập

1. `Outlet` trong React Router dùng để làm gì?
2. Khi nào nên dùng `useLoaderData`?
3. Phân biệt `useNavigate` và `<Link>`?
4. Lazy loading giúp ích gì cho hiệu suất?
5. Nested route hoạt động thế nào trong layout?

---

**Tổng kết:** Ngày 6 giúp bạn nắm vững cách tổ chức route hiện đại với React Router v6.4+: loader, nested, lazy loading và xử lý lỗi – giúp xây dựng kiến trúc routing sạch, hiệu suất và dễ bảo trì.
