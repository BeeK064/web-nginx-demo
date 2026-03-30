#3. Cài đặt Nginx
``` bash
sudo apt update
sudo apt install nginx -y
```
#4. Kiểm tra trạng thái
```bash
systemctl status nginx
```
#5. Lệnh cơ bản
```bash
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
```
#6. Thư mục quan trọng

/etc/nginx/ thư mục gốc
/etc/nginx/nginx.conf thư mục chứa file cài đặt của nginx
/etc/nginx/sites-available/ thư mục chứa tất cả các site
/etc/nginx/sites-enabled/ thư mục chứa các site được trỏ tới (site được bật)
/var/www/html/ thư mục chứa nội dung site
