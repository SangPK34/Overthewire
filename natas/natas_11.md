<img width="1482" height="759" alt="image" src="https://github.com/user-attachments/assets/ce530c2f-fd13-481d-96fb-37766dd95503" />## 🕵️‍♂️ Challenge:
Username: natas11  
Password: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk  
URL: http://natas11.natas.labs.overthewire.org  

<img width="1740" height="654" alt="image" src="https://github.com/user-attachments/assets/aa970471-d456-4b44-b9a6-84037e4771b1" />


## 📝 Solution: 
Xem source code:  

<img width="907" height="1010" alt="image" src="https://github.com/user-attachments/assets/b4059f1f-388e-4f42-b757-1b0a14ac8682" />

Dựa vào code, ta có thể hiểu cơ chế hoạt động của các hàm:  

$defaultdata = array(...): Khởi tạo mảng mặc định chứa showpassword và bgcolor.  

xor_encrypt($in): thực hiện XOR byte-theo-byte giữa chuỗi đầu vào và key (key sẽ lặp nếu ngắn). Vì XOR là nghịch đảo, hàm này dùng được cho cả mã hóa và giải mã.  

loadData($def): nạp dữ liệu người dùng từ cookie data. Cụ thể: nếu cookie data tồn tại thì base64_decode → gọi xor_encrypt để giải mã → json_decode thành mảng.  

Nếu mảng hợp lệ và có cả showpassword + bgcolor và bgcolor thỏa regex màu (#RRGGBB) thì gán vào $mydata. Nếu không hợp lệ, trả về $def (mặc định).  

saveData($d): lưu dữ liệu $d vào cookie data bằng cách json_encode($d) → xor_encrypt(...) (mã hóa) → base64_encode(...) → setcookie("data", ...).  

if(array_key_exists("bgcolor",$_REQUEST)) { ... } — nếu client gửi bgcolor hợp lệ (theo regex), cập nhật $data['bgcolor'].  

saveData($data); — cập nhật cookie với dữ liệu mới.  

Phần HTML: dùng $data['bgcolor'] để set background; nếu $data['showpassword']=="yes" thì in mật khẩu.  

Mục tiêu của chúng ta là tìm key xor, sau đó dùng input `{"showpassword":"no","bgcolor":"#ffffff"}` xor lại với khóa đó để được cookie mới, gán lại để lấy mật khẩu.  

Các bước:  
Đầu tiên lấy giá trị cookie data để xor với plaintext đã biết là: `{"showpassword":"no","bgcolor":"#ffffff"}`, sẽ được key xor:  

<img width="1482" height="759" alt="image" src="https://github.com/user-attachments/assets/61592406-14f9-4c30-a1cf-97514b14b529" />

Giá trị base64 của cookie Data hiện tại:  

> HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg=

Đem lên cyberchef để xor tìm key:  

<img width="1134" height="631" alt="image" src="https://github.com/user-attachments/assets/9442b442-452d-4ca3-a631-c6be1253a49d" />

Vậy key là các chuỗi được lặp lại liên tục:  

> eDWo

Bây giờ dùng nó để xor lại với chuỗi `{"showpassword":"yes","bgcolor":"#ffffff"}` sẽ được cookie cần:  

<img width="1171" height="616" alt="image" src="https://github.com/user-attachments/assets/a22e025a-7275-48b3-b6db-f1a315145f46" />

Vậy cookie tìm được là:  

> HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5

Gán vào Cookie data và reload trang thôi:  

<img width="1648" height="768" alt="image" src="https://github.com/user-attachments/assets/0c94109c-86f9-4b06-91be-31110230ff41" />


>### 🎯 Password: ***yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB***
