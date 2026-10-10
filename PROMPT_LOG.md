# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)
- **Họ và tên:** Hoàng Trung Kiên
- **MSSV:** 526000177
- **Tên đề tài Website:** Landing Page VALORANT Champions Shanghai 2026
- **Công cụ AI đã sử dụng:** Gemini / Claude

## 1. Yêu cầu ban đầu (System/Initial Prompt)
>Bạn là một Senior Front-End Developer và UI/UX Designer chuyên nghiệp. Hãy giúp tôi code hoàn chỉnh một Landing Page giới thiệu giải đấu eSports "VALORANT Champions Shanghai 2026" tuân thủ tuyệt đối các tiêu chuẩn kỹ thuật khắt khe sau đây:

1. QUY CHUẨN CẤU TRÚC SEMANTIC HTML5 (Bắt buộc dùng đúng 5 thẻ ngữ nghĩa chính, không lạm dụng thẻ div vô nghĩa):
- <header>: Chứa logo VALORANT Champions 2026 và thanh điều hướng chính.
- <nav>: Thanh menu điều hướng các phần (Trang chủ, Giới thiệu, Lịch thi đấu, Đội tuyển, Vé & Merch).
- <main>: Khung bao bọc toàn bộ nội dung trọng tâm của trang.
- <section> / <article>: Chia các khối nội dung rõ ràng (Hero Banner, Giới thiệu giải đấu tại Thượng Hải, Lịch trình, Danh sách 16 đội, Bộ sưu tập Merch).
- <footer>: Chân trang chứa thông tin bản quyền Riot Games, liên hệ và mạng xã hội.

