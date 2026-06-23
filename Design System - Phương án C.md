# Design System — Phương án C (Daylight Discovery)

> Hệ thống thiết kế chuẩn cho toàn bộ giao diện **nightlife.hn**.
> Mọi màn hình / component mới PHẢI tuân theo file này để đồng nhất.
> Nguồn gốc: chốt từ `Phương án C - Trang chủ tối ưu.dc.html`.

---

## 0. Nguyên tắc tổng

- **Phong cách:** sáng – sạch – như app du lịch/đặt chỗ. Nền sáng, thẻ trắng, bo góc mềm, đổ bóng nhẹ. KHÔNG dùng nền tối toàn trang.
- **Màu thương hiệu:** tím `#6d28d9` là màu hành động duy nhất (nút, tab active, link, nhãn nhấn). Không phát sinh màu nhấn khác.
- **Chữ:** font `Inter` cho mọi nơi.
- **Bố cục ưu tiên hành động:** Search → Danh mục → Gợi ý → Coupon → Xếp hạng → Dịch vụ → Khám phá → Hướng dẫn. Khối tạo hành động/chuyển đổi đặt cao; nội dung khám phá (video/tour/blog) đặt thấp.
- **Ảnh:** dùng placeholder gradient (xem §8) cho tới khi có ảnh thật; không vẽ minh hoạ bằng SVG.
- **Emoji:** không dùng trong UI. Icon lấy từ icons8 (xem §9).

---

## 1. Bảng màu (color tokens)

### Thương hiệu & nền
| Vai trò | HEX | Dùng cho |
|---|---|---|
| Primary | `#6d28d9` | Nút chính, tab active, link, nhãn nhấn |
| Primary soft | `#f1ebff` | Nền chip/nhãn tím, nền nút phụ |
| Primary border | `#e0d6f7` | Viền nút phụ (outline tím) |
| Page bg (canvas) | `#f5f4f2` | Nền thân trang/khung thẻ lớn |
| Surface | `#ffffff` | Header, footer, card, thanh nav |
| Guide bg | `linear-gradient(135deg,#f6f1ff,#fdeef5)` | Khối hướng dẫn; viền `#ece4fb` |

### Chữ & đường kẻ
| Vai trò | HEX |
|---|---|
| Text primary | `#1f1d29` |
| Text secondary | `#5b5870` |
| Muted | `#8a879a` |
| Muted nhạt | `#a8a5b4` |
| Border / divider | `#ececec` |
| Input border | `#e2e0e8` |
| Placeholder | `#9a98a6` |

### Nhấn theo ngữ cảnh
| Vai trò | HEX | Ghi chú |
|---|---|---|
| Sao / đánh giá | `#e8923a` | "★ 4.9" |
| Nhãn vị trí (video) | `#ec4899` | text |
| Mở cửa / trạng thái OK | `#1f8a52` trên `#e6f7ee` | "● Đang mở" |
| Giảm giá (badge) | chữ `#5a3d00` trên `#ffd24d` | "-30%" |

### Hero / banner gradient (chuẩn)
```css
background:
  radial-gradient(120% 100% at 18% 20%, rgba(214,51,108,.55), transparent 50%),
  linear-gradient(140deg, #7b2d6b, #3a1f6e);
```

### Huy hiệu thứ hạng (vương miện Top 5)
| Hạng | Nền badge | Màu số |
|---|---|---|
| 1 — Vàng | `#E8B84B` | `#5a3d00` |
| 2 — Bạc | `#B9C2CC` | `#3a424d` |
| 3 — Đồng | `#C8814B` | `#5a3300` |
| 4 — Xanh lá | `#5BC08A` | `#0a3d28` |
| 5 — Xanh dương | `#5BA6E0` | `#0a2e4d` |

### Nhãn pill theo loại (chip nền nhạt)
| Loại | Chữ | Nền |
|---|---|---|
| Hồng / ưu đãi | `#c0246a` | `#fce4ef` |
| Tím / đề xuất | `#6d28d9` | `#f1ebff` |
| Teal / mới nổi | `#1f7a8c` | `#e0f2f5` |
| Amber / hot | `#b06a00` | `#fdefd6` |

---

## 2. Typography

- **Font:** `'Inter', sans-serif` — weight 400 / 500 / 600 / 700 / 800.
- **Quy tắc cỡ chữ:**

