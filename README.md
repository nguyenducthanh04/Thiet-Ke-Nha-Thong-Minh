# XÂY DỰNG THIẾT KẾ HỆ THỐNG NHÀ THÔNG MINH
 <div style="text-align: center;">

# Hệ thống nhà thông minh

</div>

Hệ thống nhà thông minh tích hợp các tính năng hiện đại như mở cửa bằng quét khuôn mặt và thẻ từ, cảnh báo rò rỉ khí gas cảnh báo bằng còi, đèn LED, tự động mở cửa sổ và gửi tin nhắn thông báo đến Pushover, cùng tự động bật đèn bằng cảm biến ánh sáng.
# Giới thiệu
- Mở cửa bằng khuôn mặt: Người dùng quét khuôn mặt để mở. Hệ thống xác định khuôn mặt khớp hay không khớp, nếu khớp sẽ tự động mở cửa và ngược lại sẽ không mở cửa.
- Mở cửa bằng thẻ từ: Người dùng sử dụng thẻ từ RFID để quét vào hệ thống xác nhận mở cửa, nếu khớp thẻ cửa sẽ tự động mở, nếu sai thẻ sẽ không mở cửa. Quét lại một lần nữa cửa sẽ tự động đóng hoặc để cửa mở hết 1 phút cửa sẽ tự động đóng lại. 
- Cảnh báo khí gas: Nếu hệ thống cảm biến khí gas phát hiện khí gas, đèn LED sẽ nhấp nháy, còi sẽ kêu lên, cửa sổ sẽ mở ra đồng thời sẽ gửi tin nhắn thông báo đến Pushover.
- Cảm biến ánh sáng bật đèn: Đèn LED sẽ tự động bật nếu môi trường cảm biến tiếp xúc thiếu ánh sáng.
# Hệ thống
![image](https://github.com/user-attachments/assets/04d9da18-c132-4642-96b0-d643cd312b08)
# Công nghệ sử dụng
Phần cứng:
- Camera (sử dụng Camera laptop)
- Đầu lọc thẻ từ RFID
- Cảm biến khí gas
- Cảm biến ánh sáng
- Đèn và còi báo động
- Động cơ servo
- Arduino
Phần mềm:
- Thư viện face_recognition và OpenCV trong Python
- Ứng dụng pushover
# Yêu cầu hệ thống
Phần cứng:
- Arduino, 3 đèn led, còi, cảm biến khí gas, cảm biến ánh sáng, 3 servo, đầu lọc thẻ từ
- Cáp USB để kết nối máy tính với Arduino
Phần mềm:
- Python (xử lý nhận diện khuôn mặt, điều khiển cửa và thực hiện gửi thông báo)
- Arduino IDE (nạp code Arduino)
- Pushover(dùng để gửi thông báo) 
## Cài đặt thư viện cần thiết
```pip3 install opencv-python pyserial requests flask numpy```
# Hướng dẫn cắm dây bảng mạch
Linh kiện	Chân Arduino	Kết nối chi tiết
Gas Sensor (MQ-series)	A0	AO -> A0, VCC -> 5V, GND -> GND
Light Sensor 1 (LDR)	A1	LDR -> A1, 10kΩ -> 5V, GND
Light Sensor 2 (LDR)	A2	LDR -> A2, 10kΩ -> 5V, GND
Light Sensor 3 (LDR)	A3	LDR -> A3, 10kΩ -> 5V, GND
Buzzer (Active)	8	(+) -> 8 (qua 100-220Ω), (-) -> GND
LED Gas Warning	7	Anode -> 7 (qua 220Ω), Cathode -> GND
LED Light 1	6	Anode -> 6 (qua 220Ω), Cathode -> GND
LED Light 2	5	Anode -> 5 (qua 220Ω), Cathode -> GND
LED Light 3	4	Anode -> 4 (qua 220Ω), Cathode -> GND
Gas Servo	9	Signal -> 9, VCC -> 5V, GND -> GND
Face Servo	10	Signal -> 10, VCC -> 5V, GND -> GND

