# MONITOR ZABBIX #

# I, Lý thuyết #
p

**1. Zabbix Overview**

+ Zabbix là một công cụ để  giám sát hệ thống mạng, các thiết bị mạng, giám sát khả năng sẵn sàng và hiệu năng của mạng và thiết bị mạng. Nếu có xảy ra lỗi thì sẽ có cảnh báo gửi tới người quản trị mạng qua sms, email...

+ Là công cụ mã nguồn mở miễn phí.


+ Được phát hành theo giấy phép GPlv2, không giới hạn về sức chứa và số lượng thiết bị được giám sát  

+ Hỗ trợ bất kỳ kích thước của mô hình mạng nào. Có thể là mô hình nhỏ hoặc mô hình lớn, thường xuyên cập nhật và phát hành phiên bản mới.
+ Zabbix được viết năm 1998, là dự án của Alexei Vladishev (Alexei Vladishev dùng để monitor hệ thống database)

**2. Zabbix Features**

Zabbix cũng cấp những tính năng quan trọng và cần thiết cho việc monitor hệ thống và các thiết bị mạng.

Zabbix dựa trên các agent và agentless để giám sát hệ thống mạng và các thiết bị mạng. Các thiết bị mạng phải hỗ trợ giao thức SNMP. Zabbix giám sát hiệu suất, hiệu năng của máy chủ vật lý cũng như máy ảo.

Trong Th có lỗi xảy ra zabbix cảnh báo cho người quản trị, tuy nhiên zabbix không có khả năng phát hiện hay dự đoán lỗi có thể xảy ra.

**2.1. Open source**

**2.2. Agent-based vs Agentless**

* Agent-based

Đây là một phần mềm được gọi là agent được cài đặt trên máy chủ local và các thiết bị cần monitor. Mục tiêu của nó là thu thập thông tin gửi về zabbix-server và có thể cảnh báo tới người quản trị.

Agent được cài đặt đơn giản nhẹ nhàng, tiêu thụ ít tài nguyên của server.

Lợi ích của việc sử dụng agent là phân tích sâu hơn, ngoài ra có thể chuẩn đoán được hiệu suất phần cứng, cung cấp khả năng cảnh bảo và report.

*  Agentless

Agentless là một giải pháp không yêu cầu bất kỳ cài đặt agent riêng biệt nào. Phân tích mạng dựa trên giám sát package tiếp. Nó được sử dụng để giám sát tính sẵn sàng của mạng và hiệu suất. Tuy nhiên, nó không cung cấp bất kỳ thông tin chi tiết nào về lỗi.

Dựa trên giao thức SNMP hoặc WMI, được dựa trên một trạm quản lý trung tâm, giám sát tất cả các thiết bị mạng khác.


Việc cài đặt không ảnh hưởng đến hiệu suất của server . Quá trình triển khai dễ dàng hơn, không phải cập nhật thường xuyên từ các agent. Tuy nhiên lại không đi sâu thu thập được các số liệu, không cung cấp khả năng phân tích và báo cáo.


**2.3 Auto discovery**

Hệ thống được cập nhật khi hệ thông có sự thay đổi Các thiết bị mới được thêm cần được tự độ phát hiện. 
Để theo dõi việc tự động thay đổi môi trường liên tục thay đổi được sử dụng tính năng Auto discovery.

Đây là một tính năng cho phép thực hiện tìm kiếm các phần tử mạng. Ngoài ra, nó sẽ tự động thêm các thiết bị mới và loại bỏ các thiết bị không còn là một phần của mạng. Nó cũng thực hiện việc khám phá các network interface, các port và các hệ thống file.

Auto discovery có thể được sử dụng để tìm ra trạng thái hiện tại trong mạng. Những thiết bị và dịch vụ nào hiện có trên mạng? Ngoài ra, nó giúp trong các vấn đề bảo mật. Nó giúp xác minh những cổng nào được kích hoạt.

