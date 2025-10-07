## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.  
For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.  
Note: localhost is a hostname that refers to the machine you are working on  

Commands you may need to solve this level  
> ssh, telnet, nc, openssl, s_client, nmap

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit13`, cổng `2220`  
```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

Khi đã ssh thành công, ta kiểm tra bên trong thì thấy có 1 khóa ssh riêng tư:  

<img width="619" height="534" alt="image" src="https://github.com/user-attachments/assets/e50b9821-2d58-4091-93a3-7568b6d9c964" />

Bây giờ, với khóa này, chạy lệnh sau để truy cập ssh vào máy bandit14:  
```bash
ssh -i sshkey.private -p 2220 bandit14@localhost
```

<img width="843" height="626" alt="image" src="https://github.com/user-attachments/assets/c435a49a-edd0-4953-8073-bb876ecfbc33" />

Như vậy là ssh thành công! Bây giờ lấy pass của bandit14 thôi:  
```bash
cat /etc/bandit_pass/bandit14
```
<img width="457" height="81" alt="image" src="https://github.com/user-attachments/assets/a33d54ee-2fcc-45f0-88a0-d6238b91493e" />


>### 🎯 Pass: ***MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS***
