# design.md — Bản đồ giao diện & màn hình (nightlife.hn)

> Catalog toàn bộ màn hình mockup của **nightlife.hn** (Phương án C — *Daylight Discovery*).
> Nguồn chân lý thiết kế: [`Design System - Phương án C.md`](Design%20System%20-%20Ph%C6%B0%C6%A1ng%20%C3%A1n%20C.md). Kế hoạch gốc: [`Kế hoạch giao diện - NightLife.md`](K%E1%BA%BF%20ho%E1%BA%A1ch%20giao%20di%E1%BB%87n%20-%20NightLife.md).
> Cập nhật: 23/06/2026 — đợt dựng bổ sung Đối tác + Admin + màn hệ thống.

---

## 0. Tổng quan

- Đây là **prototype bấm-được** (clickable), mỗi màn là **một file HTML rời** trong `app/`, dùng framework `x-dc` + [`support.js`](support.js), dữ liệu/logic chung trong [`app/shared.js`](app/shared.js). **Chỉ inline style**, nội dung tiếng Việt có dấu.
- **3 nhóm người dùng (actor) + 1 nhóm hệ thống:**
  1. **Khách (Public)** — `app/desktop/` + `app/mobile/`
  2. **Đối tác (Partner)** — `app/partner/desktop/` + `app/partner/mobile/`
  3. **Admin (CMS)** — `app/admin/desktop/` + `app/admin/mobile/`
  4. **Hệ thống / Lỗi / Thông báo** — `app/system/` (phía khách) + `app/admin/desktop/loi-*.html`, `thong-bao.html` (phía admin)
- **Điểm vào (hub):** mở [`index.html`](index.html) → mục lục bấm vào từng cụm. Mọi màn dưới đây đều có link mở trực tiếp.
- Mỗi màn dựng **song song desktop (1100–1180px) + mobile (frame 390px + status bar + bottom nav)**. Trạng thái: ✅ đã có từ trước · 🆕 dựng mới đợt này.

---

## 1. Cấu trúc thư mục

```
app/
├── shared.js                # dữ liệu + helper dùng chung (NL.VENUES, NL.CAST, NL.RANK, fav, booking…)
├── desktop/   (20)          # Khách — desktop
├── mobile/    (20)          # Khách — mobile (frame 390px + bottom nav)
├── partner/
│   ├── desktop/ (5)         # Đối tác — desktop (sidebar CMS)
│   └── mobile/  (5)         # Đối tác — mobile (có màn quét QR camera nền tối)
├── admin/
│   ├── desktop/ (17)        # Admin CMS — desktop (12 màn + login + 4 màn hệ thống admin)
│   └── mobile/  (12)        # Admin CMS — mobile
└── system/    (6)           # Màn hệ thống/lỗi phía khách (desktop + mobile cạnh nhau)
```

---

## 2. KHÁCH — Public

