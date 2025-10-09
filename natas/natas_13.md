## 🕵️‍♂️ Challenge:
Username: natas13  
Password: trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC  
URL: http://natas13.natas.labs.overthewire.org  

<img width="1377" height="645" alt="image" src="https://github.com/user-attachments/assets/ca4c5858-02ad-4d0a-9a67-ed2f533f2037" />


## 📝 Solution: 
Giống thử thách trước nhưng lần này họ đã có cơ chế kiểm tra, chỉ chấp nhận các file dạng ảnh.  

<img width="977" height="982" alt="image" src="https://github.com/user-attachments/assets/bf6b890a-9f1e-42a1-9988-b486624f5bb2" />

Ta có thể thấy hàm exif_imagetype() là hàm kiểm tra định dạng của một file ảnh dựa vào các bytes đầu tiên chứ không dựa vào phần mở rộng (.jpg, .png, .gif, ...).  
Vậy nên, ta có thể đánh lừa hàm này bằng cách thêm các byte định dạng ảnh vào phần đầu nội dung file php.  
Trước tiên, tìm các tiêu đề của các dạng ảnh phổ biến:  

<img width="597" height="395" alt="image" src="https://github.com/user-attachments/assets/a73b6b83-e2ac-4c36-8f87-91ed6b5e2f6f" />

Mình sẽ lấy định dạng BMP cho dễ, chèn `BM` vào đầu nội dung file PHP:  
```php
BM<?php
header('Content-Type: text/plain; charset=utf-8');
echo file_get_contents('/etc/natas_webpass/natas14');
```
Ở devtool, chỉnh jpg thành php:  

<img width="1150" height="423" alt="image" src="https://github.com/user-attachments/assets/bf2355fe-5cb4-46b4-9980-b3bcbe433369" />

Sau đó upload file php vừa soạn:  

<img width="717" height="332" alt="image" src="https://github.com/user-attachments/assets/777455db-8f7c-4734-bd80-3968a6b2c34d" />

Nhấn vào file php đó để thực thi:  

<img width="865" height="282" alt="image" src="https://github.com/user-attachments/assets/76320284-40d2-4ea4-99db-910e1ac15518" />

>### 🎯 Password: ***BMz3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ***
