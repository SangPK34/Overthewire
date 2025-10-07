## 🕵️‍♂️ Challenge:  
### The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.  

Commands you may need to solve this level  
> ssh, telnet, nc, openssl, s_client, nmap

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit14`, cổng `2220`  
```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

ssh thành công vào máy bandit14, tiến hành gửi mật khẩu hiện tại cho máy chủ localhost, cổng 30000 qua lệnh netcat:  
```bash
nc localhost 30000
```
<img width="354" height="81" alt="image" src="https://github.com/user-attachments/assets/9837090c-8bca-4bee-a506-0cfa46a274cc" />

Sau khi nhận đúng pass, máy chủ netcat sẽ trả về pass cho level sau.  

>### 🎯 Pass: ***8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo***
