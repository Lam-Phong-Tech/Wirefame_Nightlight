# CLAUDE.md — Chỉ dẫn dự án

Đây là dự án mockup giao diện **nightlife.hn**. Đã chốt hướng thiết kế **Phương án C (Daylight Discovery)**.

## Quy tắc bắt buộc cho MỌI giao diện mới
Trước khi dựng bất kỳ màn hình / component nào, ĐỌC và TUÂN THEO file **`Design System - Phương án C.md`** (ở thư mục gốc). Đó là nguồn chân lý duy nhất về màu, font, spacing, bo góc, đổ bóng, component và thứ tự bố cục.

Tóm tắt ràng buộc cốt lõi (chi tiết xem file trên):
- **Phong cách:** sáng – sạch – app du lịch. Không nền tối toàn trang.
- **Màu hành động duy nhất:** tím `#6d28d9`. Nền canvas `#e7e5df`, thẻ lớn `#f5f4f2`, surface `#fff`.
- **Font:** `Inter` (400/500/600/700/800).
- **Card:** bo `16px` + shadow `0 3px 12px rgba(40,20,60,.06)`.
- **Tab khu vực** nhất quán: Tổng hợp · Hà Nội · TP.HCM · Đà Nẵng · Hải Phòng. **Ranking giới hạn Top 5** (ưu tiên Cast trước → Quán) + vương miện (vàng/bạc/đồng/lá/dương).
- **Cast:** KHÔNG hiển thị lịch trống/tình trạng rảnh (khó kiểm soát). Chỉ nhập ngày sinh, tuổi tự tính. Album ảnh + Video là P0 ở cả Store & Cast.
- **Bố cục ưu tiên hành động:** Search → Danh mục → Gợi ý → Coupon → Xếp hạng → Dịch vụ → Khám phá → Hướng dẫn.
- **Ảnh:** gradient placeholder. **Icon:** icons8 (fluency cho danh mục, ios line cho UI nhỏ). Không emoji.
- **Code:** mỗi màn hình là một Design Component `.dc.html`, **chỉ inline style**, dữ liệu/tab-state trong `class Component`. Nội dung tiếng Việt có dấu.
- Luôn dựng kèm **bản mobile** (frame 390px + bottom nav); vùng chạm ≥ 44px.

## File tham chiếu để fork khi dựng mới
- `Phương án C - Trang chủ tối ưu.dc.html` — trang chủ chốt (desktop + mobile, ranking/dịch vụ tương tác).
- `Phương án C - Các trang.dc.html` — bộ trang phụ (danh sách quán, chi tiết, cast, ưu đãi, đăng nhập…).

Khi làm trang mới, ưu tiên copy & fork từ các file trên để giữ đồng nhất.
