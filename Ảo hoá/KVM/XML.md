# Tổng quan về file XML
- VM trong KVM có 2 thành phần chính là VM's definition được lưu dưới dạng file XML mặc định ở thư mục ```/etc/libvirt/qemu``` và VM's storage lưu dưới dạng file image
- File domain XML chứa những thông tin về thành phần của máy ảo (CPU, RAM, các thiết lập các thiết bị I/O,...)
- Libvirt dùng những thông tin này để tiến hành khởi chạy tiến trình QEMU-KVM tạo máy ảo
- KVM cũng có các file XML khác để lưu trữ các thông tin liên quan tới network, storage,...
- Mục đích chính của XML là đơn giản hoá việc chia sẻ dữ liệu giữa các hệ thống khác nhau, đặc biệt là các hệ thống được kết nối Internet

### Các thành phần của file XML
- File XML được tổ chức theo các khối lệnh trong một khối lệnh tổng quan, cú pháp tương tự HTML khi có thẻ mở và thẻ đóng

![image](https://github.com/Tubui160999/thuctap_nhanhoa/blob/master/KVM/images/filexml.png)

- Thẻ ngoài cùng bao các thẻ khác là ```domain```, thẻ này không thể thiếu trong file cấu hình. Tham số type cho biết hypervisor đang sử dụng của VM
- ```name```: Thông tin về VM
- ```uuid```: Mã nhận dạng quốc tế duy nhất cho máy ảo, format theo RFC 4122, nếu thiếu trường uuid khi khởi tạo, mã này sẽ được tự động sinh ra
- ```title```: Tiêu đề của máy ảo
- ```description```: Đoạn mô tả của máy ảo
- ```metadata```: Chứa thông tin của file xml
- ```memory```: Dung lượng RAM của máy ảo được cấp khi khởi tạo máy
- ```unit```: Đơn vị, mặc định là KiB
- ```currentMemory```: Dung lượng RAM tối đa có thể sử dụng

- ```vcpu```: Tổng số vcpu được cấp cho máy ảo khi được tạo
    - ```cpuset```: Danh sách các CPU vật lý mà máy ảo đang sử dụng
    - ```current```: Chỉ định cho phép kích hoạt nhiều hơn số CPU đang sử dụng
    - ```placement```: Vị trí của CPU, giá trị có thể là ```static``` hoặc ```dynamic```

- ```os```: Chứa các thông tin về hệ điều hành của máy ảo
    - ```arch```: Hệ điều hành thuộc kiến trúc 32bit hoặc 64bit
    - ```machine```: Thông tin về kernel của hệ điều hành
    - ```loader```: Read-only có giá trị ```yes``` hoặc ```no``` chỉ ra file writable hay read-only, ```type``` có giá trị ```rom``` hoặc ```pflash``` chỉ ra nơi guest memory được kết nối
    - ```kernel```: Đường dẫn tới kernel image trên hệ điều hành máy chủ
    - ```initrd```: Đường dẫn tới ramdisk image trên hệ điều hành máy chủ
    - ```cmdline```: Xác định giao diện điều khiển thay thế

- Các sự kiện xảy ra của OS
    - ```on_poweroff```: Hành động sẽ được thực hiện khi người dùng yêu cầu tắt máy
    - ```on_reboot```: Hành động được thực hiện khi người dùng yêu cầu reset máy
    - ```on_crash```: Hành động được thực hiện khi có sự cố

- Các hành động có thể được thực thi khi gặp các sự kiện trên
    - ```destroy```: Chấm dứt và giải phóng tài nguyên
    - ```restart```: Chấm dứt và sau đố khởi động lại giữ nguyên cấu hình
    - ```preserve```: Chấm dứt nhưng dữ liệu vẫn được lưu lại
    - ```rename-restart```: Khởi động lại với tên mới
    - ```destroy``` và ```restart``` được hỗ trợ trong cả ```on_poweroff``` và ```on_reboot```, ```rename-restart``` được dùng trong ```on_poweroff```

- ```cpu``` chứa các mô tả yêu cầu của guest CPU, thuộc tính ```match``` xác định mức độ liên kết của CPU ảo được cung cấp cho guest phù hợp với các yêu cầu này, các giá trị của ```match``` có thể là ```minimum```, ```exact``` hay ```strict```

- clock: Thiết lập về thời gian

- offset: Giá trị utc, localtime, timezone, variable

- feature: Là hypervisor cho phép thao tác bật tắt một số tính năng, ví dụ
    ```sh
    <features>
    <pae/>
    <acpi/>
    <apic/>
    <hap/>
    <privnet/>
    <hyperv>
        <relaxed state='on'/>
        <vapic state='on'/>
        <spinlocks state='on' retries='4096'/>
        <vpindex state='on'/>
        <runtime state='on'/>
        <synic state='on'/>
        <reset state='on'/>
        <vendor_id state='on' value='KVM Hv'/>
        <frequencies state='on'/>
        <reenlightenment state='on'/>
        <tlbflush state='on'/>
    </hyperv>
    <kvm>
        <hidden state='on'/>
    </kvm>
    <pvspinlock state='on'/>
    <gic version='2'/>
    <ioapic driver='qemu'/>
    <hpt resizing='required'>
        <maxpagesize unit='MiB'>16</maxpagesize>
    </hpt>
    <vmcoreinfo state='on'/>
    <smm state='on'>
        <tseg unit='MiB'>48</tseg>
    </smm>
    <htm state='on'/>
    </features>
    ```

    - pae: Chế độ địa chỉ vật lý mở rộng cho phép 32-bit và lớn hơn 4GB RAM
    - acpi: Sử dụng trong việc quản lý máy ảo

- ```devices```: Khai báo thông tin về các thành phần của máy ảo như disk, network,...
    - ```emulator```: Khai báo đường dẫn tới thư viện ảo hoá các thiết bị
    
### Ví dụ về một file XML hoàn chỉnh cấu hình cho máy ảo
```sh
<domain type='kvm'>
  <name>tubui</name>
  <uuid>4e893778-bbb5-11ec-9796-b8ca3a5eb048</uuid>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>2097152</currentMemory>
  <vcpu placement='static'>5</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-rhel7.0.0'>hvm</type>
    <boot dev='cdrom'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>SandyBridge</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/libexec/qemu-kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/tubui.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
	  <source file="/var/lib/libvirt/images/CentOS-7-x86_64-Minimal-2009.iso"/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:28:5f:94'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target type='isa-serial' port='0'>
        <model name='isa-serial'/>
      </target>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='unix'>
      <target type='virtio' name='org.qemu.guest_agent.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='2'/>
    </channel>
    <input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='2'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <address type='usb' bus='0' port='3'/>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```