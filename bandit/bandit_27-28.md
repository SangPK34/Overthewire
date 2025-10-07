## 🕵️‍♂️ Challenge:  
### There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.  

Clone the repository and find the password for the next level.  

Commands you may need to solve this level  
> git

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit27`, cổng `2220`  
```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB

Sau khi ssh thành công, tạo 1 thư mục tạm để clone repo github đề cho:  
```bash
tmp="$(mktemp -d)"
cd "$tmp"
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
```
Sau khi nhập pass, ta đã clone được 1 repo, cd vào nó để kiểm tra.  

<img width="832" height="152" alt="image" src="https://github.com/user-attachments/assets/b5d916d4-a383-4d83-9739-be9faec2a02a" />

Như vậy là có file chứa mật khẩu ở trong luôn.  

>### 🎯 Pass: ***Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN***
