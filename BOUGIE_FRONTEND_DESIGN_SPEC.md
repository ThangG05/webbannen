# BOUGIE — IMMERSIVE BRAND WEBSITE
## Product-grounded UI/UX & Frontend Implementation Specification for Codex

> **Mục tiêu:** Xây dựng website marketing frontend-only, giàu trải nghiệm 3D, mềm mại, trẻ trung, cao cấp cho thương hiệu nến thơm Bougie. Đây là đặc tả triển khai, không phải mã nguồn hoàn chỉnh.

## 1. Nguồn thông tin và nguyên tắc
- Nguồn: tài liệu Word `Anh4_Bougie (2).docx`, đặc biệt mục 1, 3, 4, 5.2 và các hình minh họa ở trang 8, 10, 11, 14.
- Bougie: startup nến thơm tại Hà Nội, thành lập năm 2026; thông điệp trọng tâm: **bán cảm xúc và khoảnh khắc, không chỉ bán mùi hương**.
- **Thông tin sản phẩm/giá** bên dưới lấy từ tài liệu; những mô tả UI, CTA, animation và cấu trúc kỹ thuật là **đề xuất thiết kế**.
- Không tự khẳng định thời gian cháy, trọng lượng, thành phần sáp, chứng nhận an toàn, số lượng bán, review hoặc ưu đãi nếu chưa có dữ liệu xác thực. Không lấy ảnh mockup làm bằng chứng cho thông số sản phẩm.
- Không dùng tên, ảnh, logo của một thương hiệu khác làm tài sản chính thức. Kiểm tra quyền sử dụng hình ảnh trong Word trước khi đăng công khai.

## 2. North Star: creative direction
**Concept:** `A Little Flame, A Whole Feeling.` — mỗi cú cuộn là một chương của câu chuyện mùi hương.

**Brand adjectives:** tactile, dreamy, warm, contemporary, playful elegance, calm, cinematic.

**Visual tokens (đề xuất):**
| Token | Giá trị | Mục đích |
|---|---|---|
| `--ivory` | `#FAF6F0` | nền chính |
| `--cream` | `#F1E5D7` | nền thứ cấp |
| `--blush` | `#EAC8C3` | điểm nhấn mềm mại |
| `--caramel` | `#B77B58` | CTA và ánh sáng |
| `--forest` | `#34473D` | chiều sâu, Cozy Winter |
| `--ink` | `#342D2A` | chữ chính |
| `--gold` | `#C8A574` | đường viền tinh tế |

Typography: heading `Cormorant Garamond` hoặc `DM Serif Display`; body `Manrope` hoặc `Inter`; font có hỗ trợ tiếng Việt. H1 desktop clamp(3.5rem, 7vw, 8rem), mobile clamp(2.5rem, 10vw, 4.5rem). Khoảng trắng rộng, lưới 12 cột desktop, 4 cột mobile, góc bo lớn có tiết chế; tránh giao diện thương mại điện tử dạng ô lưới dày đặc.

**Art direction:** chụp nến trên đá travertine, vải linen, bàn gỗ, hoa khô, cửa sổ nắng chiều; kết hợp mô hình 3D thủy tinh, chất sáp và lửa. Ảnh là phương tiện kể chuyện, không dùng ảnh stock không đồng nhất. Sử dụng ảnh từ Word làm reference visual; tạo hoặc xin asset chất lượng cao riêng cho website.

## 3. Kiến trúc thông tin và hành trình UX
### Navigation
`Home` · `The Mood Collection` · `Seasonal Editions` · `Make It Yours` · `Workshop` · `Our Story` · `Contact`.

Website nên ưu tiên **một trang landing page nhiều chương** có anchor navigation, kèm các route frontend riêng cho trải nghiệm chuyên sâu:
- `/` — landing experience.
- `/collection` — bộ sưu tập Mood, lọc theo cảm xúc.
- `/collection/:slug` — chi tiết từng nến.
- `/seasonal` — bộ sưu tập theo mùa.
- `/customize` — configurator cá nhân hóa, client-side.
- `/workshop` — giới thiệu workshop.
- `/story` — câu chuyện thương hiệu.
- `/contact` — liên hệ và social.

