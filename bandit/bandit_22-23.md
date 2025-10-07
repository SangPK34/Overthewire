## 🕵️‍♂️ Challenge:  
### A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read.  
If you are having problems understanding what it does, try executing it to see the debug information it prints.  

Commands you may need to solve this level  
> cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit22`, cổng `2220`  
```bash
ssh bandit22@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

Tương tự với level trước, thử đọc nội dung của `cronjob_bandit23`  

<img width="781" height="383" alt="image" src="https://github.com/user-attachments/assets/068b0da5-a241-4866-bc91-133a5832aae4" />

<img width="862" height="325" alt="image" src="https://github.com/user-attachments/assets/31cbd8f1-f40a-4b1d-b740-df62c645cb0d" />

Nội dung file:  
> #!/bin/bash  
myname=$(whoami)  
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)  
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"  
cat /etc/bandit_pass/$myname > /tmp/$mytarget  

Phân tích: Đầu tiên, nó khởi tạo giá trị myname bằng lệnh whoami, ở đây là `bandit23`, sau đó, nó khởi tạo chuỗi `I am user bandit23` rồi chuyển thành giá trị md5:

> "8ca319486bfbbc3663ea0fbe81326349  -"

Tùy chọn `| cut -d ' ' -f 1` mục đích để lấy đúng chuỗi md5 là `8ca319486bfbbc3663ea0fbe81326349`.  

Sau đó sẽ ghi mật khẩu bandit23 vào file `/tmp/8ca319486bfbbc3663ea0fbe81326349`  
Vậy đọc nó thôi:  

<img width="738" height="77" alt="image" src="https://github.com/user-attachments/assets/7be38038-7c12-45fc-b34b-0a1ca811a2b9" />


>### 🎯 Pass: ***0Zf11ioIjMVN551jX3CmStKLYqjk54Ga***
