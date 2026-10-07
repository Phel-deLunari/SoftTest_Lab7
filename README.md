# BÁO CÁO THỰC HÀNH: KIỂM THỬ API VỚI POSTMAN

* **Môn học:** Đánh giá & Kiểm thử phần mềm
* **Họ và tên:** Nguyễn Minh Đức
* **MSSV:** [Điền MSSV của bạn vào đây]
* **Công cụ sử dụng:** Postman Desktop App, JSONPlaceholder API, GitHub

---

## 1. Giới thiệu tổng quan
Bài thực hành hướng dẫn làm quen với quy trình kiểm thử giao diện lập trình ứng dụng (API) bằng công cụ Postman:
- Khởi tạo Collection và cấu hình Request theo phương thức `GET`.
- Phân tích cấu trúc phản hồi từ API: Mã trạng thái HTTP (Status Code), thời gian phản hồi (Response Time), và định dạng dữ liệu trả về (JSON).
- Xây dựng các đoạn mã kiểm thử tự động (Assertions) bằng ngôn ngữ JavaScript trên Postman.
- Thực thi tự động toàn bộ bộ kiểm thử thông qua công cụ Collection Runner.

---

## 2. API sử dụng để kiểm thử
- **Endpoint:** `https://jsonplaceholder.typicode.com/users`
- **Phương thức:** `GET`
- **Mục đích:** Lấy danh sách thông tin người dùng từ máy chủ công khai.

---

## 3. Các bước thực hiện & Kết quả minh chứng

### 3.1. Gửi Request GET thành công
Thực hiện gửi phương thức `GET` đến endpoint `/users`. Máy chủ phản hồi thành công mã trạng thái `200 OK` cùng danh sách dữ liệu người dùng định dạng JSON.

![Request GET thành công](01_get_request.png)

---

### 3.2. Viết mã kiểm thử tự động (Post-response Scripts)
Sử dụng thư viện `pm` tích hợp sẵn trong Postman để xác minh phản hồi trả về đúng mã trạng thái `200`:
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