**Primary user journeys:**
1. Khách mới → Hero → chọn tâm trạng → khám phá nến → xem chi tiết → CTA liên hệ.
2. Người mua quà → Seasonal / Customize → xem preview → copy cấu hình → liên hệ đặt tư vấn.
3. Người quan tâm trải nghiệm → Workshop → tìm hiểu quy trình → CTA hỏi lịch qua kênh chính thức.

Không hiển thị giỏ hàng/checkout giả, số chỗ còn lại giả hoặc nút đặt hàng mà không có hành động thực. CTA liên hệ dùng URL social/email thực tế do nhóm cung cấp; trong lúc chưa có thì ghi rõ placeholder cấu hình và không render liên kết hỏng.

## 4. Detailed page blueprint
### 4.1 Global shell
- Preloader tinh tế tối đa ~1.5 giây **chỉ khi cần**, không chặn người dùng để trình diễn animation; tránh flash of unstyled content.
- Header floating translucent, logo Bougie, nav, nút `Explore the Scents`; khi scroll chuyển từ transparent sang frosted cream.
- Desktop menu hover có underline dạng nét vẽ; mobile full-screen menu với transition mềm, đóng bằng Escape và backdrop.
- Footer editorial: logo, tagline, collections, contact/social, copyright, disclaimer thông tin.
- Scroll progress line rất mảnh; custom cursor chỉ desktop pointer chính xác, không thay thế cursor mặc định khi không cần.

### 4.2 Hero — The first spark
**Layout:** màn hình đầu full viewport, headline lớn bên trái, nến 3D nổi bên phải, ánh sáng ấm lan nhẹ theo ngọn lửa; vài hạt bụi sáng hoặc đường hương trừu tượng.

**Copy đề xuất:**
- Eyebrow: `BOUGIE · SCENTED MOMENTS`
- H1: `A Little Flame. A Whole Feeling.`
- Subtitle: `Discover scented candles designed for the moods, spaces, and moments that matter.`
- CTA 1: `Explore the Collection` → `/collection`
- CTA 2: `Find Your Mood` → section Mood Finder

**Motion:** hero candle xoay chậm khi idle, pointer tilt ±5°, parallax nhẹ; flame shader/animated plane, subtle bloom; chữ xuất hiện theo dòng 0.6–0.9s. Khi scroll, nến dịch chuyển và scale thành sản phẩm mở đầu section kế. **Không bắt buộc WebGL để thấy nội dung**: luôn có ảnh poster/fallback.

### 4.3 Brand manifesto — We sell feelings
Split editorial composition: câu chuyện ngắn + ảnh lifestyle + chữ kinetic typography `NOT JUST A SCENT. A FEELING.`. Nêu các trường hợp dùng: self-care, không gian sống, quà tặng. Không đưa financial projection hoặc thông tin tổ chức nội bộ lên landing page.

### 4.4 Mood Finder — signature interaction
**Điểm khác biệt quan trọng nhất:** câu hỏi `How do you want to feel today?` với 4 lựa chọn mood dạng pill/card, hiệu ứng chuyển màu nền và hạt hương:
- `Warm & Indulgent` → Vanilla Chivas.
- `Soft & Romantic` → Romantic Lavender.
- `Fresh & Free` → Floral Ocean.
- `Cozy & Grounded` → Cozy Winter.

Khi chọn mood: thay 3D jar/ảnh, palette, headline, notes và CTA; URL có thể lưu lựa chọn bằng query parameter, không cần backend. Keyboard-accessible, selected state rõ ràng, tránh animation gây chóng mặt. Không gọi đây là thuật toán AI nếu chỉ mapping tĩnh.

### 4.5 Signature Mood Collection
4 product chapters xen kẽ, thay vì card grid nhàm chán. Mỗi chapter có sản phẩm lớn, lớp nền riêng, mùi hương hiển thị dạng `scent notes`, storytelling và nút `Discover This Scent`. Cho phép chuyển qua tab/drag slider và có nút prev/next rõ ràng.

