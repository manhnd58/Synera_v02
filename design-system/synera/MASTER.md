# SYNERA design system — BankDash-inspired

Thiết kế lấy cảm hứng thị giác từ “BankDash - Dashboard UI Kit - Admin Template Dashboard - Admin Dashboard (Community)” trên Figma Community và được chuyển thể cho vận hành SYNERA. Giữ cấu trúc và nghiệp vụ sản phẩm; không sao chép nội dung, số liệu hay các tính năng ngân hàng.

## Nguyên tắc

- Sáng, gọn và dễ quét thông tin: sidebar trắng, nền xám xanh, card trắng.
- Dải chuyển sắc tím–xanh dương–cyan là màu nhận diện cho hành động và điều hướng đang chọn; trạng thái dùng màu riêng kèm nhãn chữ.
- Nền có sắc xanh ngọc–xanh trời với các vùng sáng mờ; sidebar, header và card dùng lớp kính mờ nhẹ để tạo chiều sâu nhưng vẫn giữ độ đọc.
- Phân cấp bằng khoảng trắng, card bo tròn, đường viền mảnh và shadow nhẹ thay vì khung đậm.
- Tập trung các việc vận hành có thể hành động ngay: đơn, tồn, gợi ý và hành trình.
- Không tạo số dư, doanh thu, giao dịch hoặc biểu đồ tài chính khi dữ liệu SYNERA không cung cấp.

## Tokens

| Vai trò | Token | Giá trị |
|---|---|---|
| Nền ứng dụng | `canvas` | `#F5F7FB` |
| Card, bảng, header | `surface` | `#FFFFFF` |
| Nền trung tính | `muted-surface` | `#F5F7FA` |
| Accent nhẹ | `accent` | `#F0EDFF` |
| Sidebar | `nav` | `#FFFFFF` |
| Điều hướng đang chọn | `nav-active` | `#654BC8` |
| Hover điều hướng | `nav-hover` | `#F5F2FF` |
| Văn bản chính | `text` | `#232323` |
| Văn bản phụ | `muted` | `#718096` |
| Hành động / link / focus | `primary` | `#654BC8` |
| Hover hành động | `primary-hover` | `#4E3BB0` |
| Viền | `border` | `#E6ECF2` |

Gradient thương hiệu: `linear-gradient(110deg, #7047C6 0%, #466BD0 54%, #147B9E 100%)`. Dùng gradient cho điểm nhấn lớn có nền đặc như CTA và mục điều hướng chọn; chữ link và focus dùng tím/xanh đơn sắc để giữ độ đọc và độ tương phản.

Trạng thái thành công, cảnh báo và lỗi tiếp tục sử dụng màu hiện có; không dựa vào màu duy nhất để truyền đạt trạng thái.

## Bố cục và thành phần

- Sidebar desktop 248px, trắng, điều hướng đang chọn tím–xanh chuyển sắc; có thể thu gọn và vẫn hỗ trợ drawer mobile.
- Header trắng cao 72px với tìm kiếm, thông báo, dữ liệu demo và bộ chọn vai trò.
- Content có khoảng đệm rộng; card radius 12–16px, viền sáng và shadow nhẹ.
- Dashboard: lời chào, bốn KPI điều hướng được, danh sách đơn, bảng tồn kho và cột phụ cho việc cần làm, gợi ý, hành trình.
- Nút, input, tab, badge và bảng dùng chung token để giữ nhất quán giữa các màn hình.
- Responsive: KPI chuyển từ bốn sang hai cột; màn hình nhỏ dùng một cột và giữ vùng chạm tối thiểu.

## Chuyển động

- Dùng nhịp chuyển động mềm có easing cho điều hướng, nút, tab, card, dialog và thông báo.
- Khi vào màn hình, nội dung xuất hiện với độ nâng và blur nhẹ; nút có ánh sáng lướt ngắn khi hover.
- Dùng backdrop blur nhẹ ở header/dialog/toast; tránh áp kính mờ lên vùng nội dung làm giảm độ đọc.
- GSAP điều phối chuyển trang, stagger KPI, đếm số, nội dung cuộn vào màn hình và dialog; CSS giữ các micro-interaction nhẹ.
- Dùng `useGSAP()` có scope và cleanup khi animation thuộc vòng đời React.
- ScrollTrigger chỉ áp dụng cho panel nằm ngoài viewport lúc mở trang, không pin nội dung dashboard.
- Chỉ animate transform/opacity; không tạo tween lặp liên tục hoặc cho mọi node cùng lúc.
- Bắt buộc tắt animation và transition khi `prefers-reduced-motion: reduce`.

## UX và nghiệp vụ

- Tôn trọng reduced motion, focus-visible, điều hướng bàn phím và nhãn truy cập.
- Giữ luồng xác nhận đơn → giữ hàng → xác nhận kiện → đặt giao → bàn giao thực → xuất kho.
- Các gợi ý phải có căn cứ và do người dùng xác nhận; giao diện không tự thực hiện giao dịch.
- Không đưa dữ liệu tiền hàng/COD/công nợ vào giao diện nhân viên kho nếu payload nghiệp vụ không cho phép.
- Mẫu và dữ liệu hiện tại chỉ phục vụ prototype; không kết nối hãng vận chuyển hay dịch vụ thật.

## Nguồn giao diện

- `app/admin-layout.css`: token theme, shell quản trị, card và responsive.
- `app/synera.css`: primitive, trạng thái, biểu mẫu và thành phần dùng chung.
- `app/views/dashboard.jsx`: cấu trúc dashboard và nội dung KPI.
- `components/synera/ui.jsx`: panel, bảng, nút, badge, form và dialog dùng lại.
- `app/interface.jsx`: sidebar, header, điều hướng và bộ chọn vai trò.