| # | Màn hình | Desktop | Mobile | Feature | Trạng thái |
|---|----------|---------|--------|---------|------------|
| P1 | Trang chủ | [mở](app/desktop/trang-chu.html) | [mở](app/mobile/trang-chu.html) | WEB-01..07 | ✅ |
| P2 | Tìm quán — danh sách + lọc | [mở](app/desktop/danh-sach-quan.html) | [mở](app/mobile/danh-sach-quan.html) | SEA-01..05 | ✅ |
| P3 | Bảng xếp hạng | [mở](app/desktop/xep-hang.html) | [mở](app/mobile/xep-hang.html) | RAN-01..03 | ✅ |
| P4 | Chi tiết quán | [mở](app/desktop/chi-tiet-quan.html) | [mở](app/mobile/chi-tiet-quan.html) | STO-01..11 | ✅ |
| P5 | Tìm Cast — danh sách | [mở](app/desktop/danh-sach-cast.html) | [mở](app/mobile/danh-sach-cast.html) | SEA-01, CAS-07 | ✅ |
| P6 | Chi tiết Cast | [mở](app/desktop/chi-tiet-cast.html) | [mở](app/mobile/chi-tiet-cast.html) | CAS-01..11 | ✅ |
| P7 | Đặt chỗ (form) | [mở](app/desktop/dat-cho.html) | [mở](app/mobile/dat-cho.html) | BOO-01..03 | ✅ |
| P8 | Xác nhận đặt chỗ | [mở](app/desktop/xac-nhan.html) | [mở](app/mobile/xac-nhan.html) | BOO-06 | ✅ |
| P8b | Lịch sử đặt chỗ (3 trạng thái) | [mở](app/desktop/lich-su-dat-cho.html) | [mở](app/mobile/lich-su-dat-cho.html) | BOO-06 | ✅ |
| **P9** | **Chi tiết mã / QR (Coupon)** | [mở](app/desktop/chi-tiet-ma.html) | [mở](app/mobile/chi-tiet-ma.html) | MEM-03,04 | 🆕 |
| P10 | Ví ưu đãi (coupon của tôi) | [mở](app/desktop/vi-uu-dai.html) | [mở](app/mobile/vi-uu-dai.html) | MEM-04B,06 | ✅ |
| P11 | Ưu đãi / Sự kiện | [mở](app/desktop/uu-dai.html) | [mở](app/mobile/uu-dai.html) | STO-08 | ✅ |
| P12 | Đăng nhập / Đăng ký | [mở](app/desktop/dang-nhap.html) | [mở](app/mobile/dang-nhap.html) | MEM-01 | ✅ |
| P13 | Tài khoản của tôi | [mở](app/desktop/tai-khoan.html) | [mở](app/mobile/tai-khoan.html) | MEM-02,07 | ✅ |
| **P14** | **Gửi hóa đơn (Bill) + lịch sử duyệt** | [mở](app/desktop/gui-hoa-don.html) | [mở](app/mobile/gui-hoa-don.html) | BIL-01..04 | 🆕 |
| **P15** | **Blog — danh sách** | [mở](app/desktop/blog.html) | [mở](app/mobile/blog.html) | CON-01 | 🆕 |
| **P16** | **Blog — chi tiết** | [mở](app/desktop/blog-chi-tiet.html) | [mở](app/mobile/blog-chi-tiet.html) | CON-02 | 🆕 |
| **P17** | **Đăng ký đối tác (Join Us)** | [mở](app/desktop/dang-ky-doi-tac.html) | [mở](app/mobile/dang-ky-doi-tac.html) | PAR-01 | 🆕 |
| **P18** | **Trang pháp lý (Legal)** | [mở](app/desktop/legal.html) | [mở](app/mobile/legal.html) | CON-04 | 🆕 |
| **P19** | **Đã lưu / Yêu thích** | [mở](app/desktop/da-luu.html) | [mở](app/mobile/da-luu.html) | STO-06, CAS-03 | 🆕 |

**Ghi chú P9–P19 (đợt mới):**
- **P9** thẻ coupon lớn: ảnh QR, mức giảm theo hạng (Guest 5% / Member 8% / VIP 10%), hạn dùng đếm ngược, trạng thái *Đang giữ chỗ*, hướng dẫn đưa mã cho nhân viên quét, nút *Lưu vào ví*.
- **P14** form gửi hóa đơn (quán/số tiền/thời gian bắt buộc; ảnh chứng từ khuyến khích) + lưu ý *gửi trong 10 ngày, chỉ tổng tiền* + lịch sử bill (Pending / Đã duyệt +điểm / Bị từ chối + lý do + nút *Gửi lại*).
- **P15/P16** blog SEO: lưới card + filter chuyên mục; chi tiết có cột "bài liên quan / quảng cáo quán".
- **P17** landing lợi ích + form đăng quán (*không yêu cầu giấy phép*).
- **P18** 1 cột dễ đọc + mục lục anchor (desktop).
- **P19** tab Quán/Cast, card có nút tim đỏ, kèm trạng thái rỗng minh họa.

---

## 3. ĐỐI TÁC — Partner (P0)

> Layout desktop = khung CMS sidebar 230px + main. Mobile = frame 390px + bottom nav 4 mục. Đối tác **chỉ xem dữ liệu tổng hợp của quán mình**, không xem thông tin khách chi tiết.

| # | Màn hình | Desktop | Mobile | Feature | Trạng thái |
|---|----------|---------|--------|---------|------------|
| PA1 | Đăng nhập đối tác | [mở](app/partner/desktop/dang-nhap.html) | [mở](app/partner/mobile/dang-nhap.html) | PAR-04 | 🆕 |
| PA2 | Dashboard tối thiểu | [mở](app/partner/desktop/dashboard.html) | [mở](app/partner/mobile/dashboard.html) | PAR-08 | 🆕 |
| PA3 | Quét / xác nhận mã QR | [mở](app/partner/desktop/quet-qr.html) | [mở](app/partner/mobile/quet-qr.html) | MEM-05B | 🆕 |
| PA4 | Đối soát dịch vụ đã dùng | [mở](app/partner/desktop/doi-soat.html) | [mở](app/partner/mobile/doi-soat.html) | PAR-04 | 🆕 |
| PA5 | Đăng / cập nhật thông tin (chờ duyệt) | [mở](app/partner/desktop/dang-tin.html) | [mở](app/partner/mobile/dang-tin.html) | PAR-04B | 🆕 |

