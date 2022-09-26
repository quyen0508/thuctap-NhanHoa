# So sánh các công cụ ảo hoá (VMware vSphere, KVM, Hyper-V, Xen)
| Tiêu chí | vSphere | KVM | Hyper-V | Xen |
| - | - | - | - | - |
| Hệ điều hành | EXSi | Promox, Debian, Ubuntu,... | Windows Server, Windows 10 | XCP-NG |
| Bản quyền | Miễn phí (giới hạn chức năng) | Miễn phí | Miễn phí | Miễn phí |
| Open-Source | Không | Có | Không | Có |
| RAM/Host | 12 TB | 12 TB | 24 TB | 5 TB |
| RAM/VM | 6 TB | 6 TB | 12 TB | 1,5 TB |
| CPU/VM | 120 | 240 | 240 | 32 |
| VM Disk | 62 TB | 10 TB | 64 TB | 2 TB |
| VM Live Migration | Có | Có | Có | Có |
| VM Replication | Có | Có | Có | Có |
| Overcommit Resources | Có | Có | Có | **Không** |
| Disk I/O Throttling | Có | Có | Có | Có |
| Hot Plug of Virtual Resources | Có | Có | Có | Có |

### Lựa chọn công cụ ảo hoá
- Tất cả các công cụ trên đều là ảo hoá phần cứng (tức là hypervisor loại 1), vì vậy việc lựa chọn sẽ dựa theo yếu tố liên quan đến tính năng, chi phí, sự ổn định và tính tương thích,...
- Các công ty cung cấp dịch vụ Cloud Computing thường sử dụng KVM hoặc Xen nhờ ưu điểm mã nguồn mở
- Ngược lại, các công ty doanh nghiệp thường lựa chọn Hyper-V hoặc vSphere vì sự ổn định và giải pháp hỗ trợ kỹ thuật tốt