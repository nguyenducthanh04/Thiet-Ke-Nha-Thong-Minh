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
## Phần cứng:
- Camera (sử dụng Camera laptop)
- Đầu lọc thẻ từ RFID
- Cảm biến khí gas
- Cảm biến ánh sáng
- Đèn và còi báo động
- Arduino
- Động cơ servo
## Phần mềm:
- Thư viện face_recognition và OpenCV trong Python
- Ứng dụng pushover
# Yêu cầu hệ thống
## Phần cứng:
- Arduino, 3 đèn led, còi, cảm biến khí gas, cảm biến ánh sáng, 3 servo, đầu lọc thẻ từ
- Cáp USB để kết nối máy tính với Arduino
## Phần mềm:
- Python (xử lý nhận diện khuôn mặt, điều khiển cửa và thực hiện gửi thông báo)
- Arduino IDE (nạp code Arduino)
- Pushover (dùng để gửi thông báo) 
## Cài đặt thư viện cần thiết
```pip3 install opencv-python pyserial requests flask numpy```
# Hướng dẫn cắm dây bảng mạch
Cắm dây đối với chức năng mở cửa khuôn mặt, cảnh báo khí gas, cảm biến ánh sáng: 

![image](https://github.com/user-attachments/assets/9b38467c-faf5-454c-b03c-c991f0fdf566)

Cắm dây đối với chức năng mở cửa bằng thẻ từ RFID:
- Kết nối RFID với Arduino

![image](https://github.com/user-attachments/assets/ca694cb4-f1fd-4984-8a1b-5783add3cd02)

- Kết nối servo với Arduino

![image](https://github.com/user-attachments/assets/f1a1dfc6-2b99-4303-87ec-59e3eb19dfbc)

# Hướng dẫn cài đặt và chạy chương trình
## Chuẩn bị phần cứng
- Nạp mã Arduino cho chức năng mở cửa bằng khuôn mặt, cảnh báo khí gas, cảm biến ánh sáng:
  + Mở file FaceGasLightControl.ino bằng Arduino IDE
  + Kết nối board Arduino với máy tính
  + Chạy nạp mã nguồn vào board
  + Đảm bảo chạy cổng COM8 để phù hợp với mã trong file face_recognition_with_web.py
- Nạp mã Arduino cho chức năng mở cửa bằng thẻ từ:
  + Mở file RFIDDoor.ino bằng Arduino IDE
  + Kết nối board Arduino với máy tính
  + Chạy nạp mã nguồn vào board
## Cài đặt python
Cài đặt python về máy và cài các thư viện phía trên bằng pip
## Cài đặt và đăng ký ứng dụng pushover
- Cài đặt ứng dụng về máy điện thoại bằng AppStore hoặc CH Play
- Đăng ký tài khoản trên pushover để lấy key sử dụng
## Các bước chạy chương trình
- Bước 1: Chạy file capture_faces.py để thiết lập khuôn mặt và lưu hình ảnh vào folder data_set (python capture_faces.py). Ứng dụng sẽ chạy sau đó camera máy tính mở lên, bạn cần nhập tên người dùng vào terminal sau đó enter để camera chụp lại khuôn mặt của bạn và lưu vào folder data_set.
- Bước 2: Chạy file train_faces.py để training chương trình sau khi lưu xong khuôn mặt (python train_faces.py).
- Bước 3: Chạy file face_recognition_with_web.py để sử dụng chức năng nhận diện khuôn mặt và thông báo khí gas (python face_recognition_with_web.py).
# Hướng dẫn sử dụng 
1 Nhận diện khuôn mặt mở cửa: 
- Người dùng đưa khuôn mặt vào camera để nhận diện.
- Nếu nhận diện đúng với khuôn mặt đã lưu cửa sẽ tự động mở ra.
- Sai khuôn mặt sẽ hiển cảnh báo đồng thời cửa sẽ không mở.
2 Quét thẻ từ mở cửa:
- Người dùng đưa thẻ từ vào quét.
- Nếu đúng mã thẻ cửa sẽ mở.
- Sai mã thẻ sẽ không mở cửa.
- Nếu cửa đang mở chờ hết 1 phút cửa sẽ tự động đóng.
3 Cảnh báo khí gas:
- Sử dụng bật lửa xì gas vào cảm biến.
- Cảm biến phát hiện khí gas còi sẽ kêu, đèn nhấp nháy, cửa sổ mở và thông báo qua pushover.
4 Cảm biến ánh sáng bật đèn:
- Chỉ cần lấy tay che toàn bộ cảm biến hoặc để cảm biến vào nơi thiếu ánh sáng.
- Đèn sẽ tự động bật.
# Poster
![Poster_CNTT5_ThanhNguyen](https://github.com/user-attachments/assets/88c03204-924c-4363-b59b-c254b1a99b39)

