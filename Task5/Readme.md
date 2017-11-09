# Router và một số lệnh cơ bản

>Người thực hiện: Lưu Văn Lân

>Ngày update:09/11/2017

# Mục lục:

[1. ROUTER](#1)

[2. Quá trình boot của ROUTER.](#2)

[3. Quá trình tìm IOS của Router Cisco.](#3)

[4.Các mode làm việc chính của Router Cisco:](#4)

[5.Một số lệnh cơ bản trên Router Cisco](#5)


# Nội dung:

<a name="1"></a> 
# 1. ROUTER
- Các thành phần bên trong router như sau:
link
![text](https://i.imgur.com/pOaAuu7.png)

## Chức năng từng thành phần:
- **RAM** : Lưu trữ những bảng routing,ARP cache,fast-switching cache,packet buffẻing(shared RAM),và packet hold queues; RAM cũng cung cấp bộ nhớ tạm thời(running memory) cho file cấu hinh của router khi router đang hoạt động; nội dung RAM mất khi tắt nguồn hoặc restart router.

- **NVRAM** : non-volatile RAM lưu trữ file cấu hình backup/startup của route, nội dung của NVRAM vẫn được giữ khi tắt nguồn hoặc restart router.

- **Flash** : có thể xóa,có thể lập trình lại ROM nơi lưu trữ hệ điều hành và một số mã lệnh(microcode); Bộ nhớ Flash cho phép cập nhật phần mềm mà không cần lấy và thay thế chip xử lý; Nội dung Flash vẫn được giữ khi tắt nguồn hoặc restart; Bộ nhớ Flash có thể chứa nhiều versions của phần mềm IOS.

- **ROM** : chứa chương trình kiểm tra khi bật nguồn router, chương trình bootstrap, và phần mềm hệ điều hành, nâng cấp phần mềm trong ROM đòi hỏi phải lấy và thay thế chip cắm trên CPU.

- **Interfaces** : Kết nối mạng trên board mạch chủ hoặc trên interface modules riêng biệt, qua đó những packet đi vào và đi ra router.

- **CPU** : Đơn vị xử lí trung tâm. Thực hiện các lệnh của hệ điều hành để khởi động hệ thống, điều khiển các cổng giao tiếp mạng. CPU là một bộ giao tiếp mạng. CPU là một bộ vi xử lý. Trong các router lớn có thể có nhiều CPU.

<a name="2"></a>
# 2. Quá trình boot của ROUTER.
- Bootstrap sẽ được thi hành từ ROM
- Hệ điều hành có thể tìm được ở một trong những vị trí sau: FLASH - TFTP Server - ROM
- Image của hệ điều hành sẽ được nạp,sau đó phần cứng - phần mềm sẽ được xác định.
- Tập tin cấu hình sẽ được nạp vào bộ nhớ và thực hiện từng dòng lệnh.
- Nếu tập tin cấu hình không tồn tại, Router sẽ chuyển sang chế dộ Setup

<a name="3"></a>
# 3. Quá trình tìm IOS của Router Cisco.
- Bootstrap sẽ kiểm tra các file cấu hình start-up trong NVRAM
- Phân tích cấu hình để tiến hành thực thic các câu lệnh khởi động hệ thống.
- Mặc định là loađ file  đầu tiên trong bộ nhớ flash.
- Nếu không tìm thấy một IOS nào từ FLASH thì Cố gắng tìm một IOS từ các mạng máy chủ như TFTP server. Và tiến hành tải IOS xuống Flash
- Nếu không may nếu thất bại thì Router sẽ load ROMMON. ROMMON cũng có thể thể kết nối đến TFTP server. Nếu vẫn thất bại router sẽ dừng lại ở dòng lệnh của chế dộ ROMMON.

<a name="4"></a>
# 4.Các mode làm việc chính của Router Cisco:
![text](https://i.imgur.com/Tgo3tFf.png)

<a name="5"></a>
# 5.Một số lệnh cơ bản trên Router Cisco

## Lưu cấu hình
![text](https://i.imgur.com/XjK1s3E.png)

- Sao chép các file cấu hình hiện tại vào NVRAM.

## Gán tên và banner cho Router
![text](https://i.imgur.com/KfLUxSr.png)

## Cấu hình trong line-console

![text](https://imgur.com/k7pKH3g)

- Thiết lập thời gian cho một phiên hoạt động.

![text](https://i.imgur.com/hmK9G1L.png)

- Thiết lập để chống nhiễu trong các câu lệnh.

## Cấu hình trong interface
![text](https://i.imgur.com/nOQ2jqS.png)

- **type** bao gồm serial, ethernet, token ring, fddi, hssi,
loopback, dialer, null, async, atm, bri, tunnel, và vâng vâng

- **number** được dùng để định dạng cho một cổng,

![text](https://i.imgur.com/ptnA0fK.png)

- Dành cho các bộ định tuyến router, lựa chọn một interface

![text](https://i.imgur.com/VazfDcH.png)

- Thoát khỏi mode cấu hình.

## Cấu hình miêu tả interface
![text](https://i.imgur.com/zYXDvyg.png)

- string là một mô tả hay nhận xét để giúp bạn nhớ những gì gắn cho cổng này

- Số lượng kí tự tối đa của một string là 238

## Kích hoạt và hủy kích hoạt các interface
![text](https://i.imgur.com/jrOqFqV.png)

- Tắt cổng đó.

![text](https://i.imgur.com/GNoOGTw.png)

- Bật cổng đó.

## Gán địa chỉ IP cho interface
![text](https://i.imgur.com/LL6L1uK.png)

## Thể hiện thông tin trạng thái các interface
![text](https://i.imgur.com/qBg2iW2.png)

