# lamp-compose
## Thông tin về compose
| Component | Phiên bản |
|-|-|
| Apache | 2.4 |
| Mariadb | 10.6 |
| PHP | 8.0 |
| PhpMyAdmin | 5.1 |

## Chạy docker-compose
- Cần có `docker-compose` và chạy lệnh sau:
```
docker-compose up
```
- Thư mục có cấu trúc đầy đủ sau khi chạy lệnh trên như sau:
    - conf/
    - public/
    - database/

- Tổng cộng các images khi `docker-compose` sẽ có dung lượng tới ~ 610mb
- Ta có thể thay đổi port của apache thông qua "docker-compose.yml" ví dụ
mặc định là "80:80" là nó đang sử dụng port 80(Bên trái) làm port trên
host, khi muốn chuyển sang port 81 thì sửa thành "81:80"
- Tương tự đối với mariadb, khi muốn kết nối với database client bên ngoài
ta có thể chuyển sang port 3307 như
sau "3307:3306", tuy nhiên mặc định port này đã được comment nên hãy
uncomment trước khi sử dụng.

## Config
- Tất cả các config liên quan đến Mariadb, PhpMyAdmin, Apache đều nằm trong
thư mục "conf/"

## Database
- Thư mục "database/" này sẽ được tạo sau khi chạy `docker-compose`, nó
chứa dữ liệu của database vào bên trong, nó sẽ bị ignore trong git và nếu
muốn có gửi cho team nếu muốn, dung lượng thư mục này sẽ > 100mb nên cần
cân nhắc khi gửi cho người khác
- __Chú ý__:
    - Người dùng trong database là "root" và mật khẩu là env
    "MARIADB_ROOT_PASSWORD" (Mặc định là "toor" trong "docker-compose.yml")
    - Khi dùng đến database trong php, ta sẽ liên kết thông qua domain là
"mariadb"

## Public
- Thư mục "public/" này sẽ được tạo sau khi chạy `docker-compose`, nó
dùng để chữa project của chúng ta (Gồm cái html, css, js, php,...)
- Ta có thể truy cập thông qua "{your_host}:{your_port}" (Mặc định
là "localhost:80")
- __Chú ý__:
    - Ta nên chú ý khi tạo thư mục con là "pma/" vì nó đã được dùng để tạo
    trang để truy cập "PhpMyAdmin"

## PhpMyAdmin
- Ta có thể truy cập "PhpMyAdmin" thông qua đường dẫn
"{your_host}:{your_port}/pma" (Mặc định là "localhost:80/pma")
