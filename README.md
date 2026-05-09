## Bài tập môn Phát triển ứng dụng với mã nguồn mở - TEE0421
### Họ và tên: Hoàng Kim Ngọc
### MSSV:  K225480106053
### Lớp: K58KTP

## BÀI TẬP 2: SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ: viết tay ra giấy, lấy điện thoại chụp lại, upload ảnh lên github (đã nói về các nghiệp vụ trên lớp, ghi bảng)

   <img width="600" height="800" alt="z7806262353713_49e2f3cdd78ad6fc1f23b80c9dc638e9" src="https://github.com/user-attachments/assets/2983b1d6-f86c-4405-aab6-3587e1e43cec" />

2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:

- Mariadb : chứa csdl của hệ thống này
- Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)
- Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file    

sau khi có 3 service này trong file docker-compose.yml :
- run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm) => KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
- chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.
- sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
- sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả    

Hướng dẫn:
- Tạo thư mục để chứa image tự buid cho django
- Vào thư mục đó tạo file tên: Dockerfile (nội dung hỏi AI xem file này cần có nội dung gì, full comment cho từng dòng lệnh trong file này => mục tiêu kép: để hiểu và để hệ thống chạy được)
- AI sẽ nói cần thêm file requirements.txt để cài các thư viện cho python (cài qua lệnh pip) => tạo file requirements.txt với nội dung tưng ứng, trong file này cũng comment được => comment xem thư viện nào dùng để làm gì
- Sau mỗi lần sửa đỏi có thể phải chạy lệnh dạng : docker compose exec TÊN_SERVICE_DJANGO_CỦA_BẠN python manage.py migrate để tác động vào django (còn nhiều lệnh khác chứ ko luôn như này), để django thay đổi csdl hoặc thay đổi cấu hình.

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 090354" src="https://github.com/user-attachments/assets/a4852286-c399-410f-b9c1-b01ce5e090ec" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 090018" src="https://github.com/user-attachments/assets/c259e9b9-8417-4a4b-91f1-bed1553a05d0" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 090047" src="https://github.com/user-attachments/assets/d230c7e8-7158-49b4-b598-a6574ff2aa36" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 090333" src="https://github.com/user-attachments/assets/b96d9e15-3ffa-485e-9fdb-2158f9aa7570" />

  <img width="1919" height="1010" alt="Ảnh chụp màn hình 2026-05-09 092549" src="https://github.com/user-attachments/assets/1a7976c8-95ae-4d53-add8-9f80026611ed" />

  <img width="1914" height="1077" alt="Ảnh chụp màn hình 2026-05-09 095350" src="https://github.com/user-attachments/assets/e707b9bc-27e9-4618-b3e8-50664629f02a" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 092826" src="https://github.com/user-attachments/assets/3c0dbff3-ae02-489a-a1be-a2fffd05fe4a" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 092940" src="https://github.com/user-attachments/assets/e60378f2-f248-4181-b902-08b434fd59af" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 095428" src="https://github.com/user-attachments/assets/0df36513-8946-4824-abef-9ca6d1e1bb08" />

  <img width="1917" height="1078" alt="Ảnh chụp màn hình 2026-05-09 103457" src="https://github.com/user-attachments/assets/9f26e83b-96a1-4a71-be40-b5a9c5e52e87" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 095630" src="https://github.com/user-attachments/assets/4b73ae24-67da-44a0-8873-c313bb9ca939" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 095751" src="https://github.com/user-attachments/assets/b081fd0a-5b19-4eaa-953a-fb84e37c595c" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 095831" src="https://github.com/user-attachments/assets/495f006e-d7ff-4249-af57-74d5d693db30" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 103504" src="https://github.com/user-attachments/assets/18edbf1b-daa9-45f3-9195-60d2ba698f52" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 103858" src="https://github.com/user-attachments/assets/fe47db42-e507-4b02-a823-605936cc3fd4" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 103553" src="https://github.com/user-attachments/assets/0b793e73-b5d4-4914-89bc-0851179e140b" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 103656" src="https://github.com/user-attachments/assets/4dc29d9c-4740-46e9-9736-92822fd46478" />

  <img width="1919" height="1075" alt="Ảnh chụp màn hình 2026-05-09 115018" src="https://github.com/user-attachments/assets/b86d1259-856f-4159-9e72-765484a53d23" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 103845" src="https://github.com/user-attachments/assets/0fa1f943-e126-4776-9f1b-84b9d9c0fa18" />

  <img width="1919" height="1071" alt="Ảnh chụp màn hình 2026-05-09 115042" src="https://github.com/user-attachments/assets/be26c219-0c3f-4dd1-aee7-db001eeb25a2" />

  <img width="1911" height="754" alt="Ảnh chụp màn hình 2026-05-09 112746" src="https://github.com/user-attachments/assets/12563ce7-4357-4458-b8d5-0723b68a909a" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 112911" src="https://github.com/user-attachments/assets/8bb61a4f-7eec-47c6-b2a6-14c2c5642206" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113509" src="https://github.com/user-attachments/assets/84d11fe2-75d3-43f1-afce-9dd424a87e14" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113521" src="https://github.com/user-attachments/assets/f210e65c-8de5-49b7-905b-aec552fc79b0" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113531" src="https://github.com/user-attachments/assets/0a4c1f13-4a7f-4b51-8e43-f8055caf02f9" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113554" src="https://github.com/user-attachments/assets/3cc5f0fa-d53f-4d4f-a50e-7328394301cd" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113612" src="https://github.com/user-attachments/assets/32fca4e1-02ca-4a89-85a6-87e87b1852bf" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113617" src="https://github.com/user-attachments/assets/0107a3d1-2560-4105-b305-01b716acbdc8" />

  <img width="1919" height="1079" alt="Ảnh chụp màn hình 2026-05-09 113625" src="https://github.com/user-attachments/assets/94bce80d-6a69-45dc-989e-d379f60f5fac" />

  <img width="1914" height="1066" alt="Ảnh chụp màn hình 2026-05-09 113547" src="https://github.com/user-attachments/assets/84405d20-5275-4f42-b64a-25cd67bb5e16" />
