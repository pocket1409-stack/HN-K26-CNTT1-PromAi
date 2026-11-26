# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:Trần Thiện Thuâtk
- **Lớp:CNTT1
- **Link repository Pha2:https://gemini.google.com/share/example-link-42
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):ChatGPT

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**KET QUA AI**

```text
# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:** Trần Thiện Thuật
- **Lớp:** CNTT1
- **Link repository Pha2:** https://github.com/pocket1409-stack/HN-K26-CNTT1-PromAi
- **Công cụ AI đã dùng:** Gemini

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**KET QUA AI**

```json
[
  {
    "ma_lop": "NANTAY",
    "ngay_hoc": "2026-12-13",
    "nguoi_lon": 2,
    "tre_em": 1,
    "ca_hoc": "chieu",
    "ghi_chu": null
  },
  {
    "ma_lop": "BANXOAY",
    "ngay_hoc": "2027-01-10",
    "nguoi_lon": 3,
    "tre_em": 0,
    "ca_hoc": null,
    "ghi_chu": "một người bị đau cổ tay"
  },
  {
    "ma_lop": "VEGOM",
    "ngay_hoc": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "ca_hoc": "sang",
    "ghi_chu": "một bạn đi xe lăn"
  }
]
```

**Link trò chuyện:**

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
Bước 1: Tính tiền người lớn: 4 người lớn x 200.000đ = 800.000đ.
Bước 2: Tính tiền trẻ em: 2 trẻ em x 150.000đ = 300.000đ.
Bước 3: Tính tổng tiền học: 800.000 + 300.000 = 1.100.000đ.
Bước 4: Tính giảm giá nhóm: Nhóm có từ 4 người lớn trở lên được giảm 10% -> 1.100.000 x 10% = 110.000đ. Số tiền sau giảm: 990.000đ.
Bước 5: Tính các phí nung và giao: Phí nung 50.000đ/người cho 6 người = 300.000đ.
Bước 6: Tổng tiền cuối cùng phải thanh toán: 990.000 + 300.000 = 1.290.000đ.

{RESULT: 1.290.000 đồng }
```

**Link trò chuyện:**

### b) Kiểm tra kết quả AI

AI thực hiện hoàn toàn chính xác theo từng bước Chain-of-Thought: tính đúng tiền người lớn/trẻ em, áp dụng chính xác mức chiết khấu nhóm, cộng đúng phụ phí nung và trả về kết quả định dạng cuối cùng chuẩn xác.

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "hong_san_pham",
  "so_luong": 2,
  "muc_den_bu_du_kien": 300000,
  "tom_tat": "Sản phẩm bị nứt vỡ khi nung, khách yêu cầu đền bù 2 sản phẩm hỏng."
}
```

**Link trò chuyện:**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
Dựa trên Rubric chấm điểm (thang 10):
- Đúng thông tin (50%): Bài tư vấn nêu chính xác giá lớp học và chính sách đổi lịch chuẩn của workshop. (Điểm: 5.0/5.0)
- Đầy đủ (30%): Trả lời đầy đủ các thắc mắc của khách hàng và có câu mời khách cung cấp thông tin ngày học, ca học, số lượng để tiến hành đặt chỗ. (Điểm: 3.0/3.0)
- Giọng điệu (20%): Lịch sự, chuyên nghiệp, đúng mực. (Điểm: 2.0/2.0)
Tổng điểm: 10/10.
```

**Link trò chuyện:https://gemini.google.com/share/example-link-45
