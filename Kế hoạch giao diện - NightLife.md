# Kế hoạch giao diện chi tiết — NightLife Vietnam

> Lập từ tài liệu **"Tổng hợp tính năng & Phân chia Phase v2.2"** (21/06/2026).
> Phong cách UI: tuân thủ **`Design System - Phương án C.md`**. Mọi màn đều có **bản desktop + bản mobile** (mobile-first theo WEB-07).
> Trạng thái dựng: ✅ đã có · ✏️ đã có nhưng cần sửa · 🆕 cần dựng mới.

---

## I. Nguyên tắc chung

1. **Mobile-first.** Trang chủ & các màn chuyển đổi ưu tiên ranking + CTA nhanh (WEB-07). Mỗi màn dựng song song desktop (1100px) và mobile (390px + bottom nav + status bar).
2. **Sàn trung gian, KHÔNG e-commerce** (Baseline §1): không giỏ hàng, không thanh toán, không đặt món. Menu/bảng giá chỉ để tham khảo. CTA chính = **Booking** và **Lấy mã/Coupon**.
3. **3 actor → 3 cụm giao diện:** Khách (Public), Đối tác (Partner — P0), Admin (CMS). Mỗi cụm có hệ điều hướng riêng.
4. **Tab khu vực nhất quán:** Tất cả · Hà Nội · TP.HCM · Đà Nẵng · Hải Phòng (SEA-02, RAN-01). Ranking giới hạn **Top 1–5** mỗi khu vực, ưu tiên **Cast trước rồi Quán** (RAN-08).
5. **Telegram-first** cho mọi thông báo vận hành (NOT-01..03).

---

## II. Bản đồ màn hình (Screen Inventory)

### A. KHÁCH — Public (P0 trừ khi ghi khác)

| # | Màn hình | Feature ID | Phase | Trạng thái |
|---|---|---|---|---|
| P1 | Trang chủ | WEB-01..07 | P0 | ✅ (đã tối ưu) |
| P2 | Tìm quán — kết quả + bộ lọc | SEA-01..05 | P0 | ✅ |
| P3 | **Trang Xếp hạng (Ranking Page)** | RAN-01..03 | P0 | 🆕 |
| P4 | Chi tiết quán (Store Detail) | STO-01..11 | P0 | ✏️ (thêm album+video, giá, ngôn ngữ NV) |
| P5 | Tìm Cast — danh sách | SEA-01, CAS-07 | P0 | ✅ |
| P6 | Chi tiết Cast (Cast Profile) | CAS-01..11 | P0 | ✏️ (**bỏ lịch trống**, thêm album+video) |
| P7 | **Booking — form đặt chỗ** (chung quán/cast) | BOO-01..03, CAS-05 | P0 | 🆕 |
| P8 | **Xác nhận booking + Lịch sử đặt chỗ** (3 trạng thái) | BOO-06 | P0 | 🆕 |
| P9 | **Coupon/QR — chi tiết mã** (ảnh QR, hạn dùng, trạng thái) | MEM-03,04 | P0 | 🆕 |
| P10 | **Ví ưu đãi — coupon của tôi** (đang giữ chỗ / đã dùng) | MEM-04B,06 | P0 | 🆕 |
| P11 | Ưu đãi / Sự kiện / Campaign | STO-08 | P0 | ✅ |
| P12 | Đăng nhập / Đăng ký | MEM-01 | P0 | ✅ |
| P13 | **Tài khoản của tôi** (hồ sơ, hạng, điểm, lịch sử) | MEM-02,07 | P0 | 🆕 |
| P14 | **Gửi hóa đơn (Bill)** + trạng thái duyệt | BIL-01..04 | P0 | 🆕 |
| P15 | Blog — danh sách | CON-01 | P0 | 🆕 |
| P16 | Blog — chi tiết | CON-02 | P0 | 🆕 |
| P17 | Đăng ký đối tác — "Join Us" | PAR-01 | P0 | 🆕 |
| P18 | Trang Legal (bảo mật, điều khoản) | CON-04 | P0 | 🆕 |
| P19 | Đã lưu / Favorite | STO-06, CAS-03 | P1 | 🆕 (P1) |
| P20 | Tour — chi tiết | CON-03 | P2 | ⏳ (P2) |

