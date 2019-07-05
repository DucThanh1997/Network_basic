# REPEATER (BỘ TIẾP SỨC)
## Định nghĩa:
Repeater là loại thiết bị phần cứng đơn giản nhất trong các thiết bị liên kết mạng, nó được hoạt động trong tầng vật lý của 
mô hình hệ thống mở OSI. Repeater dùng để nối 2 mạng giống nhau hoặc các phần một mạng cùng có một nghi thức và một cấu hình. 
Khi Repeater nhận được một tín hiệu từ một phía của mạng thì nó sẽ phát tiếp vào phía kia của mạng.

![image](https://user-images.githubusercontent.com/45547213/60694901-03938680-9f0a-11e9-97a4-5da6d4c72516.png)

## Đặc điểm
Repeater không có xử lý tín hiệu mà nó chỉ loại bỏ các tín hiệu méo, nhiễu, khuếch đại tín hiệu đã bị suy hao (vì đã được phát với khoảng cách xa) và khôi phục lại tín hiệu ban đầu. Việc sử dụng Repeater giúp tăng thêm chiều dài của mạng.

![image](https://user-images.githubusercontent.com/45547213/60694935-232aaf00-9f0a-11e9-86bd-9c8fc5afefe8.png)

Repeater không nối được 2 mạng khác nhau

# BRIDGE (CẦU NỐI)
## Định nghĩa:
Bridge là một thiết bị có xử lý dùng để nối hai mạng giống nhau hoặc khác nhau, nó có thể được dùng với các mạng có các giao thức khác nhau. Cầu nối hoạt động trên tầng liên kết dữ liệu nên không như bộ tiếp sức phải phát lại tất cả những gì nó nhận được

## Cách thức hoạt động
- Ở mỗi đầu kết nối có một bảng các địa chỉ, các trạm được kết nối vào phía đó, khi hoạt động cầu nối xem xét mỗi gói tin nó nhận được bằng cách đọc địa chỉ của nơi gửi và nhận và dựa trên bảng địa chỉ phía nhận được gói tin nó quyết định gửi gói tin hay không và bổ xung bảng địa chỉ.

Cụ thể
- Bridge nhận được gói tin và địa chỉ
- Bridge kiểm tra xem trong bảng địa chỉ của phần mạng nhận được gói tin có địa chỉ đó hay không, nếu không có thì Bridge tự động bổ xung bảng địa chỉ (cơ chế đó được gọi là tự học của cầu nối).
- Khi đọc địa chỉ nơi nhận Bridge kiểm tra xem trong bảng địa chỉ của phần mạng nhận được gói tin có địa chỉ đó hay không, nếu có thì Bridge sẽ cho rằng đó là gói tin nội bộ thuộc phần mạng mà gói tin đến nên không chuyển gói tin đó đi, nếu ngược lại thì Bridge mới chuyển sang phía bên kia. Điều đó cho thấy sự mềm dẻo

## Đặc điểm 
Người ta đánh giá bridge qua 2 thứ
- Tốc độ lọc
- Tốc độ truyền tin

# ROUTER (BỘ TÌM ĐƯỜNG)
## Định nghĩa
Router là một thiết bị hoạt động trên tầng mạng, nó có thể tìm được đường đi tốt nhất cho các gói tin qua nhiều kết nối để đi từ trạm gửi thuộc mạng đầu đến trạm nhận thuộc mạng cuối. Router có thể được sử dụng trong việc nối nhiều mạng với nhau và cho phép các gói tin có thể đi theo nhiều đường khác nhau để tới đích.

![image](https://user-images.githubusercontent.com/45547213/60695560-4c4c3f00-9f0c-11e9-9728-096da6f472ea.png)

## Đặc điểm
Khác với bridge Router có địa chỉ riêng nên nó chỉ nhận các gói tin có địa chỉ đến là nó
Có 2 loại router:
- Router có phụ thuộc giao thức: không có khả năng thay đổi gói tin nên 2 máy phải có giao thức với nhau mới chuyển được dữ liệu
- Router không phụ thuộc vào giao thức: có thể liên kết các mạng dùng giao thức truyền thông khác nhau và có thể chuyển đôiø gói tin của giao thức này sang gói tin của giao thức kia, 

## Phương thức của router
- Phương thức véc tơ khoảng cách : mỗi Router luôn luôn truyền đi thông tin về bảng chỉ đường của mình trên mạng, thông qua đó các Router khác sẽ cập nhật lên bảng chỉ đường của mình.

- Phương thức trạng thái tĩnh : Router chỉ truyền các thông báo khi có phát hiện có sự thay đổi trong mạng vàchỉ khi đó các Routerkhác ù cập nhật lại bảng chỉ đường, thông tin truyền đi khi đó thường là thông tin về đường truyền.


## Một số giao thức hoạt động chính của Router
- RIP(Routing Information Protocol): dùng phương thức vecter khoảng cách
- NLSP (Netware Link Service Protocol): dùng phương thức vecter khoảng cách
- OSPF (Open Shortest Path First): dùng phương thức trạng thái tĩnh
OSPF-IS (Open System Interconnection Intermediate System to Intermediate System): dùng phương thức trạng thái tĩnh

# Gateway
Gateway dùng để kết nối các mạng không thuần nhất chẳng hạn như các mạng cục bộ và các mạng máy tính lớn (Mainframe), do các mạng hoàn toàn không thuần nhất nên việc chuyển đổi thực hiện trên cả 7 tầng của hệ thống mở OSI. Thường được sử dụng nối các mạng LAN vào máy tính lớn. Gateway có các giao thức xác định trước thường là nhiều giao thức, một Gateway đa giao thức thường được chế tạo như các Card có chứa các bộ xử lý riêng và cài đặt trên các máy tính hoặc thiết bị chuyên biệt.

# Hub
## Định nghĩa:
Hub thường được dùng để nối mạng, thông qua những đầu cắm của nó người ta liên kết với các máy tính dưới dạng hình sao.

## Loại
- Hub bị động (Passive Hub) : Hub bị động không chứa các linh kiện điện tử và cũng không xử lý các tín hiệu dữ liệu, nó có chức năng duy nhất là tổ hợp các tín hiệu từ một số đoạn cáp mạng.

- Hub chủ động (Active Hub) : Hub chủ động có các linh kiện điện tử có thể khuyếch đại và xử lý các tín hiệu điện tử truyền giữa các thiết bị của mạng. Qúa trình xử lý tín hiệu được gọi là tái sinh tín hiệu, nó làm cho tín hiệu trở nên tốt hơn, ít nhạy cảm với lỗi do vậy khoảng cách giữa các thiết bị có thể tăng lên.

- Hub thông minh (Intelligent Hub): cũng là Hub chủ động nhưng có thêm các chức năng mới so với loại trước, nó có thể có bộ vi xử lý của mình và bộ nhớ mà qua đó nó không chỉ cho phép điều khiển hoạt động thông qua các chương trình quản trị mạng mà nó có thể hoạt động như bộ tìm đường hay một cầu nối. Nó có thể cho phép tìm đường cho gói tin rất nhanh trên các cổng của nó, thay vì phát lại gói tin trên mọi cổng thì nó có thể chuyển mạch để phát trên một cổng có thể nối tới trạm đích.























