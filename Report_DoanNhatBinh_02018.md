# Báo cáo kết quả thực nghiệm LightGBM trên Azure

Khi khởi tạo máy ảo trên Azure, em chọn **Standard_B2as_v2** tại khu vực **Malaysia West** thay vì **Standard_B2s** như trong hướng dẫn do giới hạn tài nguyên của tài khoản sinh viên.

Thời gian huấn luyện mô hình **LightGBM** rất nhanh, chỉ khoảng **1,2 giây**. Tuy nhiên, dữ liệu có mức độ mất cân bằng lớn: tập train gồm **394 mẫu positive (lớp 1)** và **227.451 mẫu negative (lớp 0)**. Vì vậy, metric **Accuracy** đạt giá trị cao nhưng không mang nhiều ý nghĩa khi đánh giá khả năng phát hiện gian lận của mô hình.

Chỉ số **Precision = 0,6557**, nghĩa là trong số các mẫu được mô hình dự đoán là gian lận, khoảng **65,57%** thực sự là gian lận. Trong khi đó, **Recall = 0,8163**, cho thấy mô hình phát hiện được khoảng **81,63%** số giao dịch gian lận thực tế, ở mức tương đối tốt.

Thời gian inference của mô hình rất nhanh. Theo kết quả benchmark, mô hình có khả năng xử lý khoảng **1 triệu dòng mỗi giây**, cho thấy LightGBM phù hợp với các bài toán cần dự đoán với độ trễ thấp và throughput cao.