### B. ĐỐI TÁC — Partner (đã chuyển **P0**)

| # | Màn hình | Feature ID | Phase | Trạng thái |
|---|---|---|---|---|
| PA1 | Đăng nhập đối tác | PAR-04 | P0 | 🆕 |
| PA2 | Dashboard tối thiểu (đặt chỗ tại quán, lượt xem, số khách đến) | PAR-08 | P0 | 🆕 |
| PA3 | **Quét QR / xác nhận mã** giảm giá tại quán | MEM-05B | P0 | 🆕 |
| PA4 | Đối soát dịch vụ đã sử dụng | PAR-04 | P0 | 🆕 |
| PA5 | Đăng / cập nhật thông tin quán + cast (chờ Admin duyệt) | PAR-04B | P0 | 🆕 |

### C. ADMIN — CMS

| # | Màn hình | Feature ID | Phase | Trạng thái |
|---|---|---|---|---|
| AD1 | Dashboard (quán, cast, booking, bill, alert) | ADM-01 | P0 | 🆕 |
| AD2 | CRUD địa điểm (info, giá, giờ, ảnh, maps) | ADM-02 | P0 | 🆕 |
| AD3 | CRUD cast (hồ sơ, ảnh/video, tags) | ADM-03 | P0 | 🆕 |
| AD4 | Thư viện media | ADM-04 | P0 | 🆕 |
| AD5 | Quản lý campaign / discount / banner | ADM-06 | P0 | 🆕 |
| AD6 | **Ranking control thủ công** (Cast trước → Quán) | ADM-07 | P0 | 🆕 |
| AD7 | Quản lý booking (3 trạng thái) | BOO-06 | P0 | 🆕 |
| AD8 | **Duyệt/từ chối Bill** (có lý do) + doanh thu/hoa hồng | BIL-04,05, ADM-09 | P0 | 🆕 |
| AD9 | **Báo cáo doanh thu** (gộp/thuần/hoa hồng/giảm; ngày→quán→mã→khác) | BIL-06, ADM-09B | P0 | 🆕 |
| AD10 | Duyệt đối tác (Partner approval) | PAR-02 | P0 | 🆕 |
| AD11 | CMS Blog / nội dung | CON-01 | P0 | 🆕 |
| AD12 | Membership & point management | ADM-08 | P1 | ⏳ (P1) |

> **P0 cần dựng mới (ưu tiên):** P3, P4✏️, P6✏️, P7, P8, P9, P10, P13, P14, P15, P16, P17, P18 · PA1–PA5 · AD1–AD11.

---

## III. Chi tiết từng màn (P0 — Khách)

> Component & token viện dẫn theo Design System: Header §5.11, Card §5.5, Pill/Tab §5.3, Ranking row §5.7, Search §5.8, Bottom nav §5.13, Phụ lục Mobile A.

### P3 · Trang Xếp hạng (Ranking Page) 🆕
**Mục tiêu:** trang xếp hạng đầy đủ (khác block ranking ở trang chủ), mô hình quảng cáo/VIP.
- **Desktop:** Header → tiêu đề "Bảng xếp hạng" → **2 hàng tab**: (1) khu vực (Tất cả·HN·HCM·ĐN·HP); (2) danh mục (Karaoke·Bar·Massage·Nhà hàng·Casino). Toggle **Cast / Quán** (mặc định Cast trước). Thanh kỳ "Tháng X · cập nhật". Danh sách **Top 1–5** dạng ranking row §5.7 (vương miện vàng/bạc/đồng/lá/dương) — mỗi card có nút **Xem chi tiết** + **Gọi ngay** (click-to-call, RAN-03). Có badge "Tài trợ" cho quán trả phí.
- **Mobile:** tab khu vực cuộn ngang; danh mục là hàng chip cuộn ngang; toggle Cast/Quán; list dọc Top 5; nút Gọi + Chi tiết trên mỗi dòng.
- **Data:** rank, ảnh, tên, khu vực, danh mục, chỉ số (stars/hearts/views — P1, MVP để manual), cờ tài trợ.
- **States:** tab active; trạng thái rỗng "Chưa có dữ liệu khu vực này".

