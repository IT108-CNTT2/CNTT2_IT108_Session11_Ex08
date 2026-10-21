# Phân tích lỗi Database và AutoFilter

## Phần 1: Phân tích lỗi

Bảng hiện tại đang vi phạm một số quy tắc Database như:

- Có dòng tiêu đề lớn `DANH SÁCH BÁO CÁO VIÊN...` nằm phía trên bảng, làm vùng dữ liệu không còn chuẩn.
- Có hàng trống nằm giữa các bản ghi nên AutoFilter có thể bị ngắt vùng.
- Dữ liệu như `CNTT` và `CNTT ` có khoảng trắng thừa nên Filter hiểu là 2 giá trị khác nhau.
- Có dòng `TỔNG SỐ CNTT: 45` nằm ngay trong vùng dữ liệu, đây không phải là một bản ghi.
- Mỗi hàng nên là một bản ghi hoàn chỉnh, không nên chèn tổng hoặc nội dung khác vào giữa bảng.

## Phần 2: Sửa lỗi và hoàn thiện

Trước hết nên đưa bảng về dạng:

| STT | Họ và tên | Khoa/Viện | Điểm xét duyệt | Trạng thái |
|---|---|---|---|---|
| 1 | Nguyễn Văn An | CNTT | 8.5 | Đã duyệt |
| 2 | Trần Thị Bình | CNTT | 7.9 | Chờ duyệt |
| 3 | Lê Minh Châu | Điện tử | 8.2 | Đã duyệt |

Xóa các hàng trống và chuyển dòng tổng ra ngoài vùng dữ liệu.

Để xóa khoảng trắng thừa ở cột Khoa/Viện, tạo cột phụ và dùng:

`=TRIM(C2)`

Sau đó kéo công thức xuống toàn bộ danh sách.

Tiếp theo Copy cột đã làm sạch → Paste Values để thay dữ liệu cũ.

Cuối cùng chọn toàn bộ bảng và nhấn:

`Ctrl + Shift + L`

Sau đó lọc:

- Khoa/Viện = `CNTT`
- Điểm xét duyệt `>= 8.0`

Khi dữ liệu đã sạch và bảng không còn hàng trống thì AutoFilter sẽ hoạt động đúng.