**Dữ liệu lấy từ Word:**
| Product | Emotional positioning | Scent notes | Suggested use |
|---|---|---|---|
| Vanilla Chivas — The Warm Indulgence | ấm áp, sang trọng | cognac, vanilla, caramel, amber, peach | tối yên tĩnh, cặp đôi, thư giãn |
| Romantic Lavender — The Gentle Romance | nhẹ nhàng, lãng mạn | lavender, rose, sandalwood, amber, honey | đọc sách, self-care, tặng người thương |
| Floral Ocean — The Fresh Escape | tươi mới, tự do | fruity notes, ocean breeze, cedarwood, citrus | góc làm việc, giải lao |
| Cozy Winter — The Comforting Home | ấm cúng, gần gũi | pine, pine needle, cinnamon, cedarwood, patchouli | gia đình, cuối tuần, buổi tối |

**Giá:** tài liệu mục 5.2 ghi mức **520.000–550.000 VNĐ/nến** cho Mood Collection; chưa xác nhận giá chính xác từng mùi từ phần văn bản. Hiển thị `Từ 520.000đ` hoặc `520.000–550.000đ` cho dòng sản phẩm; **không gán giá cố định cho từng SKU** khi chưa xác minh. Ảnh minh họa trang 8 có nhãn giá nhưng không thay thế bảng SKU chính thức.

### 4.6 Product detail `/collection/:slug`
- Gallery hình nến, hover 3D tilt và optional 360° viewer, thumbnails có keyboard support.
- Product name, tagline, notes pyramid dạng visual, mood chips, giá hợp lệ, ngữ cảnh sử dụng.
- `The moment` kể một tình huống lifestyle ngắn; `You may also like` gợi ý 2 mùi liên quan bằng mapping tĩnh.
- CTA `Ask About This Candle` mở liên hệ có nội dung sản phẩm đã chọn hoặc copy message.
- Không bịa rating, tồn kho, khuyến mãi, thành phần hay FAQ kỹ thuật.

### 4.7 Seasonal Limited Editions
Cinematic horizontal carousel hoặc scroll-linked 3 scene:
- **Christmas Collection** — **720.000đ**; warm festive, pine/cinnamon-inspired visual chỉ là direction; không tự khẳng định note chính thức.
- **Lunar New Year Collection** — **710.000đ**; family, happiness, new beginnings, hoa và ánh sáng đỏ ấm.
- **Valentine’s Day Collection** — **730.000đ**; romantic elegant, hồng phấn, lụa, hoa.

Visual 3D gift box reveal, ribbon unfolding, chuyển cảnh theo mùa; điều khiển bằng nút, không ép horizontal scroll. Gắn `Concept / Seasonal Collection` nếu chưa xác nhận hàng đang bán; tránh tạo cảm giác còn hàng hoặc đang mở bán khi chưa rõ.

### 4.8 Make It Yours — interactive candle configurator
**Đây là feature demo frontend nổi bật**, không gửi đơn hàng thật.

Wizard 4 bước có progress rõ ràng:
1. Choose your scent (danh sách đã xác nhận).
2. Choose jar/candle color (màu demo do team định nghĩa; không khẳng định mọi tùy chọn đều sẵn có).
3. Choose label style (2–4 template minh họa).
4. Add a personal message (tên/ngày/lời chúc; giới hạn ký tự, live preview).

Preview nến 3D cập nhật theo lựa chọn; thay label bằng texture canvas/SVG render lên mesh hoặc ảnh composited. Summary hiển thị `Giá tham khảo: 600.000–700.000đ / sản phẩm, tùy mức tùy chỉnh và chất liệu`.

Actions: `Copy My Design` tạo đoạn mô tả cấu hình trong clipboard; `Share` dùng Web Share API nếu có, fallback copy; `Contact Bougie` chỉ bật khi có URL liên hệ hợp lệ. Không lưu thông tin cá nhân trên server; dữ liệu chỉ ở browser, có nút reset.

### 4.9 Workshop — Make Your Own Moment
- Hero workshop bằng ảnh thật (sau khi xác nhận quyền dùng), typography nghệ thuật.
- Timeline 3 bước: `Explore scents` → `Create your candle` → `Take your creation home`.
- Nêu đúng tài liệu: **2 buổi/tháng**, **1.000.000đ/người**, người tham gia tự làm nến với hướng dẫn và mang sản phẩm về.
- CTA `Ask About Upcoming Workshops` → kênh liên hệ thực, **không hiển thị ngày tổ chức chưa được cung cấp**.
- Motion: giọt sáp chảy/đổ khuôn bằng video hoặc animation lightweight; không cần physics nặng.