- **PA2**: 3 thẻ (Đặt chỗ tại quán · Lượt xem · Khách đến) + biểu đồ cột 7 ngày + ghi chú quyền dữ liệu.
- **PA3**: khung quét QR (mobile = camera nền tối `#16121f`, 4 góc tím) → panel kết quả "Mã hợp lệ — Đang giữ chỗ" → *Xác nhận đã dùng* / *Từ chối*.
- **PA4**: tab kỳ (Hôm nay/7 ngày/30 ngày) + bảng/list mã đã xác nhận + dòng tổng.
- **PA5**: form quán + cast (ngày sinh→tuổi tự tính, **không lịch trống**) + upload ảnh/video + banner *Chờ Admin duyệt*.

---

## 4. ADMIN — CMS

> Layout chuẩn: sidebar 236px (12 mục, nhóm VẬN HÀNH / NỘI DUNG / PHÂN TÍCH) + topbar (title · search · chuông · avatar) + vùng nội dung. Desktop-first; mobile rút gọn để xem cơ bản (top app bar + bottom nav 5 mục: Tổng quan · Booking · Bill · Đối tác · Thêm).

| # | Màn hình | Desktop | Mobile | Feature | Trạng thái |
|---|----------|---------|--------|---------|------------|
| AD1 | Dashboard (tổng quan) | [mở](app/admin/desktop/dashboard.html) | [mở](app/admin/mobile/dashboard.html) | ADM-01 | 🆕 |
| AD2 | CRUD Quán / Địa điểm | [mở](app/admin/desktop/quan.html) | [mở](app/admin/mobile/quan.html) | ADM-02 | 🆕 |
| AD3 | CRUD Cast | [mở](app/admin/desktop/cast.html) | [mở](app/admin/mobile/cast.html) | ADM-03 | 🆕 |
| AD4 | Thư viện Media | [mở](app/admin/desktop/media.html) | [mở](app/admin/mobile/media.html) | ADM-04 | 🆕 |
| AD5 | Campaign / Discount / Banner | [mở](app/admin/desktop/campaign.html) | [mở](app/admin/mobile/campaign.html) | ADM-06 | 🆕 |
| AD6 | Ranking control thủ công | [mở](app/admin/desktop/ranking.html) | [mở](app/admin/mobile/ranking.html) | ADM-07 | 🆕 |
| AD7 | Quản lý Booking (3 trạng thái) | [mở](app/admin/desktop/booking.html) | [mở](app/admin/mobile/booking.html) | BOO-06 | 🆕 |
| AD8 | Duyệt / Từ chối Bill (+ lý do) | [mở](app/admin/desktop/bill.html) | [mở](app/admin/mobile/bill.html) | BIL-04,05 | 🆕 |
| AD9 | Báo cáo doanh thu | [mở](app/admin/desktop/bao-cao.html) | [mở](app/admin/mobile/bao-cao.html) | BIL-06, ADM-09 | 🆕 |
| AD10 | Duyệt đối tác | [mở](app/admin/desktop/doi-tac.html) | [mở](app/admin/mobile/doi-tac.html) | PAR-02 | 🆕 |
| AD11 | CMS Blog / Nội dung | [mở](app/admin/desktop/blog.html) | [mở](app/admin/mobile/blog.html) | CON-01 | 🆕 |
| AD12 | Membership & điểm | [mở](app/admin/desktop/membership.html) | [mở](app/admin/mobile/membership.html) | ADM-08 | 🆕 |
| — | Đăng nhập Admin | [mở](app/admin/desktop/dang-nhap.html) | — | — | 🆕 |

- **AD6 Ranking**: 2 hàng tab (khu vực × Cast/Quán), Top 5 có handle kéo-thả + vương miện màu + badge *Tài trợ*; ưu tiên **Cast trước → Quán**.
- **AD8 Bill**: tab Chờ duyệt / Đã duyệt / Bị từ chối; nút *Duyệt* + *Từ chối* (mở ô nhập **lý do**); KPI doanh thu/hoa hồng/giảm.
- **AD9 Báo cáo**: tab Gộp / Thuần / Hoa hồng / Giảm giá; bộ lọc ngày → quán → mã; KPI + biểu đồ + bảng + nút *Xuất Excel/PDF* (giả lập).
- **AD7 Booking**: điều phối qua **LINE** (kênh liên hệ Admin đã chốt).

---

## 5. HỆ THỐNG · LỖI · THÔNG BÁO

