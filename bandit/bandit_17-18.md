## 🕵️‍♂️ Challenge:  
### There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new  

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19  

Commands you may need to solve this level  
> cat, grep, ls, diff

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit17`, cổng `2220`  
```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> EReVavePLFHtFlFsjn3hyzMlvSuSAcRD

Khi ssh thành công, kiểm tra bên trong thì thấy có 2 tệp:  

<img width="268" height="82" alt="image" src="https://github.com/user-attachments/assets/11c09700-88a0-4559-8282-4ee54dc8af31" />

Theo đề bài, mật khẩu cho level sau nằm trong `passwords.new` và là dòng duy nhất khác biệt giữa `passwords.old` và `passwords.new`.  
Ta dùng lệnh này để in ra sự khác nhau giữa nội dung 2 file:  
```bash
diff passwords.new passwords.old
```

<img width="480" height="118" alt="image" src="https://github.com/user-attachments/assets/b440dff6-13a2-4a89-b9d7-51172f0bead8" />

Như vậy là dòng khác biệt ở file new chính là pass cần tìm.  

>### 🎯 Pass: ***x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO***
