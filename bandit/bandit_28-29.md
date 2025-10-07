## 🕵️‍♂️ Challenge:  
### There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220.  
The password for the user bandit28-git is the same as for the user bandit28.  

Clone the repository and find the password for the next level.  

Commands you may need to solve this level  
> git

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit28`, cổng `2220`  
```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

Sau khi ssh thành công, tạo 1 thư mục tạm để clone repo github đề cho:  
```bash
tmp="$(mktemp -d)"
cd "$tmp"
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
```
Sau khi nhập pass, ta đã clone được 1 repo, cd vào nó để kiểm tra.  

<img width="686" height="279" alt="image" src="https://github.com/user-attachments/assets/09557394-4998-4152-a13d-0fa99196ccab" />
 
Mật khẩu bị ẩn, bây giờ hãy hiển thị lịch sử commit kèm theo phần thay đổi của từng commit.:  
```bash
git log -p
```
<img width="934" height="607" alt="image" src="https://github.com/user-attachments/assets/3e92cc01-0478-4d8d-8ac1-d79da74eb5ea" />

Như vậy pass đã lộ ra.  

>### 🎯 Pass: ***4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7***