### 4.10 Our Story & brand differentiators
- Brand story: thành lập 2026 tại Hà Nội; nến thơm dành cho không gian sống, thư giãn, quà tặng.
- 4 pillars: `Mood-led discovery`, `Personalized gifting`, `Creative workshops`, `Modern minimalist design`.
- Scent recommendation service có thể được diễn giải bằng Mood Finder client-side; không quảng bá AI thật.
- Tránh tuyên bố khoa học về chữa bệnh, giảm lo âu hoặc cải thiện giấc ngủ.

### 4.11 Contact / final conversion
Final full-bleed scene với ngọn nến cháy nhẹ và CTA `Let's Create Your Moment`.
- Liên hệ: Instagram / Facebook / TikTok / email chỉ khi team cung cấp URL.
- Social links có external indicator và aria-label.
- Có thể thêm nút `Copy product inquiry` hoặc `Copy workshop inquiry` để người dùng chủ động gửi qua social.
- Không làm contact form giả nhận dữ liệu rồi không gửi đi.

## 5. Animation & 3D system
### Priority P0 (bắt buộc)
1. Hero 3D candle với idle rotation, hover tilt, flame animation và poster fallback.
2. Scroll reveal bằng transform/opacity; không animate layout properties tốn CPU.
3. Mood Finder chuyển palette, ảnh/model, copy mượt.
4. Product transitions crossfade / depth effect.
5. Customizer live preview + 4 bước hoạt động thật trong browser.

### Priority P1 (nâng cao)
6. Cinematic scroll handoff giữa hero và collection (chỉ desktop đủ hiệu năng).
7. 3D gift-box opening ở Seasonal.
8. Animated scent ribbons/particles bằng shader hoặc SVG tối ưu.
9. Magnetic buttons rất nhẹ, liquid hover, smooth section transitions.

### Priority P2 (chỉ làm sau khi đo hiệu năng)
10. Refraction/glass shader, realistic wax subsurface look, bloom có kiểm soát.
11. Pointer-driven scene lighting, cinematic camera transitions.
12. Ambient sound **mặc định tắt**, chỉ phát sau hành động chủ động; có nút mute rõ ràng.

**Motion spec:** duration micro 150–250ms, card 300–500ms, scene 700–1100ms; easing `cubic-bezier(.22,1,.36,1)`. Không dùng scroll hijacking. Hỗ trợ `prefers-reduced-motion`: tắt auto rotation, particles, parallax và chuyển cảnh phức tạp, vẫn đủ nội dung.

**3D constraints:** 1 WebGL canvas chính khi có thể; giới hạn DPR khoảng 1–1.75 tùy thiết bị, texture nén WebP/AVIF/KTX2 nếu phù hợp, lazy-load GLB, dispose geometries/materials khi unmount, IntersectionObserver để pause render offscreen. Mobile low-end dùng ảnh/video poster hoặc scene đơn giản. Không để canvas chặn scroll/click.

## 6. Stack và cấu trúc code đề xuất
- **Vite + React + TypeScript** cho SPA frontend-only; React Router cho route.
- **Tailwind CSS** + CSS custom properties để giữ design system; component primitives accessible.
- **Three.js + React Three Fiber + Drei** cho 3D; **GSAP + ScrollTrigger** cho timeline scroll phức tạp, **Framer Motion / Motion** cho microinteractions nếu cần. Tránh animate cùng một element bằng 2 thư viện.
- **Lucide** icons; React Helmet Async hoặc giải pháp prerender/static generation để đảm bảo SEO metadata; nếu SEO là mục tiêu lớn, ưu tiên **Astro + React islands** thay cho SPA thuần (vẫn frontend-only/static hosting).
- Content lưu ở `src/data/*.ts` hoặc `src/content/*.json`, không hardcode trong component.

