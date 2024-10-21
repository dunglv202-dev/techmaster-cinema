# Ảnh chụp giao diện

![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/1.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/2.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/3.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/4.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/5.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/6.png?raw=true)
![Ảnh chụp](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/7.png?raw=true)

# Cài đặt và chạy chương trình

- Clone github repository, chạy lệnh để pull các submodule về
  ```
  git submodule init
  git submodule update
  ```
- Di chuyển tới thư mục `docker` trong project
- Tạo file `.env` với nội dung tham khảo file [`.env.example`](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/docker/.env.example)
- Copy file [`application-local.yaml`](https://github.com/dunglv202-dev/techmaster-cinema/blob/main/assets/application-local.yaml) trong thư mục `assets` vào trong `src/main/resources` của phần backend
- Chạy lệnh `docker compose build` và `docker compose up -d` để build image và chạy các container
- Try cập tại địa chỉ [http://localhost](http://localhost) trên trình duyệt
- Xem log trực tiếp của backend sử dụng `docker compose logs -f backend`
- Truy cập và xem databáe tại [http://localhost:81](http://localhost:81)

# Chú ý

- Để sử dụng data sẵn có, cần phải thiết lập `spring.sql.init.mode=always` tại `application.yaml` hoặc `application-local.yaml` trong lần đầu khởi chạy backend
- Với dữ liệu test hiện tại chỉ đang có 2 lịch chiếu phim Joker vào ngày 20/10 tại Hà Nội, phim At Cafe 6 ngày 25/10 tại Hồ Chí Minh
