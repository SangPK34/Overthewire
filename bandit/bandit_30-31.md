## 🕵️‍♂️ Challenge:  
### There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220.  
The password for the user bandit30-git is the same as for the user bandit30.  

Clone the repository and find the password for the next level.  

Commands you may need to solve this level  
> git

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit30`, cổng `2220`  
```bash
ssh bandit30@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

Sau khi ssh thành công, tạo 1 thư mục tạm để clone repo github đề cho:  
```bash
tmp="$(mktemp -d)"
cd "$tmp"
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
```
Sau khi nhập pass, ta đã clone được 1 repo, cd vào nó để kiểm tra.  

<img width="582" height="131" alt="image" src="https://github.com/user-attachments/assets/5c11fc77-90ea-48c5-8f6d-1fd99fe29615" />
 
Mọi cách ở level trước đều ko khả quan, thử kiểm tra các tag của repo:  
```bash
git tag
```
<img width="513" height="69" alt="image" src="https://github.com/user-attachments/assets/727d8dac-8e20-4639-9f0e-046080739499" />

Kiểm tra nó:  
```bash
git show secret
```
<img width="592" height="78" alt="image" src="https://github.com/user-attachments/assets/f6877dd2-a944-4871-9eb5-402a22e4137a" />

:D  

>### 🎯 Pass: ***fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy***
