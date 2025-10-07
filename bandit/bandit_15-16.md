## 🕵️‍♂️ Challenge:  
### The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.  

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.  

Commands you may need to solve this level  
> ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit15`, cổng `2220`  
```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

Khi ssh thành công, tiến hành gửi mật khẩu của cấp độ hiện tại tới cổng 30001 trên máy chủ cục bộ bằng mã hóa SSL/TLS:  
```bash
openssl s_client -connect localhost:30001
```

<img width="1091" height="854" alt="image" src="https://github.com/user-attachments/assets/f02b765a-0f27-470a-9b52-1acc0df5a669" />


>### 🎯 Pass: ***kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx***
