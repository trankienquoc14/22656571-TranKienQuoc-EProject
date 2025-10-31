
# EProject - Giai đoạn 1

## Tổng quan dự án
Dự án này là một ứng dụng microservices bao gồm các dịch vụ sau:

1. **API Gateway**: Cổng vào cho tất cả các request từ client.
2. **Auth Service**: Xử lý xác thực và phân quyền người dùng.
3. **Order Service**: Quản lý đơn hàng và các thao tác liên quan.
4. **Product Service**: Quản lý sản phẩm.

## Chạy dự án

1. **Cài đặt thư viện**:
   Vào từng thư mục dịch vụ và chạy:
   ```bash
   npm install
   ```
2. **Khởi động các dịch vụ**:
  - Tải dự án lên docker
   ```bash
   docker compose up --build 
   ```
![alt text](public/image/buildProject_docker1.png)
   - Chạy lại docker
   ```bash
   docker-compose up -d
   ```
![alt text](public/image/buildProject_docker.png)
   - Kiểm tra các container đang có trên máy 
![alt text](public/image/containerDocker.png)
3. **Kiểm thử API với POSTMAN**:
   Sử dụng POSTMAN để kiểm thử các endpoint của từng dịch vụ
### Auth Service 
- **Đăng ký**
   - Phương thức: POST
   - URL: http://localhost:3003/auth/register
   - Body (JSON):
      ```json
      {
         "username": "trankienquoc",
         "password": "12345"
      }
      ```
   - Kết quả test postman
![alt text](public/image/register.png)
   - Kiểm tra trên mongo db
![alt text](public/image/mongoDB.png)
![alt text](public/image/register_DB.png)
- **Đăng nhập**
   - Phương thức: POST
   - URL: http://localhost:3003/auth/login
   - Body (JSON):
      ```json
      {
         "username": "trankienquoc",
         "password": "12345"
      }
      ```
   - Kết quả test postman
![alt text](public/image/login.png)
- **Dashboard **
   - Phương thức: GET
   - URL: http://localhost:3003/auth/dashboard
   - Kết quả test postman
![alt text](public/image/dashboard.png)
### Product Service 
- **Thêm sản phẩm**
   - Phương thức: POST
   - URL: http://localhost:3003/products/api/products
   - Body (JSON):
      ```json
      {
         "name": "Iphone 17",
         "price": 3000000,
         "description": "Sang trọng, tinh tế"
      }
      ```
   - Kết quả test postman
![alt text](public/image/addProduct_token.png)
![alt text](public/image/addProduct.png)
   - Kiểm tra trên mongo db
![alt text](public/image/addProduct_DB.png)
- **Lấy danh sách sản phẩm**
   - Phương thức: GET
   - URL: http://localhost:3003/products/api/products
   - Kết quả test postman
![alt text](public/image/getProduct.png)
   - Kiểm tra trên mongo db
![alt text](public/image/getProduct_DB.png)
- **Lấy sản phẩm theo id**
- Phương thức: GET
   - URL: http://localhost:3003/products/api/products/:id
   - Kết quả test postman
![alt text](public/image/getProductById_token.png)
![alt text](public/image/getProductById.png)
### Order Product 
   - Phương thức: POST
   - URL: http://localhost:3003/products/api/products/buy
   - Body (JSON):
      ```json
      {
         "ids": [
            "id_product1",
            "id_product2"
         ]
      }
      ```
   - Kết quả test postman
![alt text](public/image/orderProduct_token.png)
![alt text](public/image/orderProduct.png)
   - Kiểm tra trên mongo db
![alt text](public/image/orderProduct_DB.png)
### RabbitMQ
![alt text](public/image/rabbitMQ.png)
