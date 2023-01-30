Hướng dẫn cài đặt Squid Proxy trên linux
Sau khi vps được setup xong thì bạn login vào ssh của vps và thực hiện lần lượt các câu lệnh bên dưới.

1. Cài đặt Squid
```
yum -y install squid
```

2. Cấu hình để Squid để tự động chạy mỗi khi Server khởi động lại.
centos
```
chkconfig squid on
```
ubuntu
```
update-rc.d -f squid enable
```

3. Khởi động Squid.
```
service squid start
```

4. Cấu hình lại squid

```
nano /etc/squid/squid.conf
```

Đổi Port tại dòng: http_port xxx (xxx là port mình muốn)
Đổi http_access deny all thành http_access allow all
Ấn Ctrl + X, chọn Y để lưu lại file

Khởi động lại squid:

```
service squid restart
```

5. Mở firewall:
```
firewall-cmd --permanent --add-port=xxx/tcp
```

(xxx là port mà b đã đổi ở bước 4, nếu không đổi ở b4 thì mặc định là 3128)

```
firewall-cmd --reload
```

Nếu ở bước này gặp lỗi Lỗi firewall-cmd command not found thì xem hướng dẫn fix tại đây. Sau khi fix xong thì thực hiện lại bước 5 nhé

Cuối cùng là chúng ta vào http://www.proxy-checker.org để check xem là proxy mình đã hoạt động hay chưa.
```
https://www.youtube.com/watch?v=oigAG1SDxxo
```
