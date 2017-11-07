# Data Link Layer + ARP, Physical Layer, Cable

>Người thực hiện: Lưu Văn Lân

>Ngày update:07/11/2017

# Mục lục

[1.Ethernet là gì . Cấu trúc Ethernet Frame.](#1)

[2.Địa chỉ MAC? Cấu trúc địa chỉ MAC.](#2)

[3.Broadcast Domain và Collisions Domain.](#3)

[4. Tốc độ truyền tải của HUB và SWITCH.](#4)

[5. Phương pháp CSMA/CD.](#5)

[6. ARP? Cơ chế hoạt động của ARP trong cùng LAN? Khác LAN?](#6)

[7. Cáp Crossover và cáp Straight-through](#7)

[8. Chuẩn bấm cáp](#8)

# Nội dung 

<a name="1"></a>
# 1.Ethernet là gì . Cấu trúc Ethernet Frame.
- Ethernet là một họ lớn và đa dạng gồm các công nghệ mạng dựa khung dữ liệu(frame-based) dành cho mạng LAN

- Hiện nay Ethernet đã được chuẩn hóa thành IEEE 802.3

## Cấu trúc Ethernet Frame

|Preamble|Destination|Source|Type|Data|FCS|
-------------------------------------------

- Preamble: 8 byte báo hiệu bắt đầu một frame
- Destination: 6 byte thể hiện địa chỉ MAC đích
- Source: 6 byte thể hiện địa chỉ MAC nguồn
- Type: 2 byte chỉ rõ giao thức lớp mạng
- Data: 46-1500 byte dữ liệu được chuyển đi
- FCS: 4 byte là một cyclic redundancy check (CRC) kiểm tra gói frame.

## Chuẩn IEEE 802.3

|Preamble|SOF|Destination|Source|Type|Data|FCS|
-----------------------------------------------

- Không khác Ethernet chỉ thêm một trường SOF 1 byte và trường Preamble còn lại 7 byte.

- SOF: Giới hạn cho việc bắt đầu gói frame

<a name="2"></a>
# 2.Địa chỉ MAC? Cấu trúc địa chỉ MAC.
- Địa chỉ MAC là mã duy nhất được gán bởi nhà sản xuất cho từng phần cứng mạng( như card không dây hoặc card Ethernet). Viết tắc là Media acces control. Mỗi mã tương ứng duy nhất cho một thiết bị.

- Địa chỉ MAC là một bộ sáu cặp hai ký tự, cách nhau bằng dấu hai chấm. Ví dụ 00:1B:44:11:3A:B7 là một địa chỉ MAC.

- ĐỊa chỉ MAC có độ dài là 48 bit. Trong đó chia làm 2 phần:
	- Một phần do nhà sản xuất quy định gọi là OUI.
	- Một phần do IEEE quy định dành cho các vendor.

<a name="3"></a>
# 3.Broadcast Domain và Collisions Domain.
- Collisions Domain(Miền đụng độ):
	- Là các segment lạng vật lý được kết nối ở đó có các đụng độ có thể xảy ra.
	- Mỗi khi một đụng độ xảy ra trên mạng, tất cả các hoạt động truyền lại dừng lại trong một khoảng thời gian.
	- Thiết bị thuộc lớp 1 không chia tách miền đụng độ mà chỉ mở rộng miền đụng độ.
	- Thiết bị thuộc lớp 2 và 3 chia tách miền đụng độ thành các miền đụng độ nhỏ hơn (sự phân đoạn mạng – segmentation).

- Broadcast Domain(Miền quảng bá):
	- Một broacast domain là một nhóm các miền đụng độ được kết nối bởi các thiết bị lớp 2.
	- Các gói tin broadcast nếu nhiều quá mức có thể làm giảm hiệu suất của mạng LAN.
	- Broadcast được kiểm soát bởi thiết bị lớp 3.Router có thể phân chia các broad cacst domain.

- Cách xác định:
	- Một Port của Router là 1 Broadcast Domain
	- Các port Router được nối lại với nhau chỉ tính là 1
	- Một port của SW, router là một Collision Domain
	- Các port của SW, Router nối lại với nhau chỉ tính là 1
	- Hub là 1 Collision Domain	

<a name="4"></a>
# 4. Tốc độ truyền tải của HUB và SWITCH.
- Với HUB, một khung dữ liệu được truyền đi hoặc phát tới tất cả các cổng của thiết bị mà không phân biệt các cổng với nhau. Ngoài ra một Hub 10/100 Mbps phải chia sẻ băng thông với tất cả các cổng của nó. Tức là hiệu suất truyền tải sẽ giảm đi nhiều.

- Với Switch với chức năng ghi nhớ địa chỉ MAC của tất cả các thiết bị nó kết nối tới. Với thông tin này switch có thể xác định hệ thống nào đang chờ ở cổng nào và luôn truyền tải với băng thông tối đa.

> Kết lại Switch có tốc độ truyền tải cao hơn và là sự lựa chọn tốt hơn so với Hub.

<a name="5"></a>
# 5. Phương pháp CSMA/CD.
- CSMA/CD(Carrier Sense Multiple Access with Collision Detect) đây là một trong nhiều phương pháp truy cập hay sử dụng trong mạng LAN, cải tiến từ phương pháp CSMA.

- Tiến trình phương pháp này như sau:
	- 1. Một thiết bị có frame cần truyền sẽ lắng nghe đường truyền đến khi nào đường truyền Ethernet không còn bị chiếm:
	- 2. Khi đường truyền Ethernet không còn bị chiếm nó bắt đầu gửi frame.
	- 3. Máy gửi cũng bắt đầu lắng nghe để đảm bảo rằng không có xung đột xảy ra.
	- 4. Nếu có xung đột, tất cả các máy trạm đã từng gửi frame sẽ gửi ra một tín hiệu nghẽn để đảm bảo tất cả các máy trạm đều nhận ra collision.
	- 5. Sau khi tín hiệu nghẽn là hoàn tất, mỗi máy gửi của những frame bị xung đột sẽ khởi dộng một bộ định thời timer và chờ hết khoảng thời gian này sẽ cố gắng truyền lại. Những máy không tạo ra collision sẽ không phải chờ.
	6. Sau khi các thời gian định thời là hết, máy gửi có thể bắt đầu lần nữa với bước 1.

- CSMA/CD được phát triển từ CSMA để tăng hiệu quả của phương thức CSMA, bằng cách dừng việc truyền tín hiệu ngay khi phát hiện thấy xung đột, giảm thiểu thời gian chờ để thực hiện việc truyền tiếp theo. (CSMA không kết thúc việc truyền dữ liệu nếu phát hiện xung đột, những máy đang truyền sẽ tiếp tục truyền, những máy gây xung đột sau khi nhận được thông báo sẽ dừng một khoảng thời gian trước khi cố gắng truyền tiếp).

<a name="6"></a>
# 6. ARP? Cơ chế hoạt động của ARP trong cùng LAN? Khác LAN?
- ARP(Address Resolution Protocol) Giao thức phân giải địa chỉ được sử dụng để chuyển địa chỉ từ tầng mạng (network layer) sang tần liên kết dữ liệu theo mô hình OSI. Hay còn thể nói là phân giải địa chỉ IP sang địa chỉ MAC (địa chỉ máy).

## Cơ chế hoạt động ARP trong mạng LAN

### Ví dụ Máy A gửi tới máy B có địa chỉ là 192.168.1.120

- Bước 1: Thiết bị A sẽ kiểm tra cache của mình(nơi lưu trữ các tham chiếu giữa địa chỉ iP và MAC).Nếu đã có địa chỉ MAC của ip 192.168.1.120 thì lập tức chuyển sang bước 9.
- Bước 2: Bắt đầu khởi tạo gói tin ARP Request. Nó sẽ gửi một gói tin broadcast đến toàn bộ các máy khác trong mạng với địa chỉ MAC và IP máy gửi là địa chỉ của chính nó, địa chỉ IP máy nhận là 192.168.1.120, và địa chỉ MAC máy ff:ff:ff:ff:ff:ff
- Bước 3: Thiết bị A phân phát gói tin ARP Request trên toàn mạng. Switch nhận được gói tin broadcast nó sẽ chuyển gói tin này tới tất cả các máy trong mạng LAN đó.
- Bước 4: Các thiết bị trong mạng đều nhận được gói tin ARP Request. Máy tính kiểm tra trường địa chỉ Target Protocol Address. Nếu trùng với địa chỉ của mình thì tiếp tục xử lý, nếu không thì hủy gói tin.
- Bước 5: Thiết bị B có IP trùng với IP trong trường Target Protocol Address sẽ bắt đầu quá trình khởi tạo gói tin ARP Reply bằng cách:
	- Lấy các trường Sender Hardware Address và Sender Protocol Address trong gói tin ARP nhận được đưa vào làm Target trong gói tin gửi đi.
	- Đồng thời thiết bị sẽ lấy địa chỉ MAC của mình để đưa vào trường Sender Hardware Address.
- Bước 6: Thiết bị B đồng thời cập nhật bảng ánh xạ địa chỉ IP và MAC của thiết bị nguồn vào bảng ARP cache của mình để giảm bớt thời gian xử lý cho các lần sau (hoạt động cập nhật danh bạ).
- Bước 7: Thiết bị B bắt đầu gửi gói tin Reply đã được khởi tạo đến thiết bị A.
- Bước 8: Thiết bị A nhận được gói tin reply và xử lý bằng cách lưu trường Sender Hardware Address trong gói reply vào địa chỉ phần cứng của thiết bị B.
- Bước 9: Thiết bị A update vào ARP cache của mình giá trị tương ứng giữa địa chỉ IP(địa chỉ network) và địa chỉ MAC(Địa chỉ datalink) của thiết bị B. Lần sau sẽ không còn cần tới request.

<a name="7"></a>
# 7. Cáp Crossover và cáp Straight-through
- Straight-Through Cable sử dụng để nối các thiết bị khác loại:
	- switch với router
	- switch với pc
	- switch với server
	- hub với pc
	- hub với server

- Crossover Cable sử đụng để nối các thiết bị cùng loại:
	- switch với switch
	- switch với hub
	- hub với hub
	- router với router
	- router với router
	- router với pc
	- pc với pc

<a name="8"></a>
# 8. Chuẩn bấm cáp
- Có hai chuẩn bấm cap là T568A (chuẩn A) và T568B (chuẩn B)
	- Chuẩn A: Trắng xanh lá - Xanh lá - Trắng cam - Xanh dương - Trắng xanh dương - Cam - Trắng nâu - Nâu (hơi loằng ngoằng, khó nhớ). Còn được gọi là chuẩn thẳng, để nối hai thiết bị khác loại với nhau như máy tính - switch, switch - router. 
	- Chuẩn B: Trắng cam - Cam - Trắng xanh lá - Xanh dương - Trắng xanh dương - Xanh lá - Trắng nâu - Nâu (dễ nhớ hơn cái trên). Còn được gọi là chuẩn chéo, dùng để kết nối hai thiết bị cùng loại với nhau. Khi cần kết nối hai máy tính bằng dây cáp mạng chúng ta cũng dùng chuẩn này.


