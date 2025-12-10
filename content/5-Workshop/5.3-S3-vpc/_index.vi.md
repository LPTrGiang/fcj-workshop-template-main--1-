---
title : "Truy cập S3 từ VPC"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Sử dụng Gateway endpoint

Trong phần này, bạn sẽ thiết lập điểm cuối Gateway để một phiên bản EC2 có thể truy cập Amazon S3 một cách riêng tư. Bằng cách sử dụng điểm cuối Gateway, tất cả các nội dung tải lên các bucket S3 của bạn đều nằm trong mạng AWS và không đi qua internet công cộng.

Để tạo điểm cuối, bạn chỉ cần chọn VPC mục tiêu và chỉ định Amazon S3 là dịch vụ bạn muốn kết nối.

![overview](/images/5-Workshop/5.3-S3-vpc/diagram2.png)

#### Nội dung

- [Tạo gateway endpoint](3.1-create-gwe/)
- [Test gateway endpoint](3.2-test-gwe/)