```text
src/
  app/                # routing, providers, page shell
  pages/              # Home, Collection, Product, Seasonal, Customize, Workshop, Story, Contact
  components/
    layout/           # Header, MobileMenu, Footer, PageTransition
    ui/               # Button, Container, Typography, Tabs, Modal, Toast
    sections/         # Hero, Manifesto, MoodFinder, ProductShowcase, Seasonal, etc.
    three/            # CandleScene, CandleModel, Flame, SceneFallback, GiftBoxScene
    customize/        # Stepper, OptionPicker, LabelEditor, LivePreview, Summary
  data/               # products, seasonal, navigation, brand content
  hooks/              # useReducedMotion, useMediaQuery, useWebGLSupport
  styles/             # tokens, globals, motion
  assets/             # optimized photos, poster images, models, fonts (licensed)
  utils/              # currency, share/copy, validation
public/
  og/                 # social preview images
  models/             # optimized .glb
  images/             # responsive product/lifestyle assets
```

## 7. Component contracts và state
- `Product`: `id`, `slug`, `name`, `tagline`, `mood`, `notes[]`, `description`, `useCases[]`, `image`, `model?`, `priceDisplay`, `status`.
- `SeasonalEdition`: `id`, `name`, `priceVnd`, `occasion`, `story`, `image`, `status`.
- `Customization`: `scentId`, `jarColorId`, `labelTemplateId`, `personalMessage`, `recipientName?`, `dateText?`.
- `ContactConfig`: `email?`, `instagram?`, `facebook?`, `tiktok?`; chỉ render kênh có URL hợp lệ.
- Mood Finder state: `selectedMood`, có default hợp lý, cập nhật `aria-pressed`/tab state và live content.
- Wizard state: validate text, reset, preview và copy; không thu thập hoặc lưu PII lâu dài.

## 8. Responsive design & accessibility
- Breakpoints: mobile 360–767px, tablet 768–1023px, desktop 1024–1439px, wide >=1440px.
- Mobile hero: headline trước, ảnh/3D sau; CTA luôn thấy, canvas không vượt màn hình.
- Mobile product explorer: swipe **và** nút điều hướng, không bắt buộc gesture; cards có vùng chạm >=44px.
- Font body tối thiểu 16px, line-height >=1.5; contrast tối thiểu WCAG AA, visible focus ring, alt text, semantic headings.
- Dialog/menu focus trap đúng, Escape đóng, restore focus; mọi chức năng có thể dùng bàn phím.
- Video không autoplay có âm thanh; 3D mang tính trang trí có mô tả văn bản tương đương.
- Bilingual có thể bổ sung sau; bản đầu ưu tiên tiếng Anh theo nội dung thương hiệu trong Word, cấu trúc content cho phép chuyển sang tiếng Việt.

## 9. Performance, SEO và analytics
- Targets: LCP <=2.5s, CLS <=0.1, INP <=200ms tại thiết bị mạng phổ thông theo điều kiện đo thực tế; không đảm bảo bằng cảm tính.
- Tải hero poster trước; WebGL hydrate sau khi nội dung đầu đã hiển thị; preload đúng 1 ảnh hero và font cần thiết.
- Responsive images `srcset/sizes`, AVIF/WebP, lazy load ngoài viewport, tránh video nặng trong critical path.
- Metadata title/description riêng từng route, OG image, canonical, sitemap và robots; JSON-LD Organization/Product chỉ khi thông tin thực sự xác minh.
- Analytics privacy-friendly chỉ khi được cấu hình, theo dõi `hero_cta_click`, `mood_selected`, `product_view`, `customizer_completed`, `contact_click`; không gửi dữ liệu lời nhắn cá nhân.
- Static deployment: Vercel/Netlify/Cloudflare Pages; cấu hình fallback route SPA hoặc prerender tùy stack.

## 10. Assets cần chuẩn bị
**Bắt buộc:** logo vector Bougie, 4 ảnh hero/product Mood, 3 ảnh Seasonal, ảnh workshop có quyền sử dụng, 1–2 ảnh brand story, thông tin liên hệ chính thức.

**Khuyến khích:** 1 GLB candle base có các material variants, label texture, 3 gift-box variants, 4–6 lifestyle short clips, favicon, OG image. Khi thiếu GLB: dùng ảnh compositing + CSS 3D transform có chất lượng, không chặn triển khai.

**Reference từ Word:** trang 8 (Mood Collection), trang 10 (Seasonal), trang 11 (Customized Candle), trang 11–13 (Workshop), trang 14 (brand differentiators). Hình trong báo cáo chỉ làm reference cho bố cục, màu sắc và sản phẩm, cần kiểm tra độ phân giải/quyền sử dụng.

