# SỰ CẦN THIẾT PHẢI CÓ MÔ HÌNH TRUYỀN THÔNG
![image](https://user-images.githubusercontent.com/45547213/60645424-d770fa80-9e62-11e9-9988-2cd1f8cc9f00.png)
Để gửi 1 gói tin, hãy xét ví dụ ở trên đây.

- Ứng dụng 1 trên máy tính A muốn gửi dữ liệu cho Ứng dụng 2 ở máy tính B
- Ứng dụng 1 sẽ chuyển dữ liệu xuống dưới tầng truyền dữ liệu và yêu cầu gửi sang điểm tiếp cận dữ liệu của máy B
- Đồng thời các thông tin kiểm soát cũng sẽ được gửi cùng
- Cụ thể, máy A gửi khối dữ liệu muốn chuyển xuống tầng vận chuyển, tầng vận chuyển chia khối đó ra thành khối nhỏ
và đóng gói chúng thành các gói tin.
- Mỗi 1 gói sẽ chứa các thông tin của nó và phần thông tin kiểm soát được gọi là header. Mỗi 1 header sẽ chứa
  + Địa chỉ của điểm tiếp cận giao dịch
  + Số thứ tự của gói tin vì khối dữ liệu chia gói tin ra thành nhiều mảnh 
  + Mã sửa lỗi để kiểm tra gói tin đó có bị lỗi hay không
- Bước tiếp theo tầng vận chuyển máy A sẽ chuyển từng gói tin và địa chỉ của máy tính đích (ở đây là B) xuống tầng tiếp cận mạng 
với yêu cầu chuyển chúng đi.
- Để thực hiện được yêu cầu này tầng tiếp cận mạng cũng tạo các gói tin của mình trước khi truyền qua mạng. 
- Các gói tin này được gắn ở phần đầu gồm địa chỉ máy nhận và mức độ ưu tiên của gói tin

# MỘT SỐ MÔ HÌNH CHUẨN HÓA
## Mô hình OSI
Theo mô hình OSI chương trình truyền thông được chia ra thành 7 tầng với những chức năng phân biệt cho từng tầng.
Hai tầng đồng mức khi liên kết với nhau phải sử dụng một giao thức chung. 
Trong mô hình OSI có hai loại giao thức chính được áp dụng: 
  + Giao thức có liên kết (connection – oriented) : trước khi truyền dữ liệu hai tầng đồng mức cần thiết lập một liên kết logic 
  và các gói tin được trao đổi thông qua liên kết náy, việc có liên kết logic sẽ nâng cao độ an toàn trong truyền dữ liệu.
  + Giao thức không liên kết (connectionless): trước khi truyền dữ liệu không thiết lập liên kết logic 
  và mỗi gói tin được truyền độc lập với các gói tin trước hoặc sau nó.
  
![image](https://user-images.githubusercontent.com/45547213/60646777-62072900-9e66-11e9-8e9a-18d40bb9c006.png)

Như vậy với giao thức có liên kết, quá trình truyền thông phải gồm 3 giai đoạn phân biệt:

Thiết lập liên kết (logic)–> Truyền dữ liệu –> Hủy bỏ liên kết (logic)

Đối với giao thức không liên kết thì chỉ có duy nhất một giai đoạn truyền dữ liệu mà thôi.

**Gói tin**: Gói tin (Packet) được hiểu như là một đơn vị thông tin dùng trong việc liên lạc, chuyển giao dữ liệu trong mạng máy tính. 
Những thông điệp (message) trao đổi giữa các máy tính trong mạng, được tạo dạng thành các gói tin ở máy nguồn. 
Và những gói tin này khi đích sẽ được kết hợp lại thành thông điệp ban đầu. 
Một gói tin có thể chứa đựng các yêu cầu phục vụ, các thông tin điều khiển và dữ liệu.

Trên quan điểm mô hình mạng phân tầng tầng mỗi tầng chỉ thực hiện một chức năng là nhận dữ liệu từ tầng bên trên
để chuyển giao xuống cho tầng bên dưới và ngược lại. Chức năng này thực chất là gắn thêm và gỡ bỏ phần đầu (header) 
đối với các gói tin trước khi chuyển nó đi. Nói cách khác, từng gói tin bao gồm phần đầu (header) và phần dữ liệu. 
Khi đi đến một tầng mới gói tin sẽ được đóng thêm một phần đầu đề khác và được xem như là gói tin của tầng mới, 
công việc trên tiếp diễn cho tới khi gói tin được truyền lên đường dây mạng để đến bên nhận.

Tại bên nhận các gói tin được gỡ bỏ phần đầu trên từng tầng tướng ứng và đây cũng là nguyên lý của bất cứ mô hình phân tầng nào.

# CÁC CHỨC NĂNG CHỦ YẾU CỦA CÁC TẦNG CỦA MÔ HÌNH OSI.
## Tầng 1: Tầng Vật Lý
- Tầng vật lý (Physical layer) là tầng dưới cùng của mô hình OSI là. Nó mô tả các đặc trưng vật lý của mạng:
  + Các loại cáp được dùng để nối các thiết bị
  + Các loại đầu nối được dùng
  + Các dây cáp có thể dài bao nhiêu v.v…

- Tầng Vật lý không có gói header, ở tầng này có 2 phương thức chính đồng bộ (synchronous) và dị bộ (asynchronous)
  + Asynchronous: cho phép các tín hiệu gửi đi mà không cần quan tâm đến các tín hiệu đồng bộ, sử dụng các bit đặc biệt để tách
  các xâu bit (START, STOP)
  + Synchronous: sử dụng phương thức truyền cần có đồng bộ giữa máy gửi và máy nhận, 
  nó chèn các ký tự đặc biệt như SYN (Synchronization),
  EOT (End Of Transmission) hay đơn giản hơn, một cái “cờ ” (flag) giữa các dữ liệu của máy gửi để báo hiệu 
  cho máy nhận biết được dữ liệu đang đến hoặc đã đến.
 
 ## Tầng 2: Tầng liên kết dữ liệu
 
 Tầng liên kết dữ liệu (data link layer) quy định
 - các phương thức, kích thước, địa chỉ máy gửi và nhận của mỗi gói tin được gửi đi
 - Các cơ chế truy nhập thông tin trên mạng và phương tiện sao cho nó đưa đến thông tin cho người nhận
 
 Ở tầng liên kết có 2 phương thức liên kết đó là 
 - 1 điểm - 1 điểm: 2 máy sẽ thiết lập 1 đường truyền riêng biệt để nối các điểm vào với nhau
 - 1 điểm - nhiều điểm: tất cả các máy phân chia chung 1 đường truyền vật lý
 
 Tầng liên kết dữ liệu cũng cung cấp cách phát hiện và sửa lỗi cơ bản để đảm bảo cho dữ liệu nhận được giống hoàn toàn với dữ liệu gửi đi.
 Nếu một gói tin có lỗi không sửa được, tầng liên kết dữ liệu phải chỉ ra được cách thông báo cho nơi gửi biết gói tin đó
 có lỗi để nó gửi lại.

Tầng liên kết có 2 giao thức:
- Giao thức hướng ký tự: được xây dựng dựa trên các ký tự đặc biệt của một bộ mã chuẩn nào đó (như ASCII hay EBCDIC)

- Giao thức hướng bit dùng các cấu trúc nhị phân (xâu bit) để xây dựng các phần tử của giao thức (đơn vị dữ liệu, các thủ tục…)
và khi nhận, dữ liệu sẽ được tiếp nhận lần lượt từng bit một.

## Tầng 3: Tầng Mạng (Network)

Tầng mạng (network layer) thực hiện việc kết nối các mạng với nhau bằng cách tìm đường (routing) cho các gói tin từ một mạng này
đến một mạng khác. Nó xác định việc chuyển hướng, vạch đường các gói tin trong mạng, các gói này có thể phải đi qua nhiều chặng 
trước khi đến được đích cuối cùng. Nó luôn tìm các tuyến  không tắc nghẽn để đưa các gói tin đến đích.

Tầng mạng cung các các phương tiện để truyền các gói tin qua mạng, thậm chí qua một mạng của mạng (network of network). 
Bởi vậy nó cần phải đáp ứng với nhiều kiểu mạng và nhiều kiểu dịch vụ cung cấp bởi các mạng khác nhau. 
Hai chức năng chủ yếu của tầng mạng là chọn đường (routing) và chuyển tiếp (relaying). 
Tầng mạng là tầng quan trọng nhất khi liên kết hai loại mạng khác nhau như mạng Ethernet với mạng Token Ring 
khi đó phải dùng một bộ tìm đường (quy định bởi tầng mạng) để chuyển các gói tin từ mạng này sang mạng khác và ngược lại.

Kĩ thuật chọn đường gồm 2 chức năng chính sau đây: 
- Quyết định chọn đường tối ưu dựa trên các thông tin đã có về mạng tại thời điểm đó thông qua những tiêu chuẩn tối ưu nhất định.
- Cập nhật các thông tin về mạng, tức là thông tin dùng cho việc chọn đường, trên mạng luôn có sự thay đổi thường xuyên 
nên việc cập nhật là việc cần thiết.


![image](https://user-images.githubusercontent.com/45547213/60650868-33418080-9e6f-11e9-9afa-8a6db48ffe64.png)

## Tầng 4: Vận chuyển (Transport)
Tầng vận chuyển (transport layer) là tầng cơ sở mà ở đó một máy tính của mạng chia sẻ thông tin với một máy khác. 
Tầng vận chuyển:
- Đồng nhất mỗi trạm bằng một địa chỉ duy nhất và quản lý sự kết nối giữa các trạm. 
- Chia các gói tin lớn thành các gói tin nhỏ hơn trước khi gửi đi. 
- Đánh số các gói tin và đảm bảo chúng chuyển theo đúng thứ tự.
- Tầng cuối cùng chịu trách nhiệm về mức độ an toàn trong truyền dữ liệu nên giao thức tầng vận chuyển phụ thuộc 
rất nhiều vào bản chất của tầng mạng.
- Có 3 giao thức
  + Mạng loại A: Có tỷ suất lỗi và sự cố có báo hiệu chấp nhận được (tức là chất lượng chấp nhận được). 
  Các gói tin được giả thiết là không bị mất. Tầng vận chuyển không cần cung cấp các dịch vụ phục hồi hoặc sắp xếp thứ tự lại.
  + Mạng loại B: Có tỷ suất lỗi chấp nhận được nhưng tỷ suất sự cố có báo hiệu lại không chấp nhận được. 
  Tầng giao vận phải có khả năng phục hồi lại khi xẩy ra sự cố.
  + Mạng loại C: Có tỷ suất lỗi không chấp nhận được (không tin cậy) hay là giao thức không liên kết. 
  Tầng giao vận phải có khả năng phục hồi lại khi xảy ra lỗi và sắp xếp lại thứ tự các gói tin.
  
## Tầng 5: Giao dịch (Session)

Tầng giao dịch (session layer) thiết lập “các giao dịch” giữa các trạm trên mạng, 
nó đặt tên nhất quán cho mọi thành phần muốn đối thoại với nhau và lập ánh xa giữa các tên với địa chỉ của chúng. 
Một giao dịch phải được thiết lập trước khi dữ liệu được truyền trên mạng, 
tầng giao dịch đảm bảo cho các giao dịch được thiết lập và duy trì theo đúng qui định.
- Cung cấp các điểm đồng bộ để kiểm soát việc trao đổi dữ liệu.
- Áp đặt các qui tắc cho các tương tác giữa các ứng dụng của người sử dụng.
- Cung cấp cơ chế “lấy lượt” (nắm quyền) trong quá trình trao đổi dữ liệu.

Tầng giao dịch có các hàm cơ bản sau:
- Give Token cho phép người sử dụng chuyển một token cho một người sử dụng khác của một liên kết giao dịch.
- Please Token cho phép một người sử dụng chưa có token có thể yêu cầu token đó.
- Give Control dùng để chuyển tất cả các token từ một người sử dụng sang một người s? d?ng khác.

## Tầng 6: Tầng trình diễn
Tầng trình diễn (Presentation layer) phải chịu trách nhiệm chuyển đổi dữ liệu gửi đi trên mạng từ một loại biểu diễn này sang một loại khác.

Tầng trình diễn cũng có thể được dùng kĩ thuật mã hóa để xáo trộn các dữ liệu trước khi được truyền đi và giải mã ở đầu đến để bảo mật.

## Tầng 7: Tầng ứng dụng
Tầng ứng dụng (Application layer) là tầng cao nhất của mô hình OSI, nó xác định giao diện giữa người sử dụng và môi trường OSI và 
giải quyết các kỹ thuật mà các chương trình ứng dụng dùng để giao tiếp với mạng.

































