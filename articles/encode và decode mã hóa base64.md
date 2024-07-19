Đợt này mình đang có dự án sử dụng base64 để mã hóa token, để gửi tới API. Nên mình xin chia sẻ cách mã hóa base64 sử dụng ngôn ngữ lập trình Python.

Base64 là gì?

Mã hóa Base64 là một loại mã hóa byte thành ký tự ASCII và ngược lại. Tên của mã hóa này xuất phát trực tiếp từ định nghĩa toán học của các cơ số – chúng tôi có 64 ký tự đại diện cho các số.

Bộ ký tự Base64 chứa:
+ 26 chữ hoa
+ 26 chữ thường
+ 10 số
+ + và / cho các dòng mới (một số triển khai có thể sử dụng các ký tự khác)

Để mã hóa base64 chúng ta sử dụng thư viện base64 được built-in sẵn trong Python. Ví dụ chúng ta mã hóa chuỗi ký tự:

```
import base64
message = "https://vinasupport.com"
message_bytes = message.encode('ascii')
base64_bytes = base64.b64encode(message_bytes)
base64_message = base64_bytes.decode('ascii')
print(base64_message)
```

Kết quả: aHR0cHM6Ly92aW5hc3VwcG9ydC5jb20=

Hướng dẫn Decode Base64 sử dụng Python

Và bây giờ chúng ta hãy giải mã ngược lại chuỗi base64: aHR0cHM6Ly92aW5hc3VwcG9ydC5jb20=

```
import base64
base64_message = 'aHR0cHM6Ly92aW5hc3VwcG9ydC5jb20='
base64_bytes = base64_message.encode('ascii')
message_bytes = base64.b64decode(base64_bytes)
message = message_bytes.decode('ascii')
print(message)
```
