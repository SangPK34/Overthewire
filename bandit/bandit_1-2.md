## 🕵️‍♂️ Challenge:  
## Level 0 → Level 1
### The password for the next level is stored in a file called readme located in the home directory.  
Use this password to log into bandit1 using SSH.  
Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

Commands you may need to solve this level  
> ls , cd , cat , file , du , find

## 📝 Solution:
Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit1`, cổng `2220`  
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

Khi đã ssh thành công, tiến hành kiểm tra các file đang có trên máy:  
```bash
ls
```

<img width="238" height="49" alt="image" src="https://github.com/user-attachments/assets/6a793b8b-ff2e-4f2b-bd50-d795f06e0b29" />

Ta thấy có 1 file với tên là 1 kí tự "-".  
Nếu mở trực tiếp bằng lệnh **`cat -`** sẽ ko thể mở được, vì trong câu lệnh linux, '-' được hiểu là 1 option của lệnh đó,  
Ví dụ **`ls -a`** thì **`a`** được coi là tùy chọn hiển thị cả các file ẩn.  
Vậy bây giờ làm sao để kiểm tra hoặc đọc file "-" này, chỉ cần ghi rõ đường dẫn của nó là được:  
```bash
file ./-
cat ./-
```
<img width="300" height="104" alt="image" src="https://github.com/user-attachments/assets/488d3589-c5a7-49bf-ae00-88c73fad4471" />

Như vậy là xong, ta có mật khẩu cho level tiếp theo.  

>### 🎯 Pass: ***263JGJPfgU6LtdEvgfWU1XP5yac29mFx***
