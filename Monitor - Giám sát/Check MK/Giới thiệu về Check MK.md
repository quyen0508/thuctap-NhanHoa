# Sơ lược về OMD - Check MK
- OMD viết tắt của Open Monitoring Distribution là một dự án được phát triển từ năm 2010 bởi Mathias Kettner. OMD sử dụng nhân Nagios Core kết hợp với các phần mềm mã nguồn mở khác như Nagios, Check MK, NagVis, PNP4Nagios, DocuWiki,... để đóng gói thành một sản phẩm phục vụ nhu cầu giám sát, cảnh báo và hiển thị
- OMD có các distro là OMD-LABS và CHECK_MK RAW
- Check MK được phát triển từ năm 2008 như là một plugin của Nagios Core
- Check MK là một phần của OMD, hiện có 2 phiên bản là Check MK Raw Edition (CRE) và Check MK Enterprise Edition (CEE)

![image](https://github.com/shaidoka/thuctap-NhanHoa/raw/main/CheckMK_Zabbix/CheckMK/images/OMD.png)

### Ưu điểm trong thiết kế kiến trúc của OMD
- OMD được xây dụng từ những đóng góp của cộng đồng về những khó khăn hay khuyết điểm mà Nagios gặp phải, từ đố đưa ra quyết định cần tích hợp thêm nhưng sản phẩm gì để cải thiện
- Việc cài đặt trở nên vô cùng đơn giản. OMD được đóng gói hoàn chỉnh trong một packet, việc cài đặt và cấu hình chỉ mất khoản 10 phút chỉ với 1 câu lệnh

![image](https://github.com/shaidoka/thuctap-NhanHoa/raw/main/CheckMK_Zabbix/CheckMK/images/OMD_Infrastructure.png)

- Check MK ra đời để giải quyết bài toán về hiệu năng mà Nagios gặp phải trong quá khứ. Cơ chế mới của Check MK cho phép việc mở rộng hệ thống trở nên dễ dàng hơn, có thể giám sát nhiều hệ thống chỉ từ một máy chủ Nagios server
- Có 2 module mà Check MK sử dụng để cải thiện đáng kể hiệu năng là **Livestatus** và **Livecheck**
- Livestatus có những thay đổi để cải thiện hiệu năng
    - Livestatus sử dụng Nagios Event Broker API như NDO, nhưng nó không chủ động ghi dữ liệu ra. Thay vào đó, nó sẽ mở một socket để dữ liệu có thể được lấy ra theo yêu cầu
    - Livestatus tiêu tốn ít CPU
    - Livestatus không làm cho Disk I/O thay đổi khi truy vấn trạng thái dữ liệu
    - Không cần cấu hình, không cần cơ sở dữ liệu, không cần quản lý
- Cách thức hoạt động của Livecheck
    - Livecheck sử dụng các helper process, các core giao tiếp với helper thông qua Unit socket (không xảy ra trên file system)
    - Chỉ có một helper program được fork thay vì toàn bộ Nagios Core
    - Các tiến trình fork được phân tán trên tất cả các CPU thay vì chỉ 1 như trước
    - Process VM size tổng chỉ khoảng 100KB