## 11. Phân kỳ Codex
### Phase 1 — Foundation
Tạo project, design tokens, font, responsive layout, routes, data models, header/footer, accessible components, SEO metadata. Render đầy đủ content không cần 3D.

### Phase 2 — Brand landing
Xây hero, manifesto, Mood Finder, collection, seasonal, workshop, story, contact. Chỉnh bố cục desktop/mobile trước khi thêm hiệu ứng nặng.

### Phase 3 — Interactive frontend
Xây detail page, customizer wizard, live label preview, copy/share, state management, error/empty states. Tất cả CTA hoạt động, không có dead buttons.

### Phase 4 — 3D & cinematic motion
Thêm CandleScene, flame, scroll choreography, gift box scene, scent particles; fallback, reduced motion, mobile performance.

### Phase 5 — QA & polish
Lighthouse, axe accessibility, Playwright E2E, responsive screenshot, SEO, bundle analysis, broken-link check, cross-browser QA.

## 12. Acceptance criteria / Definition of Done
- [ ] Toàn bộ thông tin sản phẩm đúng tài liệu; giá Mood theo khoảng, Seasonal và workshop chính xác.
- [ ] Không có backend, auth, cart, payment, fake booking hoặc fake reviews.
- [ ] Có đủ các trang/section trong sitemap, mọi route và CTA hoạt động.
- [ ] Mood Finder chọn được cả 4 mood và thay nội dung/visual tương ứng.
- [ ] Configurator 4 bước có preview, validate, reset, copy summary, không gửi dữ liệu lên server.
- [ ] 3D hero hoạt động trên desktop hỗ trợ WebGL; mobile/reduced-motion có fallback rõ ràng.
- [ ] 360px, 390px, 768px, 1024px, 1440px không tràn ngang; menu mobile usable.
- [ ] Keyboard navigation, contrast, alt text, focus states, reduced-motion đạt yêu cầu.
- [ ] Không có lỗi console nghiêm trọng, ảnh vỡ, placeholder link giả hoặc animation che nội dung.
- [ ] Build production thành công; asset được tối ưu; các chỉ số Core Web Vitals được đo và báo cáo.

## 13. Prompt trực tiếp cho Codex

```text
Bạn là Senior Creative Frontend Engineer + UI/UX Designer. Hãy xây dựng website marketing frontend-only cho Bougie dựa trên toàn bộ file BOUGIE_FRONTEND_DESIGN_SPEC.md này. Ưu tiên giao diện editorial luxury trẻ trung, mềm mại, 3D cinematic và UX có ý nghĩa. Không tạo backend, API, login, cart, checkout hay dữ liệu giả như đánh giá/tồn kho/lịch workshop.

Thực hiện theo phases; trước tiên xây hệ thống design và responsive layout đẹp, sau đó interactions, rồi mới bổ sung 3D có fallback. Mọi nội dung sản phẩm phải khớp spec. Nếu thiếu asset, tạo placeholder có chú thích rõ và giữ bố cục hoàn chỉnh; không tự chế thông số hoặc đường dẫn social. Tạo code TypeScript sạch, reusable components, semantic HTML, keyboard accessibility, prefers-reduced-motion, lazy loading và tối ưu Core Web Vitals.

Sau mỗi phase chạy build/lint và sửa lỗi. Cuối cùng báo cáo cấu trúc source, cách chạy, những asset cần thay thế, các trang đã hoàn thiện, kiểm thử responsive/a11y/performance và các mục chưa thể xác minh.
```

## 14. Các thông tin cần nhóm xác nhận trước khi public
1. Logo chính thức, brand colors và quyền dùng ảnh trong báo cáo.
2. Giá chính xác của từng SKU Mood (nếu muốn hiển thị riêng từng nến).
3. Tình trạng bán thực tế của từng seasonal edition và các lựa chọn tùy chỉnh có sẵn.
4. Link Instagram/Facebook/TikTok/email chính thức; cách tiếp nhận yêu cầu tư vấn.
5. Thời gian/địa điểm workshop thực tế nếu muốn công bố lịch.
6. Ngôn ngữ website chính thức: tiếng Anh, tiếng Việt hay song ngữ.
