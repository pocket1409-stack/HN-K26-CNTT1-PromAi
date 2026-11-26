# BÀI LÀM PHA 1 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:Trần Thiện Thuật
- **Lớp:CNTT1
- **Link repository Pha1:https://github.com/pocket1409-stack/HN-K26-CNTT1-PromAi

> Pha 1 (70 phút đầu, KHÔNG dùng AI). Viết xong, kéo thả file này vào repository Pha1 trước mốc giờ giám thị công bố.

## 4.1. Bảo vệ dữ liệu và chống ảo giác

### a) Ghi chú đã ẩn danh hoá

**GHI CHU DA AN DANH**

```text
Khách hàng {TEN_KHACH}
SĐT {SO_DIEN_THOAI}
CCCD {CAN_CUOC_CONG_DAN}
email {email}

```

### b) Hai câu lệnh chống ảo giác

**CAU LENH**

```text

```

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**PROMPT**

```text
C - Context: Bạn là nhân viên mới của Đất Việt WorkShop.

R - Request: Mở 3 lớp trải nghiệm :nặn gốm bằng tay,làm gốm bàn xoay và vẽ trang trí gốm.

E - Explanation: Mỗi đối tượng JSON đại diện cho một tin nhắn và phải có đầy đủ 5 trường dữ liệu: 
QUY TẮC CHUẨN HOÁ (5 quy tắc)
1. ma_lop lấy theo bảng mã lớp.
2. ngay_hoc dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc trẻ em thì tre_em là 0 và mọi khách là người lớn.
4. ca_hoc chỉ nhận "sang", "chieu" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về sức khoẻ, đi lại, khó khăn khi thao tác; không có thì null.



A - Action: Phân tích từng tin nhắn theo các ví dụ mẫu dưới đây:

Tin nhắn mẫu 1:
Đăng ký giúp mình lớp vẽ gốm ngày 09/11/2026, 1 người lớn 2 bé, ca sáng nha. Một bé thuận tay trái.
Kết quả đúng:
{"ma_lop": "VEGOM", "ngay_hoc": "2026-11-09", "nguoi_lon": 1, "tre_em": 2, "ca_hoc": "sang", "ghi_chu": "1 bé thuận tay trái"}

Tin nhắn mẫu 2:
Lớp bàn xoay còn chỗ ca chiều không ạ, em đi 1 mình, hôm nào cũng được.
Kết quả đúng:
{"ma_lop": "BANXOAY", "ngay_hoc": null, "nguoi_lon": 1, "tre_em": 0, "ca_hoc": "chieu", "ghi_chu": null}



T - Tone: Khách quan, chính xác, tuân thủ định dạng máy đọc (machine-readable).

E - Extras: Chỉ trả về duy nhất mảng JSON hợp lệ, không kèm theo lời chào hỏi, giải thích hay ký tự thừa nào khác.

<tin_nhan>
TN1: Cho mình 2 người lớn với 1 bé 10 tuổi học nặn gốm bằng tay ngày 13/12 nhé, ca chiều.

TN2: Đặt 3 chỗ lớp bàn xoay ngày 10/01/2027 ạ. Một người bị đau cổ tay.

TN3: Lớp vẽ gốm tháng 12 còn chỗ không ạ? Nhóm em 4 người lớn, một bạn đi xe lăn, học ca sáng.

</tin_nhan>
```

## 4.3. Báo giá bằng Chain-of-Thought

### a) Prompt

**PROMPT**

```text
Bước 1: Tính tiền người lớn.
Bước 2: Tính tiền trẻ em.
Bước 3: Tính tổng tiền học.
Bước 4: Tính giảm giá nhóm (nếu đủ điều kiện) và số tiền sau giảm giá.
Bước 5: Tính các phí nung và giao.
Bước 6: Tính tổng tiền cuối cùng phải thanh toán.

Dòng cuối cùng của câu trả lời bắt buộc viết theo đúng định dạng:
{RESULT: <tổng tiền> đồng }
```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text
yêu cầu cấu trúc JSON gồm đúng 4 trường hợp sau :
 -"hong_san_pham" (chuỗi ký tự-string): sản phẩm bị nứt, vỡ khi nung hoặc khi giao: hoàn 150.000 đồng cho mỗi sản phẩm bị hỏng.
- "giao_tre"(số nguyên):số sp giao sản phẩm trễ quá 7 ngày so với hẹn: tặng voucher 50.000 đồng/khách.
- "huong_dan"(chuỗi ký tự): khiếu nại về thái độ người hướng dẫn: tặng voucher 100.000 đồng/khách.
- "khac"(chuỗi ký tự): chuyển bộ phận Chăm sóc khách hàng xem xét, chưa đề xuất mức đền bù
```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. kết quả phân loại khiếu nại (JSON của Trạm 1) và chính sách đền bù. Chỉ dùng chính sách trong thẻ <chinh_sach> để tính tổng mức đền bù. Trả về đúng một đối tượng JSON, không giải thích

2.

### c) Câu lệnh viết tiếp

**CAU LENH**

```text
(viết email phản hồi khách: xin lỗi, nêu đúng mức đền bù trong JSON, không tự đặt mức khác, giọng điệu chân thành, chuyên nghiệp, dưới 150 từ.

```

## 4.5. Prompt chấm bài theo Rubric

**PROMPT**

```text
RUBRIC CHẤM (thang 10)
- Đúng thông tin (50%): giá và chính sách đổi lịch đúng với thông tin chuẩn.
- Đầy đủ (30%): trả lời đủ cả hai câu hỏi của khách và mời khách cung cấp ngày học, ca học, số người để đặt chỗ.
- Giọng điệu (20%): lịch sự, chuyên nghiệp, không dùng từ ngữ suồng sã.

```

## 4.6. Hoàn thiện System Prompt

> Phần Vai trò và Chuẩn đầu ra đã cho sẵn. Viết tiếp phần Quy tắc ràng buộc và Xử lý ngoại lệ.

```text
[Vai trò]
Bạn là "Trợ lý Đất Việt", nhân viên tư vấn trên website của Đất Việt Workshop, giúp khách chọn và đặt chỗ một trong 3 lớp: NANTAY (Nặn gốm bằng tay), BANXOAY (Làm gốm bàn xoay), VEGOM (Vẽ trang trí gốm).

[Quy tắc ràng buộc]
1.  Chính sách đổi lịch: đổi trước giờ học từ 48 giờ trở lên miễn phí; từ 12 đến dưới 48 giờ phí 30.000 đồng/người; dưới 12 giờ không được đổi.
2.
3.

[Chuẩn đầu ra]
Trả lời bằng tiếng Việt, lịch sự, tối đa 120 từ. Giá lớp trình bày dạng gạch đầu dòng. Kết thúc bằng một câu hỏi về nhu cầu tiếp theo của khách.

[Xử lý ngoại lệ]
- Khách hỏi ngoài phạm vi: Lịch sự xin lỗi khách hàng, nêu rõ bạn chỉ hỗ trợ tư vấn thông tin và ổi trước giờ học từ 48 giờ trở lên miễn phí; từ 12 đến dưới 48 giờ phí 30.000 đồng/người; dưới 12 giờ không được đổi.


- Khách cung cấp thiếu thông tin:
```
Lịch sự hỏi lại khách hàng chính xác các trường thông tin còn thiếu (như tên, lịch học) để kiểm tra chính xác; tuyệt đối không tự suy đoán hay bịa thông tin.