### P4 · Chi tiết quán (Store Detail) ✏️
**Bổ sung so với bản đã dựng:**
- **Album ảnh + Video (P0, STO-11):** thêm tab/section gallery có video (gắn link YouTube/TikTok hoặc upload) + lightbox/swipe.
- **Đặc điểm nhân sự (STO-04):** khối "tỷ lệ quốc tịch + khả năng ngôn ngữ" (vd: 60% nói tiếng Nhật) — rất quan trọng với khách Nhật.
- **Bảng giá (STO-07):** phí hệ thống/phòng/đồ uống/phụ thu/thuế — **chỉ hiển thị tham khảo**, kèm dòng "Giá tham khảo, không đặt món trên web".
- **Campaign/first-time offer (STO-08):** banner ưu đãi + thời gian áp dụng.
- **CTA:** "Đặt chỗ" (→ P7) + "Lấy mã ưu đãi" (→ P9) + SĐT click-to-call. Booking gửi Admin điều phối (STO-09), KHÔNG gửi thẳng quán.
- Giữ: breadcrumb, giờ mở/đóng + ngày nghỉ (STO-02), địa chỉ + Google Maps (STO-03), cast grid (STO-05), đánh giá, gợi ý quán liên quan (STO-10).
- **Mobile:** ảnh hero + carousel; sheet thông tin bo góc; **CTA booking sticky đáy** (BOO-02).

### P6 · Chi tiết Cast (Cast Profile) ✏️
**Sửa bắt buộc theo bản chốt:**
- ❌ **BỎ "Lịch trống tuần này"** — bản đã dựng đang hiển thị lịch; tài liệu mục 33/CAS-04 chốt **KHÔNG hiển thị lịch trống** (khó kiểm soát). Cần gỡ khối này ở cả desktop & mobile.
- ➕ **Album ảnh + Video (P0):** gallery đa góc + lightbox/swipe (CAS-09), cho gắn link/upload video.
- ➕ **Greeting / personal message** (CAS-08, kiểm duyệt).
- Giữ: ảnh đại diện lớn (CAS-01), breadcrumb (CAS-02), bio (tên/cung HĐ/kỹ năng/ngôn ngữ — field public chốt sau, CAS-06), tags (độ tuổi/phong cách/ngôn ngữ/ngoại hình — CAS-07), **sidebar link ngược về quán** (CAS-10).
- **CTA:** "Đặt hẹn với [Cast]" → P7 (form chung + tham chiếu cast, CAS-05) + "Nhắn tin" (chat P1).

### P7 · Booking — Form đặt chỗ 🆕
**Dùng chung cho quán & cast** (CAS-05). Mở dạng trang (desktop) / bottom-sheet (mobile).
- **Trường tối thiểu (BOO-03):** Tên · SĐT · Số người · Khung giờ · Quán (auto) · **Cast tham chiếu** (nếu đặt từ cast) · Ghi chú.
- **2 lựa chọn (BOO-01):** đặt nhanh bằng form **hoặc** đăng nhập để nhận ưu đãi cao hơn (hiển thị badge "Member 8% / VIP 10%").
- Tùy chọn liên kết **mã giảm giá** (BOO-09).
- Nút "Gửi yêu cầu đặt chỗ" → tạo booking trạng thái **Mới**, gửi Telegram Admin (BOO-04).
- **Mobile:** sheet kéo lên, CTA sticky.

