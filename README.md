# Ảnh chụp giao diện

![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/1.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/2.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/3.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/4.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/5.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/6.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/7.png?raw=true)

# Hướng dẫn cài đặt và chạy chương trình thủ công

- Clone github repository, chạy lệnh để pull các submodule về

```
git submodule init
git submodule update
```

- Mở thư mục backend và frontend với IDE
- Chạy frontend: chạy lệnh `yarn install` và `yarn dev`
- Chạy backend:
  - Tạo file cấu hình có tên `application-local.yaml` tại đường dẫn `src/main/resources/`. Tham khảo nội dung file [application.yaml](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/application-local.yaml?raw=true)
  - Chạy ứng dụng Spring Boot với IDE
- Cài đặt và thiết lập nginx:

  - Cài [nginx](https://nginx.org/) nếu máy chưa cài đặt
  - Thêm thiết lập sau vào file cấu hình nginx và chạy lệnh `nginx -s reload` để áp dụng cấu hình

    ```
    server {
        listen       		80;
        server_name  		localhost;

        location /api {
            proxy_pass                          http://localhost:8080/api;
            proxy_set_header Host               $host;
            proxy_set_header X-Real-IP          $remote_addr;
            proxy_set_header X-Forwarded-For    $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto  $scheme;
        }

        location / {
            proxy_pass                          http://localhost:5173;
            proxy_set_header Host               $host;
            proxy_set_header X-Real-IP          $remote_addr;
            proxy_set_header X-Forwarded-For    $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto  $scheme;
        }
    }
    ```

# Chú ý

- Để sử dụng data sẵn có, cần phải thiết lập `spring.sql.init.mode=always` tại `application.yaml` hoặc `application-local.yaml` trong lần đầu khởi chạy backend
- Với dữ liệu test hiện tại chỉ đang có 2 lịch chiếu phim Joker vào ngày 20/10 tại Hà Nội, phim At Cafe 6 ngày 25/10 tại Hồ Chí Minh
