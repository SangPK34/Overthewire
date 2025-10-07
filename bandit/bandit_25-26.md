## 🕵️‍♂️ Challenge:  
### Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.  

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.  

Commands you may need to solve this level  
> ssh, cat, more, vi, ls, id, pwd
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit25`, cổng `2220`  
```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

ssh thành công, kiểm tra thì có 1 khóa ssh:  

<img width="285" height="64" alt="image" src="https://github.com/user-attachments/assets/4b9b0d87-6fe2-4048-a563-c70dd87e5ad1" />

Tiến hành đăng nhập ssh vào bandit26:  
```bash
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```
Ta có thể thấy máy chủ ssh bandit26 ngay lập tức bị đóng lại:  

<img width="631" height="178" alt="image" src="https://github.com/user-attachments/assets/66dd03f4-2ed1-42cb-a523-98f68f4c3817" />

Vậy nguyên nhân là gì, trước tiên chúng ta cần kiểm tra xem người dùng bandit26 đã sử dụng shell nào:  

<img width="866" height="293" alt="image" src="https://github.com/user-attachments/assets/0c11bd50-ce3a-4fdf-8392-1be4685e4a85" />

Chúng ta có thể thấy nó dẫn đến một tập lệnh có tên `showtext`, mở một tệp có tên là `text.txt` bằng `more`.  
Vậy nguyên nhân vừa kết nối ssh đã bị đóng là do lệnh more đã đọc hết file txt kia, có vẻ là do nó rất ngắn.  
Vậy ta phải làm sao để nó chưa thể đọc hết file txt ngay khi ssh vào được.  
Hãy kéo nhỏ tab terminal lại rồi ssh lại đi :D  

<img width="684" height="181" alt="image" src="https://github.com/user-attachments/assets/85a22aa1-ede7-4b79-bb78-d156b4f1bb78" />

Bây giờ hãy vào chế độ vim bằng phím v:  

<img width="583" height="321" alt="image" src="https://github.com/user-attachments/assets/25cdd07b-9f1c-4b1b-adce-08de21e92f44" />

Dùng lệnh sau để lấy lại shell:  
```bash
:set shell=/bin/bash
:shell
```

<img width="585" height="323" alt="image" src="https://github.com/user-attachments/assets/c94f7471-33dc-4b10-bc67-639ae008cf7b" />

Tuyệt, giờ thì lấy pass thôi:  
```bash
cat /etc/bandit_pass/bandit26
```

<img width="613" height="134" alt="image" src="https://github.com/user-attachments/assets/0cc22e7a-8dc1-4bd5-9bdc-64a76398a623" />

Done...  

>### 🎯 Pass: ***s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ***