### P8 · Xác nhận + Lịch sử đặt chỗ 🆕
- **Màn xác nhận:** "Đã gửi yêu cầu" + tóm tắt + lưu ý "Admin sẽ liên hệ" + quy tắc hủy (trước 01 giờ, BOO-08A).
- **Lịch sử đặt chỗ:** list theo 3 trạng thái chip: **Mới / Đã hủy / Hoàn tất** (BOO-06). Mỗi item: quán/cast, thời gian, số người, nút **Hủy** (nếu còn ≥1h) — không cho sửa trực tiếp, muốn đổi thì hủy & đặt lại / liên hệ Admin (BOO-08B/C).

### P9 · Coupon/QR — Chi tiết mã 🆕
- Thẻ coupon lớn: tên ưu đãi, **ảnh QR**, tên quán áp dụng, mức giảm theo hạng (5/8/10%), **hạn dùng** (Guest 24h / Member 7 ngày — đếm ngược), **trạng thái** (Đang giữ chỗ / Đã sử dụng / Hết hạn).
- Hướng dẫn: "Đưa mã cho nhân viên quán quét khi tới quán" (MEM-05B).
- Nút "Lưu vào ví" → P10. Mã hết hạn tự hủy (MEM-04B).

### P10 · Ví ưu đãi (Coupon của tôi) 🆕
- Tab trạng thái: **Đang giữ chỗ · Đã sử dụng · Hết hạn**.
- Mỗi dòng: mini-QR, tên, quán, hạn dùng/đếm ngược, giá trị giảm.
- **Lịch sử dùng (MEM-06):** ngày, quán, bill liên kết, giá trị giảm.

### P13 · Tài khoản của tôi 🆕
- Header hồ sơ: avatar, tên, **badge hạng** (Guest/Member/VIP) + mức giảm tương ứng.
- **Thẻ điểm:** tổng điểm, hạn (1 năm), tiến trình nâng hạng; nút "Đổi quà" (P1).
- Tabs: Đặt chỗ (→P8) · Ví ưu đãi (→P10) · Hóa đơn (→P14) · Đã lưu (P1) · Cài đặt (ngôn ngữ — ưu tiên tiếng Nhật).
- **Mobile:** trang trong tab "Tài khoản" của bottom nav.

### P14 · Gửi hóa đơn (Bill) 🆕
- Form: chọn quán (bắt buộc) · số tiền (bắt buộc) · thời gian dùng dịch vụ (bắt buộc) · cơ sở/địa điểm (tùy chọn) · **ảnh/chứng từ (khuyến khích, không bắt buộc — BIL-01)** · liên kết booking/coupon (tùy chọn).
- Lưu ý: "Gửi trong vòng **10 ngày** kể từ ngày dùng dịch vụ" (BIL-02C); "Chỉ ghi tổng tiền, không nhập chi tiết món" (BIL-02B).
- Sau gửi: trạng thái **Pending** → (Admin duyệt) **Đã duyệt** / **Bị từ chối** (kèm **lý do**, nút gửi lại — BIL-04).
- **Lịch sử bill:** list trạng thái + điểm được cộng (1tr = 10đ trên bill gốc).

### P15 · Blog — danh sách / P16 · Blog — chi tiết 🆕
- **List:** lưới card (thumbnail + tag chuyên mục + tiêu đề), filter chuyên mục, dùng cho SEO + quảng bá quán.
- **Detail (CON-02):** thumbnail lớn, nội dung cột trái, cột phải "bài liên quan / ads"; SEO metadata (CON-06). Mobile: 1 cột.

### P17 · Đăng ký đối tác "Join Us" 🆕
- Landing thuyết phục (lợi ích hợp tác) + form: tên quán, loại hình, khu vực, liên hệ, mô tả, ảnh. **Không yêu cầu giấy phép** (PAR-07).
- Gửi → CMS + Telegram Admin (PAR-01/NOT-03). Màn cảm ơn "Admin sẽ liên hệ".

