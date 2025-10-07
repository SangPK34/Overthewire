## 🕵️‍♂️ Challenge:  
### There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220.  
The password for the user bandit29-git is the same as for the user bandit29.  

Clone the repository and find the password for the next level.  

Commands you may need to solve this level  
> git

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit29`, cổng `2220`  
```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

Sau khi ssh thành công, tạo 1 thư mục tạm để clone repo github đề cho:  
```bash
tmp="$(mktemp -d)"
cd "$tmp"
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
```
Sau khi nhập pass, ta đã clone được 1 repo, cd vào nó để kiểm tra.  

<img width="566" height="233" alt="image" src="https://github.com/user-attachments/assets/0fe59c84-587e-43e5-b847-23150c0bc9da" />

Sử dụng lệnh sau để kiểm tra các nhánh của repo:  
```
git branch -a
```
<img width="580" height="140" alt="image" src="https://github.com/user-attachments/assets/a3ca646d-7bfb-4451-8f3d-fed551030b92" />

Thử di chuyển vào nhánh dev:  
```bash
git checkout dev
```

<img width="619" height="221" alt="image" src="https://github.com/user-attachments/assets/a11be881-9602-4f2d-a6c0-14c1783df865" />

Có 1 file README, đọc thử nó:  

<img width="571" height="181" alt="image" src="https://github.com/user-attachments/assets/d65c42d6-a282-4e1e-b570-847f1d0561ed" />

Vậy là xong.  

>### 🎯 Pass: ***qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL***
