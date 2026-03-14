#  Hệ thống Quản lý Thư viện Đại học

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google_Gemini-4285F4?style=for-the-badge&logo=google&logoColor=white)

**Ứng dụng web quản lý thư viện trường Đại học — xây dựng bằng Vibe Coding với Google AI Studio**

[Demo trực tiếp](https://jaydenb127.github.io/Management-library-system-vibe-coding2) · [ Báo cáo](#) · [ Báo lỗi](../../issues)

</div>

---

##  Giới thiệu

Đây là bài tập **Vibe Coding 2** — xây dựng hệ thống quản lý thư viện đại học hoàn chỉnh bằng cách sử dụng AI tools (Google AI Studio - Gemini 2.5 Pro & Claude) để sinh code từ prompt kỹ thuật.

Ứng dụng chạy hoàn toàn trên **client-side** (Single Page Application), không cần backend, dữ liệu được lưu trữ qua `localStorage`.

---

##  Tính năng

###  Xác thực & Phân quyền
- Đăng nhập với 2 vai trò: **Admin** và **Thủ thư**
- Phân quyền giao diện theo vai trò (Admin thấy đầy đủ chức năng)

###  Quản lý Độc giả
- Đăng ký, sửa, xóa thẻ thư viện sinh viên
- Tìm kiếm & lọc theo lớp, giới tính, trạng thái
- In thẻ thư viện
- Xem lịch sử mượn trả

###  Quản lý Sách
- Quản lý đầu sách (thêm, sửa, xóa) theo chuyên ngành
- Quản lý bản sao từng đầu sách với trạng thái thời gian thực
- Tìm kiếm theo tên sách, tác giả, nhà xuất bản

###  Quản lý Mượn / Trả
- Tạo phiếu mượn với kiểm tra ràng buộc nghiệp vụ
- Xử lý trả sách, tự động tính ngày trễ hạn
- Danh sách phiếu mượn với lọc và tìm kiếm

###  Báo cáo thống kê
- Top đầu sách được mượn nhiều nhất (biểu đồ)
- Danh sách độc giả chưa trả sách
- Dashboard tổng quan với số liệu realtime

### ⚙️ Quản lý Người dùng *(Admin only)*
- Thêm, sửa, xóa tài khoản thủ thư
- Kích hoạt / khóa tài khoản

### UI/UX
- Dark / Light mode
- Responsive (mobile, tablet, desktop)
- Toast notifications
- Badge cảnh báo sách quá hạn

---

## Chạy ứng dụng

### Cách 1: Mở trực tiếp (đơn giản nhất)
```bash
# Chỉ cần mở file index.html bằng trình duyệt
# Không cần cài đặt gì thêm
```

### Cách 2: Chạy với Vite (development)

**Yêu cầu:** Node.js >= 18

```bash
# 1. Clone repo
git clone https://github.com/your-username/library-management.git
cd library-management

# 2. Cài dependencies
npm install

# 3. Tạo file .env.local và thêm API key
cp .env.example .env.local
# Điền GEMINI_API_KEY vào .env.local

# 4. Chạy dev server
npm run dev
```

Mở trình duyệt tại `http://localhost:3000`

---

## Tài khoản mặc định

| Vai trò | Username | Password |
|---------|----------|----------|
| Admin | `admin` | `admin123` |
| Thủ thư | `thuthu1` | `123456` |

---

##  Công nghệ sử dụng

| Công nghệ | Mục đích |
|-----------|----------|
| HTML5 / CSS3 / JavaScript (ES6+) | Nền tảng SPA |
| Tailwind CSS (CDN) | Giao diện responsive |
| Chart.js (CDN) | Biểu đồ thống kê |
| Font Awesome | Icon |
| localStorage | Lưu trữ dữ liệu client-side |
| Google AI Studio (Gemini 3.1 Pro) | Triển khai ý tưởng sinh code và fix bug |
| Qwen Plus 3.5| Đề xuất cách giải quyết các lỗi bổ sung thêm các chức năng bổ sung |
| Claude (Anthropic) | Phân tích yêu cầu & viết prompt |
| Vite + React + TypeScript | Build tooling |

---

##  Cấu trúc dự án

```
library-management/
├── index.html          # Toàn bộ ứng dụng SPA (HTML + CSS + JS)
├── src/
│   ├── App.tsx         # React entry (scaffold mặc định)
│   ├── main.tsx
│   └── index.css
├── .env.example        # Template biến môi trường
├── package.json        
├── vite.config.ts      
└── README.md
```

> **Lưu ý:** Toàn bộ logic ứng dụng nằm trong `index.html`. Thư mục `src/` là scaffold mặc định từ Vite, không ảnh hưởng đến chức năng chính.

---

##  Mô hình dữ liệu

```
Users ──────────────── PhieuMuon
DocGia ─────────────── PhieuMuon
BanSao ─────────────── PhieuMuon
DauSach ────────────── BanSao
ChuyenNganh ────────── DauSach
```

Dữ liệu được lưu trong `localStorage` với key `lib_sys_data`, tự động khởi tạo dữ liệu mẫu khi chạy lần đầu.

---

##  Nhóm thực hiện

| STT | Họ tên | MSSV | Vai trò |
|-----|--------|------|---------|
| 1 | Bùi Thành Đạt | 23724811| Nhóm trưởng |
| 2 | Lê Ngọc Huy | 23727381 | Thành viên |
| 3 | Bùi Huy Bảo | 2372061 | Thành viên |
| 4 | La Thiên Bảo | 23723801 | Thành viên |

---

##  Quy trình Vibe Coding

```
1. Đọc & phân tích đề bài
        ↓
2. Xác định Actor, Use Case, Data Model
        ↓
3. Viết prompt kỹ thuật chi tiết (với Claude)
        ↓
4. Sinh code MVP với Google AI Studio (Gemini 3.1 Pro)
        ↓
5. Kiểm thử từng chức năng trên trình duyệt
        ↓
6. Phản hồi lỗi → AI fix → lặp lại
        ↓
7. Deploy GitHub Pages + nộp báo cáo
```

---

##  License

MIT License — Bài tập học thuật, vui lòng không sử dụng cho mục đích thương mại.