### P18 · Legal 🆕
- Trang tĩnh: Chính sách bảo mật + Chính sách hoạt động (CON-04), 1 cột dễ đọc, mục lục bên cạnh (desktop).

---

## IV. Chi tiết Partner & Admin (rút gọn — dựng sau cụm Khách)

### Partner (P0)
- **PA1 Đăng nhập:** form gọn, brand panel (như P12).
- **PA2 Dashboard:** 3 thẻ số liệu tối thiểu (đặt chỗ tại quán · lượt xem trang · số khách đến) + biểu đồ đơn giản. **KHÔNG** dữ liệu khách chi tiết (PAR-08).
- **PA3 Quét QR:** màn camera/scan (mobile-first) → hiện thông tin mã → nút "Xác nhận đã dùng" → đổi trạng thái Đã sử dụng.
- **PA4 Đối soát dịch vụ:** danh sách mã/dịch vụ đã xác nhận tại quán, lọc theo ngày.
- **PA5 Đăng thông tin:** form quán/cast/giá/ảnh/video → trạng thái **Chờ duyệt** → Admin duyệt/từ chối (PAR-04B).

### Admin CMS (P0)
- Layout chuẩn CMS: sidebar điều hướng trái + topbar + vùng nội dung (desktop-first; mobile chỉ cần xem cơ bản).
- **AD1 Dashboard · AD2 CRUD quán · AD3 CRUD cast · AD4 Media · AD5 Campaign · AD6 Ranking thủ công (kéo-thả Cast trước→Quán) · AD7 Booking · AD8 Duyệt Bill (nút Duyệt/Từ chối + ô lý do) · AD9 Báo cáo (tabs: Gộp/Thuần/Hoa hồng/Giảm giá; bộ lọc ngày→quán→mã→khác) · AD10 Duyệt đối tác · AD11 Blog CMS.**

---

## V. Thứ tự dựng đề xuất (theo MVP doc §7)

1. **Hoàn thiện cụm public lõi:** P4✏️ (album+video+giá+ngôn ngữ), P6✏️ (**bỏ lịch trống** + album+video), P3 (Ranking Page).
2. **Booking & coupon:** P7, P8, P9, P10.
3. **Tài khoản & bill:** P13, P14.
4. **Nội dung & onboarding:** P15, P16, P17, P18.
5. **Partner (P0):** PA1–PA5.
6. **Admin CMS (P0):** AD1–AD11.
7. **P1/P2 sau:** Favorite (P19), Membership/point CMS (AD12), Tour (P20), chat realtime, video trang chủ, Excel/PDF, paid ranking tự động.

Mỗi bước dựng **desktop + mobile** song song, fork từ `Phương án C - Trang chủ tối ưu.dc.html` / `Phương án C - Các trang.dc.html` để giữ đồng nhất.

---

## VI. Quyết định đã chốt (cập nhật 22/06)

1. **Bỏ lịch trống Cast** — ✅ đã gỡ hoàn toàn khỏi P6 (cả desktop & mobile), gồm cả badge "Đang rảnh tối nay"; thay bằng khối **Album ảnh & Video**.
2. **Taxonomy loại hình** — chốt: *core* Bar/Club/Lounge · Karaoke/KTV · Girls bar; *phễu* Massage/Spa · Nhà hàng · Khách sạn · Casino. Bộ lọc hiển thị: Bar · Karaoke · Massage/Spa · Nhà hàng · Casino.
3. **Field Cast public** — chỉ nhập **ngày sinh**; **tuổi tự tính** theo ngày sinh khi hiển thị.
4. **Kênh liên hệ Admin** (hủy/đổi booking) — **LINE** (gắn nút LINE).
5. **Khu vực** — 4 thành phố HN · HCM · ĐN · HP + **Tổng hợp** cho mọi tab khu vực.
6. **Admin CMS** — mockup **cả P0 và P1** (gồm AD12 Membership & point management).

> Các điểm trên đã ghi vào `Design System - Phương án C.md` §7. Bắt đầu dựng theo thứ tự §V.
