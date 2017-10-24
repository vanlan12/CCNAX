# Mạng căn bản

> Ngưòi thực hiện: Lưu Văn Lân

> Ngày update: 24/10/2017

# Mục lục

[I.Network là gì ?](#1)

[II.Network là gì ?](#2)

[III.Network là gì ?](#3)

[IV.Network là gì ?](#4)

[V.Network là gì ?](#5)

[VI.Network là gì ?](#6)

# Nội dung

<a name="1"></a>
# 1. Network là gì ?.
- Network là một mạng lưới kết nối các thiết bị(máy tính,máy in,laptop,...) lại với nhau thông qua một đường truyền vật lý theo một kiến trúc nào đó (Network architecture). Và có phạm vi không gian không giới hạn.

- Chức năng chính của network là trao đổi dữ liệu và chia sẻ tài nguyên giữa các thiết bị trong network với nhau.

<a name="2"></a>	
# 2. Đặc điểm của một mạng máy tính.
- Ngày nay với một lưu lưọng thông tin cực lớn, thì mạng máy tính đã trở thành một thứ thiết yếu và có mặt ở tất cả mọi lĩnh vực trong đời sống. Và một network được đánh gía theo các tiêu chuẩn sau đây: 

## Speed
- Tốc độ xử lí và truy xưất thông tin của mạng một cách nhanh chóng và tối ưu nhất. Trong khi thực tế việc truy xuất và xử lí thông tin có thể làm nghẽn mạng và mất thông tin. 

## Cost
- Gía thành khi lắp đặt và bảo trì hệ thống.

## Security
- Độ bảo mật thông tin và an toàn khi truy cập và xử lí dữ liệu trong mạng. 

## Availability
- Tính khả dụng của mạng đó đối với mọi lĩnh vực trong thực tế. Khi mà mọi thành viên của mạng đều có thể tiếp cận các thông tin trong hệ thống mà không quan tâm các thông tin đó đưọc lưu trữ ở đâu.

## Scalability
- Khả năng mở rộng của mạng đó đối với các trường hợp buộc phải thay đổi quy mô của mạng trong thực tế.

## Reliability
- Độ tin cậy của một hệ thống. Khi xảy ra trục trặc có thể dễ dàng bảo trì máy móc và lưu trữ(back up) dữ liệu. Hoặc khi có một máy hỏng sẽ có máy khác lên thay. 

## Topology

- Mô hình mạng của hệ thống tùy theo yêu cầu của hệ thống như về quy mô, tính chất,... mà sẽ có cách lắp đặt theo các mô hình khác nhau.

<a name="3"> </a>
# 3. Đặc điểm của các kiểu topology network.

## Bus topology.
![text](https://i.imgur.com/27bXSeU.png)
- Tất cả các thiết bị đều nhận chung tín hiệu.

## Star topology
![text](https://i.imgur.com/lLcA7a9.png)
- Tất cả thông tin đều đi qua điểm trung tâm.
- Mô hình này sẽ sụp đổ nếu điểm trung tâm đó bị hỏng.

## Extended-Star Topology
![text](https://i.imgur.com/nJvSDww.png)
- Tính linh hoạt cao hơn star topology.

## Ring Topology
![text](https://i.imgur.com/jyDnSCz.png)
- Tín hiệu di chuyển xung quanh hình vòng.
- Chỉ cần hư một điểm cả hệ thống sẽ sụp

## Dual-Ring Topology
![text](https://i.imgur.com/azcLkpe.png)
- Tín hiệu di chuyển theo 2 hưóng ngược nhau.
- Tính linh hoạt cao hơn Dual-Ring Topology.

## Full-Mesh Topology
![text](https://i.imgur.com/w8gozEH.png)
- Có tính chịu lỗi cao
- Tốn tiền để duy trì mô hình này.

## Partial-Mesh Topology
![text](https://i.imgur.com/eEckeGa.png)
- Cần phải cân nhắc trong việc lựa chọn giữa Khả năng chịu lỗi và gía thành.

<a name="4"></a>
# 4. Mô hình OSI
- Mô hình OSI ra đời trong hoàn cảnh hầu hết các mạng lưới truyền thông đều do các công ty lớn triển khai theo những tiêu chuẩn về hệ thống riêng của mình. Và hệ quả là vì có quá nhiều giao thức nên các thiết bị mạng gặp khó khăn và hầu như là không thể giao tiếp với nhau.

- Do đó mô hình OSI với mục đích là đưa ra một tiêu chuẩn về giao thức truyền thông của riêng mình để giúp các công ty có thể làm việc hiệu quả với nhau hơn.

## 7 Lớp mô hình OSI:

### Tầng 1 : PHYSICAL(Tầng vật lý)
- Định nghĩa tất cả mọi thứ về điện, vật lý, cách thức và các chức năng đặc biệt cho việc kích hoạt,duy trì và hủy kích hoạt giữa các liên kết vật lý với nhau.

- Đơn vị của tầng này là bits.

### Tầng 2: DATA LINK(Tầng liên kết dữ liệu: MAC và LLC)
- Định nghĩa về cách thức dữ liệu được định hình cho việc truyền tải và cách thức truy nhập vào đường truyền đưọc điều khiển như thế nào.
- Cung cấp các cách thức phát hiện lỗi.

- Đơn vị của tầng này là frames.

### Tầng 3: NETWORK(Tầng mạng)
- Thực hiện chức năng định tuyến các data packets(gói dữ liệu).
- Lựa chọn con đường tốt nhất để truyền dữ liệu.
- Cung cấp địa chỉ vật lý(MAC) và lựa chọn đường đi.

- Đơn vị của tầng này là Packets.

### Tầng 4: TRANSPORT(Tầng vận chuyển)
- Quản lí, điều khiển việc truyền dữ liệu giữa các đầu cuối.
- Bảo đảm độ tin cậy của việc truyền dữ liệu.
- Thiết lập, duy trì và chấm dứt các mạch ảo.
- Cung cấp cơ chế phát hiện lỗi an toàn, phục hồi sự điều khiển dòng thông tin.

- Đơn vị của tầng này là Segments.

### Tầng 5: SESSION(Tầng phiên)
- Kiểm soát các phiên hội thoại giữa các máy tính.
- Tầng này thiết lập, quản lí và kết thúc các phiên kết nối giữa các ứng dụng

- Đơn vị tầng này là Data

### Tầng 6: PRESENTATION(Tầng biểu diễn dữ liệu)
- Đảm bảo dữ liệu là đọc được bởi hệ thống nhận.
- Định hình dữ liệu.
- Cấu trúc dữ liệu.
- Cung cấp các giao thức mã hóa dữ liệu.
- Thiết lập cú pháp truyền dữ liệu cho tầng ứng dụng.

- Đơn vị tầng này là Data

### Tầng 7: Aplication(Tầng ứng dụng)
- Cung cấp  dịch vụ mạng đến những quá trình ứng dụng.
- Cung cấp cơ chế xác thực ngưòi dùng.

<a name="5"></a>
# 5. TCP/IP
- Mô hình TCP/IP là mô hình cải tiến của mô hình OSI.
- Mô hình TCP/IP được định nghĩa bằng 4 tầng:
	+ Tầng 4 đưọc gộp lại từ 3 tầng cuối của OSI(Aplication,Presentation,Session) thành tầng gọi là Aplication.
	+ Tầng 3 là tầng Transport.
	+ Tầng 2 là tầng Internet(Đổi từ tên network bên OSI)
	+ Tầng 1 được gộp lại từ 2 tầng đầu của OSI(Data Link,Physical) thành tầng gọi là tầng Network Acess

<a name="6"></a>
# 6.Giống và khác của TCP/IP và OSI
**Các điểm giống nhau:**
- Cả hai đều là phân lớp.
- Cả hai đều có lớp ứng dụng, qua đó có nhiều dịch vụ mạng khác nhau.
- Cả hai có lớp mạng và lớp vận chuyển có thể so sánh được.
- Kỹ thuật chuyển mạch gói đưọc chấp thuận.

**Các điểm khác nhau:**
- Các giao thức TCP/IP là các chuẩn cơ sở cho Internet phát triển,như vậy mô hình TCP/IP chiếm được niềm tin chỉ vì các giao thức của nó. Ngưọc lại các mạng thông thường không được xây dựng trên nền OSI, ngay cả khi mô hình được dùng như một hưóng dẫn. Nói cách khác nó là một văn phạm nghèo và có nhiều thiếu sót.

<a name="7"></a>
# 7. Câu hỏi 

## Các ứng dụng tiêu biểu ở Tầng Application (Ứng dụng) của Mô hình OSI.
- Domain name System
- Hypertext Transfer Protocol

