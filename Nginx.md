🚀 PHẦN 1: CÀI NGINX TỪ ĐẦU
1. Update hệ thống
```sudo apt update```
2. Cài Nginx
```sudo apt install nginx -y```
3. Kiểm tra Nginx chạy chưa
```systemctl status nginx```

👉 Nếu thấy active (running) là OK

🌐 PHẦN 2: TRUY CẬP WEB<br>
Cách 1: Trên chính server
```curl localhost```
<br>Cách 2: Trên máy khác (Windows)

<br>Mở trình duyệt:

http://IP_SERVER<br>

👉 Nếu thấy trang “Welcome to nginx” là thành công<br>

📁 PHẦN 3: HIỂU CẤU TRÚC THƯ MỤC
Thư mục quan trọng:
/var/www/html → chứa web <br>
/etc/nginx/nginx.conf → config chính <br>
/etc/nginx/sites-available/ → config web <br>
/etc/nginx/sites-enabled/ → web đang chạy <br>
🧪 PHẦN 4: SỬA WEB MẶC ĐỊNH
1. Mở file HTML
```sudo nano /var/www/html/index.html```
2. Sửa thành:
```<h1>Hello Nginx </h1>```
3. Lưu:
Ctrl + O → Enter
Ctrl + X
4. Reload Nginx
```sudo systemctl reload nginx```

👉 Refresh trình duyệt → thấy nội dung mới

⚙️ PHẦN 5: TẠO WEBSITE RIÊNG
1. Tạo file config
```sudo nano /etc/nginx/sites-available/myweb```
2. Dán:
```
server {
    listen 80;
    server_name localhost;

    root /var/www/myweb;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
3. Tạo thư mục web
```sudo mkdir -p /var/www/myweb```
4. Tạo file web
```sudo nano /var/www/myweb/index.html```

Nội dung:

```<h1>My Website 🔥</h1>```
5. Kích hoạt website
``` sudo ln -s /etc/nginx/sites-available/myweb /etc/nginx/sites-enabled/ ```

6. Kiểm tra config
```sudo nginx -t```

👉 Nếu hiện syntax is ok là chuẩn

7. Reload Nginx
```sudo systemctl reload nginx```
🎯 KẾT QUẢ<br>
Truy cập IP → thấy web bạn tạo<br>
Bạn đã:
Cài nginx ✅<br>
Sửa web mặc định ✅<br>
Tạo website riêng ✅<br>
⚡ TIP QUAN TRỌNG (rất dễ quên)<br>
Sửa web → cần reload nginx<br>
Sai config → dùng:
```sudo nginx -t```
Xem tiến trình:
```ps aux | grep nginx```
