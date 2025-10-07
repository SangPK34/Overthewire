## 🕵️‍♂️ Challenge:  
### A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

Commands you may need to solve this level  
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit21`, cổng `2220`  
```bash
ssh bandit21@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> EeoULMCra2q0dSkYj561DX7s1CpBuOBt

Kết nối vào ssh, dựa vào đề bài, ta kiểm tra các chương trình chạy tự động theo chu kỳ, gọi là cron.
Các chương trình nằm ở `/etc/cron.d` kiểm tra bằng lệnh:  
```bash
ls -la /etc/cron.d
```
<img width="597" height="285" alt="image" src="https://github.com/user-attachments/assets/6dd1e6d4-79b9-4007-9f4b-9e0374f06e57" />

Ở level này, ta nên chú ý đến `cronjob_bandit22`.  
Đọc thử nó và phân tích:  
```bash
cat /etc/cron.d/cronjob_bandit22
```

<img width="557" height="57" alt="image" src="https://github.com/user-attachments/assets/3db38a37-1009-4c2a-98bb-dc9010b2a863" />

Từ output, ta thấy cronjob này chạy file `/usr/bin/cronjob_bandit22.sh` với tư cách người dùng `bandit22`.  
5 dấu * nghĩa là nó được chạy mỗi phút, mỗi ngày.  
Thử đọc nội dung file đó:  
```bash
cat /usr/bin/cronjob_bandit22.sh
```
<img width="638" height="88" alt="image" src="https://github.com/user-attachments/assets/eeef4309-6c7a-4fb3-b7c0-473db39f3866" />

Ta có thể hiểu là cứ mỗi chu kì, nó tạo thư mục `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` và lưu mật khẩu bandit22 vào đó.  
Đọc nó:  

<img width="747" height="89" alt="image" src="https://github.com/user-attachments/assets/b4f3fd74-1447-4833-97a9-f6f8e0258c91" />


>### 🎯 Pass: ***tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q***
