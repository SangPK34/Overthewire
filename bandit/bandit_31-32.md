## 🕵️‍♂️ Challenge:  
### There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220.  
The password for the user bandit31-git is the same as for the user bandit31.  

Clone the repository and find the password for the next level.  

Commands you may need to solve this level  
> git

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit31`, cổng `2220`  
```bash
ssh bandit31@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy

Sau khi ssh thành công, tạo 1 thư mục tạm để clone repo github đề cho:  
```bash
tmp="$(mktemp -d)"
cd "$tmp"
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
```
Sau khi nhập pass, ta đã clone được 1 repo, cd vào nó để kiểm tra.  

<img width="645" height="243" alt="image" src="https://github.com/user-attachments/assets/d945d861-5bef-4b5a-903f-12e0ad01a3d7" />

Tệp `README` bắt ta phải đẩy một tệp lên kho lưu trữ. Vì vậy ta tạo tệp:  
```bash
echo 'May I come in?' > key.txt
```
Tuy nhiên ta ko thể đẩy file lên theo cách bình thường, vì tệp `.gitignore` chặn việc thêm các tệp `.txt`:  

<img width="607" height="179" alt="image" src="https://github.com/user-attachments/assets/2bc09eda-0494-448e-bca7-9ad9d6f9e2ec" />

Để khắc phục:  
```bash
git add -f key.txt
git commit -m "ahihi"
git push origin master
```
<img width="779" height="126" alt="image" src="https://github.com/user-attachments/assets/c803b59b-b26a-4db8-bee0-4e00f63f4011" />


<img width="914" height="616" alt="image" src="https://github.com/user-attachments/assets/fedd95dd-9d7d-4b20-a619-63c1ed82b982" />


>### 🎯 Pass: ***3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K***
