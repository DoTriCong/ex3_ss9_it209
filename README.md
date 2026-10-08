# Bài 3: Dockerfile đóng gói trang web HTML tĩnh

## Mô tả
Đóng gói một trang HTML tĩnh vào image `nginx:alpine`.

## Cấu trúc thư mục
```
homework/session_09/ex3/
├── Dockerfile
├── index.html
└── README.md
```

## Nội dung các tệp

**index.html**
```html
<h1>Hello Docker Session 09!</h1>
```

**Dockerfile**
```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

- `FROM nginx:alpine`: dùng image Nginx bản Alpine (nhẹ) làm nền.
- `COPY ...`: chép `index.html` vào thư mục mặc định Nginx phục vụ web.

## Cách chạy

```bash
# 1. Build image
docker build -t my-html-app:v1 .

# 2. Chạy container ở cổng 8081
docker run -d -p 8081:80 --name html-app my-html-app:v1

# 3. Kiểm tra
curl http://localhost:8081
```

## Kết quả mong đợi
```
<h1>Hello Docker Session 09!</h1>
```

## Dọn dẹp
```bash
docker rm -f html-app
```
