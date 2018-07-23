 # Cơ chế zabbix giám sát qua agent zabbix #

- Một zabbix agent được viết bằng ngôn ngữ C, chạy trên nhiều nền tảng khác nhau như Unix, Linux, Windows và chúng sử dụng để thu thập dữ liệu như CPU, memory, disk, network từ một thiết bị được sử dụng.

- Là một tiến trình nhỏ, tài nguyên sử dụng ít: Zabbix agent là một service đơn giản có thể chạy trên một thiết bị có nguồn tài nguyên giới hạn, cấu hình thấp.

Cấu hình monitor ở trên một thành phần tập trung zabbix server, quản lý các agent một cách dễ dàng, sử dụng một file cấu hình duy nhất trên tất cả các server.

- Để thu thập và lấy được data zabbix sử dụng 2 cơ chế phổ biến sau:

    passive check (polling)

    active checks (trapping)

Zabbix check thông tin trong một khoảng thời gian interval nhất định. Khoảng thời gian interval này có thể được cấu hình trong chế độ passive check (polling).

 **Passive check (polling):**

    Zabbix server (hoặc proxy) yêu cầu lấy giá trị từ zabbix agent

    Tiến trình agent nhận thông báo và trả lại giá trị tới zabbix server (hoặc proxy).


    Server chủ động hỏi - client thu thập rồi trả lời thỏa mãn yêu cầu của server (agent đóng vai trò bị động, agent quyết định vai trò)

**Active checks (trapping):**

    Zabbix agent yêu cầu từ Zabbix server (hoặc proxy) danh sách các lisk check (agent chủ động đi hỏi client xem list check cần thu thập data là gì và gửi lại kết quả, clent đóng vai trò chủ động)

    Agent gửi kết quả định kỳ về server


**Một số chức năng, thông số agent có thể thu thập được**


- Network	

        Packets/bytes transfered
        Errors/dropped packets
        Collisions

- CPU	

        Load average
        CPU idle/usage
        CPU utilization data per individual process
- Memory

        Free/used memory
        Swap/pagefile utilization
- Disk	

        Space free/used
        Read and write I/O
- Service	

        Process status
        Process memory usage
        Service status (ssh, ntp, ldap, smtp, ftp, http, pop, nntp, imap)
        Windows service status
        DNS resolution
        TCP connectivity
        TCP response time
- File	

        File size/time
        File exists
        Checksum
        MD5 hash
        RegExp search
- Log	

        Text log
        Windows eventlog
- Other	

        System uptime
        System time
        Users connected
        Performance counter (Windows)

**Một số chức năng mở rộng**