| Vai trò | Size | Weight |
|---|---|---|
| Tiêu đề trang (label trên cùng) | 30px | 800 |
| Hero H2 (desktop) | 44px | 800 |
| Tiêu đề khối (section) | 20px | 700 |
| Tiêu đề phụ | 18px | 700 |
| Tên card / item | 14–15px | 600 |
| Body | 13–15px | 400 |
| Phụ / meta | 11.5–12.5px | 400–500 |
| Micro (nhãn nhỏ) | 10.5px | 600 |

- `line-height` tiêu đề ~1.06–1.15; body ~1.6–1.7.
- Tiêu đề dài: thêm `text-wrap:pretty`.
- **Mobile:** Hero H2 22px/800; tiêu đề khối 15px/700; tên item 13–14px.

---

## 3. Bo góc, đổ bóng, spacing

### Bo góc (border-radius)
| Phần tử | Radius |
|---|---|
| Khung thẻ lớn (page card) | 6px |
| Hero / banner | 20px |
| Card nội dung | 16px |
| Card nhỏ / thumbnail | 12–14px |
| Nút chính | 11px |
| Pill / tab / chip | 14–20px (bo tròn) |
| Badge hạng | 9px |
| Avatar / logo tròn | 50% |
| Khung điện thoại (mobile) | 32px |

### Đổ bóng (box-shadow)
| Mức | Giá trị |
|---|---|
| Card thường | `0 3px 12px rgba(40,20,60,.06)` |
| Card nổi | `0 4px 16px rgba(40,20,60,.07)` |
| Thanh search nổi | `0 12px 30px rgba(40,20,60,.12)` |
| Khung lớn / mockup | `0 12px 40px rgba(0,0,0,.12)` |
| Khung điện thoại | `0 12px 40px rgba(0,0,0,.16)` |

### Spacing
- Padding header: `18px 34px` (desktop) · `6px 18px` (mobile).
- Padding khối nội dung desktop: `8px 34px 28px` (trên ít, dưới 28).
- Gap lưới card: `12–16px`. Gap danh sách dọc: `10px`.
- Lề ngang mobile: `18px`.
- Vùng chạm tối thiểu **44px** (nút, tab, item bấm).

---

## 4. Lưới & layout

- **Desktop frame:** rộng `1100px`, nền thẻ `#f5f4f2`.
- **Mobile frame:** rộng `390px`, viền `1px #e3e0da`, bo `32px`; có status bar (40px) + bottom nav (64px).
- Lưới danh mục: `grid-template-columns:repeat(6,1fr)` (desktop) · `repeat(4,1fr)` (mobile).
- Lưới card gợi ý/coupon: 3–4 cột desktop; mobile chuyển sang **cuộn ngang** (`overflow-x:auto`) hoặc 2 cột.
- Khi xếp nhiều frame cạnh nhau để review: wrapper ngoài `width:max-content; min-width:100%; min-height:100vh; padding:48px; background:#e7e5df`, bên trong `display:flex; gap:56px; align-items:flex-start` — KHÔNG căn giữa trục ngang.

---

## 5. Component chuẩn (copy-paste inline style)

> Toàn bộ dùng **inline style** (xem §10). Trạng thái hover/active của tab tính trong logic, không dùng class.

### 5.1 Nút chính (Primary button)
```html
<div style="font-weight:600;font-size:14px;color:#fff;background:#6d28d9;border-radius:11px;padding:12px 26px;">Tìm</div>
```
### 5.2 Nút phụ (Outline)
```html
<span style="font-size:13px;color:#6d28d9;font-weight:600;border:1px solid #e0d6f7;border-radius:11px;padding:10px 22px;">Xem tất cả ›</span>
```
### 5.3 Pill / Tab
- Active: `background:#6d28d9;color:#fff;border:1px solid #6d28d9;`
- Inactive: `background:#fff;color:#5b5870;border:1px solid #ececec;`
- Chung: `border-radius:14–18px;padding:8px 16px;font-size:13px;font-weight:600;cursor:pointer;`
- Toggle nhỏ (Quán/Cast, tab dịch vụ): bọc `background:#fff;border:1px solid #ececec;border-radius:18px;padding:4px;`, item active nền tím bo `14px`, inactive nền trong suốt.

