# CHƯƠNG 3: CÁC THÀNH PHẦN CƠ BẢN TRONG MẠNG MÁY TÍNH
## 3.1 Thế nào là 1 mạng máy tính
Để được gọi là mạng máy tính cần thỏa những yêu cầu sau
- Hai máy tính

- Một giao tiếp mạng trên mỗi máy (NIC : Network interface Card)

- Môi trường truyền :

- Dây cáp mạng

- Môi trường truyền không dây.

- Hệ điều hành mạng :
  UNIX, Windows 98, Windows NT,…, Novell Netware,…
  
  ## Cấu trúc mạng cục bộ
  
– Cấu trúc của mạng (hay topology của mạng mà qua đó thể hiện cách nối các mạng máy tính với nhau ra sao).

– Các nghi thức truyền dữ liệu trên mạng (các thủ tục hướng dẫn trạm làm việc làm thế nào và lúc nào có thể thâm nhập vào đường dây cáp để gửi các gói thông tin ).

– Các loại đường truyền và các chuẩn của chúng .

– Các phương thức tín hiệu.


### Cấu trúc mạng (Topology)
Có 2 kiểu chính
- Peer to peer:
Với phương thức “một điểm – một điểm”,  các đường truyền riêng biệt được thiết lâp để nối các cặp máy tính lại với nhau. 
Mỗi máy tính có thể truyền và nhận trực tiếp dữ liệu hoặc có thể làm trung gian như lưu trữ những dữ liệu 
mà nó nhận được rồi sau đó chuyển tiếp dữ liệu đi cho một máy khác để dữ liệu đó đạt tới đích.

- Peer to many peer
Theo phương thức “một điểm – nhiều điểm ” tất cả các trạm phân chia chung một đường truyền vật lý. 
Dữ liệu được gửi đi từ một máy tính sẽ có thể được tiếp nhận bởi tất cả các máy tính còn lại, 
bởi vậy cần chỉ ra điạ chỉ đích của dữ liệu để mỗi máy tính căn cứ vào đó kiểm tra xem dữ liệu có phải dành cho mình không nếu đúng 
thì nhận còn nếu không thì bỏ qua.

![image](https://user-images.githubusercontent.com/45547213/60577642-eba4f100-9da9-11e9-85ae-810ff8c78e27.png)

### Những kiểu bố trí chính của mạng cục bộ
#### Bus
Trong dạng đường thẳng các máy tính đều được nối vào một đường dây truyền chính (bus). 
Đường truyền chính này được giới hạn hai đầu bởi một loại đầu nối đặc biệt gọi là terminator 
(dùng để nhận biết là đầu cuối để kết thúc đường truyền tại đây).
Mỗi trạm được nối vào bus qua một đầu nối chữ T (T_connector) hoặc một bộ thu phát (transceiver). 
Khi một trạm truyền dữ liệu, tín hiệu được truyền trên cả hai chiều của đường truyền theo từng gói một,
mỗi gói đều phải mang địa chỉ trạm đích. Các trạm khi thấy dữ liệu đi qua nhận lấy, kiểm tra, 
nếu đúng với địa chỉ của mình thì nó nhận lấy còn nếu không phải thì bỏ qua.

#### Ring
Các máy tính được liên kết với nhau thành một vòng tròn theo phương thức “một điểm – một điểm “, 
qua đó mỗi một trạm có thể nhận và truyền dữ liệu theo vòng một chiều và dữ liệu được truyền theo từng gói một. 
Mỗi gói dữ liệu đều có mang địa chỉ trạm đích, mỗi trạm khi nhận được một gói dữ liệu nó kiểm tra nếu đúng với địa chỉ của mình 
thì nó nhận lấy còn nếu không phải thì nó sẽ phát lại cho trạm kế tiếp, cứ như vậy gói dữ liệu đi được đến đích. 
Với dạng kết nối này có ưu điểm là không tốn nhiều dây cáp, tốc độ truyền dữ liệu cao, 
không gây ách tắc tuy nhiên các giao thức để truyền dữ liệu phức tạp và nếu có trục trặc trên một trạm thì cũng ảnh hưởng đến toàn mạng.

#### Star
Ở dạng hình sao, tất cả các trạm được nối vào một thiết bị trung tâm có nhiệm vụ nhận tín hiệu từ các trạm 
và chuyển tín hiệu đến trạm đích với phương thức kết nối là phương thức “một điểm – một điểm “. 
Thiết bị trung tâm hoạt động giống như một tổng đài cho phép thực hiện việc nhận và truyền dữ liệu từ trạm này tới các trạm khác. 
Tùy theo yêu cầu truyền thông trong mạng , thiết bị trung tâm có thể là một bộ chuyển mạch (switch), 
một bộ chọn đường (router) hoặc đơn giản là một bộ phân kênh (Hub). Có nhiều cổng ra và mỗi cổng nối với một máy.



![image](https://user-images.githubusercontent.com/45547213/60578904-3f183e80-9dac-11e9-937e-cbded014ca2c.png)

### Phương thức truyền tín hiệu
Thông thường có hai phương thức truyền tín hiệu trong mạng cục bộ là dùng băng tần cơ sở (baseband) và băng tần rộng (broadband). 
Sự khác nhau chủ yếu giữa hai phương thức truyền tín hiệu này là băng tầng cơ sở chỉ chấp nhận một kênh dữ liệu duy nhất 
trong khi băng rộng có thể chấp nhận đồng thời hai hoặc nhiều kênh truyền thông cùng phân chia giải thông của đường truyền.

Hầu hết các mạng cục bộ sử dụng phương thức băng tần cơ sở.

### Giao thức truyền tín hiệu
Để truyền được dữ liệu trên mạng người ta phải có các thủ tục nhằm hướng dẫn các máy tính của mạng làm thế nào 
và lúc nào có thể thâm nhập vào đường dây cáp để gửi các gói dữ kiện. 

a. Giao thức chuyển mạch (yêu cầu và chấp nhận)

b. Giao thức đường dây đa truy cập với cảm nhận va chạm (Carrier Sense Multiple Access with Collision Detection hay CSMA/CD )

c. Giao thức dùng thẻ bài vòng (Token ring)

d. Giao thức dung thẻ bài cho dạng đường thẳng (Token bus)

### Đường cáp truyền mạng
- Cáp xoắn cặp
- Cáp đồng trục
- Cáp sợi quang (Fiber – Optic Cable)






































