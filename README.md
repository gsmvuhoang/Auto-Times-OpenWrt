Đồng bộ hóa thời gian trong OpenWrt bằng cách lấy dữ liệu thời gian từ miền đã chọn.

Hỗ trợ đồng bộ thời gian khi có kết nối modem/internet.

Trình kiểm tra kết nối (nếu sử dụng chế độ cron, tập lệnh sẽ kiểm tra kết nối, sau đó khởi động lại ứng dụng VPN nếu không có kết nối internet)

Cài đặt múi giờ tự động tuân theo LuCI - System - System - Timezone.

Hỗ trợ cài đặt múi giờ cho VPN: OpenClash ,Passwall, ShadowsocksR, ShadowsocksR++, V2ray, V2rayA, Xray, Libernet, Xderm Mini, Wegare STL

Cài đặt các gói yêu cầu trước bằng cách mở Terminal hoặc PuTTY:

```
opkg update && opkg install curl wget
```
Dán lệnh bên dưới để cài đặt tập lệnh time_open_wrt:
```
wget --no-check-certificate "https://raw.githubusercontent.com/gsmvuhoang/Auto-Times-OpenWrt/main/time_open_wrt" -O /usr/bin/time_open_wrt && chmod +x /usr/bin/time_open_wrt
```

Nhập lệnh bên dưới vào LuCI -> System -> Startup -> Local Startup:

Ví dụ dùng tên miền google:
```
/usr/bin/time_open_wrt www.google.com
```

Ví dụ dùng mạng Viettel:
```
/usr/bin/time_open_wrt m.tv360.vn
```

Nhập lệnh bên dưới vào LuCI -> System -> Scheduled Tasks để kiểm tra kết nối cứ sau 1 giờ, sau đó khởi động lại vpn nếu không có kết nối:

Ví dụ dùng tên miền google:
```
0 * * * * /usr/bin/time_open_wrt www.google.com cron
```

Ví dụ dùng mạng Viettel:
```
0 * * * * /usr/bin/time_open_wrt m.tv360.vn cron
```
Nhập lệnh bên dưới vào LuCI -> System -> Scheduled Tasks để auto restart router lúc 3h sáng:
```
0 3 * * * /bin/sh -c "reboot"
```

Để update tập lệnh hãy thực hiện lệnh bên dưới:
```
/usr/bin/time_open_wrt update
```

# Mọi thắc mắc vui lòng liên hệ: gsm.vuhoang

Phát triển
tập lệnh và code của AlkhaNet by Teguh Surya Mungaran và được tùy biến lại bởi gsm.vuhoang
