---
title : "Chuẩn bị tài nguyên"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

Các thành phần này hoạt động cùng nhau để mô phỏng chuyển tiếp DNS và phân giải tên tại chỗ.

---

#### Triển khai ngăn xếp CloudFormation

Mẫu CloudFormation tạo các dịch vụ bổ sung cần thiết để mô phỏng môi trường tại chỗ:

+ Vùng lưu trữ riêng Route 53 lưu trữ bản ghi bí danh cho điểm cuối PrivateLink S3
+ Điểm cuối **Bộ giải quyết nội bộ Route 53** cho phép **VPC Cloud** phân giải các truy vấn DNS đến đến Vùng lưu trữ riêng
+ Điểm cuối **Bộ giải quyết nội bộ Route 53** cho phép **VPC On-prem** chuyển tiếp các truy vấn DNS từ S3 đến **VPC Cloud**

![route 53 diagram](/images/5-Workshop/5.4-S3-onprem/route53.png)

1. Click link sau để mở [AWS CloudFormation console](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://s3.amazonaws.com/reinvent-endpoints-builders-session/R53CF.yaml&stackName=PLOnpremSetup). Mẫu yêu cầu sẽ được tải sẵn vào menu. Chấp nhận tất cả mặc định và nhấp vào Tạo stack.

![Create stack](/images/5-Workshop/5.4-S3-onprem/create-stack.png)

![Button](/images/5-Workshop/5.4-S3-onprem/create-stack-button.png)

Quá trình triển khai có thể mất vài phút. Bạn có thể chuyển sang bước tiếp theo mà không cần chờ hoàn tất.

---

#### Cập nhật bảng định tuyến riêng tại chỗ

Hội thảo này sử dụng **strongSwan VPN** chạy trên một phiên bản EC2 để mô phỏng kết nối giữa trung tâm dữ liệu tại chỗ và đám mây AWS.

Hầu hết các thành phần đã được cung cấp sẵn, nhưng để hoàn tất cấu hình, bạn phải cập nhật bảng định tuyến **VPC On-prem** để lưu lượng truy cập hướng đến đám mây được định tuyến qua phiên bản strongSwan VPN.

1. Mở **bảng điều khiển Amazon EC2**.

2. Chọn phiên bản có tên **infra-vpngw-test**.

Trên tab *Chi tiết*, sao chép **ID phiên bản** và dán vào trình soạn thảo văn bản để tham khảo sau này.

![ec2 id](/images/5-Workshop/5.4-S3-onprem/ec2-onprem-id.png)

3. Đi đến VPC menu bằng cách gõ "VPC" vào Search box

4. Click vào Route Tables, chọn RT Private On-prem route table, chọn Routes tab, và click Edit Routes.

![rt](/images/5-Workshop/5.4-S3-onprem/rt.png)

5. Click Add route.
+ Destination: CIDR block của Cloud VPC
+ Target: ID của infra-vpngw-test instance (bạn đã lưu lại ở bước trên)

![add route](/images/5-Workshop/5.4-S3-onprem/add-route.png)

6. Click Save changes