### 5.1 Phía Khách — `app/system/` (mỗi file gồm cả desktop + mobile cạnh nhau)

| Màn | File | Nội dung |
|-----|------|----------|
| 403 — Truy cập bị từ chối | [mở](app/system/loi-403.html) | "Bạn không có quyền truy cập" + nút Đăng nhập / Về trang chủ |
| 404 — Không tìm thấy | [mở](app/system/loi-404.html) | "Không tìm thấy trang" + ô tìm kiếm + Về trang chủ |
| 500 — Lỗi máy chủ | [mở](app/system/loi-500.html) | Lỗi máy chủ + mã sự cố + nút Thử lại |
| Đang bảo trì | [mở](app/system/bao-tri.html) | Trang bảo trì + thời gian dự kiến + liên hệ LINE |
| Popup & Toast (showcase) | [mở](app/system/popup-toast.html) | Modal Thành công/Cảnh báo/Lỗi/Xác nhận + 4 loại toast |
| Loading & Empty (showcase) | [mở](app/system/loading-empty.html) | Skeleton shimmer + các trạng thái rỗng (chưa đặt chỗ / chưa lưu / không kết quả / ví trống) |

### 5.2 Phía Admin — `app/admin/desktop/` (trong khung admin)

| Màn | File | Nội dung |
|-----|------|----------|
| 403 — Admin (không đủ quyền) | [mở](app/admin/desktop/loi-403.html) | Chặn theo vai trò (vd Biên tập viên không vào được Báo cáo) + Yêu cầu cấp quyền |
| 404 — Admin | [mở](app/admin/desktop/loi-404.html) | Không tìm thấy trang quản trị |
| 500 — Admin | [mở](app/admin/desktop/loi-500.html) | Lỗi hệ thống + mã sự cố (ERR-…) + Tải lại / Báo kỹ thuật |
| Trung tâm thông báo & lỗi Admin | [mở](app/admin/desktop/thong-bao.html) | Danh sách thông báo (đối tác/bill/booking chờ) + banner lỗi/cảnh báo (mất kết nối, lưu thất bại, hết phiên) + toast admin |

---

## 6. Tổng kết đợt dựng mới (🆕 = 59 file)

| Cụm | Desktop | Mobile | Tổng |
|-----|---------|--------|------|
| Khách (P9, P14, P15, P16, P17, P18, P19) | 7 | 7 | 14 |
| Đối tác (PA1–PA5) | 5 | 5 | 10 |
| Admin (AD1–AD12 + login) | 13 | 12 | 25 |
| Hệ thống khách (`app/system/`) | 6 (gồm cả mobile trong cùng file) | — | 6 |
| Hệ thống admin (403/404/500/thông báo) | 4 | — | 4 |
| **Tổng** | | | **59** |

Hub [`index.html`](index.html) đã bổ sung 4 mục mới: *Khách — màn bổ sung · Đối tác (Partner) · Admin CMS · Hệ thống · Lỗi · Thông báo*.

---

## 7. Điều hướng (wiring)

- **index.html** là hub mở mọi cụm.
- **Khách**: header (Trang chủ · Tìm quán · Cast · Bảng xếp hạng · Tour · Blog) + bottom nav mobile (Trang chủ · Cast · Ưu đãi · Đặt chỗ · Tài khoản). Các màn mới nối link nội bộ (blog → blog-chi-tiet, chi-tiet-ma → vi-uu-dai…).
- **Đối tác**: sidebar (Tổng quan · Quét mã QR · Đối soát · Đăng thông tin · Cài đặt) / bottom nav 4 mục.
- **Admin**: sidebar 12 mục đồng nhất giữa mọi trang (chỉ đổi mục active) / bottom nav 5 mục.

> Gợi ý hoàn thiện thêm (không bắt buộc): cập nhật header các trang Khách cũ để link "Blog"/"Đăng ký đối tác" trỏ thẳng vào màn mới; bổ sung mục "Đã lưu" vào bottom nav mobile.

---

## 8. Ngoài phạm vi đợt này (P1/P2 — làm sau)

| # | Màn | Phase |
|---|-----|-------|
| P20 | Tour — chi tiết | P2 |
| — | Chat realtime (nhắn tin Cast) | P1 |
| — | Đổi quà bằng điểm | P1 |
| — | Video trang chủ nâng cao, paid ranking tự động | P1/P2 |

> Toàn bộ ràng buộc thiết kế (màu, font, spacing, component, tab khu vực, ranking Top 5, bỏ lịch trống Cast…) tuân theo [`Design System - Phương án C.md`](Design%20System%20-%20Ph%C6%B0%C6%A1ng%20%C3%A1n%20C.md).
