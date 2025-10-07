## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.  
For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name.  
Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)  

Commands you may need to solve this level  
> grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit12`, cổng `2220`  
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

Ssh thành công, ta kiểm tra các file đang có thì có file data.txt với nội dung là 1 hexdump:  
Bây giờ tạo 1 folder tạm và di chuyển file data.txt vào:  

<img width="623" height="758" alt="image" src="https://github.com/user-attachments/assets/84f42ecd-6f51-403e-9468-79051a8e4a32" />

Lệnh `xxd <input_file> <output_file>` sẽ tạo 1 ra file hexdump của file input. Khi thêm tùy chọn `-r` sẽ là khôi phục hexdump.  
```bash
xxd -r data.txt  ok.data
```

<img width="1485" height="243" alt="image" src="https://github.com/user-attachments/assets/6c74f6a4-ffcf-4d90-80d4-5db005ce2bf6" />

Bây giờ kiểm tra định dạng file vừa khôi phục:  
```bash
file ok.data
```

<img width="1345" height="63" alt="image" src="https://github.com/user-attachments/assets/c8bbbaa6-3c17-456a-aa58-a4a55285eee3" />

Đây là 1 file gzip, giải nén nó bằng cách đổi đuôi về đúng dạng gzip là `.gz`, sau đó dùng lệnh `gunzip` để giải nén nó:  

<img width="493" height="74" alt="image" src="https://github.com/user-attachments/assets/27767299-2a47-4396-ba0a-a604befcf6ef" />

Kiểm tra file vừa giải nén được:  

<img width="416" height="36" alt="image" src="https://github.com/user-attachments/assets/76f35e75-cd4a-4ce2-8152-0e485635bf6d" />

Lần này là bzip2, tiếp tục đổi đuôi về `.bz2` và dùng `bunzip2` để giải nén:  

<img width="1298" height="107" alt="image" src="https://github.com/user-attachments/assets/4c2d566d-89c6-4931-81ee-fe879494fae7" />

Lần này lại được file gzip, làm tương tự:  

<img width="458" height="106" alt="image" src="https://github.com/user-attachments/assets/0d240488-611b-4d89-886b-baad102a87f5" />

Lần này lại tới file tar, đổi đuôi file về `.tar` rồi giải nén:  

<img width="488" height="72" alt="image" src="https://github.com/user-attachments/assets/6e1c7bc6-9b41-4675-9de5-15614ebd240e" />

Ta lại được file tar nữa, làm tương tự, tương tự và tương tự đến khi ra pass :D :  

<img width="1335" height="406" alt="image" src="https://github.com/user-attachments/assets/bdc8ea68-cf0c-4c34-a433-e022fe74aaba" />

Cuối cùng cũng ra.  


>### 🎯 Pass: ***FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn***
