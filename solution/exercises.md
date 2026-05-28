# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, câu trả lời thường ổn định, trực tiếp và ít thay đổi giữa các lần chạy. Khi tăng lên 0.5 hoặc 1.0, mô hình bắt đầu diễn đạt tự nhiên và đa dạng hơn. Ở mức 1.5, câu trả lời có thể sáng tạo hơn nhưng cũng dễ lan man hoặc thêm chi tiết kém chắc chắn hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Với chatbot hỗ trợ khách hàng, tôi sẽ chọn temperature khoảng 0.2 đến 0.5. Mức này giúp câu trả lời vẫn tự nhiên nhưng ưu tiên sự ổn định, chính xác và hạn chế việc mô hình tự suy diễn thông tin không có căn cứ.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Mỗi ngày có khoảng 10.000 x 3 x 350 = 10.500.000 token đầu ra. GPT-4o có giá 0.010 USD mỗi 1K output token, còn GPT-4o-mini có giá 0.0006 USD mỗi 1K output token. Vì vậy GPT-4o đắt hơn khoảng 0.010 / 0.0006 = 16.67 lần. Với workload này, GPT-4o tốn khoảng 105 USD/ngày, còn GPT-4o-mini tốn khoảng 6.30 USD/ngày.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng với chi phí cao hơn trong các trường hợp cần chất lượng lập luận tốt, xử lý yêu cầu phức tạp, phân tích tài liệu quan trọng hoặc hỗ trợ người dùng trong tình huống có rủi ro cao. GPT-4o-mini phù hợp hơn cho các tác vụ khối lượng lớn như trả lời FAQ, chatbot hỗ trợ cơ bản, phân loại nội dung, tóm tắt ngắn hoặc các yêu cầu cần tối ưu chi phí và tốc độ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi câu trả lời dài hoặc người dùng cần thấy phản hồi ngay lập tức, ví dụ chatbot tư vấn, trợ lý học tập, công cụ viết nội dung hoặc hệ thống giải thích từng bước. Khi có streaming, người dùng không phải chờ toàn bộ câu trả lời hoàn tất mới bắt đầu đọc, nên trải nghiệm có cảm giác nhanh và tự nhiên hơn. Non-streaming phù hợp hơn khi phản hồi ngắn, cần xử lý hoặc kiểm duyệt toàn bộ kết quả trước khi hiển thị, hoặc khi ứng dụng cần trả về một JSON/kết quả có cấu trúc hoàn chỉnh.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
