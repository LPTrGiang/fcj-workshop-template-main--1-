---
title: "Introduction"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### VPC endpoints
+ **VPC endpoints** là các thiết bị ảo được thiết kế theo chiều ngang, có tính sẵn sàng cao và khả năng chịu lỗi. Chúng cho phép tài nguyên tính toán trong VPC giao tiếp với các dịch vụ AWS mà không tạo ra rủi ro về tính sẵn sàng.
+ Tài nguyên chạy trong VPC có thể truy cập **Amazon S3** thông qua **Gateway endpoint**. Ngoài ra, **PrivateLink Interface endpoints** có thể được sử dụng cho các tài nguyên chạy trong VPC hoặc tại môi trường on-premises.

#### Workshop overview
Trong workshop này, bạn sẽ sử dụng hai VPC:
+ **"VPC Cloud"**: chứa các tài nguyên trên đám mây như **Gateway endpoint** và một EC2 instance dùng để kiểm thử.
+ **"VPC On-Prem"**: mô phỏng môi trường on-premises (nhà máy hoặc trung tâm dữ liệu doanh nghiệp). Một EC2 instance chạy strongSwan đã được triển khai sẵn và tự động thiết lập kết nối VPN Site-to-Site với AWS Transit Gateway. Kết nối VPN này mô phỏng việc kết nối từ on-premises lên AWS.  
  Để giảm chi phí, workshop chỉ cung cấp một thiết bị VPN. Trong môi trường production, AWS khuyến nghị triển khai nhiều thiết bị VPN để đảm bảo tính sẵn sàng cao.
