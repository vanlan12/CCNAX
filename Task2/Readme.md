# Transport layer, Network Layer

>Người thực hiện: Lưu Văn Lân

>Ngày update:26/10/2017	

# Mục lục

[1.Chức năng tầng Transport](#1)

[2.Các kiểu kết nối.](#2)

[3.UDP và TCP](#3)

[4. Bắt tay 3 bưóc.](#4)

[5.Một số giao thức và port của một số ứng dụng tiêu biểu](#5)

# Nội dung

<a name="1"></a>
# 1.Chức năng tầng Transport.
	- Tầng giao vận chịu trách nhiệm đáp ứng các đòi hỏi về dịch vụ của tầng phiên(session layer) và đưa ra các yêu cầu dịch vụ đối với tầng mạng(network layer).

	- Tầng giao vận cung cấp dịc vụ xuyên dụng chuyển dữ liệu gĩưa các máy chủ(hosts). Tầng này chịu trách nhiệm sửa lỗi(error recovery), điều khiển lưu lưọng dữ liệu, đảm bảo dữ liệu đưọc chuyển tải một cách trọn ven.

<a name="2"></a>
# 2.Các kiểu kết nối.
	- Ơ tầng transport  có 2 kiểu kết nối là Reliable và Best-Effort.

	- Đối với kiểu Reliable:
		+ Đây là kiểu kết nôi sử dụng giao thức TCP.
		+ Kiểu kết nối này có độ tin cậy cực cao nhưng bù lại tốc độ truyền tải chậm hơn kiểu Best-Effort.
		+ Khi truyền tải gói tin sẽ được đem phân mảnh và đánh số tránh thất lạc gói tin khi truyền.
		+ Một số dịch vụ tưong ứng: Email,File sharing,Downloading,..

	- Đối với kiểu Best-Effort
		+ Đây là kiểu kết nối sẻ dụng giao thức UDP.
		+ Kiểu kết nối này ưu tiên truyền tải nhanh chóng nhưng ko đảm bảo cho độ an toàn của gói tin khi đưọc truyền đi.
		+ Khi tryền đi cả gói tin sẽ đưọc truyền đi. ko cần phân mảnh hay đánh dấu gói tin.
		+ Một số dịch vụ tưong ứng: Voice streaming, Video streaming

<a name="3"></a>
# 3.UDP và TCP
	- UDP:
		+ Hoạt động tại tầng transport của mô hình OSI và TCP/IP
		+ Cung cấp các dịch vụ có quyền truy cập vào tầng network với cơ chế dộ tin cậy là ko có
		+ Là giao thức kết nối theo kiểu connection-less,ko cần thiết lập phiên kết nối trưóc khi chuyển đi
		+ Cung cấp cơ chế kiểm tra lỗi hạn chế
		+ Cung cấp cơ chế truyền tin một cách nhanh nhất
		+ Không có tính năng phục hồi dữ liệu

	-TCP:
		+ Hoạt động tại tầng transport của mô hình TCP/IP
		+ Truy cập vào tầng mạng của các ứng dụng
		+ Là giao thức kết nối Connection-oriented. NGhĩa là thiết lập phiên kết nối trước khi chuyển đi
		+ Hoạt động heo kiểm full-duplex
		+ Cơ chế kiểm tra lỗi toàn diện
		+ Phân mảnh của gói dữ liệu
		+ Sau khi đã truyền tải thành công sẽ có xác nhận đã gửi đi thành công
		+ Có cơ chế phục hồi dữ liệu

<a name="4"></a>
# 4. Bắt tay 3 bưóc.
	- Kết nối bắt tay 3 bưóc có cấu trúc:
		sender ____________________receiver
		SYN seq=X----------------->SYN receiver(step 1)
		SYN receiver<--------------SEND ACK X+1 AND SYN Y(step 2)
		SEND ACK Y+1-------------->(step 3)



<a name="5"></a>
# 5.Một số giao thức và port của một số ứng dụng tiêu biểu

|Tên giao thức		| Giao thức | port   |
|-------------------|-----------|--------|
|HTTP				| TCP		| 80	 |
|HTTPS				| TCP		| 443	 |
|DNS				| TCP\UDP   | 53	 |
|SSH				| TCP       | 22	 |
|Telnet				| TCP		| 23	 |
|FTP-data transfer	| TCP		| 20	 |
|FTP-control		| TCP		| 21	 |
|SMTP				| TCP		| 25     |
