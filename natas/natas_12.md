## 🕵️‍♂️ Challenge:
Username: natas12  
Password: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB  
URL: http://natas12.natas.labs.overthewire.org  

<img width="1408" height="523" alt="image" src="https://github.com/user-attachments/assets/919a701f-d1b9-48bb-bda4-d9399b60a465" />


## 📝 Solution: 
Đọc mã nguồn trang:  

<img width="1062" height="1001" alt="image" src="https://github.com/user-attachments/assets/6fc740fa-d756-4199-abd5-89dc21576b45" />

Ta thấy hàm `genRandomString()` tạo chuỗi độ dài 10 kí tự với mỗi kí tự lấy random từ chuỗi `0123456789abcdefghijklmnopqrstuvwxyz`.  

Hàm `function makeRandomPath($dir, $ext)` kết hợp với `genRandomString()` để tạo ra một đường dẫn file ngẫu nhiên, không bị trùng trong thư mục `$dir`.  

Hàm này `makeRandomPathFromFilename($dir, $fn)` giúp tự động lấy phần đuôi file từ tên file gốc `$fn`, rồi tạo một đường dẫn ngẫu nhiên tương ứng bằng hàm `makeRandomPath()`.

Đoạn `if(array_key_exists("filename", $_POST))` kiểm tra xem trong dữ liệu gửi bằng POST có biến filename không, nếu có thì xử lý upload, nếu không thì bỏ qua hoặc thông báo lỗi.  

`$target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);`: tạo đường dẫn ngẫu nhiên để lưu file trong thư mục `upload/`.  
Ví dụ:  
$_POST["filename"] = "avatar.png"  
makeRandomPathFromFilename() trả về `upload/a8f7c9z3xq.png` → đảm bảo không trùng file cũ.  

`filesize($_FILES['uploadedfile']['tmp_name']) > 1000`: Kiểm tra nếu file tạm (được PHP lưu khi upload) lớn hơn 1000 byte thì từ chối tải lên.  

`move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)`: Di chuyển file từ thư mục tạm sang vị trí đích `$target_path`.  
Nếu thành công thì in ra link tải, ví dụ:  

> The file <a href="upload/a8f7c9z3xq.png">upload/a8f7c9z3xq.png</a> has been uploaded

else cuối cùng
→ Trường hợp không có filename trong POST (người dùng không gửi tên file), có thể in thông báo lỗi hoặc bỏ qua.  

<img width="809" height="273" alt="image" src="https://github.com/user-attachments/assets/ab13ca5a-4eb8-4d95-a41f-0c0deeff77b2" />

Đoạn này ta có thể thấy nó sẽ đổi đuôi file mà ta upload lên thành dạng `.jpg`  

Sử dụng f12 để tìm đến đoạn code đó và sửa jpg thành php.  

Soạn 1 file php có nội dung:  
```php
<?php
header('Content-Type: text/plain; charset=utf-8');
echo file_get_contents('/etc/natas_webpass/natas13');
```
Ta sẽ lợi dụng lỗ hỏng file injection, do ko kiểm tra kĩ dạng file upload của web để đọc mật khẩu.  

Sau khi đã đổi jpg thành php trong devtool, ta nhấn tải lên file php đã soạn:  

<img width="490" height="273" alt="image" src="https://github.com/user-attachments/assets/42c9bea2-9c97-4c12-9908-031352a8d332" />

Nhấn vào file php để nó thực thi:  

<img width="898" height="249" alt="image" src="https://github.com/user-attachments/assets/31e5cd45-78ef-4312-a673-129b0dd12160" />

>### 🎯 Password: ***trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC***
