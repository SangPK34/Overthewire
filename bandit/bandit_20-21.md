## 🕵️‍♂️ Challenge:  
### There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument.  
It then reads a line of text from the connection and compares it to the password in the previous level (bandit20).  
If the password is correct, it will transmit the password for the next level (bandit21).  

NOTE: Try connecting to your own network daemon to see if it works as you think  

Commands you may need to solve this level  
> ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit20`, cổng `2220`  
```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

Khi ssh thành công, kiểm tra thì thấy có file setuid, kiểm tra cách nó hoạt động:  

<img width="1473" height="120" alt="image" src="https://github.com/user-attachments/assets/82620eb3-1c60-4517-b853-166e171fa79f" />

Bây giờ ta sẽ sử dụng `netcat` tạo kết nối ở chế độ máy chủ, lắng nghe kết nối đến rồi đưa mật khẩu bandit20:  

```bash
echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 8386 &
```
Bây giờ chạy file setuid kia:  
```bash
./suconnect 8386
```

<img width="822" height="151" alt="image" src="https://github.com/user-attachments/assets/ad9ebb80-6cb9-4642-a8d8-73d5aa51ab37" />

Vậy là mật chuỗi mà netcat đưa đã khớp với mật khẩu bandit20 nó cần, nên nó trả mật khẩu level tiếp theo cho mình.  

>### 🎯 Pass: ***EeoULMCra2q0dSkYj561DX7s1CpBuOBt***
