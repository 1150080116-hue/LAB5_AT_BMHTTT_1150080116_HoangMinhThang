# LAB5_AT_BMHTTT_1150080116_HoangMinhThang
Phiên bản môi trường
Oracle VirtualBox
pfSense	CE 2.7.2-RELEASE (amd64), FreeBSD 14.0-CURRENT, build 07/12/2023
Máy trong LAN	Windows Server 2025 Standard Evaluation (Desktop Experience), bản 26100
Mô hình mạng:

Vùng	Cách gắn	Địa chỉ
WAN (em0)	Adapter 1, Bridged qua card Wi-Fi	192.168.1.10/24 (DHCP từ router nhà)
LAN (em1)	Adapter 2, Host-only	pfSense 10.0.0.1/8, máy thật 10.0.0.100/8
DMZ (em2)	Adapter 3, Internal Network dmz-net	pfSense 172.16.0.1/16
VM pfSense: RAM 2 GB, 2 CPU, ổ VDI 16 GB, FreeBSD 64-bit, cài ZFS stripe, đã tháo ISO.

VM DC: RAM 2 GB, ổ 50 GB, một card Host-only. Đang cài Windows Server.
Cấu hình pfSense đã làm:

Console: LAN = 10.0.0.1/8, không bật DHCP.
Setup Wizard: hostname pfSense, domain home.arpa, DNS 8.8.8.8, múi giờ +07, WAN DHCP, đổi mật khẩu admin.
Gán em2 thành OPT1, đặt tên DMZ, IP 172.16.0.1/16.
Outbound NAT: chế độ Hybrid.
Rule LAN: tắt hai Default allow, giữ Anti-Lockout, tạo Base rule LAN to any (Pass, Any, LAN subnets → Any), đã Reset States.