Auto discovery có thể ping hoặc truy vấn mọi thiết bị trên mạng. Nếu mạng có Hệ thống Phát hiện xâm phạm (IDS), tính năng phát hiện tự động có thể kích hoạt báo động xâm nhập.

Phát hiện tự động đóng một phần thiết yếu trong giám sát mạng, một số công cụ  khác không cung cấp tính năng này. Đó là lý do tại sao các quản trị mạng nên chú ý auto discovery khi chọn công cụ giám sát mạng.

**2.4. Low-level discovery**

 Low-level discovery (LLD) được sử dụng để giám sát các hệ thống file và interface mà không cần tạo và thêm thủ công từng phần tử. LLD là một tính năng động tự động thêm và xóa các phần tử. Nó cũng tự động tạo ra triggers, graphs cho file systems, network interfaces và SNMP tables.

**2.5. Trend Prediction**

Một số công cụ theo dõi mạng có một tính năng dự đoán. Nó được sử dụng để phát hiện một lỗi trước khi nó xảy ra. Điều này được thực hiện bằng cách thu thập dữ liệu về băng thông mạng và trạng thái của các thiết bị theo mức độ hoạt động. Tất cả các thông tin được lưu trữ trong cơ sở dữ liệu SQL. Các kết quả giám sát tiếp theo được so sánh với thông tin được lưu trữ trong cơ sở dữ liệu. Nếu một số thay đổi giữa dữ liệu đã được tìm thấy, giám sát mạng sẽ tạo ra một cảnh báo.

Dự đoán xu hướng cho phép phát hiện vấn đề trước, để quản trị viên mạng có thể giải quyết nó trước khi người dùng cuối nhận thấy nó. Mặc dù tính năng này hay nhưng hầu hết các sản phẩm vẫn không hỗ trợ tính năng này.

**2.6. Logical grouping**

Trong các mạng lớn bao gồm nhiều thiết bị, khó để theo dõi và khắc phục tất cả các thiết bị trong quá trình giám sát mạng. Logical grouping cho phép kết hợp cùng một loại thiết bị lại với nhua. Kết quả là logical grouping giúp việc giám sát các mạng cấp doanh nghiệp dễ dàng hơn đáng kể.

Logical grouping cho phép kết hợp cùng một loại thiết bị mạng thành các nhóm. Đối với mỗi nhóm có thể được xác định những gì cần được theo dõi và những hành động nên được thực hiện trong trường hợp xảy ra lỗi. Ngoài ra, với việc Logical grouping có thể định cấu hình cài đặt hợp nhất cho tất cả phần tử của nhóm. Nếu một hoặc nhiều phần tử của nhóm ngừng hoạt động một cảnh báo sẽ được hiển thị.

Có thể tạo các nhóm lồng nhau cho các mạng lớn. Điều này có nghĩa là các nhóm có thể được tạo bên trong một nhóm khác. Kết quả là, việc quản lý các thiết bị mạng bên trong một mạng lớn trở nên dễ dàng hơn.

**3. Zabbix architecture**