### 5.4 Chip / nhãn nhỏ
```html
<span style="font-size:10.5px;color:#6d28d9;background:#f1ebff;border-radius:12px;padding:2px 9px;font-weight:600;">Đề xuất nhiều</span>
```
### 5.5 Card địa điểm
```html
<div style="background:#fff;border-radius:16px;overflow:hidden;box-shadow:0 3px 12px rgba(40,20,60,.06);">
  <div style="height:118px;background:linear-gradient(140deg,#d6336c,#7b2d6b);"></div>
  <div style="padding:12px;">
    <div style="font-weight:600;font-size:14px;">Tên quán</div>
    <div style="font-size:11.5px;color:#8a879a;margin-top:3px;">Khu vực · Loại hình</div>
    <span style="display:inline-block;margin-top:8px;font-size:10.5px;color:#c0246a;background:#fce4ef;border-radius:12px;padding:2px 9px;font-weight:600;">Nhãn</span>
  </div>
</div>
```
### 5.6 Card coupon
- Ảnh trên + badge giảm giá góc trái: `background:#ffd24d;color:#5a3d00;font-size:18px;font-weight:800;border-radius:12px;padding:6px 12px;`
- Chân card: nhãn thời hạn (chip) + link `Lấy mã ›` (`#6d28d9`).
- Luôn kèm shortcut "Cách lấy mã & tích điểm →" (nền `#f1ebff`) cạnh tiêu đề, link tới khối hướng dẫn.

### 5.7 Dòng xếp hạng (Top 5)
```html
<div style="display:flex;align-items:center;gap:14px;background:#fff;border:1px solid #ececec;border-radius:14px;padding:12px 14px;">
  <span style="width:30px;height:30px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:14px;color:#5a3d00;background:#E8B84B;">1</span>
  <span style="width:46px;height:46px;border-radius:50%;background:linear-gradient(140deg,#d6336c,#7b2d6b);"></span>
  <div style="flex:1;"><div style="font-weight:600;font-size:15px;">Tên</div><div style="font-size:12.5px;color:#8a879a;margin-top:2px;">Khu vực</div></div>
  <div style="font-size:12.5px;color:#6d28d9;font-weight:600;">12.4k lượt</div>
</div>
```
- Luôn kèm thanh kỳ: `background:#f1ebff;color:#6d28d9;` "Kỳ: Tháng X/2026 · Cập nhật … · Top 5".
- **Giới hạn cứng 5 dòng/tab.** Có nút "Xem bảng xếp hạng đầy đủ ›".

### 5.8 Thanh tìm kiếm nổi (hero)
Nền trắng, bo `16px`, `padding:12px`, shadow `0 12px 30px rgba(40,20,60,.12)`, kéo lên đè hero bằng `margin-top:-32px`. Gồm: ô địa điểm (tím, có icon marker) · ô tìm (placeholder `#9a98a6`) · nút "Tìm".

### 5.9 Card video
Thumbnail gradient + nút play tròn trắng giữa (`rgba(255,255,255,.9)`, icon play tím) + badge thời lượng góc phải dưới. Dưới: avatar tròn nhỏ + tên + nhãn vị trí `#ec4899`. Đặt trong hàng cuộn ngang.

### 5.10 Khối hướng dẫn (3 bước)
Nền `linear-gradient(135deg,#f6f1ff,#fdeef5)`, viền `#ece4fb`, bo `20px`. Mỗi bước: số trong ô bo `10px` nền `#6d28d9` chữ trắng + tiêu đề + mô tả muted.

### 5.11 Header
Nền trắng, dưới có `border-bottom:1px solid #ececec`. Trái: logo `nightlife` (tím `.hn` đen) + menu. Phải: chip `VI · 日本語` (nền `#f1ebff`) · "Đăng nhập" · nút "Đăng ký đối tác" (nền tím bo 22px). Có thể `position:sticky;top:0`.

### 5.12 Footer
Nền trắng, `border-top:1px solid #ececec`, chữ `#8a879a` 12px, hai cụm trái/phải.

### 5.13 Bottom nav (mobile)
Cao 64px, nền trắng, `border-top:1px solid #ececec`, 5 mục icon+label. Mục active: icon + chữ `#6d28d9` weight 600; còn lại `#b6b3c0`.

---

## 6. Thứ tự khối trang chủ (chuẩn chốt)

1. Header (sticky)
2. Hero + Search
3. Quick Categories (6 desktop / 4 mobile)
4. Đề xuất tối nay đi đâu (biên tập, KHÁC ranking)
5. Coupon Hot **+ shortcut "Cách lấy mã & tích điểm"**
6. Bảng xếp hạng — tab thành phố (Tất cả · Hà Nội · TP.HCM) × toggle Quán/Cast, **Top 5** + vương miện
7. Dịch vụ nổi bật — tab Nhà hàng / Spa & Massage
8. Khám phá: Video Hot (cuộn ngang) · Tour · Cẩm nang khu vực & Blog
9. Hướng dẫn lấy mã & tích điểm (chi tiết, gần cuối)
10. Footer (mobile: + Bottom nav)

