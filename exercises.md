python -m venv venv
.\venv\Scripts\activate
pip install -r requirements.txt
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
> *Khi temperature tăng dần từ 0.0 đến 1.5, câu trả lời đi từ mức độ chính xác, nhất quán và an toàn sang mức độ ngẫu nhiên, sáng tạo nhưng dễ bị lỗi diễn đạt và sai lệch thông tin. Ví dụ, ở mức 0.0 mô hình luôn chọn sự thật về "xuất khẩu cà phê", nhưng ở mức 1.5 câu chữ bắt đầu lộn xộn và có thể bịa đặt ra sự thật mới*

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *Nên đặt từ 0.0 đến 0.2 để đảm bảo câu trả lời luôn chính xác, đồng nhất*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *GPT-4o đắt hơn GPT-4o-mini đúng 16,67 lần.*

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *GPT-4o xứng đáng: Khi cần thực hiện các tác vụ phức tạp, đòi hỏi tư duy logic cao hoặc phân tích chuyên sâu. Ví dụ: Hệ thống tự động kiểm tra và phát hiện lỗi logic trong các điều khoản của hợp đồng kinh tế. GPT-4o-mini tốt hơn: Khi cần xử lý các tác vụ đơn giản, lặp đi lặp lại với số lượng lớn để tối ưu chi phí và tốc độ. Ví dụ: Hệ thống tự động phân loại hàng nghìn đánh giá của khách hàng thành "Tích cực" hoặc "Tiêu cực" mỗi ngày.*

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Streaming quan trọng nhất trong các ứng dụng đòi hỏi phản hồi ngay lập tức để giữ chân người dùng, như chatbot trò chuyện, trình soạn thảo có hỗ trợ AI, hoặc các tính năng “dự đoán tiếp theo”. Trong trường hợp này, việc nhận được những ký tự đầu tiên giúp giảm cảm giác chờ đợi và tăng tính tương tác tự nhiên. Ngược lại, non-streaming phù hợp hơn cho các tác vụ xử lý dữ liệu lớn, nơi mà kết quả hoàn chỉnh được tổng hợp sau cùng. Chẳng hạn, khi phân tích hàng loạt văn bản để trích xuất thông tin hoặc tóm tắt tài liệu dài, việc nhận toàn bộ dữ liệu cùng lúc sẽ dễ dàng xử lý hơn và không làm gián đoạn quy trình tổng thể. Hơn nữa, đối với các tác vụ không yêu cầu hiển thị tức thời hoặc yêu cầu nhiều bước xử lý nội bộ, non-streaming giúp tiết kiệm tài nguyên và đơn giản hóa việc quản lý trạng thái.* 


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
