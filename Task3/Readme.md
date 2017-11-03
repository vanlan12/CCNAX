# IP, Subneting, VLSM

>Người thực hiện: Lưu Văn Lân

>Ngày update:03/11/2017

# Mục lục

[1.Chức năng của lớp Network.](#1)

[2.Các đặc tính của internet protocol.](#2)

[3.IP HEADER](#3)

[4.Địa chỉ IP](#4)

[5.Một số Phân vùng địa chỉ.](#5)

[6.Subnet mask,Subnet, Prefix length.](#6)

[7.Cách chia subnet và VLSM.](#7)

# Nội dung

<a name="1"></a>
# 1. Chức năng của lớp Network.
	- Định tuyến các gói dữ liệu.
	- Lựa chọn con đường tốt nhất để chuyển dữ liệu đi mà vẫn đảm bảo được chất lượng dịch vụ mà tầng giao vận yêu cầu.
	- Cung cấp các cách để định vị địa chỉ logic và lựa chọn đường đi.

<a name="2"></a>
# 2. Các đặc tính của internet protocol.
	- Giao thức vận hành tại tầng network của mô hình OSI.
	- Cung cấp dịch vụ gửi dữ liệu không đảm bảo.
	- Các gọi được xử lí độc lập và riêng lẽ với nhau.
	- Địa chỉ phân cấp với nhau.
	- Cung cấp chuyển vận tốt nhất.
	- Ko có chức năng phục hồi dữ liệu.

### IP ADDRESSES
	- IP dùng để phân biệt các phương tiện trên một mạng lưới địa chỉ.
	- Mỗi một máy chủ(máy tính,thiết bị mạng,..) chỉ có duy nhất một địa chỉ ip.
	- Host ID:
		- Xác định máy chủ cá nhân.
		- Được các tổ chức phân công cho các thiết bị riêng lẻ.

<a name="3"></a>
# 3.IP HEADER

- Version(4 bit): Chỉ ra phiên bản IP đang được dùng.
	- IP Header Length(IHL)(4 bit): Chỉ ra chiều dài của header. Chiều dài tối đa là 64 bit.
	- Type of service(TOS)(8 bit): Chỉ ra cách thức xử lí gói dữ liệu,có độ ưu tiên hay ko, độ trễ cho phép của gói dữ liệu.
	- Packet Length(16 bit): CHiều dài toàn bộ IP datagram tính theo byte, bao gồm data và phần header.
	- Identification(16 bit): Mã số đánh dấu của IP Datagram. Khi phân mảnh ra thì mỗi IP datagram sẽ cố một mã số riêng.
	- Flag(3 bit): Gồm 6 cờ.
		- Bit 0: Ko dùng
		- Bit 1: Cho biết gói có phân mảnh ko
		- Bit 2: Nếu bị phân mảnh thì cho biết mảnh này có phải mảnh cuối ko.
	- Fragment Offset(13 bit): Báo bên nhận vị trí offset của các mảnh so với gói ip datagram gốc.
	- Time To Live(TTL)(8 bit):  Chỉ ra số bước nhảy (hop) mà một gói có thể đi qua. Con số này sẽ giảm đi 1, khi gói tin đi qua 1 router
	- Protocol(8 bit): Chỉ ra giao thức nào của tầng trên(Transport) sẽ nhận phần data sau công đoạn xử lí IP datagram.

- Header CheckSum (16 bit): Hỗ trợ cho Router phát hiện lỗi bit trong khi nhận IP datagram. Giúp bảo đảm sự toàn vẹn của IP Header.
	- Source IP Address (32 bit): Chỉ ra địa chỉ của thiết bị truyền IP diagram (Xem cấu trúc của địa chỉ IPv4).
	- Destination IP Address (32 bit): Chỉ ra địa chỉ IP của thiết bị sẽ nhận IP diagram (Xem cấu trúc của địa chỉ IPv4).
	- IP Option: kích thước không cố định, chứa các thông tin tùy chọn như: Time stamp – thời điểm đã đi qua Router, Security – cho phép Router nhận gói dữ liệu không, nếu không thì gói sẽ bị hủy, Record Router – lưu danh sách địa chỉ IP của Router mà gói phải đi qua, Source Route – bắt buộc đi qua Router nào đó. Lúc này sẽ không cần dùng bảng định tuyến ở mỗi Router nữa.
	- Padding: Các số 0 được bổ sung vào trường này để đảm bảo IP Header luôn là bội số của 32 bit.

<a name="4"></a>
# 4.Địa chỉ IP.
- Một địa chỉ Ip là một dãy số nhị phân 32 bit.
- Để dễ đọc thì dãy số nhị phân đó được chia thành 4 octet 8 bit.
- Mỗi octet(hoặc byte) có thể được chuyển qua hệ nhị phân.
- Địa chỉ gồm 2 phần là phần NETWORK và phần HOST.

>Dạng thập phân : 130.57.30.56

>Dạng nhị phân : 10000010. 00111001.00011110.00111000

## Địa chỉ IP gồm có 3 lớp:
	- Lớp A : 
		- Octet đầu là NETWORK, 3 Octet sau là phần HOST. 
		- Octet đầu tiên có giá trị từ 1->126
	- Lớp B : 
		- 2 Octet đầu là NETWORK, 2 Octet sau là phần HOST.
		- Octet đầu tiên có giá trị từ 128->191
	- Lớp C : 
		- 3 Octet đầu là NETWORK, Octet cuối là HOST.
		- Octet đầu tiên có giá trị từ 192->223

	- Giá trị **127** là địa chỉ của lớp A dùng để làm địa chỉ loopback và ko thể dùng để định danh cho địa chỉ mạng.

## Địa chỉ mạng
	- Là địa chỉ có tất cả bit phần HOST bằng 0.

## Địa chỉ Broadcast
	- Là địa chỉ có tất cả các bit phần HOST bằng 1.

<a name="5"></a>
# 5. Một số Phân vùng địa chỉ.

## Địa chỉ IP công cộng(Public):
	- Lớp A : 1.0.0.0 tới 9.255.255.255 / 11.0.0.0 tới 126.255.255.255
	- Lớp B : 128.0.0.0 tới 172.15.255.255 / 172.32.0.0 tới 192.255.255.255
	- Lớp C : 192.0.0.0 tới 192.167.255.255 / 192.168.0.0 tới 223.255.255.255

## Địa chỉ IP nội bộ(Private):
	- Lớp A : 10.0.0.0 tới 10.255.255.255
	- Lớp B : 172.16.0.0 tới 172.31.255.255
	- Lớp C : 192.168.0.0 tới 192.168.255.255

<a name="6"></a>
# 6. Subnet mask,Subnet, Prefix length
- Trong các môi trường khác nhau ta cần chia nhỏ mạng ra để dễ quản lý và tiết kiệm được địa chỉ IP. Và các mạng nhỏ được chia ra từ mạng chính được gọi là **SUBNET**.

- Subnet mask là một dải 32 bit nhị phân đi kèm với một địa chỉ IP, được các host dùng để xác định địa chỉ mạng của địa chỉ IP này.
	- Ví dụ: Lớp A: 255.0.0.0 , Lớp B: 255.255.0.0, Lớp C: 255.255.255.0

- Số prefix đơn giản là chỉ số bit mạng trong địa chỉ IP.
	- Ví du: 192.168.1.1/24, 172.16.0.0/16 hay 10.0.0.0/8,.v.v…

<a name="7"></a>
# 7. Cách chia subnet và VLSM

## SUBNET
	- Để có thể chia nhỏ một mạng lớn thành nhiều mạng con, người ta thực hiện thêm một số bit bên phần host để làm phần mạng, các bit mượn này gọi là các bit subnet. Tùy vào số bit subnet mà ta có các mạng con với kích cỡ khác nhau.

	- Cách tính: Gọi n là số bit mượn và m là số bit host còn lại. Ta có: 
		- Số subnet có thể chia được:
 			- 2^n nếu có hỗ trợ subnet – zero.
 			- 2^n-2 nếu không hỗ trợ subnet – zero.
			- Luật subnet – zero: nếu hệ điều hành trên host không bật tính năng subnet – zero, khi chia subnet ta phải bỏ đi không dùng hai mạng con ứng với các bit subnet bằng 0 hết và các bit subnet bằng 1 hết. Ngược lại nếu hệ điều hành bật tính năng subnet – zero , ta có quyền sử dụng hai mạng con này. Nhìn chung, các hệ điều hành ngày nay đều bật tính năng subnet – zero một cách mặc định,do đó nếu không thấy nói gì thêm trong yêu cầu, ta sử dụng cách chia có hỗ trợ subnet – zero.
			- Số host có thể có trên mỗi subnet: 2^m – 2 (host/subnet). 

## VLSM
	-Kỹ thuật chia một mạng thành các mạng có độ dài khác nhau.
		- Xét các mạng có số host từ cao xuống thấp .
		- Lần lượt từ mạng có số host cao nhất xuống thấp nhất. Tìm xem số bit mượn là bao nhiêu thì đủ cho mạng. 
		- Cứ mỗi lần xét xong một mạng. Số mạng dư ra sẽ dùng để chia cho các mạng dưới nữa và lần lượt cho tới hết.

