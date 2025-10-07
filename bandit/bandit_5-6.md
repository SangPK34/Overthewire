## 🕵️‍♂️ Challenge:  
### The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:  

human-readable  
1033 bytes in size  
not executable  
Commands you may need to solve this level  
> ls , cd , cat , file , du , find
## 📝 Solution:

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit5`, cổng `2220`  
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

ssh thành công, kiểm tra xem có file hay folder nào ko thì thấy có folder `inhere`, vào trong kiểm tra thì thấy có rất nhiều folder khác:  

<img width="1169" height="151" alt="image" src="https://github.com/user-attachments/assets/e22594f0-6827-4e81-ad0e-0c324f030bd2" />

Kiểm tra thử bên trong các folder thì các file có tên chứa kí tự ở đầu, và chứa dấu cách trong tên:  

<img width="875" height="55" alt="image" src="https://github.com/user-attachments/assets/b25873c7-0e7d-4b5e-b65f-da4d87bed80d" />

Bây giờ, trở lại thư mục `inhere` và dùng lệnh này để kiểm tra loại file của các file bên trong:  
```bash
file */{.,}* | grep ASCII
```

<img width="638" height="768" alt="image" src="https://github.com/user-attachments/assets/c4ae26ae-e5e8-41af-94c9-5121d60b45e9" />

Như các bạn thấy, có rất nhiều file cùng loại ASCII có thể đọc. Nhưng theo đề bài, ta cần tìm file có kích thước `1033 byte` và ko thể thực thi.  
Ta dùng lệnh:  
```bash
find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII
```
Giải thích:  
`find .` : bắt đầu tìm từ thư mục hiện tại.  

`-type f` : chỉ lấy file thường.  

`-size 1033c` : kích thước chính xác 1033 bytes (c = bytes).  

`! -executable` : loại bỏ file có quyền thực thi.  

`-exec file '{}' \;` : với mỗi file, chạy file để biết định dạng; '{}' là chỗ find chèn tên file . `\;` là kết thúc -exec.

`| grep ASCII` : chỉ giữ các dòng mà file trả về có chữ ASCII.  

<img width="891" height="57" alt="image" src="https://github.com/user-attachments/assets/e2382161-e7b8-45b8-a6b5-ecd16ef74cbb" />

<img width="870" height="165" alt="image" src="https://github.com/user-attachments/assets/61e4cd4b-ab37-43c3-8fef-a444eb90370a" />

Vậy là xong rồi!

>### 🎯 Pass: ***HWasnPhtq9AVKe0dmk45nxy20cvUa6EG***
