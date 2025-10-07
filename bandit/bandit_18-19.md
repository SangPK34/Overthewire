## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Commands you may need to solve this level
> ssh, ls, cat
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit18`, cổng `2220`  
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

Tuy nhiên khi nhập đúng pass, server lại đóng luôn và trả về:  

> Byebye !  
Connection to bandit.labs.overthewire.org closed.

Vậy là ta sẽ ko thể vào được bên trong để dùng lệnh, nhưng liệu có thể thực hiện lệnh mà ko cần ssh vào bên trong ko?  
Có đó, hãy dùng 'lệnh' ngay sau lệnh ssh, khi nó hỏi mật khẩu thì nhập đúng mật khẩu và lệnh đó sẽ được thực hiện, ví dụ ở đây mình làm:   
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 'echo ehehehehe'
```
<img width="640" height="311" alt="image" src="https://github.com/user-attachments/assets/39ac898a-3d0b-43ab-a85c-368d50113b1c" />

Vậy bây giờ chỉ cần xem có file nào bên trong ko:  
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 'ls'
```

<img width="614" height="275" alt="image" src="https://github.com/user-attachments/assets/a4fb0815-9f6e-49f2-b781-166bfa219347" />

Vậy là có file readme, đọc nó:  
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat readme'
```

<img width="629" height="317" alt="image" src="https://github.com/user-attachments/assets/7bd157a2-bc2e-4826-9553-b7ecc04c1ecf" />

Vậy là xongggg.  

>### 🎯 Pass: ******
