# SYNERA UI — BankDash-inspired

Thiết kế hiện tại lấy cảm hứng thị giác từ Figma Community: “BankDash - Dashboard UI Kit - Admin Template Dashboard - Admin Dashboard”. Đây là bản chuyển thể cho dashboard vận hành SYNERA, không phải bản sao từng màn hình hay chức năng ngân hàng. Luồng nghiệp vụ, nội dung và số liệu vẫn là của prototype.

## Hướng thiết kế

- Nền xanh ngọc–xanh trời có vùng sáng mờ; sidebar, header và card dùng kính mờ nhẹ. Điều hướng đang chọn và CTA dùng gradient tím–xanh dương–cyan theo màu nhận diện.
- Canvas xám xanh nhạt, card trắng bo góc lớn, viền tinh tế và đổ bóng nhẹ.
- Dashboard có lời chào, KPI theo thao tác, đơn cần xử lý, tồn kho, việc cần làm, gợi ý và hành trình.
- Không thêm số dư tài khoản, doanh thu, giao dịch ngân hàng hoặc biểu đồ giả để bắt chước nội dung BankDash.
- Duy trì responsive, drawer trên mobile, focus bàn phím và reduced-motion.
- Chuyển cảnh, hover và thao tác dùng chuyển động “liquid glass” nhẹ: nội dung vào mềm, ánh sáng lướt trên nút, tab có gạch chân chuyển động; tôn trọng `prefers-reduced-motion`.
- GSAP React quản lý stagger chuyển trang, KPI đếm số và ScrollTrigger cho panel phía dưới viewport; animation được cleanup khi đổi route hoặc unmount.

## Quy tắc SYNERA

Giữ luồng xác nhận đơn → giữ hàng; xác nhận kiện; chủ/người có quyền xác nhận đặt giao; bàn giao thực → xuất kho một lần. Kho không nhận dữ liệu tiền hàng/COD/công nợ. Gợi ý vẫn phải có căn cứ và người xác nhận. Không sao chép các chức năng khuyến mại, kế toán thuế hay marketplace ngoài phạm vi SYNERA.

## Source

- `app/admin-layout.css`: theme BankDash-inspired, bố cục quản trị và responsive.
- `app/synera.css`: primitives, component cơ bản, trạng thái và responsive.
- `app/views/dashboard.jsx`: bố cục tổng quan và KPI vận hành.
- `app/views/operations.jsx`: danh sách và hàng đợi xử lý.
- `app/interface.jsx`: shell, thu gọn sidebar, tìm kiếm và deep link.
- `design-system/synera/MASTER.md`: token và quy tắc thiết kế hiện hành.

Các chức năng chưa triển khai đầy đủ tiếp tục được ghi tại COVERAGE.md. Đây là prototype với dữ liệu minh họa, chưa nối hệ thống vận chuyển hay dịch vụ thật.