2. KỸ THUẬT CSS & CSS VARIABLES:
- Khai báo đầy đủ trong :root { ... } các biến CSS cho màu sắc chủ đạo (Màu đỏ đặc trưng VALORANT #ff4655, màu nền tối eSports #0f1923, màu phụ trợ, font chữ, spacing).
- Ứng dụng mô hình layout hiện đại: Sử dụng linh hoạt CSS Flexbox và CSS Grid để dàn trang Responsive hoàn hảo trên mọi thiết bị (Mobile, Tablet, Desktop).
- Tự viết hiệu ứng tương tác :hover và :focus mượt mà cho toàn bộ nút bấm (CTA buttons), thẻ đội tuyển (cards) và menu links (ví dụ: chuyển màu, phóng to nhẹ, hiệu ứng glow neon).

3. TÍCH HỢP THƯ VIỆN HIỆU ỨNG:
- Tích hợp Animate.css qua CDN để tạo hiệu ứng động bắt mắt cho tiêu đề lớn (Hero Title) và nút bấm CTA chính.
- Tích hợp AOS (Animate On Scroll) qua CDN để tạo hiệu ứng cuộn trang mượt mà (fade-up, zoom-in) cho các section nội dung.

4. NỘI DUNG CHÍNH CỦA LANDING PAGE (VALORANT Champions Shanghai 2026):
- Thời gian sự kiện: 24/9 - 18/10/2026.
- Địa điểm: Thượng Hải, Trung Quốc (Vòng bảng/Playoffs tại Jing'an Sports Center, Top 4 & Chung kết tại Mercedes-Benz Arena).
- Tổng giải thưởng: $2,250,000 USD.
- Giao diện mang đậm chất gaming, hiện đại, phối màu Đen - Đỏ - Trắng đặc trưng của VALORANT.

Hãy xuất ra code gồm 2 file riêng biệt: index.html và style.css (kèm đầy đủ các thẻ script/link CDN của Animate.css, AOS, Font chữ). Viết code sạch sẽ, comment rõ ràng từng phần.

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iterations)

### Lần 1: Kiểm tra cấu trúc Semantic HTML & CSS Variable
- **Prompt đã dùng:** "Kiểm tra lại toàn bộ file HTML vừa tạo, đảm bảo tôi không bị lạm dụng thẻ div ở phần danh sách đội tuyển. Hãy chắc chắn các thẻ <section> có id rõ ràng để phục vụ cuộn trang và biến màu sắc phải nằm trọn trong :root."
- **Kết quả AI tạo ra:** AI đã refactor lại code, thay thế các thẻ `<div>` bọc nội dung thông thường bằng `<section>` và `<article>`, khai báo chuẩn cú pháp `--primary-color: #ff4655;` trong `:root`.
- **Nhận xét & Tinh chỉnh của SV:** AI đã tuân thủ tốt cấu trúc ngữ nghĩa, tuy nhiên phần layout grid của các thẻ bài viết (cards) trên mobile bị tràn viền, tôi yêu cầu AI bổ sung `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` để responsive tốt hơn.

### Lần 2: Tích hợp thư viện AOS và tối ưu hiệu ứng cuộn trang
- **Prompt đã dùng:** "Thêm thư viện CSS và JS của AOS (Animate On Scroll) vào trang HTML. Cấu hình để khi cuộn trang đến phần lịch thi đấu và thông tin địa điểm (Mercedes-Benz Arena), các khối div/section sẽ hiện lên với hiệu ứng `data-aos='fade-up'` mượt mà."
- **Thách thức gặp phải:** Hiệu ứng AOS bị lỗi không chạy hoặc bị chớp nháy khi tải trang lần đầu do thiếu đoạn khởi tạo JavaScript `AOS.init();`.
- **Cách sửa prompt (Debug prompt):** "Thư viện AOS không chạy khi cuộn trang. Hãy kiểm tra xem tôi đã thiếu đoạn mã khởi tạo JavaScript `AOS.init();` ở cuối file chưa? Hãy bổ sung đầy đủ CDN và đoạn script khởi tạo vào đúng vị trí."

### Lần 3: Tối ưu UI/UX, thêm Modal Mua vé & Hiệu ứng Thông báo (Toast Notification)
- **Prompt đã dùng:** "Thiết kế một Modal Popup mua vé ẩn/hiện mượt mà khi người dùng bấm vào các nút "Mua Vé" / "Mua Vé VIP". Modal có form điền thông tin (Họ tên, Email, Số lượng vé) và nút xác nhận.
- Thêm một Toast Notification (Thông báo góc màn hình) kiểu game hiện đại để khi người dùng bấm "Mua", hệ thống hiển thị thông báo thành công: "Đặt vé thành công! Kiểm tra email để nhận mã QR." kèm hiệu ứng trượt vào (slide-in)."
- **Kết quả AI tạo ra:** AI đã viết xong file `style.css` với các hiệu ứng glassmorphism, hover card phát sáng neon, bổ sung thêm giao diện ẩn của Modal Form đặt vé và Toast Notification.
- **Nhận xét & Tinh chỉnh của SV:** AI ban đầu làm modal bị đè lên nội dung và mất nút đóng (close button), tôi đã yêu cầu AI tinh chỉnh lại thuộc tính `position: fixed`, `z-index: 9999`, và thêm một đoạn JavaScript nhỏ để bật/tắt modal khi người dùng bấm vào các nút CTA mua vé.

## 3. Đánh giá cá nhân về quá trình Vibe Coding
- **AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?:** AI giúp tôi thiết kế khung bố cục (layout structure) nhanh chóng, viết sẵn hàng trăm dòng CSS cho hiệu ứng `:hover`, đổ màu gradient, thiết kế giao diện eSports tối màu (dark theme) cực kỳ sắc nét mà không mất công mò mẫm từng thuộc tính thủ công.

### Lần 4: Thêm các hiệu ứng thị giác nâng cao (Cyberpunk Glow & Advanced Hover)
- **Prompt đã dùng:** "Tôi muốn nâng cấp file "style.css" của Landing Page VALORANT Champions Shanghai 2026 trở nên cực kỳ bắt mắt, hoành tráng, mang đậm phong cách eSports/Cyberpunk với các hiệu ứng thị giác nâng cao sau đây:

1. HIỆU ỨNG NỀN VÀ KHÔNG GIAN (ATMOSPHERE & PARTICLES/GLOW):
- Thêm các khối ánh sáng nền mờ ảo (Glow Orbs / Ambient Light) trôi nổi chậm rãi ở Hero Section và các section chính (màu đỏ chủ đạo #ff4655 và xanh ngọc #00ffcc) sử dụng keyframe animation (`@keyframes float` và `pulse`).
- Thêm hiệu ứng lưới góc cạnh (Cyberpunk grid overlay) hoặc đường quét tia sáng ngang màn hình (scanlines nhẹ) để tạo chiều sâu công nghệ.

2. HIỆU ỨNG ĐỘC ĐÁO CHO CHỮ & TIÊU ĐỀ (GLITCH / NEON TEXT):
- Tiêu đề chính (`<h1>` Hero Title) và các tiêu đề section (`.section-title`) phải có hiệu ứng đổ bóng neon rực rỡ (`text-shadow`) và hiệu ứng chữ lóe sáng (glitch/flicker) nhẹ khi hover hoặc khi load trang.
- Thêm đường viền gạch chân hoặc góc cắt chéo (diagonal cut corners) đặc trưng của giao diện game VALORANT cho các thẻ card (Đội tuyển, Vé, Lịch trình).

3. HIỆU ỨNG TƯƠNG TÁC CHUỘT & HOVER ĐỈNH CAO (ADVANCED HOVER):
- Các thẻ card đội tuyển (`.team-card`) và vé (`.merch-card`) khi `:hover` sẽ xuất hiện viền sáng chạy quanh khung (border glow animation) và phóng to nổi khối 3D nhẹ (`transform: translateY(-8px) scale(1.02)`).
- Các nút bấm (CTA buttons) khi hover sẽ tạo hiệu ứng loang sáng từ tâm (ripple/shimmer effect) hoặc phát tia sáng đỏ rực.

4. HIỆU ỨNG THANH CUỘN & LOADING (SCROLLBAR & ACCENTS):
- Tùy chỉnh thanh cuộn (Custom Scrollbar) màu đỏ/tối ton-sur-ton với giao diện trang web.
- Đảm bảo tất cả các hiệu ứng mới này mượt mà, không gây giật lag (sử dụng `will-change` và `transform` để tối ưu GPU acceleration) và hoàn toàn responsive trên di động.

Hãy cập nhật lại toàn bộ file "style.css" tích hợp các hiệu ứng này một cách hài hòa, không bị rối mắt."
- **Kết quả AI tạo ra:** AI đã bổ sung các lớp ánh sáng nền (glow orbs) chuyển động mượt mà, hiệu ứng viền neon chạy quanh thẻ card khi hover và tối ưu hóa hệ thống màu sắc chủ đạo.
- **Nhận xét & Tinh chỉnh của SV:** Các hiệu ứng ban đầu hơi chói mắt và làm ảnh hưởng tới độ đọc của chữ, tôi đã yêu cầu AI giảm độ mờ (opacity) của lớp nền sáng và tinh chỉnh lại độ tương phản cho phần chữ trắng trên nền tối để đảm bảo tiêu chuẩn UI/UX thẩm mỹ cao.

### Lần 5: Chuẩn hóa font chữ hỗ trợ Tiếng Việt (Inter Font)
- **Prompt đã dùng:** "Hãy cập nhật lại phần khai báo font chữ trong file "index.html" và "style.css" của dự án:
1. Đảm bảo toàn bộ website (từ tiêu đề, menu, nội dung, nút bấm) sử dụng họ font chữ **'Inter'** làm font chính (hoặc kết hợp 'Rajdhani' cho tiêu đề lớn nhưng phải đảm bảo hỗ trợ đầy đủ bảng mã tiếng Việt Unicode).
2. Kiểm tra và bổ sung đúng link Google Fonts cho Inter với đầy đủ các trọng số (weights: 400, 500, 600, 700) trong thẻ <head> của file HTML.
3. Cập nhật lại thuộc tính `font-family` trong file CSS ở `:root` hoặc `body` để áp dụng triệt để font Inter cho toàn trang, giúp hiển thị tiếng Việt có dấu cực kỳ sắc nét, rõ ràng và không bị lỗi font."
- **Kết quả AI tạo ra:** AI đã thêm đầy đủ link Google Fonts của Inter vào `<head>` và cập nhật lại toàn bộ biến `font-family` trong file CSS.
- **Nhận xét & Tinh chỉnh của SV:** Đảm bảo tiếng Việt hiển thị trên các thẻ tiêu đề và nút bấm không bị lỗi font, đồng thời giữ được nét hiện đại, tối giản đúng chuẩn giao diện eSports.

- **Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?:** Cần chỉ định rõ ràng các ràng buộc kỹ thuật từ đầu (ví dụ: bắt buộc dùng thẻ ngữ nghĩa nào, biến CSS tên gì) để tránh việc AI lạm dụng thẻ `<div>`. Khi tích hợp thư viện bên ngoài như AOS, cần nhắc AI kiểm tra cả phần script khởi tạo (JS Initialization) chứ không chỉ gắn mỗi link CDN CSS.