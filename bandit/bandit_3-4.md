## 🕵️‍♂️ Challenge:  
## Level 3 → Level 4 
### The password for the next level is stored in a hidden file in the inhere directory.  

Commands you may need to solve this level  
> ls , cd , cat , file , du , find
## 📝 Solution:  

Kết nối ssh đến máy chủ `bandit.labs.overthewire.org` với tên người dùng `bandit3`, cổng `2220`  
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```
Password lấy từ thử level trước:  
> MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

Ssh thành công, ta ls để kiểm tra xem có file hay thư mục nào đang tồn tại ko:  

<img width="189" height="43" alt="image" src="https://github.com/user-attachments/assets/29370642-6eaa-4d51-b869-d82528823e37" />

Như vậy là có folder `inhere`, để vào trong folder, nhập:  
```bash
cd inhere
```
Kiểm tra các file đang có trong thư mục này thì ko thấy có gì, đọc lại đề bài thì có vẻ chúng đang bị ẩn.  
Để hiển thị các file ẩn ta dùng lệnh:  
```bash
ls -a
```
<img width="300" height="73" alt="image" src="https://github.com/user-attachments/assets/179534d6-5f08-425e-8d15-551a34f199db" />

Vậy là ta thấy tệp ẩn đã xuất hiện, bây giờ đọc nó:  

<img width="446" height="69" alt="image" src="https://github.com/user-attachments/assets/d626335c-40d8-4e8d-858d-fda9fdd74e71" />

Như vậy là xong, ta đã có được pass của level sau.  

>### 🎯 Pass: ***2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ***
