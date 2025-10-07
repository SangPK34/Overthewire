## 🕵️‍♂️ Challenge:  
### After all this git stuff, it’s time for another escape. Good luck!

Commands you may need to solve this level
sh, man

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit32`, cổng `2220`  
```bash
ssh bandit32@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K

Sau khi ssh thành công, ta sẽ thấy ở level này đang chạy 1 shell mà khiến mọi input của ta đều trở thành chữ in hoa.  

<img width="826" height="691" alt="image" src="https://github.com/user-attachments/assets/edb711cf-0acc-4d9b-b7ec-47e24865ed3f" />

Sau khi tìm hiểu trên mạng thì mình biết được rằng biến $0 tham chiếu đến 1 shell, ví dụ:  

<img width="460" height="87" alt="image" src="https://github.com/user-attachments/assets/3268a13b-f24e-4bbe-ad08-59a83cdeb7b3" />

Vậy để thực thi shell bash, nhập:  
```bash
$0
```
<img width="123" height="89" alt="image" src="https://github.com/user-attachments/assets/f9b16b1b-1cc2-4661-8d74-e60d47516b86" />

Như vậy là ta đã lấy lại được shell gốc, tiến hành lấy pass như bình thường.  

<img width="339" height="73" alt="image" src="https://github.com/user-attachments/assets/18296c3a-6850-4b35-a570-9b795954c270" />

>### 🎯 Pass: ***tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0***