**Mô-típ Tab thành phố** (Tất cả/HN/HCM) tái sử dụng nhất quán cho Xếp hạng và Video.

---

## 7. Tab khu vực, taxonomy & quy ước dữ liệu hiển thị

### 7.1 Tab khu vực (chốt 22/06)
- **5 giá trị cố định:** **Tổng hợp** (toàn quốc — nhãn có thể là "Tất cả") · **Hà Nội** · **TP.HCM** · **Đà Nẵng** · **Hải Phòng**.
- Một component tab dùng chung cho mọi khối có lọc (Ranking, Video, Search). Trên mobile cho cuộn ngang.
- Bấm tab → đổi danh sách tương ứng (logic trong class, render bằng `<sc-for>`).

### 7.2 Taxonomy loại hình (chốt 22/06)
- **Nightlife core:** Bar / Club / Lounge · Karaoke / KTV · Girls bar.
- **Dịch vụ phễu (chỉ hiển thị thông tin):** Massage / Spa · Nhà hàng · Khách sạn · Casino.
- Bộ lọc Search/Ranking rút gọn hiển thị: **Bar · Karaoke · Massage/Spa · Nhà hàng · Casino**.

### 7.3 Quy ước hiển thị dữ liệu
- **Tuổi Cast:** chỉ lưu **ngày sinh**; tuổi **tự tính** từ ngày sinh để hiển thị (vd "Michi · 23"). Không nhập tuổi tay.
- **KHÔNG hiển thị lịch trống / tình trạng rảnh của Cast** (khó kiểm soát — chốt CAS-04). Không dùng badge "Đang rảnh", "Lịch trống".
- **Ranking:** giới hạn Top 1–5/khu vực; ưu tiên **Cast trước → Quán**.
- **Album ảnh + Video là P0** ở cả Store Detail và Cast Profile (cho gắn link hoặc upload). Thumbnail video có nút play tròn trắng, icon play tím.
- **Kênh liên hệ Admin** (hủy/đổi booking): **LINE**.
- **Bảng giá/menu:** chỉ tham khảo — luôn kèm ghi chú "không đặt món trên web".

---

## 8. Gradient placeholder ảnh
Dùng khi chưa có ảnh thật (`linear-gradient(140deg, …)` hoặc `linear-gradient(180deg, …)` cho ảnh dọc):

```
#d6336c→#7b2d6b   (hồng tím)
#3a8fb0→#2d5fae   (xanh dương)
#8a6ad0→#5d3da8   (tím)
#e0a23a→#c0782d   (cam)
#e0598a→#a8336b   (hồng)
#5fae8a→#2d8a6a   (xanh lá)
```
Overlay chữ trên ảnh dọc: `linear-gradient(0deg, rgba(20,8,16,.8), transparent)`.

---

## 9. Icon
- **Danh mục / tiêu đề khối:** icons8 **fluency** (màu) — vd `https://img.icons8.com/fluency/96/cocktail.png`.
- **UI nhỏ** (chevron, like, share, search, marker, play): icons8 **ios** line, tint theo ngữ cảnh:
  - Tím: `.../6D28D9/<icon>.png`
  - Trắng (trên ảnh): `.../FFFFFF/<icon>.png`
  - Xám nhạt (inactive): `.../B6B3C0/<icon>.png`
- Cờ Nhật cho cast nói tiếng Nhật: `https://img.icons8.com/color/96/japan.png`.

---

## 10. Quy ước code (bắt buộc để đồng nhất)

- Mỗi màn hình là **Design Component** `Tên.dc.html` (DC). Không dùng `.jsx`/`.html` rời.
- **Chỉ inline style** — không stylesheet, không class CSS, không design-token CSS. (Trừ `@font-face`/`@keyframes`/reset trong `<helmet>`.)
- Font khai báo 1 lần trong `<helmet>` (link Google Fonts Inter). `body{background:#e7e5df;}` cho nền canvas review.
- Dữ liệu danh sách + trạng thái tab để trong `class Component extends DCLogic`; render bằng `<sc-for>` / `<sc-if>`. Trạng thái active của tab tính trong `renderVals()` rồi đổ ra style string.
- Không hardcode text vào hole `{{ }}`; hole chỉ cho giá trị runtime (danh sách, trạng thái).
- Tiếng Việt có dấu cho mọi nội dung hiển thị.

