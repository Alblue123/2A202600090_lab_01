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

> Với giá trị temperature càng thấp thì nội dung càng cố định hơn, do khi đặt temperature thấp thì model sẽ ưu tiên các token có xác suất cao nhất. Với giá trị temperature cao thì phân phối có xu hướng đều ra, khiến cho kết quả trở nên khác, có vẻ sáng tạo hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**

> Vì khách hàng cần câu trả lời chính xác và ổn định, em sẽ set temperature từ 0-0.3 sao cho kết quả không bị hallucinations và nhất quán.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**

> Tổng số token/ngày: 10.000 * 3 * 350 = 10.500.000
>
> Chi phí GPT-4o/ngày = 10.500.000*0,010
>
> Chi phí GPT-4o-mini/ngày = 10.500.000*0,0006
>
> Tỉ lệ đắt hơn: 16.67

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**

> Trường hợp chi phí cao hơn cho GPT-4o là xứng đáng như chatbot tư vấn, ở các lĩnh vực nhạy cảm như tài chính, y tế, cần dữ liệu chính xác và tránh rủi ro
>
> Trường hợp GPT-4o-mini tốt hơn: với những trường hợp câu hỏi đơn giản và lặp lại như giờ làm việc, chính sách chăm sóc khách hàng, etc.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)

> Streaming phù hợp cho các bài toán thời gian thực, ví dụ như chatbot CSKH, giúp người dùng nhận phản hồi ngay lập tức từng phần, cải thiện trải nghiệm tương tác. Non-streaming phù hợp cho các tác vụ backend hoặc xử lý nền, nơi không cần hiển thị kết quả ngay, mà chỉ cần kết quả cuối cùng sau khi xử lý xong.

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