![](https://i.imgur.com/pJk3TPx.png)


Zabbix bao gồm các thành phần sau: abbix Server, Zabbix Proxy, Zabbix Agent
và Web Interface.

+ Zabbix server: Đây là thành phần trung tâm của phần mềm Zabbix. Zabbix Server có thể kiểm tra các dịch vụ mạng từ xa thông qua các báo cáo của Agent gửi về cho Zabbix Server và từ đó nó sẽ lưu trữ tất cả các cấu hình cũng như là các số liệu thống kê.


+ Zabbix Proxy: Là phần tùy chọn của Zabbix có nhiệm vụ thu nhận dữ liệu, lưu trong bộ nhớ đệm và chuyển đến Zabbix Server.


+ Zabbix Agent: Để giám sát chủ động các thiết bị cục bộ và các ứng dụng (ổ cứng, bộ nhớ…) trên hệ thống mạng. Zabbix Agent sẽ được cài lên trên Server và từ đó Agent sẽ thu thập thông tin hoạt động từ Server mà nó đang chạy và báo cáo dữ liệu này đến Zabbix Server để xử lý.


+ Web interface: Để dễ dàng truy cập dữ liệu theo dõi và sau đó cấu hình từ giao diện web cung cấp.

**4. Ưu điểm của zabbix**

Zabbix đáp ứng các yêu cầu của công cụ giám sát mạng đáng tin cậy tới 90%. Nó thực hiện cả giám sát agent-based, agentless. Hỗ trợ Low level Discovery, Auto-Discovery Logical grouping. Tất cả các tính năng nêu trên làm cho Zabbix trở thành một công cụ giám sát mạng hoàn hảo, đáp ứng đầy đủ các yêu cầu của bất kỳ mạng kích thước nào. Tuy nhiên Zabbix không hỗ trợ dự đoán TH xấu xảy ra.

Zabbix là một công cụ giám sát mạng đáng tin cậy. Nếu Zabbix cảnh báo người dùng về một lỗi nào đó, có tin tưởng 100% rằng vấn đề như vậy tồn tại. Ngoài ra, một trong những lợi thế chính của Zabbix là khả năng mở rộng của nó vì nó là khả năng áp dụng cho các môi trường có kích thước bất kỳ.


**5. Vấn đề cần cải thiện trong zabbix**

**5.1. Web Interface**
Thao tác sử dụng hiện tại của giao diện người dùng quá phức tạp. Người dùng cho Zabbix mới có thể gặp sự cố với Giao diện web. Một số thao tác cơ bản có thể tốn thời gian ngay cả đối với người dùng có kinh nghiệm. Phải thao tác quá nhiều cho một hoạt động cơ bản.

**5.2. API**
API có thể có hiện tượng rất chậm, đặc biệt là khi nói đến các hoạt động template linking. Ví dụ, có 10000 host và quản lý một mạng muốn liên kết chúng thành một template đơn giản. Nó sẽ mất khoảng 10-20 phút, tùy thuộc vào phần cứng. Ngoài ra, nó sẽ tạo ra quá nhiều truy vấn SQL. Số lượng họ thậm chí có thể đạt đến hàng triệu.

**5.3. Reporting**

**5.4. Scalability**

**5.5. Security**


<h1>II, Cài đặt Zabbix version 3.4 on Ubuntu 16.04</h1>

## 1, Chuẩn bị ##

**Small** - 	CentOS	- Virtual Appliance	- MySQL InnoDB	- monitor 100 host 


**Medium**	- CentOS	- 2 CPU cores/2GB RAM -	MySQL InnoDB	- monitor 500 host

**Large**	- RedHat Enterprise Linux	- 4 CPU cores/8GB RAM	- RAID10 MySQL InnoDB or PostgreSQL	- monitor >1000 host

**Very large**	- RedHat Enterprise Linux	- 8 CPU cores/16GB RAM -	Fast RAID10 MySQL InnoDB or PostgreSQL	- monitor >10000 host

**+ Set địa chỉ IP tĩnh, kiểm tra kết nối ra Internet, update các package**

![](https://i.imgur.com/2bs6vVJ.png)




## 2, Cài đặt Zabbix-server##


**- Download repo zabbix và unpackage**


	root@ubuntu:/# wget http://repo.zabbix.com/zabbix/3.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.4-1+xenial_all.deb
	root@ubuntu:/# dpkg -i zabbix-release_3.4-1+xenial_all.deb


![](https://i.imgur.com/WlN0rqH.png)


**- Update lại package mới + Cài đặt zabbix server và các gói cài đặt cần thiết: zabbix server, zabbix client, mysql, php...**

	root@ubuntu:/# apt-get update -y


![](https://i.imgur.com/L6w3xvV.png)



	root@ubuntu:/# apt-get install zabbix-server-mysql zabbix-frontend-php zabbix-agent zabbix-get zabbix-sender snmp snmpd snmp-mibs-downloader php7.0-bcmath php7.0-xml php7.0-mbstring

![](https://i.imgur.com/Y2K8nTO.png)


**- Edit time zone của zabbix server**

+ Mở file /etc/zabbix/apache.conf chỉnh time zone Việt Nam : Asia/Ho_Chi_Minh

		root@ubuntu:/# vi /etc/zabbix/apache.conf

![](https://i.imgur.com/ZVJwjsa.png)


+ Reload lại service apache

		root@ubuntu:/# systemctl reload apache2


**- Tạo database và user truy cập databaser**


+ Truy cập vào database

		root@ubuntu:/# mysql -u root -p

![](https://i.imgur.com/Jjyr6Tu.png)

+ Tao dabase với tên là zabbixdb


		MariaDB [(none)]> create database zabbixdb character set utf8 collate utf8_bin;

![](https://i.imgur.com/8hErVqI.png)

+ Gán quyền và đặt password cho database vừa tạo ở trên

		MariaDB [(none)]> grant all privileges on zabbixdb.* to zabbixuser@localhost identified by '123456a@';

+ Xác nhận query và thoát


		MariaDB [(none)]> flush privileges;

		MariaDB [(none)]> quit


![](https://i.imgur.com/qC95PgH.png)

+ Import database ban đầu của zabbix

		root@ubuntu:/# cd /usr/share/doc/zabbix-server-mysql/
		root@ubuntu:/usr/share/doc/zabbix-server-mysql# zcat create.sql.gz | mysql -u root -p zabbixdb
		Enter password:

+ Config database


		root@ubuntu:/# vi /etc/zabbix/zabbix_server.conf

Tìm và sửa các thông số

		DBHost=localhost
		DBName=zabbixdb
		DBUser=zabbixuser
		DBPassword=123456a@



![](https://i.imgur.com/3cWTtmy.png)


+ Restart service zabbix-server, zabbix-agent


		root@ubuntu:/# systemctl enable zabbix-server 
		root@ubuntu:/# systemctl start zabbix-server
		root@ubuntu:/# systemctl enable zabbix-agent 
		root@ubuntu:/# systemctl start zabbix-agent


**- Truy cập bằng trình duyệt hoàn tất kết nối qua giao diện**

Truy cập đường dẫn: http://172.16.3.199/zabbix


![](https://i.imgur.com/pUdcJcx.png)


Check các thành phần bắt buộc có để cài đặt zabbix server thành công



![](https://i.imgur.com/YgUWXzv.png)

 Nhập các thông tin kết nối đền database đã tạo ở trên

![](https://i.imgur.com/u85xCY9.png)


Nhập name hiển thị đại diện cho zabbix server


![](https://i.imgur.com/K51yYj0.png)

Check lại thông tin đã nhập

![](https://i.imgur.com/nO8TVoU.png)

Cấu hình thành công


![](https://i.imgur.com/9bAsZwb.png)

Login với tài khoản mặc định Admin/zabbix

![](https://i.imgur.com/7SMZgbs.png)

- Cài đặt thành công zabbix


![](https://i.imgur.com/gKSqonc.png)



# 3, Cài đặt zabbix agent trên client #


**- Cài đặt trên server OS Ubuntu**

	wget http://repo.zabbix.com/zabbix/3.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.4-1+xenial_all.deb
	dpkg -i zabbix-release_3.4-1+xenial_all.deb

	sudo apt-get update
	sudo apt-get install zabbix-agent

+ Chỉnh sửa file config để kết nối tới zabbix server

		vi /etc/zabbix/zabbix_agentd.conf

Tìm và chỉnh sửa các thông tin sau để kết nối tới zabbix server


		Server=172.16.3.193

		ListenPort=10050

		ServerActive=172.16.3.193


![](https://i.imgur.com/BghIgFv.png)



+ Khởi động lại service zabbix-agent

		service zabbix-agent restart


**- Cài đặt trên OS Centos**
CentOS/RHEL 7:

	rpm -Uvh http://repo.zabbix.com/zabbix/3.4/rhel/7/x86_64/zabbix-release-3.4-2.el7.noarch.rpm

CentOS/RHEL 6:

	rpm -Uvh http://repo.zabbix.com/zabbix/3.4/rhel/6/x86_64/zabbix-release-3.4-1.el6.noarch.rpm

Cài đặt

	yum install zabbix-agent
	

+Chỉnh sửa config

	Server=172.16.3.193

	ListenPort=10050

	ServerActive=172.16.3.193


#III. Giới thiệu về Dashboard Zabbix #

Đây là giao diện tổng quan khi cài đặt zabbix thành công. Gồm nhiều mục lớn như Monitoring, Inventory, Reports, Configuration, Administrator. Trong các tab lớn sẽ bao gồm nhiều task thành phần nhỏ hơn.

![](https://i.imgur.com/XVNxgwV.png)


## 3.1. Tab Monitoring ##


![](https://i.imgur.com/c6xpY6q.png)

+**Dashboard**: Là giao diện hiển thị các dashboard trực quan để người quản trị nhìn trực tiếp, người quản trị có thể tạo ra rất nhiều các dashboard khác nhau, nhưng tại một tab screen chỉ có thể xem được 1 dashboard bất kỳ nào đó.

Từ Dashboard có thể nhanh chống liên kết đến các thành phần như Graphs, Screens, Mapbằng cách thêm các thành phần mong muốn vào mục Favourite graphs, Favourite Screen và Favourite map.

+Problems: Hiển thị các vấn đề đối với từng device mà zabbix server thu thập dữ liệu về. Hỗ trợ cơ chế lọc theo ý người quản trị.

![](https://i.imgur.com/ZJfmqjk.png)

+Overview: Là sự tổng hợp thông tin về data zabbix zerver thu thập được, có thể lọc them group -> host -> Kiểu data.

![](https://i.imgur.com/e7VAhYK.png)


+Latest data: Dữ liệu mới nhất mà zabbix server thu thập được.

![](https://i.imgur.com/WqVd6Tu.png)

+Triggers: Là một điều kiện khi thỏa mãn điều kiện của Triggers mà người lập trình đặt ra thì sẽ thực hiện một hành động nào đó tiếp theo.

![](https://i.imgur.com/nNu32ee.png)

+Graphs:  Là các thông tin dữ liệu được biểu diễn dưới dạng biểu đồ theo thời gian thực ví dụ như trafiic qua interface của thiết bị, thông tin về tình trạng CPU, RAM, ổ cứng… Các thông tin này được định nghĩa trong các templates.

Hỗ trợ lọc theo group -> host -> Dạng graph

Tại một thời điểm chỉu xem được 1 thông số dạng graph của 1 server. Cung cấp cái nhìn đơn lẻ về một đối tượng nhất định cần giám sát

![](https://i.imgur.com/j1XMqL7.png)


+Screen: L tập hợp các thông tin như Graphs, maps,data overview… vào chung một màn hình giám sát. Giúp người quản trị có thể lựa chọn các thông tin cần thiết hiển thị, giúp có cái nhìn tổng quát những thông tin mà người quản trọ mong muốn.

![](https://i.imgur.com/NiFg7vM.png)

+Maps: Là thành phân cung cấp khả năng giám sát hệ thống dưới hình thức mô hình mạng. Giúp người quản trị có cái nhìn tổng quan về hệ thống sống mạng dưới dạng sơ đồ, trong trường hợp có sự cố sẽ giúp người quản trị đánh giá tầm ảnh hưởng của thiết bị gặp sự cố và đưa ra giải pháp phù hợp.

![](https://i.imgur.com/1fwhYj7.png)

+Discovery: Tính năng cho phép zabbix server tự động tìm kiếm các thiết bị được cài đặt zabbix agent đã cấu hình kết nối về zabbix server trong cùng mạng với zabbix server.

![](https://i.imgur.com/fz3rDLa.png)



## 3.2. Tab Configuration ##

+ Host group: Tập hợp lại các host có chung một mục đích sử dụng hoặc người quản trị tâp hợp lại để phục vụ một mục đích quản lý chung.

![](https://i.imgur.com/FfNtPUx.png)

+ Templates: Đây là tập hợp các thực thể có thể áp dụng cho các Host, một Template sẽ chứa trong nó các tập lệnh để truy vấn lấy dữ liệu, hiển thị thông tin dữ liệu lấy được, thông tin tình trạng thiết bị, hiển thị và thông báo lỗi…

Trong mỗi Template, các tệp lệnh được chia thành: items, triggers, graphs, applications, screens (có từ Zabbix 2.0),low-level discovery rules (có từ Zabbix 2.0), web scenarios (có từ Zabbix 2.2). Tùy theo giám sát thiết bị, dịch vụ, ứng dụng… nào thì các thành phần này được thiết lập khác nhau.

Có thể import template tự viết vào.

![](https://i.imgur.com/NGyKNcG.png)

+ Host: Là một máy tính, server, vps, chạy các hệ điều hành khác nhau hoặc một thực thể trong hệ thống mạng như là máy in, máy chấm công, máy photo, máy camera có hỗ trợ các giao thức mà monitor zabbix cung cấp.

![](https://i.imgur.com/TW736G4.png)

+ Maintance: Có thể xác định thời gian bảo trì cho máy chủ và group trong Zabbix. Có hai loại Maintance - với thu thập dữ liệu và không thu thập dữ liệu.

Ví dụ server của bạn off trong khoảng thời gian này để nâng cấp sửa chữa, thì maintance sẽ được lựa chọn cấu hình để không thu thập data trong khoảng thời gian đó. 

![](https://i.imgur.com/Zkos0c5.png)

+ Action: Nơi cấu hình, lựa chọn các kiểu thông báo khi có sự kiện xảy ra bởi cấu hình trigger

![](https://i.imgur.com/vBhVqY3.png)

## IV, Mã hóa dữ liệu trong Zabbix ##

Để tránh việc bị các attacker ghe lén các metric của zabbix agent đẩy về zabbix server, zabbix hỗ trợ mã hóa các metric theo kiểu mã hóa đối xứng và mã hóa bất đối xứng. Trong hướng dẫn này tôi sẽ sử dụng loại mã hóa đối xứng sử dụng thuật toán PSK (pre-shared keys). Thuật toán này giữa agent và server sẽ sử dụng chung 1 key cho việc mã hóa và giải mã metric.

![](https://i.imgur.com/2GIOjxH.png)


+ Install OpenSSL

		apt-get install openssl

+ Tạo pre-shared keys sử dụng OpenSSL

		root@ubuntu:~# openssl rand -hex 32
	
		b6551750895e3598194adb58d13d6c654f212f65f552089be3d72982caa057ce

![](https://i.imgur.com/xaBxKM0.png)

+ Tạo file pre-shared keys .PSK 

		vi /etc/zabbix/zabbix_agentd.psk

paste key vừa tạo vào file

		b6551750895e3598194adb58d13d6c654f212f65f552089be3d72982caa057ce
+ Sử file config agent

		vi /etc/zabbix/zabbix_agentd.conf
		TLSConnect=psk
		TLSAccept=psk TLSPSKFile=/etc/zabbix/zabbix_agentd.psk TLSPSKIdentity=PSK 001

+ Restart lại service zabbix
	
		service zabbix-server restart	

+ Cấu hình mã hóa PSK trên Zabbix web

Click: Configuration → Hosts

Select host vào muốn mã hóa và click chọn Encryption

Thêm PSK đã tạo vào

![](https://i.imgur.com/1MoHwz4.png)

+ Thiết lập kết nối mã hóa thành công giữa zabbix server - zabbix agent

![](https://i.imgur.com/sEF1iaP.png)