---

## 11. Checklist khi tạo màn hình mới
- [ ] Nền sáng `#f5f4f2`/trắng, không nền tối toàn trang.
- [ ] Chỉ dùng tím `#6d28d9` làm màu hành động.
- [ ] Font Inter, đúng thang cỡ chữ §2.
- [ ] Card bo 16px + shadow `0 3px 12px rgba(40,20,60,.06)`.
- [ ] Tab active/inactive đúng §5.3; tab thành phố đủ 3 giá trị.
- [ ] Ranking giới hạn Top 5 + vương miện đúng màu §1.
- [ ] Vùng chạm ≥ 44px; có bản mobile (frame 390px + bottom nav).
- [ ] Ảnh = gradient placeholder §8; icon theo §9.
- [ ] Khối hành động/chuyển đổi đặt cao, content khám phá đặt thấp.

---

## Phụ lục A — Khác biệt Mobile

> Mọi token ở §1–§3 (màu, font, bo góc, đổ bóng) **giữ nguyên**. Mục này chỉ liệt kê những gì khác desktop.

### A.1 Khung & cấu trúc
- **Frame:** rộng `390px`, nền `#f5f4f2`, viền `1px solid #e3e0da`, bo `32px`, shadow `0 12px 40px rgba(0,0,0,.16)`. Chiều cao: để tự co theo nội dung (trang chủ dài cuộn dọc); các màn ngắn có thể cố định `810px` + `overflow:hidden`.
- **Status bar:** cao `40px`, nền trắng — trái giờ "21:00" (13px/700), phải biểu tượng pin. Trên hero ảnh tối thì chữ status đổi sang trắng.
- **Lề ngang nội dung:** `18px` (desktop là `34px`).
- **Header:** logo + chip vị trí (marker tím) trên một hàng; bên dưới là hàng search + nút lọc.

### A.2 Thang cỡ chữ mobile
| Vai trò | Mobile |
|---|---|
| Hero H2 | 22px / 800 |
| Tiêu đề khối | 15px / 700 |
| Tên item / card | 13–14px / 600 |
| Body | 13px |
| Meta / phụ | 10.5–11.5px |
| Micro (nhãn) | 9.5–10px |

### A.3 Lưới & cuộn
- Danh mục nhanh: `grid repeat(4,1fr)` (desktop 6). Mỗi ô là tile nền `#f6f1ff` cao 54px + nhãn dưới.
- Danh sách card (gợi ý, dịch vụ, video): chuyển sang **cuộn ngang** `display:flex;gap:11px;overflow-x:auto` với item `flex:none;width:140–150px`. Dùng class `.hscroll` (scrollbar mảnh) khai báo trong `<helmet>`.
- Card danh sách quán/coupon: layout **ngang** (ảnh trái ~84–118px + nội dung phải) thay vì dọc.
- Ranking: tab thành phố + toggle Quán/Cast thu nhỏ; dòng item gọn hơn (badge 26px, avatar 38px, padding `9px 11px`).

### A.4 Search & thanh tác vụ
- Ô search: cao `44px`, bo `12px`, kèm nút vuông `44×44` nền tím cho bộ lọc.
- Hành động chính ở chi tiết: thanh đáy cố định (`position:absolute;bottom:0`) nền trắng + nút primary tràn ngang.

### A.5 Bottom nav (bắt buộc trên mọi màn mobile)
- Cao `64px`, nền trắng, `border-top:1px solid #ececec`, `padding-bottom:6px`.
- 5 mục: Trang chủ · Cast · Ưu đãi · Đã lưu · Tài khoản — icon + label.
- Mục active: icon (fluency/ios-filled) + chữ `#6d28d9` weight 600. Mục thường: icon ios line + chữ `#b6b3c0`.

### A.6 Thứ tự khối trang chủ mobile
Header → Search → Danh mục (4 ô) → Hero mini → Đề xuất (cuộn ngang) → Coupon + shortcut → Ranking (tab thành phố, Top 5) → Dịch vụ nổi bật (cuộn ngang) → Video Hot (cuộn ngang) → Hướng dẫn lấy mã → Bottom nav.

### A.7 Vùng chạm
- Mọi nút/tab/item bấm ≥ **44px** chiều cao. Tile danh mục, nút search, nút đáy đều tuân thủ.
