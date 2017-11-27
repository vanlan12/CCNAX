# Routing Overview, Static Route

>Người thực hiện: Lưu Văn Lân

>Ngày update:27/11/2017

# Mục lục

[1. Chức năng của router](#1)

[2. Routing Table](#2)

[3. Routing Protocol](#3)

[4. AD (Administrative Distance)](#4)

[5. Metric](#5)

# 1. Chức năng của router
- Router có chức năng gửi các gói dữ liệu mạng giữa 2 hoặc nhiều mạng, từ một tới nhiều điểm đích đến cuối cùng của router.
- Cho phép các bộ định tuyến khác biết về những thay đỏi.
- Xác định vị trí để chuyển tiếp gói dữ liệu đi.

# 2. Routing Table
- Bảng định tuyến là bảng lưu trữ mọi thông tin về các mạng IP và các thông tin về các con đường cách mà chúng có thể giao tiếp được với nhau.Việc xây dựng các bảng định tuyến mục tiêu chính của các giao thức định tuyến.

- Nội dung trong Routing Talbe:
	- Directly connected: Router gắn vào mạng này.
	- Static routing: Nhập bằng tay bởi một quản trị viên hệ thống.
	- Dynamic routing: Tự học bằng cách trao đổi thông tin giữa các bảng định tuyến với nhau.
	- Default route: Học tĩnh hoặc động. Được sử dụng khi không rõ tuyến đường định tuyến tới mạng.

# 3. Routing Protocol:
- Có 2 dạng của routing protocol:
	- 1.Distance vector(RIP,IGRP)
	- 2.Link state(OSPF,IS-IS)

## Distance vector protocol:
- Giống như tên gọi của nó giao thức này sử dụng khoảng cách để xác định đường đi tốt nhất tới một mạng từ xa. KHoảng cách thường là số lượng các bước nhảy (routers) tới mạng đích.
- Giao thức này gửi bảng định tuyến hoàn chỉnh tới mỗi neighbor(mỗi neighbor được kết nối trực tiếp với router và đều sử dụng chung một giao thức định tuyến).

## Link state:
- Về phương diện chức năng giao thức này có cùng chức năng là tìm ra đường đi tốt nhất tới đích, nhưng phương pháp thì lại khác. Khác với giao thức distance vector protocols, link state protocols không quảng bá toàn bộ bảng định tuyến. Thay vào đó , nó quảng bá thông tin bằng một mô hình mạng(liên kết nối trực tiếp,các router láng giềng,,,) để cuối cùng tất cả các bộ định tuyến chạy một giao thức trạng thái liên kết đều có cơ sở dữ liệu topo giống nhau.

# 4. AD (Administrative Distance)
- AD là tiêu chí đầu tiên mà router sử dụng để xác định giao thức định tuyến nào cần sử dụng nếu hai giao thức cung cấp thông tin cho cùng một đích. AD là thước đo sự đáng tin cậy của nguồn thông tin định tuyến. AD chỉ có ý nghĩa cục bộ và không được quảng bá trong bản cập nhật đinh tuyến.

- Giá trị AD nào nhỏ hơn thì giao thức đó sẽ đáng tin cậy hơn

- Giá trị AD của một số routing protocol:

|Static route| 1 |
------------------
|BGP         | 20|
------------------
|EIGRP		 | 90|
------------------
|IGRP        |100|
------------------
|OSPF        |110|
------------------
|RIP         |120|
------------------

# 5. Metric 
- Routing protocols sẽ chọn route nào được đánh giá là tốt nhất đến mỗi subnet. Việc lựa chọn này dựa vào việc route nào có metric càng nhỏ thì được đánh giá là càng tốt. Với mỗi giao thức thì lại có cách đánh giá riêng về metric. 

- Ví dụ với RIP thì phải đánh giá qua số lượng router(hop count) phải đi qua để đến subnet đích. Còn với OSPF,EIGRP thì lại khác.

- Cách đánh giá metric trên mỗi giao thức thường là những yếu tố:
	- Bandwidth
	- Delay
	- Hop Count
	- Cost

  
 # 6. Static route
 - Static route là cách định tuyến mà người quản trị mạng sẽ tự tay cấu hình định tuyến lên mỗi thiết bị.

 - Cách cấu hình:

 # RouterX(config)# ip route network  [mask] {address | interface}[distance] [permanent]


