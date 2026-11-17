

| STT | Tên UC |
| :---- | :---- |
| UC01 | Khởi động game |
| UC02 | Cài đặt |
| UC03 | Quản lý nghề |
| UC04 | Quản lý nhân vật |
| UC05 | Khám phá thế giới |
| UC06 | Quan hệ NPC |
| UC07 | Quest |
| UC08 | Kinh doanh |
| UC09 | Inventory |
| UC10 | Shop |
| UC11 | Quản lý tiền |
| UC12 | Công ty |
| UC13 | Kỹ năng |
| UC14 | Mini Game |
| UC15 | Thành tựu |

Ví Dụ mẫu viết đặc tả Use Case 

| Mã Use Case: |  |
| :---- | :---- |
| Tên Use Case: |  |
| Mục Đích: |  |
| Mô tả: |  |
| Actor: | \+Chính: \+Phụ: |
| Mức ưu tiên: |  |
| Tần suất sử dụng: |  |

Trigger:  
Tiền điều kiện:  
Hậu điều kiện:  
Luồng chính:  
1\.  
2\.  
Luồng thay thế:  
**A1. abcde**

* **abcxyz**

**A2. abcde**

* **abcxyz**

Luồng ngoại lệ:  
**E1. abcde**  
**E2. abcde**  
Business Rule / Quy tắc nghiệp vụ:

* **BR1**  
* **BR2**

Include:  
Extend:  
Yêu cầu phi chức năng:  
Giao diện liên quan:  
Ghi Chú:

**Ghi chú chuẩn hóa cho toàn bộ tài liệu Use Case**

* Mã UC của module lớn được thống nhất theo dạng UC01.x.  
* Các Use Case con được đặc tả độc lập nhưng vẫn phải giữ quan hệ với Use Case cha.  
* Business Rule chỉ ghi các quy tắc đã xác định hoặc cần thiết cho hành vi của Use Case; các giá trị chi tiết chưa thống nhất sẽ được chốt ở giai đoạn thiết kế.  
* Yêu cầu phi chức năng chưa có số liệu cụ thể được ghi ở mức nguyên tắc, tránh tự đặt thông số không được nhóm thống nhất.  
* Khi nhóm gửi module tiếp theo, cách đánh số sẽ tiếp tục theo cấu trúc đã thống nhất: UC02, UC03...; các chức năng con dùng UC02.1, UC02.2... tương ứng.

**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC01 | khởi động game | Tổng quát |
| UC01.1 | Đăng nhập | Được UC01 gọi; bao gồm Lưu game, Tiếp tục game, Thoát game |
| UC01.2 | Đăng kí | Được UC01 gọi, bao gồm Tạo nhân vật và Chọn nhân vật |
| UC01.3 | Tạo nhân vật | Được UC01.2 gọi, sau đó được Chọn nhân vật Extend  |
| UC01.4 | Chọn nhân vật | Có thể mở rộng Tạo nhân vật |
| UC01.5 | Lưu game | bao gồm các luồng liên quan trong phiên chơi |
| UC01.6 | Tiếp tục game | bao gồm tiến độ từ Lưu game, và các luồng liên quan |
| UC01.7 | Thoát game | được gọi khi người chơi kết thúc phiên chơi |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC01 Khởi động game  | UC01.1, UC01.2  | Không  | Use Case cấp module  |
| UC01.1 Đăng nhập  | UC01.5, UC01.6, UC01.7  | Không  | Hoạt động theo luồng, phiên đã cấp |
| UC01.2 Đăng ký  | UC01.3  | Không  | Tạo nhân vật sau đăng ký  |
| UC01.3 Tạo nhân vật  | Không  | UC01.4  | Tạo xong có thể tiến hành luồng chạy chính |
| UC01.4 Chọn nhân vật  | UC01.5  | UC01.3  | Có thể chuyển sang tạo nhân vật  |
| UC01.5 Lưu game  | Không | Không  | Chức năng dùng chung  |
| UC01.6 Tiếp tục game  | UC01.5  | Không  | Khôi phục từ Save  |
| UC01.7 Thoát game  | UC01.5  | Không  | Có thể lưu trước khi thoát  |

**Đặc tả UC01**

| Mã Use Case | UC01 |
| :---- | :---- |
| Tên Use Case | Khởi động game |
| Mục đích | Cho phép người chơi mở trò chơi và truy cập vào giao diện chính để bắt đầu hoặc tiếp tục chơi.  |
| Mô tả | Khi người chơi mở game, hệ thống khởi tạo môi trường trò chơi, kiểm tra dữ liệu cần thiết, tải tài nguyên và hiển thị giao diện để người chơi thực hiện các chức năng tiếp theo.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi lần mở game |

Trigger  
Người chơi ấn vào biểu tượng trò chơi.  
Tiền điều kiện

* Game đã được cài đặt.  
* Thiết bị đáp ứng cấu hình tối thiểu.  
* Dữ liệu game không bị lỗi.

Hậu điều kiện

* Nếu thành công: Menu chính được hiển thị và người chơi có thể lựa chọn chức năng.  
* Nếu thất bại: Hệ thống hiển thị thông báo lỗi và kết thúc chương trình hoặc yêu cầu người chơi xử lý lỗi.

Luồng chính

1. Người chơi khởi động game.  
2. Hệ thống khởi tạo Engine.  
3. Hệ thống kiểm tra dữ liệu và các tài nguyên cần thiết.  
4. Hệ thống tải tài nguyên của game như hình ảnh, âm thanh, dữ liệu và các thành phần cần thiết khác.  
5. Hệ thống hiển thị Splash Screen nếu có.  
6. Hệ thống hiển thị Menu chính.  
7. Người chơi lựa chọn chức năng.  
8. Hệ thống điều hướng người chơi đến Use Case tương ứng.

Luồng thay thế  
A1. Thiếu dữ liệu hoặc Resource

* Hệ thống phát hiện tài nguyên cần thiết bị thiếu hoặc không thể tải.  
* Hệ thống hiển thị thông báo lỗi.  
* Hệ thống không cho phép tiếp tục vào game và kết thúc chương trình hoặc yêu cầu xử lý lỗi.

A2. Không đọc được Save

* Hệ thống phát hiện dữ liệu Save không thể đọc.  
* Hệ thống thông báo Save bị lỗi.  
* Hệ thống cho phép người chơi tạo Save mới nếu chức năng này được hỗ trợ.

A3. Phiên bản không tương thích

* Hệ thống phát hiện phiên bản dữ liệu hoặc game không tương thích.  
* Hệ thống hiển thị yêu cầu cập nhật hoặc xử lý phiên bản tương ứng.

Luồng ngoại lệ  
Không xác định ngoại lệ riêng ở cấp Use Case. Các lỗi khởi tạo, tải Resource hoặc đọc dữ liệu được xử lý theo các luồng thay thế trên.  
Business Rule / Quy tắc nghiệp vụ

* BR01: Game phải hoàn tất các bước khởi tạo cần thiết trước khi cho phép người chơi vào Menu chính.  
* BR02: Không cho phép tiếp tục vào game khi tài nguyên bắt buộc bị lỗi.  
* BR03: Hệ thống phải kiểm tra dữ liệu Save trước khi cho phép sử dụng chức năng Tiếp tục game.

Include  
UC01.1 Đăng nhập; UC01.2 Đăng ký.  
Extend  
Không.  
Yêu cầu phi chức năng  
Không.  
Giao diện liên quan  
Màn hình khởi động/Splash Screen và Menu chính.  
Ghi chú  
Không.

| Mã Use Case | UC01.1  |
| :---- | :---- |
| Tên Use Case | Đăng nhập  |
| Mục đích | Cho phép người chơi xác thực tài khoản và truy cập vào dữ liệu nhân vật của mình.  |
| Mô tả | Người chơi nhập thông tin tài khoản. Hệ thống kiểm tra thông tin xác thực và cho phép tiếp tục nếu thông tin hợp lệ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi cần truy cập tài khoản  |

**Trigger**  
Người chơi chọn chức năng Đăng nhập từ giao diện khởi động.  
**Tiền điều kiện**

* Game đã khởi động thành công.  
* Người chơi chưa đăng nhập vào tài khoản.

**Hậu điều kiện**

* Nếu thành công: Người chơi được xác thực và có thể thực hiện các chức năng liên quan đến nhân vật/phiên chơi.  
* Nếu thất bại: Người chơi vẫn ở giao diện đăng nhập và được yêu cầu nhập lại thông tin.

**Luồng chính**

1. Người chơi chọn Đăng nhập.  
2. Hệ thống hiển thị giao diện đăng nhập.  
3. Người chơi nhập thông tin tài khoản.  
4. Người chơi xác nhận đăng nhập.  
5. Hệ thống kiểm tra thông tin xác thực.  
6. Nếu hợp lệ, hệ thống xác nhận đăng nhập thành công.  
7. Hệ thống chuyển người chơi sang khu vực quản lý/chọn nhân vật hoặc chức năng tiếp theo theo thiết kế.

**Luồng thay thế**  
**A1. Thông tin đăng nhập không hợp lệ**

* Hệ thống thông báo thông tin đăng nhập không chính xác.  
* Người chơi nhập lại thông tin.

**A2. Người chơi hủy đăng nhập**

* Hệ thống hủy thao tác đăng nhập.  
* Quay về giao diện trước đó.

**Luồng ngoại lệ**  
Lỗi hệ thống hoặc không thể truy cập dữ liệu tài khoản: hiển thị thông báo và không tạo phiên đăng nhập.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ tạo phiên đăng nhập khi thông tin xác thực hợp lệ.  
* BR02: Không hiển thị hoặc lưu mật khẩu dưới dạng dữ liệu có thể đọc trực tiếp.

**Include**  
UC01.5 Lưu game; UC01.6 Tiếp tục game; UC01.7 Thoát game (theo sơ đồ hiện tại).  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Thời gian phản hồi đăng nhập cần đủ nhanh để không gây gián đoạn trải nghiệm; giá trị cụ thể sẽ được nhóm xác định khi triển khai.  
**Giao diện liên quan**  
Màn hình Đăng nhập.  
**Ghi chú**  
Cách xác thực online/offline cần được nhóm thống nhất trong thiết kế hệ thống.

| Mã Use Case | UC01.2 |
| :---- | :---- |
| Tên Use Case | Đăng kí |
| Mục đích | Cho phép người chơi tạo tài khoản mới để sử dụng hệ thống game.  |
| Mô tả | Người chơi cung cấp thông tin đăng ký. Hệ thống kiểm tra dữ liệu và tạo tài khoản nếu hợp lệ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi chưa có tài khoản  |

**Trigger**  
Người chơi chọn chức năng Đăng ký.  
**Tiền điều kiện**

* Game đã khởi động.  
* Người chơi chưa có tài khoản hoặc muốn tạo tài khoản mới.

**Hậu điều kiện**

* Nếu thành công: Tài khoản mới được tạo và người chơi có thể tiếp tục theo luồng hệ thống.  
* Nếu thất bại: Tài khoản không được tạo và người chơi được yêu cầu chỉnh sửa dữ liệu.

**Luồng chính**

1. Người chơi chọn Đăng ký.  
2. Hệ thống hiển thị biểu mẫu đăng ký.  
3. Người chơi nhập các thông tin được yêu cầu.  
4. Hệ thống kiểm tra tính hợp lệ của dữ liệu.  
5. Hệ thống kiểm tra điều kiện tạo tài khoản.  
6. Nếu hợp lệ, hệ thống tạo tài khoản.  
7. Hệ thống thông báo đăng ký thành công.  
8. Hệ thống cho phép người chơi tiếp tục sang bước tạo nhân vật theo thiết kế.

**Luồng thay thế**  
**A1. Thông tin đăng ký không hợp lệ**

* Hệ thống chỉ ra thông tin cần chỉnh sửa.  
* Người chơi sửa và gửi lại biểu mẫu.

**A2. Tài khoản đã tồn tại**

* Hệ thống thông báo tài khoản đã tồn tại.  
* Người chơi nhập thông tin khác hoặc chuyển sang Đăng nhập.

**A3. Người chơi hủy đăng ký**

* Hệ thống hủy thao tác.  
* Quay về giao diện trước đó.

**Luồng ngoại lệ**  
Không thể lưu tài khoản hoặc xảy ra lỗi hệ thống: hiển thị thông báo và không tạo tài khoản không hoàn chỉnh.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Thông tin bắt buộc phải được nhập đầy đủ.  
* BR02: Tài khoản phải có định danh duy nhất theo cơ chế mà nhóm lựa chọn.  
* BR03: Chỉ tạo tài khoản sau khi toàn bộ dữ liệu hợp lệ.

**Include**  
UC01.3 Tạo nhân vật.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Dữ liệu tài khoản phải được bảo vệ và không làm mất dữ liệu khi thao tác đăng ký thất bại.  
**Giao diện liên quan**  
Màn hình Đăng ký.  
**Ghi chú**  
Các trường dữ liệu cụ thể như tên tài khoản, mật khẩu, email... cần thống nhất với thiết kế database.

| Mã Use Case | UC01.3 |
| :---- | :---- |
| Tên Use Case | Tạo nhân vật |
| Mục đích | Cho phép người chơi tạo một nhân vật mới để tham gia và lưu tiến trình trong game.  |
| Mô tả | Người chơi thiết lập thông tin nhân vật theo các lựa chọn mà game cung cấp. Hệ thống tạo dữ liệu nhân vật và lưu lại.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi tạo nhân vật mới |

**Trigger**  
Người chơi chọn chức năng Tạo nhân vật.  
**Tiền điều kiện**  
Người chơi đã đăng nhập hoặc đang ở luồng đăng ký theo thiết kế hiện tại.  
Hệ thống đang ở màn hình quản lý nhân vật.  
**Hậu điều kiện**

* Một nhân vật mới được tạo thành công.  
* Thông tin nhân vật được lưu vào dữ liệu game.  
* Nhân vật có thể được chọn để bắt đầu/tiếp tục phiên chơi.

**Luồng chính**

1. Người chơi chọn Tạo nhân vật.  
2. Hệ thống hiển thị giao diện tạo nhân vật.  
3. Người chơi nhập/chọn các thông tin nhân vật được game cung cấp.  
4. Người chơi xác nhận tạo nhân vật.  
5. Hệ thống kiểm tra dữ liệu.  
6. Hệ thống tạo nhân vật với các thông số ban đầu.  
7. Hệ thống lưu dữ liệu nhân vật.  
8. Hệ thống thông báo tạo nhân vật thành công.

**Luồng thay thế**  
**A1. Dữ liệu nhân vật không hợp lệ**

* Hệ thống thông báo thông tin cần chỉnh sửa.  
* Người chơi chỉnh sửa và xác nhận lại.

**A2. Người chơi hủy tạo nhân vật**

* Hệ thống hủy thao tác.  
* Quay về màn hình quản lý/chọn nhân vật.

**Luồng ngoại lệ**  
Không thể lưu dữ liệu nhân vật: thông báo lỗi và không xác nhận việc tạo nhân vật thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Nhân vật phải có các thông tin bắt buộc theo thiết kế game.  
* BR02: Nhân vật mới phải được gán các thông số khởi tạo hợp lệ.  
* BR03: Không tạo bản ghi nhân vật nếu dữ liệu đầu vào không hợp lệ.

**Include**  
Không.  
**Extend**  
Được UC01.4 Chọn nhân vật mở rộng theo sơ đồ hiện tại.  
**Yêu cầu phi chức năng**  
Thao tác tạo nhân vật không được làm mất dữ liệu tài khoản hoặc nhân vật đã có.  
**Giao diện liên quan**  
Màn hình Tạo nhân vật.  
**Ghi chú**  
Các thuộc tính cụ thể của nhân vật sẽ được đồng bộ với Use Case Quản lý nhân vật và thiết kế database.

| Mã Use Case | UC01.4 |
| :---- | :---- |
| Tên Use Case | Chọn nhân vật |
| Mục đích | Cho phép người chơi lựa chọn một nhân vật đã tồn tại để bắt đầu hoặc tiếp tục chơi.  |
| Mô tả | Hệ thống hiển thị danh sách nhân vật thuộc tài khoản. Người chơi chọn nhân vật và xác nhận để sử dụng nhân vật đó.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi lần người chơi bắt đầu một phiên với nhân vật  |

**Trigger**  
Người chơi chọn chức năng Chọn nhân vật.  
**Tiền điều kiện**

* Người chơi đã đăng nhập.  
* Tài khoản có ít nhất một nhân vật hoặc hệ thống cho phép chuyển sang Tạo nhân vật.

**Hậu điều kiện**

* Nhân vật được chọn trở thành nhân vật đang hoạt động.  
* Người chơi có thể bắt đầu hoặc tiếp tục phiên chơi với nhân vật đó.

**Luồng chính**

1. Người chơi mở chức năng Chọn nhân vật.  
2. Hệ thống tải danh sách nhân vật.  
3. Hệ thống hiển thị thông tin cơ bản của từng nhân vật.  
4. Người chơi chọn một nhân vật.  
5. Hệ thống hiển thị hoặc xác nhận thông tin nhân vật được chọn.  
6. Người chơi xác nhận.  
7. Hệ thống thiết lập nhân vật được chọn làm nhân vật đang hoạt động.  
8. Hệ thống chuyển sang bước tiếp theo của phiên chơi.

**Luồng thay thế**  
**A1. Chưa có nhân vật**

* Hệ thống thông báo chưa có nhân vật.  
* Người chơi được chuyển sang Tạo nhân vật nếu chức năng được hỗ trợ.

**A2. Người chơi hủy lựa chọn**

* Hệ thống giữ nguyên nhân vật hiện tại hoặc quay về màn hình trước.

**Luồng ngoại lệ**  
Không thể tải dữ liệu nhân vật: hiển thị thông báo và không cho phép bắt đầu phiên chơi với dữ liệu chưa xác định.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ hiển thị các nhân vật thuộc tài khoản hiện tại.  
* BR02: Chỉ một nhân vật được xác định là nhân vật đang hoạt động tại một thời điểm.  
* BR03: Không được bắt đầu phiên chơi nếu dữ liệu nhân vật không thể tải.

**Include**  
UC01.5 Lưu game theo các thao tác lưu dữ liệu liên quan.  
**Extend**  
UC01.3 Tạo nhân vật.  
**Yêu cầu phi chức năng**  
Danh sách nhân vật cần được tải và hiển thị ổn định; không được hiển thị dữ liệu của tài khoản khác.  
**Giao diện liên quan**  
Màn hình Chọn nhân vật.  
**Ghi chú**  
Quan hệ Extend với Tạo nhân vật được giữ theo sơ đồ hiện tại của nhóm.

| Mã Use Case | UC01.5 |
| :---- | :---- |
| Tên Use Case | Lưu game |
| Mục đích | Lưu lại trạng thái phiên chơi để người chơi có thể tiếp tục game ở lần sau.  |
| Mô tả | Hệ thống ghi nhận các dữ liệu cần thiết của phiên chơi và lưu vào cơ chế Save của game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo thao tác của người chơi hoặc theo cơ chế Auto Save nếu được triển khai  |

**Trigger**  
Người chơi chọn Lưu game hoặc hệ thống kích hoạt cơ chế lưu theo thiết kế.  
**Tiền điều kiện**

* Đã có dữ liệu phiên chơi hợp lệ.  
* Có nhân vật đang hoạt động.

**Hậu điều kiện**

* Dữ liệu phiên chơi được lưu thành công.  
* Người chơi có thể sử dụng dữ liệu này cho Tiếp tục game.

**Luồng chính**

1. Người chơi kích hoạt chức năng Lưu game hoặc hệ thống kích hoạt lưu.  
2. Hệ thống thu thập trạng thái cần lưu của phiên chơi.  
3. Hệ thống kiểm tra dữ liệu trước khi ghi.  
4. Hệ thống ghi dữ liệu vào Save.  
5. Hệ thống xác nhận lưu thành công.

**Luồng thay thế**  
**A1. Người chơi hủy thao tác lưu**  
Hệ thống không thay đổi dữ liệu Save hiện tại.  
**A2. Dữ liệu chưa thay đổi**  
Hệ thống có thể bỏ qua thao tác ghi mới và thông báo dữ liệu đã được lưu.  
**Luồng ngoại lệ**  
Không thể ghi Save: hệ thống thông báo lỗi và giữ nguyên dữ liệu Save gần nhất có thể khôi phục.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ lưu dữ liệu của nhân vật đang hoạt động.  
* BR02: Dữ liệu Save phải có cấu trúc nhất quán để có thể đọc lại.  
* BR03: Không được ghi dữ liệu không hợp lệ vào Save.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Việc lưu game không được làm treo hoặc đóng game bất thường.  
**Giao diện liên quan**  
Menu tạm dừng/Menu game có chức năng Lưu game.  
**Ghi chú**  
Danh sách trường dữ liệu cần lưu sẽ được chốt khi xây dựng Class Diagram và thiết kế dữ liệu.

| Mã Use Case | UC01.6 |
| :---- | :---- |
| Tên Use Case | Tiếp tục game  |
| Mục đích | Cho phép người chơi khôi phục phiên chơi từ dữ liệu Save đã có.  |
| Mô tả | Hệ thống đọc dữ liệu Save, kiểm tra tính hợp lệ và khôi phục trạng thái game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi muốn tiếp tục phiên chơi trước đó  |

**Trigger**  
Người chơi chọn Tiếp tục game.  
**Tiền điều kiện**

* Đã tồn tại dữ liệu Save.  
* Dữ liệu Save có thể được truy cập.

**Hậu điều kiện**

* Trạng thái game được khôi phục.  
* Người chơi tiếp tục chơi với dữ liệu đã lưu.

**Luồng chính**

1. Người chơi chọn Tiếp tục game.  
2. Hệ thống xác định Save tương ứng.  
3. Hệ thống đọc dữ liệu Save.  
4. Hệ thống kiểm tra tính hợp lệ và khả năng tương thích của dữ liệu.  
5. Hệ thống khôi phục nhân vật và các trạng thái cần thiết.  
6. Hệ thống tải môi trường game tương ứng.  
7. Hệ thống đưa người chơi vào phiên chơi.  
8. Hệ thống có thể thực hiện Lưu game theo cơ chế của hệ thống.

**Luồng thay thế**  
**A1. Không có Save**

* Hệ thống thông báo chưa có dữ liệu lưu.  
* Người chơi được chuyển sang tạo/chọn nhân vật hoặc bắt đầu game mới.

**A2. Save không hợp lệ**

* Hệ thống thông báo Save bị lỗi hoặc không tương thích.  
* Người chơi được yêu cầu chọn Save khác hoặc bắt đầu game mới nếu được hỗ trợ.

**Luồng ngoại lệ**  
Không thể đọc hoặc khôi phục Save: không cho phép vào phiên chơi bằng dữ liệu lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ khôi phục dữ liệu Save hợp lệ.  
* BR02: Dữ liệu khôi phục phải thuộc đúng tài khoản/nhân vật hiện tại.  
* BR03: Không ghi đè Save hợp lệ bằng dữ liệu lỗi trong quá trình khôi phục.

**Include**  
UC01.5 Lưu game theo sơ đồ hiện tại.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Thời gian tải Save phải ở mức chấp nhận được để không làm gián đoạn trải nghiệm.  
**Giao diện liên quan**  
Menu chính với chức năng Tiếp tục game; màn hình tải game nếu có.  
**Ghi chú**  
Cần thống nhất sau này liệu Continue là thao tác độc lập hay được gọi sau Chọn nhân vật.

| Mã Use Case | UC01.7 |
| :---- | :---- |
| Tên Use Case | Thoát game  |
| Mục đích | Cho phép người chơi kết thúc phiên chơi và đóng trò chơi an toàn.  |
| Mô tả | Người chơi lựa chọn thoát game. Hệ thống xác nhận yêu cầu, xử lý lưu dữ liệu nếu cần và đóng chương trình.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi lần người chơi kết thúc phiên chơi  |

**Trigger**  
Người chơi chọn chức năng Thoát game.  
**Tiền điều kiện**

* Game đang hoạt động hoặc đang ở giao diện mà chức năng Thoát game được cung cấp.

**Hậu điều kiện**

* Nếu xác nhận thoát: game được đóng và tài nguyên được giải phóng.  
* Nếu hủy: người chơi tiếp tục ở giao diện hiện tại.

**Luồng chính**

1. Người chơi chọn Thoát game.  
2. Hệ thống kiểm tra trạng thái dữ liệu phiên chơi.  
3. Hệ thống hiển thị yêu cầu xác nhận nếu cần.  
4. Người chơi xác nhận thoát.  
5. Hệ thống thực hiện lưu dữ liệu theo cơ chế đã thiết kế nếu cần.  
6. Hệ thống giải phóng tài nguyên.  
7. Hệ thống đóng chương trình.

**Luồng thay thế**  
**A1. Người chơi hủy thoát**

* Hệ thống đóng hộp thoại xác nhận.  
* Người chơi tiếp tục phiên chơi.

**A2. Cần lưu dữ liệu trước khi thoát**

* Hệ thống yêu cầu hoặc tự động thực hiện Lưu game theo thiết kế.  
* Sau khi xử lý lưu, hệ thống tiếp tục đóng game.

**Luồng ngoại lệ**  
Không thể lưu dữ liệu trước khi thoát: hệ thống thông báo lỗi và cho phép người chơi lựa chọn tiếp tục chơi hoặc thoát theo chính sách của game.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không được đóng game đột ngột khi đang thực hiện thao tác ghi dữ liệu quan trọng.  
* BR02: Nếu có dữ liệu chưa lưu và chính sách yêu cầu xác nhận, phải thông báo cho người chơi trước khi thoát.  
* BR03: Sau khi thoát, tài nguyên game phải được giải phóng phù hợp.

**Include**  
UC01.5 Lưu game khi cần theo sơ đồ hiện tại.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Game phải đóng ổn định và không làm hỏng dữ liệu Save.  
**Giao diện liên quan**  
Menu chính/Menu tạm dừng và hộp thoại xác nhận thoát.  
**Ghi chú**  
Chính sách Auto Save/Save trước khi thoát cần được nhóm thống nhất ở giai đoạn thiết kế.  
**Cấu trúc module UC02**

| Mã | Tên | Vai trò trong module |
| :---- | :---- | :---- |
| UC02  | Cài đặt  | Use Case tổng quát  |
| UC02.1 | Đồ họa  | Chức năng con  |
| UC02.2 | Âm thanh  | Chức năng con  |
| UC02.3 | Ngôn ngữ  | Chức năng con  |
| UC02.4 | Điều khiển  | Chức năng con  |
| UC02.5 | Thoát  | Chức năng con / Thoát giao diện |

**Ghi chú chuẩn hóa**

* UC02 là Use Case cấp module; các mục UC02.1–UC02.5 là các chức năng con được thể hiện trong file Cai\_dat.drawio.  
* Sơ đồ hiện tại không có Actor và không có đường liên kết giữa các ellipse, vì vậy không tự thêm Actor/Include/Extend vào sơ đồ.  
* UC02.5 “Thoát” được đặc tả là thoát khỏi giao diện Cài đặt. Chức năng “Thoát game” của module Khởi động game vẫn là UC01.7.  
* Các thông số cụ thể chưa có trong sơ đồ (ví dụ danh sách độ phân giải, số mức âm lượng, số ngôn ngữ, phím mặc định) chưa được cố định trong tài liệu.  
* Khi nhóm hoàn thiện các quan hệ UML trong sơ đồ, phần Include/Extend của tài liệu có thể được cập nhật mà không cần viết lại toàn bộ luồng.

**Đặc tả UC02**

| Mã Use Case | UC02 |
| :---- | :---- |
| Tên Use Case | Cài đặt |
| Mục đích | Cho phép người chơi điều chỉnh các thiết lập của trò chơi phù hợp với nhu cầu sử dụng.  |
| Mô tả | Người chơi truy cập giao diện Cài đặt và lựa chọn một trong các nhóm thiết lập gồm Đồ họa, Âm thanh, Ngôn ngữ, Điều khiển hoặc Thoát khỏi giao diện Cài đặt.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi khi người chơi cần thay đổi thiết lập  |

**Trigger**  
Người chơi chọn chức năng Cài đặt từ Menu chính hoặc giao diện mà game cung cấp.  
**Tiền điều kiện**

* Game đã được khởi động thành công.  
* Người chơi đang ở trạng thái có quyền truy cập giao diện Cài đặt.

**Hậu điều kiện**

* Các thiết lập hợp lệ được áp dụng theo lựa chọn của người chơi.  
* Nếu người chơi chọn Thoát, hệ thống rời giao diện Cài đặt và quay về giao diện trước đó.

**Luồng chính**

1. Người chơi chọn Cài đặt.  
2. Hệ thống hiển thị giao diện Cài đặt.  
3. Hệ thống hiển thị các lựa chọn: Đồ họa, Âm thanh, Ngôn ngữ, Điều khiển và Thoát.  
4. Người chơi chọn một chức năng cần thay đổi.  
5. Hệ thống mở giao diện thiết lập tương ứng.  
6. Người chơi thay đổi thiết lập và xác nhận nếu chức năng yêu cầu xác nhận.  
7. Hệ thống kiểm tra và áp dụng thiết lập hợp lệ.  
8. Người chơi có thể tiếp tục điều chỉnh thiết lập khác hoặc chọn Thoát.

**Luồng thay thế**  
**A1. Thiết lập không hợp lệ**

* Hệ thống phát hiện giá trị không hợp lệ hoặc không được hỗ trợ.  
* Hệ thống thông báo lỗi.  
* Hệ thống giữ giá trị trước đó hoặc yêu cầu người chơi chọn lại.

**A2. Người chơi không thay đổi thiết lập**

* Hệ thống giữ nguyên cấu hình hiện tại.  
* Người chơi có thể chọn chức năng khác hoặc Thoát.

**A3. Người chơi chọn Thoát**

* Hệ thống đóng giao diện Cài đặt.  
* Hệ thống quay về giao diện trước đó.

**Luồng ngoại lệ**  
Lỗi khi đọc hoặc ghi cấu hình: hệ thống thông báo lỗi, giữ cấu hình gần nhất có thể sử dụng và không áp dụng dữ liệu lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ áp dụng các giá trị thiết lập mà game hỗ trợ.  
* BR02: Thiết lập hợp lệ phải được áp dụng nhất quán trong phiên chơi.  
* BR03: Khi có yêu cầu lưu cấu hình, hệ thống chỉ lưu dữ liệu sau khi kiểm tra hợp lệ.  
* BR04: Chức năng Thoát chỉ rời giao diện Cài đặt, không đồng nghĩa với Thoát game.

**Include**  
Không xác định trong sơ đồ hiện tại.  
**Extend**  
Không xác định trong sơ đồ hiện tại.  
**Yêu cầu phi chức năng**  
Giao diện Cài đặt phải phản hồi ổn định và không làm gián đoạn phiên chơi.  
**Giao diện liên quan**  
Giao diện Cài đặt.  
**Ghi Chú**  
Sơ đồ hiện tại không vẽ Actor và không thể hiện quan hệ include/extend giữa UC02 và các chức năng con. Vì vậy tài liệu giữ các chức năng dưới dạng chức năng con của module.

| Mã Use Case | UC02.1 |
| :---- | :---- |
| Tên Use Case | Đồ họa  |
| Mục đích | Cho phép người chơi điều chỉnh các thiết lập hiển thị của game.  |
| Mô tả | Người chơi truy cập mục Đồ họa và thay đổi các tùy chọn hiển thị mà game hỗ trợ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi cần điều chỉnh hiển thị  |

**Trigger**  
Người chơi chọn Đồ họa trong giao diện Cài đặt.  
**Tiền điều kiện**

* Đang ở giao diện Cài đặt.  
* Thiết bị hỗ trợ các tùy chọn đồ họa được game cung cấp.

**Hậu điều kiện**

* Thiết lập đồ họa hợp lệ được áp dụng.  
* Nếu có cơ chế lưu cấu hình, giá trị mới được lưu theo thiết kế.

**Luồng chính**

1. Người chơi chọn Đồ họa.  
2. Hệ thống hiển thị các tùy chọn đồ họa.  
3. Người chơi thay đổi tùy chọn.  
4. Hệ thống kiểm tra giá trị.  
5. Người chơi xác nhận nếu cần.  
6. Hệ thống áp dụng thiết lập đồ họa.  
7. Hệ thống thông báo kết quả hoặc hiển thị thiết lập hiện tại.

**Luồng thay thế**  
**A1. Giá trị không được hỗ trợ**

* Hệ thống thông báo giá trị không hợp lệ.  
* Giữ giá trị cũ hoặc yêu cầu chọn lại.

**A2. Người chơi hủy thay đổi**

* Hệ thống không áp dụng thay đổi chưa xác nhận.  
* Quay về thiết lập trước đó.

**Luồng ngoại lệ**  
Không thể áp dụng thiết lập đồ họa: hệ thống giữ cấu hình an toàn trước đó và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không cho phép chọn cấu hình mà thiết bị/game không hỗ trợ.  
* BR02: Thiết lập mới chỉ được áp dụng sau khi hợp lệ.

**Include**  
Không xác định trong sơ đồ.  
**Extend**  
Không xác định trong sơ đồ.  
**Yêu cầu phi chức năng**  
Thay đổi thiết lập không được làm game mất ổn định.  
**Giao diện liên quan**  
Giao diện Đồ họa.  
**Ghi Chú**  
Các tùy chọn cụ thể như độ phân giải, chất lượng hình ảnh, toàn màn hình... chỉ bổ sung khi nhóm chốt thiết kế.

| Mã Use Case | UC02.2 |
| :---- | :---- |
| Tên Use Case | Âm thanh |
| Mục đích | Cho phép người chơi điều chỉnh các thiết lập âm thanh của game.  |
| Mô tả | Người chơi thay đổi các tùy chọn âm thanh mà game cung cấp.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi cần điều chỉnh âm thanh  |

**Trigger**  
Người chơi chọn Âm thanh trong giao diện Cài đặt.  
**Tiền điều kiện**  
Đang ở giao diện Cài đặt.  
**Hậu điều kiện**  
Thiết lập âm thanh hợp lệ được áp dụng cho game.  
**Luồng chính**

1. Người chơi chọn Âm thanh.  
2. Hệ thống hiển thị các tùy chọn âm thanh.  
3. Người chơi thay đổi thiết lập.  
4. Hệ thống kiểm tra giá trị.  
5. Hệ thống áp dụng thiết lập.  
6. Hệ thống cập nhật trạng thái âm thanh trong game.

**Luồng thay thế**  
**A1. Giá trị âm lượng không hợp lệ**

* Hệ thống từ chối giá trị.  
* Yêu cầu người chơi chọn lại giá trị được hỗ trợ.

**A2. Người chơi hủy thay đổi**

* Hệ thống giữ thiết lập âm thanh trước đó.

**Luồng ngoại lệ**  
Không thể áp dụng cấu hình âm thanh: giữ cấu hình trước đó và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Giá trị âm lượng phải nằm trong phạm vi mà hệ thống hỗ trợ.  
* BR02: Thiết lập âm thanh không được ảnh hưởng đến các dữ liệu game khác.

**Include**  
Không xác định trong sơ đồ.  
**Extend**  
Không xác định trong sơ đồ.  
**Yêu cầu phi chức năng**  
Thay đổi âm thanh phải được áp dụng ổn định, không làm dừng game.  
**Giao diện liên quan**  
Giao diện Âm thanh.  
**Ghi Chú**  
Có thể bổ sung các nhóm như âm lượng tổng, nhạc nền, hiệu ứng... khi nhóm chốt thiết kế.

| Mã Use Case | UC02.3 |
| :---- | :---- |
| Tên Use Case | Ngôn ngữ |
| Mục đích | Cho phép người chơi lựa chọn ngôn ngữ hiển thị được game hỗ trợ.  |
| Mô tả | Người chơi chọn một ngôn ngữ từ danh sách được hệ thống cung cấp. Hệ thống cập nhật ngôn ngữ hiển thị theo thiết kế.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi cần thay đổi ngôn ngữ  |

**Trigger**  
Người chơi chọn Ngôn ngữ trong giao diện Cài đặt.  
**Tiền điều kiện**

* Đang ở giao diện Cài đặt.  
* Game có danh sách ngôn ngữ được hỗ trợ.

**Hậu điều kiện**

* Ngôn ngữ được chọn được áp dụng hoặc được đánh dấu để áp dụng theo thiết kế.  
* Cấu hình ngôn ngữ được lưu nếu hệ thống hỗ trợ lưu.

**Luồng chính**

1. Người chơi chọn Ngôn ngữ.  
2. Hệ thống hiển thị danh sách ngôn ngữ được hỗ trợ.  
3. Người chơi chọn một ngôn ngữ.  
4. Hệ thống kiểm tra ngôn ngữ.  
5. Hệ thống áp dụng ngôn ngữ hoặc yêu cầu khởi động lại nếu cần.  
6. Hệ thống cập nhật giao diện theo ngôn ngữ đã chọn.

**Luồng thay thế**  
**A1. Ngôn ngữ không được hỗ trợ**

* Hệ thống thông báo ngôn ngữ không khả dụng.  
* Giữ ngôn ngữ hiện tại.

**A2. Người chơi hủy lựa chọn**

* Hệ thống giữ nguyên ngôn ngữ hiện tại.

**Luồng ngoại lệ**  
Không tải được dữ liệu ngôn ngữ: hệ thống giữ ngôn ngữ hiện tại và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ cho phép lựa chọn ngôn ngữ có trong danh sách hỗ trợ.  
* BR02: Không làm mất nội dung game khi chuyển đổi ngôn ngữ.

**Include**  
Không xác định trong sơ đồ.  
**Extend**  
Không xác định trong sơ đồ.  
**Yêu cầu phi chức năng**  
Việc thay đổi ngôn ngữ phải không làm lỗi bố cục giao diện.  
**Giao diện liên quan**  
Giao diện Ngôn ngữ.  
**Ghi Chú**  
Ngôn ngữ cụ thể chưa được xác định trong sơ đồ; không mặc định số lượng ngôn ngữ trong đặc tả.

| Mã Use Case | UC02.4 |
| :---- | :---- |
| Tên Use Case | Điều khiển |
| Mục đích | Cho phép người chơi thiết lập hoặc xem các phương thức điều khiển của game.  |
| Mô tả | Người chơi truy cập mục Điều khiển để xem hoặc thay đổi các thiết lập điều khiển mà game cung cấp.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Khi người chơi cần điều chỉnh cách điều khiển  |

**Trigger**  
Người chơi chọn Điều khiển trong giao diện Cài đặt.  
**Tiền điều kiện**

* Đang ở giao diện Cài đặt.  
* Game có danh sách thao tác điều khiển được hỗ trợ.

**Hậu điều kiện**

* Thiết lập điều khiển hợp lệ được áp dụng.  
* Các thao tác của người chơi sử dụng cấu hình mới theo thiết kế.

**Luồng chính**

1. Người chơi chọn Điều khiển.  
2. Hệ thống hiển thị các thao tác và phím/nút tương ứng.  
3. Người chơi thay đổi thiết lập nếu hệ thống cho phép.  
4. Hệ thống kiểm tra xung đột hoặc giá trị không hợp lệ.  
5. Người chơi xác nhận thay đổi.  
6. Hệ thống áp dụng cấu hình điều khiển.

**Luồng thay thế**  
**A1. Phím/nút bị trùng**

* Hệ thống thông báo xung đột.  
* Người chơi chọn phím/nút khác hoặc giữ cấu hình cũ.

**A2. Người chơi hủy thay đổi**

* Hệ thống không áp dụng thay đổi chưa xác nhận.

**Luồng ngoại lệ**  
Không thể lưu hoặc áp dụng cấu hình điều khiển: giữ cấu hình trước đó và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không cho phép cấu hình gây xung đột nếu hệ thống không hỗ trợ nhiều thao tác cùng một phím/nút.  
* BR02: Cấu hình mới chỉ có hiệu lực sau khi hợp lệ.

**Include**  
Không xác định trong sơ đồ.  
**Extend**  
Không xác định trong sơ đồ.  
**Yêu cầu phi chức năng**  
Thiết lập điều khiển phải được phản hồi ổn định và không gây mất thao tác trong game.  
**Giao diện liên quan**  
Giao diện Điều khiển.  
**Ghi Chú**  
Danh sách phím/nút cụ thể cần được xác định khi thiết kế gameplay và input mapping.

| Mã Use Case | UC02.5 |
| :---- | :---- |
| Tên Use Case | Thoát |
| Mục đích | Cho phép người chơi rời khỏi giao diện Cài đặt và quay về giao diện trước đó.  |
| Mô tả | Đây là chức năng Thoát được thể hiện bên trong sơ đồ Cài đặt. Chức năng này được hiểu là thoát khỏi màn hình Cài đặt, không phải thoát toàn bộ game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi lần người chơi muốn rời giao diện Cài đặt  |

**Trigger**  
Người chơi chọn Thoát trong giao diện Cài đặt.  
**Tiền điều kiện**  
Đang ở giao diện Cài đặt.  
**Hậu điều kiện**

* Giao diện Cài đặt được đóng.  
* Người chơi quay về giao diện trước đó.

**Luồng chính**

1. Người chơi chọn Thoát.  
2. Hệ thống kiểm tra có thay đổi thiết lập chưa được xử lý hay không.  
3. Nếu cần, hệ thống yêu cầu xác nhận hoặc xử lý lưu theo thiết kế.  
4. Hệ thống đóng giao diện Cài đặt.  
5. Hệ thống hiển thị lại giao diện trước đó.

**Luồng thay thế**  
**A1. Có thay đổi chưa lưu**

* Hệ thống hỏi người chơi có muốn lưu thay đổi hay không.  
* Người chơi chọn lưu, không lưu hoặc hủy thao tác thoát theo thiết kế.

**A2. Người chơi hủy thoát**

* Hệ thống đóng hộp thoại xác nhận.  
* Người chơi tiếp tục ở giao diện Cài đặt.

**Luồng ngoại lệ**  
Không thể chuyển giao diện: hệ thống giữ người chơi ở Cài đặt và thông báo lỗi nếu cần.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Thoát khỏi Cài đặt không đồng nghĩa với đóng game.  
* BR02: Không được làm mất thay đổi đã được xác nhận/lưu.

**Include**  
Không xác định trong sơ đồ.  
**Extend**  
Không xác định trong sơ đồ.  
**Yêu cầu phi chức năng**  
Chuyển giao diện phải ổn định và không làm mất trạng thái game.  
**Giao diện liên quan**  
Giao diện Cài đặt và giao diện trước đó.  
**Ghi Chú**  
Cần phân biệt rõ UC02.5 Thoát với chức năng UC01.7 Thoát game.

| Mã Use Case | UC03 |
| :---- | :---- |
| Tên Use Case | Quản lý nghề |
| Mục đích | Cho phép người chơi truy cập chức năng Nghề để tùy chỉnh, lựa chọn nghề phù hợp với nhân vật.  |
| Mô tả | Người chơi truy cập chức năng Nghề để xem danh sách nghề, kiểm tra trạng thái mở khóa và các điều kiện liên quan, lựa chọn hoặc nâng cấp nghề. Sau khi thao tác thành công, thông tin nghề của nhân vật được hệ thống cập nhật.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Nghề  
**Tiền điều kiện**

* Game đã khởi động   
* Trạng thái nhân vật hợp lệ  
* Dữ liệu nghề có thể được tải  
* Người chơi được phép truy cập chức năng nghề

**Hậu điều kiện**  
**Nếu thành công:**

* Danh sách nghề được hiển thị.  
* Trạng thái của từng nghề được cập nhật.  
* Các chức năng nghề phù hợp được hiển thị.  
* Nghề của nhân vật được cập nhật nếu người chơi thực hiện thay đổi.

**Nếu thất bại:**

* Thông tin nghề không được thay đổi.  
* Hệ thống hiển thị thông báo tương ứng.

**Luồng chính**

1. Người chơi mở chức năng Nghề \- tiếp nhận yêu cầu truy cập chức năng Nghề  
2. Tải dữ liệu nghề và trạng thái nghề của nhân vật.   
3. Kiểm tra dữ liệu nghề và điều kiện truy cập.  
4. Hiển thị danh sách nghề cùng trạng thái tương ứng như đã mở khóa, chưa mở khóa hoặc đang sử dụng.   
5. Chọn một nghề hoặc chức năng nghề muốn thực hiện \- Hiển thị thông tin chi tiết và các chức năng có thể thực hiện đối với nghề được chọn.   
6. Thực hiện lựa chọn chức năng và xác nhận nếu cần \- Kiểm tra điều kiện thực hiện chức năng.   
7. Cập nhật dữ liệu nghề của nhân vật nếu đáp ứng đầy đủ điều kiện.   
8. Thông báo kết quả và cập nhật lại giao diện Nghề. 

**Luồng thay thế**  
**A1 – Nghề chưa được mở khóa**

* Người chơi chọn một nghề chưa được mở khóa.  
* Hệ thống kiểm tra trạng thái nghề.  
* Hệ thống hiển thị nghề đang bị khóa.  
* Hệ thống hiển thị điều kiện cần thiết để mở khóa nếu có.  
* Người chơi không thể lựa chọn nghề này để sử dụng.  
* Dữ liệu nghề hiện tại không thay đổi.

**A2 – Chưa đáp ứng điều kiện của nghề** 

* Người chơi chọn nghề yêu cầu điều kiện đặc biệt.  
* Hệ thống kiểm tra điều kiện của nhân vật.  
* Hệ thống xác định người chơi chưa đáp ứng điều kiện.  
* Hệ thống thông báo điều kiện chưa đạt.  
* Không cập nhật nghề đang sử dụng.

**A3 \- Nâng cấp nghề**

* Người chơi chọn chức năng Nâng cấp nghề.  
* Hệ thống kiểm tra điều kiện nâng cấp.  
* Hệ thống kiểm tra các tài nguyên cần thiết.  
* Nếu đủ điều kiện, hệ thống hiển thị yêu cầu xác nhận.  
* Người chơi xác nhận nâng cấp.  
* Hệ thống cập nhật cấp độ nghề và trừ tài nguyên tương ứng.  
* Hệ thống thông báo nâng cấp thành công.  
* Giao diện nghề được cập nhật.

**A4 \- Không đủ tài nguyên để nâng cấp**

* Người chơi chọn chức năng nâng cấp.  
* Hệ thống kiểm tra tài nguyên.  
* Người chơi không đủ tài nguyên yêu cầu.  
* Hệ thống thông báo không đủ tài nguyên.  
* Không thực hiện nâng cấp.  
* Dữ liệu nhân vật và nghề không thay đổi.

**A5 \- Người chơi hủy thao tác**

* Hệ thống hiển thị yêu cầu xác nhận.  
* Người chơi chọn Hủy.  
* Hệ thống đóng hộp thoại xác nhận.  
* Giữ nguyên trạng thái nghề hiện tại.

**A6 \- Chuyển sang nghề khác**

* Người chơi chọn một nghề đã được mở khóa.  
* Hệ thống kiểm tra điều kiện lựa chọn.  
* Hệ thống hiển thị yêu cầu xác nhận thay đổi nghề.  
* Người chơi xác nhận.  
* Hệ thống cập nhật nghề đang sử dụng.  
* Hệ thống cập nhật các thông tin liên quan đến nhân vật.  
* Hệ thống thông báo kết quả.

**Luồng ngoại lệ**  
**E1 \- Không tải được dữ liệu nghề**

* Hệ thống không thể tải dữ liệu nghề.  
* Hệ thống thông báo lỗi.  
* Không hiển thị dữ liệu nghề không đầy đủ hoặc không hợp lệ.  
* Người chơi không thể thực hiện thay đổi nghề.

**E2 \- Dữ liệu nghề không hợp lệ**

* Hệ thống phát hiện dữ liệu nghề không hợp lệ.  
* Hệ thống thông báo lỗi.  
* Không thực hiện cập nhật nghề.  
* Giữ nguyên trạng thái nghề trước đó.

**E3 \- Lỗi khi cập nhật nghề**

* Người chơi đã xác nhận thay đổi.  
* Hệ thống xảy ra lỗi trong quá trình cập nhật.  
* Hệ thống hủy thao tác cập nhật.  
* Dữ liệu nghề và nhân vật được giữ ở trạng thái hợp lệ trước đó.  
* Hệ thống thông báo thao tác không thành công.

**Business Rule / Quy tắc nghiệp vụ** 

* **BR01:** Người chơi chỉ được lựa chọn những nghề đã được mở khóa.  
* **BR02:** Mỗi nghề phải có các điều kiện mở khóa hoặc sử dụng tương ứng nếu gameplay quy định.  
* **BR03:** Người chơi phải đáp ứng đầy đủ điều kiện trước khi lựa chọn hoặc nâng cấp nghề.  
* **BR04:** Không được nâng cấp nghề nếu người chơi không đủ tài nguyên yêu cầu.  
* **BR05:** Tài nguyên chỉ được trừ sau khi thao tác nâng cấp thành công.  
* **BR06:** Khi thay đổi nghề thành công, thông tin nghề của nhân vật phải được cập nhật đồng bộ.  
* **BR07:** Không được phép tạo ra trạng thái nghề không hợp lệ do thao tác thất bại.  
* **BR08:** Mỗi thời điểm nhân vật chỉ được sử dụng nghề theo quy tắc gameplay đã thiết kế.  
* **BR09:** Việc thay đổi nghề không được làm mất dữ liệu hoặc cấp độ của các nghề đã mở khóa, trừ khi gameplay có quy định riêng.  
* **BR10:** Mọi thay đổi liên quan đến nghề phải được lưu lại để đảm bảo trạng thái nhân vật được duy trì.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thông tin nghề phải được hiển thị chính xác theo trạng thái hiện tại của nhân vật.  
* Thao tác lựa chọn hoặc nâng cấp nghề phải có phản hồi rõ ràng.  
* Hệ thống không được làm mất dữ liệu nghề khi xảy ra lỗi.  
* Thời gian tải danh sách nghề phải đảm bảo trải nghiệm người chơi.  
* Dữ liệu nghề phải được lưu nhất quán sau khi thay đổi thành công.

**Giao diện liên quan**  
**Có thể bao gồm:**

* Danh sách nghề  
* Trạng thái mở khóa.  
* Nghề hiện tại.  
* Thông tin nghề.  
* Cấp độ nghề.  
* Điều kiện mở khóa.  
* Điều kiện nâng cấp.  
* Chi phí nâng cấp.  
* Nút Chọn/Sử dụng.  
* Nút Nâng cấp.  
* Thông báo xác nhận.  
* Thông báo kết quả.

**Ghi chú**

* UC03 là **Use Case tổng quan** cho hệ thống quản lý nghề của nhân vật.  
* Các thao tác cụ thể như xem nghề, mở khóa, nâng cấp và lựa chọn nghề nên được tách thành các Use Case con nếu sơ đồ UC của dự án yêu cầu mô tả chi tiết.  
* Điều kiện mở khóa, cấp độ nghề, chi phí nâng cấp và ảnh hưởng của nghề đến nhân vật cần được xác định trong tài liệu **đặc tả gameplay/quy tắc hệ thống** nếu chưa được chốt ở thời điểm viết Use Case. 

| Mã Use Case | UC03.1 |
| :---- | :---- |
| Tên Use Case | Chọn nghề |
| Mục đích | Cho phép người chơi lựa chọn một nghề cho nhân vật khi nghề đó đã được mở khóa và đáp ứng các điều kiện của game.  |
| Mô tả | Người chơi truy cập chức năng Chọn nghề, xem danh sách nghề, kiểm tra trạng thái mở khóa/điều kiện và xác nhận nghề muốn sử dụng. Nếu thao tác thành công, nghề của nhân vật được cập nhật.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Chọn nghề.  
**Tiền điều kiện**

* Game đã khởi động và trạng thái nhân vật hợp lệ.  
* Dữ liệu nghề có thể được tải.  
* Người chơi được phép truy cập chức năng nghề.  
* Nghề đã được mở khóa

**Hậu điều kiện**

* Nghề được chọn trở thành nghề hiện tại của nhân vật.  
* Nếu người chơi hủy hoặc thao tác thất bại, nghề hiện tại không thay đổi.

**Luồng chính**

1. Người chơi mở chức năng Chọn nghề.  
2. Hệ thống tải và hiển thị danh sách nghề.  
3. Người chơi chọn một nghề.  
4. Hệ thống hiển thị trạng thái và các điều kiện của nghề.  
5. Hệ thống kiểm tra nghề có đủ điều kiện lựa chọn hay không.  
6. Người chơi xác nhận lựa chọn.  
7. Hệ thống cập nhật nghề cho nhân vật.  
8. Hệ thống thông báo kết quả và cập nhật giao diện.

**Luồng thay thế**  
**A1 – Nghề chưa mở khóa**

* Hệ thống hiển thị trạng thái khóa và điều kiện cần đạt.  
* Không cho phép xác nhận nghề.

**A2 – Người chơi hủy**

* Hệ thống đóng thao tác lựa chọn.  
* Giữ nguyên nghề hiện tại.

**A3 – Chọn nghề đang sử dụng**

* Hệ thống thông báo đây là nghề hiện tại hoặc không thực hiện cập nhật.

**Luồng ngoại lệ**  
Không thể tải dữ liệu nghề hoặc lỗi cập nhật: hệ thống thông báo lỗi và giữ nguyên trạng thái nghề hiện tại.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ cho phép chọn nghề đã đáp ứng điều kiện.  
* BR02: Chỉ cập nhật nghề sau khi người chơi xác nhận.  
* BR03: Thao tác thất bại không được làm mất nghề hiện tại.  
* BR04: Trạng thái nghề phải được lưu nhất quán với dữ liệu nhân vật.

**Include**  
Chọn nghề sẽ include với Xem thông tin nghề  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Phản hồi thao tác rõ ràng; trạng thái nghề phải dễ phân biệt.  
**Giao diện liên quan**  
Màn hình Chọn nghề; danh sách nghề; khu vực thông tin nghề.  
**Ghi Chú**  
Không.

| Mã Use Case | UC03.2 |
| :---- | :---- |
| Tên Use Case | Xem thông tin nghề |
| Mục đích | Cho phép người chơi xem thông tin chi tiết của một nghề trước khi quyết định lựa chọn, đổi hoặc thực hiện thao tác liên quan.  |
| Mô tả | Người chơi chọn một nghề và hệ thống hiển thị thông tin của nghề như mô tả, đặc điểm, yêu cầu, trạng thái mở khóa và thông tin phát triển theo thiết kế game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn một nghề và yêu cầu xem thông tin.  
**Tiền điều kiện**

* Danh sách nghề đã được tải.  
* Dữ liệu nghề tồn tại và có thể đọc.

**Hậu điều kiện**

* Thông tin nghề được hiển thị.  
* Thao tác xem thông tin không tự động thay đổi nghề hiện tại.

**Luồng chính**

1. Người chơi chọn nghề.  
2. Hệ thống xác định nghề.  
3. Hệ thống tải dữ liệu chi tiết.  
4. Hệ thống hiển thị thông tin.  
5. Người chơi đóng thông tin hoặc chuyển sang chức năng khác nếu đủ điều kiện.

**Luồng thay thế**  
**A1 – Nghề chưa mở khóa**

* Hiển thị thông tin được phép và điều kiện mở khóa.  
* Không cho thực hiện thao tác bị khóa.

**A2 – Không có dữ liệu**

* Thông báo không thể tải thông tin.  
* Quay lại danh sách nghề.

**Luồng ngoại lệ**  
Không đọc được dữ liệu nghề: thông báo lỗi và không thay đổi trạng thái nhân vật.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Xem thông tin không làm thay đổi nghề.  
* BR02: Điều kiện hiển thị phải phản ánh trạng thái hiện tại của nhân vật.  
* BR03: Các thao tác bị khóa phải được hiển thị rõ lý do.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Thông tin phải hiển thị nhanh, rõ ràng và không gây nhầm với thao tác thay đổi nghề.  
**Giao diện liên quan**  
Màn hình/Popup Thông tin nghề.  
**Ghi Chú**  
Không.

| Mã Use Case | UC03.3 |
| :---- | :---- |
| Tên Use Case | Đổi nghề |
| Mục đích | Cho phép người chơi thay đổi nghề hiện tại của nhân vật sang một nghề khác đủ điều kiện.  |
| Mô tả | Người chơi chọn Đổi nghề, chọn nghề mới, kiểm tra điều kiện và xác nhận. Hệ thống chỉ cập nhật khi tất cả điều kiện được đáp ứng.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Đổi nghề.  
**Tiền điều kiện**

* Nhân vật đã có nghề hiện tại.  
* Dữ liệu nghề và trạng thái nhân vật hợp lệ.  
* Có nghề khác có thể được xem xét.

**Hậu điều kiện**

* Nghề mới trở thành nghề hiện tại nếu đổi thành công.  
* Nếu hủy/thất bại, nghề cũ được giữ nguyên.

**Luồng chính**

1. Người chơi mở Đổi nghề.  
2. Hệ thống hiển thị nghề hiện tại và các nghề có thể đổi.  
3. Người chơi chọn nghề mới.  
4. Hệ thống kiểm tra trạng thái mở khóa và điều kiện.  
5. Hệ thống hiển thị thông tin cần thiết.  
6. Người chơi xác nhận.  
7. Hệ thống cập nhật nghề.  
8. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Không đủ điều kiện**

* Thông báo lý do.  
* Không đổi nghề.

**A2 – Hủy xác nhận**

* Không cập nhật nghề.  
* Quay lại màn hình trước.

**A3 – Nghề chưa mở khóa**

* Hiển thị điều kiện mở khóa.  
* Không cho đổi sang nghề đó.

**Luồng ngoại lệ**  
Lỗi cập nhật: giữ nguyên nghề cũ, không trừ tài nguyên nếu có chi phí, và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ đổi sang nghề đủ điều kiện/mở khóa.  
* BR02: Phải xác nhận trước khi cập nhật.  
* BR03: Đổi thất bại không được làm mất nghề cũ.  
* BR04: Nếu có chi phí đổi nghề, chỉ trừ sau khi kiểm tra và xác nhận thành công.

**Include**  
Không.  
**Extend**  
Đổi nghề \<\<extend\>\> Xem thông tin nghề.  
**Yêu cầu phi chức năng**  
Thao tác cập nhật phải đảm bảo toàn vẹn dữ liệu.  
**Giao diện liên quan**  
Màn hình Đổi nghề; danh sách nghề; thông tin nghề.  
**Ghi Chú**  
Không.

| Mã Use Case | UC03.4 |
| :---- | :---- |
| Tên Use Case | Nâng cấp nghề |
| Mục đích | Cho phép người chơi nâng cấp cấp độ hoặc tiến trình của nghề khi đáp ứng điều kiện.  |
| Mô tả | Người chơi yêu cầu nâng cấp. Hệ thống kiểm tra cấp hiện tại, tài nguyên, điều kiện và giới hạn nâng cấp, sau đó cập nhật trạng thái nghề nếu hợp lệ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Nâng cấp nghề.  
**Tiền điều kiện**

* Nhân vật có nghề.  
* Dữ liệu cấp độ nghề hợp lệ.  
* Người chơi có đủ điều kiện nâng cấp.

**Hậu điều kiện**

* Cấp độ/trạng thái nghề được cập nhật.  
* Tài nguyên được trừ nếu game có cơ chế chi phí và nâng cấp thành công.

**Luồng chính**

1. Người chơi mở Nâng cấp nghề.  
2. Hệ thống hiển thị cấp hiện tại và yêu cầu nâng cấp.  
3. Người chơi yêu cầu nâng cấp.  
4. Hệ thống kiểm tra điều kiện.  
5. Hệ thống yêu cầu xác nhận nếu cần.  
6. Người chơi xác nhận.  
7. Hệ thống cập nhật cấp độ/trạng thái.  
8. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Thiếu tài nguyên**

* Thông báo tài nguyên còn thiếu.  
* Không nâng cấp.

**A2 – Chưa đủ điều kiện**

* Thông báo điều kiện còn thiếu.  
* Giữ trạng thái hiện tại.

**A3 – Đạt cấp tối đa**

* Thông báo không thể nâng cấp thêm.

**Luồng ngoại lệ**  
Lỗi cập nhật: không trừ tài nguyên nếu nâng cấp thất bại và giữ nguyên trạng thái trước đó.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Kiểm tra điều kiện trước khi nâng cấp.  
* BR02: Không trừ tài nguyên khi giao dịch thất bại.  
* BR03: Không vượt cấp tối đa nếu game có giới hạn.  
* BR04: Cấp độ nghề phải đồng bộ với trạng thái nhân vật.

**Include**  
Không.  
**Extend**  
Nâng cấp nghề \<\<extend\>\> Mở nghề mới  
**Yêu cầu phi chức năng**  
Phản hồi kết quả rõ ràng; tránh thao tác nâng cấp lặp gây trừ tài nguyên nhiều lần.  
**Giao diện liên quan**  
Màn hình Nâng cấp nghề.  
**Ghi Chú**  
Không.

| Mã Use Case | UC03.5 |
| :---- | :---- |
| Tên Use Case | Mở nghề mới |
| Mục đích | Cho phép người chơi mở khóa một nghề chưa được mở khi đáp ứng điều kiện.  |
| Mô tả | Hệ thống kiểm tra điều kiện mở khóa và chuyển trạng thái nghề từ chưa mở khóa sang đã mở khóa. Sau đó nghề có thể trở thành lựa chọn hợp lệ theo luật game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi yêu cầu mở một nghề chưa mở khóa.  
**Tiền điều kiện**

* Nghề tồn tại trong dữ liệu.  
* Nghề đang ở trạng thái chưa mở khóa.  
* Hệ thống đọc được điều kiện mở khóa.

**Hậu điều kiện**

* Nghề chuyển sang trạng thái đã mở khóa.  
* Trạng thái mở khóa được lưu thành công.

**Luồng chính**

1. Người chơi chọn nghề bị khóa.  
2. Hệ thống hiển thị điều kiện mở.  
3. Người chơi yêu cầu mở.  
4. Hệ thống kiểm tra điều kiện.  
5. Người chơi xác nhận nếu cần.  
6. Hệ thống cập nhật trạng thái mở khóa.  
7. Hệ thống thông báo thành công.

**Luồng thay thế**  
**A1 – Không đủ điều kiện**

* Thông báo điều kiện còn thiếu.  
* Không mở khóa.

**A2 – Nghề đã mở**

* Thông báo nghề đã mở.  
* Không cập nhật trùng.

**A3 – Người chơi hủy**

* Không thay đổi trạng thái.

**Luồng ngoại lệ**  
Lỗi ghi dữ liệu: giữ trạng thái cũ và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ mở khóa khi đủ điều kiện.  
* BR02: Không mở khóa trùng.  
* BR03: Nếu có chi phí, chỉ trừ sau khi xác nhận và cập nhật thành công.  
* BR04: Trạng thái mở khóa phải được lưu nhất quán.

**Include**  
Mở nghề mới \<\<include\>\> Xem thông tin nghề  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Không được mất trạng thái mở khóa nếu lưu thất bại.  
**Giao diện liên quan**  
Màn hình Mở nghề mới; thông tin nghề.  
**Ghi Chú**  
Không.

**Cấu trúc Use Case của module:**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC04 | Quản lý nhân vật  | Tổng quát |
| UC04.1 | Xem thông tin & chỉ số nhân vật  | Được UC04 gọi; hiển thị thuộc tính, cấp độ và mô hình nhân vật  |
| UC04.2 | Trang bị / Tháo vật phẩm  | Được UC04 gọi; cập nhật trạng thái đồ đạc và tính lại chỉ số  |
| UC04.3 | Nâng cấp thuộc tính / Kỹ năng  | Được UC04 gọi; tiêu tốn tài nguyên để tăng sức mạnh  |
| UC04.4 | Đổi nhân vật xuất trận  | Được UC04 gọi *(dùng nếu game có nhiều nhân vật/chủ tướng)*  |

**Ma trận quan hệ Use Case:**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC04 Quản lý nhân vật  | UC04.1, UC04.2, UC04.3, UC04.4  | Không  | Use Case cấp module  |
| UC04.1 Xem thông tin & chỉ số nhân vật  | Khôn | Không  | Màn hình mặc định hiển thị thuộc tính nhân vật  |
| UC04.2 Trang bị / Tháo vật phẩm  | UC04.1  | Không  | Tự động tính toán và cập nhật lại chỉ số hiển thị  |
| UC04.3 Nâng cấp thuộc tính / Kỹ năng  | UC04.1  | Không  | Yêu cầu tài nguyên; cập nhật chỉ số mới sau khi nâng  |
| UC04.4 Đổi nhân vật xuất trận  | UC04.1  | Không  | Chuyển đổi dữ liệu và hiển thị nhân vật được chọn  |

**Đặc tả UC04:**

| Mã Use Case | UC04 |
| :---- | :---- |
| Tên Use Case | Quản lý nhân vật   |
| Mục đích | Cung cấp trung tâm giao diện để người chơi xem, tùy chỉnh, nâng cấp và quản lý thông tin nhân vật.  |
| Mô tả | Use Case tổng quát cho phép người chơi truy cập màn hình nhân vật và thực hiện các thao tác chuyên sâu như xem chỉ số, mặc/tháo đồ, nâng cấp kỹ năng và đổi nhân vật.  |
| Actor | **\+Chính:** Người chơi **\+Phụ:** Hệ thống Game (Character & Storage Database) |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên trong suốt phiên chơi  |

**Trigger:**

 Người chơi bấm vào biểu tượng hoặc phím tắt "Nhân vật" (Character) trên màn hình chính (HUD).

**Tiền điều kiện:** 

Người chơi đã đăng nhập thành công và đang ở trạng thái an toàn (Sảnh chính / Main Menu / Không ở trong trận combat).

**Hậu điều kiện:** 

Các thay đổi về trang bị, thuộc tính, kỹ năng của nhân vật được lưu đồng bộ vào hệ thống.

**Luồng chính:**

1. Người chơi chọn biểu tượng "Nhân vật" từ giao diện chính.  
2. Hệ thống truy xuất dữ liệu và hiển thị Màn hình Quản lý nhân vật (Thực hiện **UC04.1: Xem thông tin & chỉ số nhân vật**).  
3. Người chơi lựa chọn các tab/tính năng quản lý tương ứng:  
   * Mặc hoặc tháo trang bị (Thực hiện **UC04.2: Trang bị / Tháo vật phẩm**).  
   * Nâng cấp thuộc tính hoặc kỹ năng (Thực hiện **UC04.3: Nâng cấp thuộc tính / Kỹ năng**).  
   * Thay đổi nhân vật/chủ tướng xuất trận (Thực hiện **UC04.4: Đổi nhân vật xuất trận**).  
4. Hệ thống cập nhật hiển thị và đồng bộ dữ liệu sau mỗi thao tác.  
5. Người chơi bấm nút "Thoát" (hoặc phím ESC/Đóng) để quay lại màn hình chính.

**Luồng thay thế:**

* A1. Chuyển đổi linh hoạt giữa các tab:  
  * 1a. Người chơi chuyển đổi trực tiếp qua lại giữa các tab chức năng (Chỉ số, Trang bị, Kỹ năng) ngay trong màn hình Quản lý mà không cần quay về Màn hình chính.

**Luồng ngoại lệ:**

* **E1. Không tải được dữ liệu nhân vật:** Hệ thống hiển thị thông báo "Không thể tải thông tin nhân vật. Vui lòng thử lại" kèm nút \[Thử lại\].  
* **E2. Mất kết nối mạng trong quá trình thao tác:** Hệ thống hiển thị cảnh báo "Mất kết nối", khóa các thao tác nâng cấp/thay đổi đồ và yêu cầu kết nối lại để lưu tiến trình.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Không cho phép người chơi mở giao diện Quản lý nhân vật khi đang trong trạng thái giao chiến (In-combat).  
* **BR2:** Mọi thao tác thay đổi chỉ số/trang bị phải được kiểm tra tính hợp lệ ở Server/Bộ nhớ trước khi lưu chính thức vào cơ sở dữ liệu. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** **UC04.1** (Xem thông tin & chỉ số), **UC04.2** (Trang bị/Tháo vật phẩm), **UC04.3** (Nâng cấp thuộc tính/Kỹ năng), **UC04.4** (Đổi nhân vật xuất trận).

**Extend:** Không.

**Yêu cầu phi chức năng:** Thời gian mở giao diện Quản lý nhân vật và chuyển đổi giữa các tab phải phản hồi tức thì, không gây giật khung hình (FPS drop). *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Giao diện màn hình chính (HUD), Màn hình Quản lý nhân vật tổng quan (Character Window).

**Ghi chú:** Cần thống nhất với bên Code và UI/UX về cách sắp xếp các Tab chức năng trên cùng một màn hình để tối ưu trải nghiệm.

| Mã Use Case | UC04.1  |
| :---- | :---- |
| Tên Use Case | Xem thông tin & chỉ số nhân vật  |
| Mục đích | Cho phép người chơi xem chi tiết thuộc tính, cấp độ, kinh nghiệm và mô hình/hình ảnh của nhân vật hiện tại.  |
| Mô tả | Hệ thống truy xuất dữ liệu nhân vật từ bộ nhớ/máy chủ và hiển thị trực quan các thông số sức mạnh lên màn hình Quản lý nhân vật.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên trong suốt phiên chơi |

**Trigger:**   
Người chơi mở giao diện Quản lý nhân vật (UC04) hoặc chuyển sang tab "Thông tin / Chỉ số".  
**Tiền điều kiện:**   
Dữ liệu nhân vật đã được tải thành công khi đăng nhập/khởi động game.  
**Hậu điều kiện:**   
Toàn bộ thuộc tính cơ bản, thuộc tính cộng thêm và mô hình nhân vật được hiển thị đầy đủ trên giao diện.  
**Luồng chính:**

1. Người chơi mở màn hình Quản lý nhân vật (hoặc chọn tab Thông tin nhân vật).  
2. Hệ thống gửi yêu cầu lấy dữ liệu thuộc tính hiện tại của nhân vật.  
3. Hệ thống tính toán và hợp nhất các chỉ số (Chỉ số gốc \+ Chỉ số cộng thêm từ trang bị, danh hiệu, buff...).  
4. Hệ thống hiển thị mô hình 2D/3D nhân vật cùng danh sách thuộc tính chính (Máu/HP, Năng lượng/MP, Sức tấn công, Giáp, Cấp độ, Thanh kinh nghiệm...).  
5. Người chơi quan sát các thông số và đóng bảng hoặc chuyển sang thao tác khác.

**Luồng thay thế:**

* A1. Xem bảng thuộc tính chi tiết (Detailed Stats):  
  * 1a. Người chơi bấm chọn nút "Chi tiết" hoặc rê chuột (hover) vào icon thuộc tính.  
  * 1b. Hệ thống mở cửa sổ phụ hiển thị toàn bộ chỉ số ẩn/chỉ số nâng cao (Tỷ lệ bạo kích, Tốc độ đánh, Kháng phép, Kháng hiệu ứng, Tốc độ di chuyển...).

**Luồng ngoại lệ:**

* E1. Không tải được dữ liệu chỉ số: Hệ thống hiển thị giá trị mặc định hoặc ký tự "-" tại các ô thuộc tính và hiển thị thông báo lỗi "Không thể tải thuộc tính nhân vật".

**Business Rule / Quy tắc nghiệp vụ:**

* BR1: Dữ liệu chỉ số hiển thị phải có sự phân biệt rõ ràng giữa Chỉ số gốc của nhân vật và Chỉ số được cộng thêm (từ Trang bị / Kỹ năng / Buff).  
* BR2: Danh mục các thuộc tính hiển thị và công thức tính toán chỉ số tổng sẽ được chốt chính thức ở giai đoạn cân bằng Game Design. (Tuân thủ quy tắc chuẩn hóa)

**Include:** Không.  
**Extend:** Không.  
**Yêu cầu phi chức năng:** Thời gian tải và cập nhật các con số thuộc tính phải phản hồi tức thì, giữ mức khung hình ổn định khi hiển thị hiệu ứng/mô hình nhân vật. (Tuân thủ ghi mức nguyên tắc)  
**Giao diện liên quan:** Giao diện Quản lý nhân vật (Tab Thông tin / Character Stats Window), Pop-up Bảng chi tiết thuộc tính.  
**Ghi chú:** Thống nhất với nhóm UI/UX về màu sắc quy chuẩn (ví dụ: Chỉ số gốc chữ trắng, Chỉ số cộng thêm chữ xanh lá/vàng) để người chơi dễ phân biệt.

| Mã Use Case | UC04.2 |
| :---- | :---- |
| Tên Use Case | Trang bị / Tháo vật phẩm  |
| Mục đích | Cho phép người chơi thay đổi các trang bị trên nhân vật để gia tăng hoặc thay đổi thuộc tính sức mạnh.  |
| Mô tả | Người chơi tương tác với Túi đồ và các ô trang bị để gắn vật phẩm vào nhân vật hoặc gỡ vật phẩm ra khỏi nhân vật.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên trong suốt quá trình chơi |

**Trigger:** Người chơi nhấp đúp, kéo thả hoặc chọn nút "Trang bị / Tháo" trên vật phẩm trong giao diện.

**Tiền điều kiện:** Màn hình Quản lý nhân vật đang mở; Vật phẩm tồn tại trong Túi đồ (Inventory).

**Hậu điều kiện:** Vật phẩm được gắn vào ô tương ứng (hoặc trả về túi đồ); Chỉ số của nhân vật được cập nhật lại thành công.

**Luồng chính:**

1. Người chơi chọn một vật phẩm trong Túi đồ và nhấn chọn "Trang bị".  
2. Hệ thống kiểm tra các điều kiện sử dụng của vật phẩm (Cấp độ yêu cầu, Lớp nhân vật phù hợp).  
3. Hệ thống chuyển vật phẩm từ Túi đồ vào ô trang bị tương ứng trên nhân vật.  
4. Hệ thống tính toán và cộng các chỉ số của vật phẩm mới vào thuộc tính tổng của nhân vật.  
5. Hệ thống lưu lại trạng thái mới và cập nhật giao diện (hiển thị trang bị mới và chỉ số mới).

**Luồng thay thế:**

* **A1. Thay thế vật phẩm đang mặc:**  
  * 1a. Ô trang bị tương ứng đã có sẵn một vật phẩm khác.  
  * 1b. Hệ thống tự động tháo vật phẩm cũ trả về Túi đồ và đưa vật phẩm mới vào ô trang bị.  
* **A2. Tháo trang bị:**  
  * 1a. Người chơi chọn một vật phẩm đang mặc trên nhân vật và bấm chọn "Tháo".  
  * 1b. Hệ thống chuyển vật phẩm từ ô trang bị về Túi đồ và trừ đi các chỉ số tương ứng khỏi nhân vật.

**Luồng ngoại lệ:**

* **E1. Không đủ điều kiện sử dụng:** Hệ thống hiển thị thông báo "Cấp độ nhân vật không đủ" hoặc "Trang bị không phù hợp" và giữ nguyên trạng thái.  
* **E2. Túi đồ đã đầy (khi thực hiện tháo trang bị):** Hệ thống hiển thị thông báo "Túi đồ đã đầy, không thể tháo trang bị" và hủy thao tác.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Mỗi loại vật phẩm chỉ được phép trang bị vào đúng ô chức năng tương ứng (Vũ khí, Giáp, Nón, Giày, Phụ kiện...).  
* **BR2:** Lượng chỉ số cụ thể gia tăng và công thức tính toán tổng sức mạnh sẽ được chốt ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** UC04.1 (Xem thông tin & chỉ số nhân vật \- để cập nhật chỉ số hiển thị).

**Extend:** Không.

**Yêu cầu phi chức năng:** Thời gian cập nhật chỉ số và thay đổi hiển thị trang bị phải diễn ra mượt mà, phản hồi tức thì dưới thao tác của người chơi. *(Tuân thủ quy tắc chuẩn hóa nguyên tắc)*

**Giao diện liên quan:** Giao diện Quản lý nhân vật, Khung trang bị (Equipment Slots), Khung Túi đồ (Inventory), Pop-up thông tin vật phẩm (Tooltip).

**Ghi chú:** Cần xác nhận với nhóm Art xem việc thay đổi trang bị có làm thay đổi mô hình/hình ảnh 2D/3D ngoài đời thực của nhân vật hay không.

| Mã Use Case | UC04.3 |
| :---- | :---- |
| Tên Use Case | Nâng cấp thuộc tính / Kỹ năng  |
| Mục đích | Cho phép người chơi tiêu tốn tài nguyên (Vàng, Đá nâng cấp, Điểm kỹ năng...) để gia tăng các chỉ số thuộc tính hoặc nâng cấp độ/hiệu ứng của kỹ năng.  |
| Mô tả | Người chơi chọn thuộc tính hoặc kỹ năng muốn nâng cấp trong giao diện Quản lý nhân vật. Hệ thống kiểm tra điều kiện tài nguyên, thực hiện cộng điểm/cấp và cập nhật lại sức mạnh nhân vật.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên khi người chơi tích lũy đủ tài nguyên  |

**Trigger:** Người chơi bấm nút "Nâng cấp" (Upgrade) hoặc biểu tượng dấu \[+\] tại thuộc tính/kỹ năng muốn nâng.

**Tiền điều kiện:** Màn hình Quản lý nhân vật đang mở; Kỹ năng/Thuộc tính đã được mở khóa; Nhân vật đạt đủ cấp độ yêu cầu (nếu có).

**Hậu điều kiện:** Tài nguyên người chơi bị trừ tương ứng; Cấp độ thuộc tính/kỹ năng tăng lên; Chỉ số nhân vật được cập nhật thành công.

**Luồng chính:**

1. Người chơi mở tab "Nâng cấp" (hoặc tab "Kỹ năng / Thuộc tính") trong giao diện Quản lý nhân vật.  
2. Hệ thống hiển thị danh sách thuộc tính/kỹ năng, cấp độ hiện tại, chi phí nâng cấp và mức chỉ số gia tăng dự kiến.  
3. Người chơi chọn thuộc tính hoặc kỹ năng cần nâng và bấm nút "Nâng cấp".  
4. Hệ thống kiểm tra tài nguyên của người chơi có đủ so với chi phí yêu cầu hay không.  
5. Hệ thống trừ tài nguyên, tăng cấp thuộc tính/kỹ năng và tính toán lại tổng chỉ số nhân vật.  
6. Hệ thống phát âm thanh/hiệu ứng nâng cấp (VFX/SFX) và cập nhật thông số mới lên giao diện.

**Luồng thay thế:**

* **A1. Nâng cấp nhanh / Nâng tối đa (Max Upgrade):**  
  * 1a. Người chơi bấm chọn nút "Nâng tối đa".  
  * 1b. Hệ thống tự động tính toán số cấp nhiều nhất có thể nâng dựa trên lượng tài nguyên hiện có và thực hiện nâng cấp hàng loạt trong 1 thao tác.  
* **A2. Tẩy điểm / Tái lập (Reset Skills/Stats):**  
  * 1a. Người chơi chọn nút "Tẩy điểm" và xác nhận tiêu tốn phí tẩy điểm.  
  * 1b. Hệ thống hoàn trả lại điểm/tài nguyên đã nâng và đưa cấp độ thuộc tính/kỹ năng về mặc định.

**Luồng ngoại lệ:**

* **E1. Không đủ tài nguyên:** Hệ thống hiển thị thông báo "Không đủ Vàng / Điểm kỹ năng" và hiệu ứng rung/làm mờ nút Nâng cấp.  
* **E2. Đạt cấp độ tối đa (Max Level):** Hệ thống hiển thị trạng thái "Đã đạt cấp tối đa (MAX)" và vô hiệu hóa nút Nâng cấp.  
* **E3. Chưa đủ cấp độ nhân vật yêu cầu:** Hệ thống hiển thị thông báo "Yêu cầu nhân vật đạt Cấp X để nâng cấp".

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Chi phí nâng cấp và điều kiện cấp độ nhân vật phải tăng dần theo từng bậc cấp độ của thuộc tính/kỹ năng.  
* **BR2:** Công thức tính tỷ lệ gia tăng chỉ số và bảng chi phí chi tiết cho từng cấp sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** UC04.1 (Xem thông tin & chỉ số nhân vật \- để tự động cập nhật và hiển thị lại chỉ số mới).

**Extend:** Không.

**Yêu cầu phi chức năng:** Phản hồi thao tác bấm nâng cấp và hiệu ứng tăng chỉ số phải diễn ra tức thì, không bị khựng/lag khi người chơi nhấp nút liên tục. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Tab Nâng cấp Thuộc tính / Kỹ năng, Khung hiển thị tài nguyên sở hữu (Gold/Gems/Skill Points), Pop-up xác nhận Nâng cấp/Tẩy điểm.

**Ghi chú:** Cần xác nhận với Game Designer xem hệ thống game có tính năng "Tẩy điểm" (A2) hay không để chốt việc làm giao diện UI cho phù hợp.

| Mã Use Case | UC04. |
| :---- | :---- |
| Tên Use Case | Đổi nhân vật xuất trận  |
| Mục đích | Cho phép người chơi thay đổi nhân vật (hoặc đội hình nhân vật) đang trực tiếp tham gia chiến đấu trong game.  |
| Mô tả | Người chơi lựa chọn một nhân vật trong danh sách đã sở hữu để gán vào vị trí xuất trận, thay thế cho nhân vật hiện tại hoặc sắp xếp lại đội hình.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Thường xuyên khi người chơi muốn thay đổi chiến thuật hoặc trải nghiệm nhân vật mới  |

**Trigger:** Người chơi bấm nút "Xuất trận" (hoặc "Chọn") tại danh sách nhân vật sở hữu.

**Tiền điều kiện:** Màn hình Quản lý nhân vật đang mở; Người chơi sở hữu từ 2 nhân vật trở lên.

**Hậu điều kiện:** Nhân vật mới được gán làm nhân vật chiến đấu chính (hoặc đưa vào ô đội hình); Trạng thái đội hình được lưu thành công.

**Luồng chính:**

1. Người chơi mở danh sách các nhân vật đã sở hữu trong giao diện Quản lý nhân vật.  
2. Người chơi chọn một nhân vật chưa xuất trận.  
3. Hệ thống hiển thị xem trước (Preview) mô hình, vai trò và thông số của nhân vật được chọn (Thực hiện **UC04.1**).  
4. Người chơi nhấn nút "Xuất trận" (hoặc "Đổi nhân vật").  
5. Hệ thống cập nhật nhân vật mới vào vị trí xuất trận chính và trả nhân vật cũ về danh sách chờ.  
6. Hệ thống hiển thị nhãn/trạng thái "Đang xuất trận" trên nhân vật mới và phát âm thanh/hiệu ứng xác nhận thành công.

**Luồng thay thế:**

* **A1. Sắp xếp đội hình nhiều nhân vật (nếu game có cơ chế Team-building):**  
  * 1a. Người chơi chọn vị trí ô cụ thể (Slot 1, Slot 2, Slot 3...).  
  * 1b. Người chơi chọn nhân vật trong danh sách để gán vào ô đó hoặc kéo thả (Drag & Drop) nhân vật vào ô mong muốn.

**Luồng ngoại lệ:**

* **E1. Nhân vật chưa được mở khóa:** Hệ thống hiển thị nút "Chưa sở hữu" (hoặc icon Ổ khóa) và vô hiệu hóa thao tác xuất trận.  
* **E2. Nhân vật đã ở trong đội hình:** Hệ thống hiển thị thông báo "Nhân vật đã xuất trận" và không thực hiện gán trùng lặp.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Luôn phải có ít nhất 01 nhân vật ở trạng thái xuất trận (không được để trống toàn bộ đội hình).  
* **BR2:** Giới hạn số lượng nhân vật xuất trận tối đa trong một đội hình sẽ được chốt chính thức ở giai đoạn thiết kế lối chơi (Game Design). *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** UC04.1 (Xem thông tin & chỉ số nhân vật \- để hiển thị bản xem trước thuộc tính của nhân vật sắp đổi).

**Extend:** Không.

**Yêu cầu phi chức năng:** Việc tải mô hình/hình ảnh 2D-3D của nhân vật mới khi xem trước và thao tác đổi nhân vật phải diễn ra mượt mà, không gây giật lag giao diện. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Giao diện Quản lý nhân vật, Danh sách nhân vật (Character List), Khung vị trí xuất trận (Party Slots).

**Ghi chú:** Cần chốt với bên Game Design xem game của team thuộc dạng chơi **1 nhân vật duy nhất** (như Action RPG truyền thống) hay **đội hình nhiều nhân vật** (như Turn-based / Gacha) để điều chỉnh giao diện ô xuất trận cho chuẩn xác.

**Cấu trúc Use Case của module:**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC05 | Khám phá thế giới  | Tổng quát |
| UC05.1 | Di chuyển & Điều hướng bản đồ  | Được UC05 gọi; xử lý di chuyển nhân vật, camera và Minimap  |
| UC05.2 | Tương tác với môi trường & NPC  | Được UC05 gọi; kích hoạt đối thoại, nhận nhiệm vụ, tương tác cơ quan  |
| UC05.3 | Mở khóa khu vực & Điểm dịch chuyển  | Được UC05 gọi; mở rộng vùng sương mù (Fog of War) và Dịch chuyển nhanh (Fast Travel)  |
| UC05.4 | Thu thập tài nguyên & Mở rương  | Được UC05 gọi; tương tác nhặt vật phẩm, thảo dược, quặng, mở rương báu  |

**Ma trận quan hệ Use Case:**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC05 Khám phá thế giới  | UC05.1, UC05.2, UC05.3, UC05.4  | Không  | Use Case cấp module  |
| UC05.1 Di chuyển & Điều hướng bản đồ  | Không | Không  | Cập nhật vị trí tọa độ liên tục trên World Map / Minimap  |
| UC05.2 Tương tác với môi trường & NPC  | UC05.1  | Không  | Yêu cầu nhân vật di chuyển đến phạm vi tương tác (Interactive Distance)  |
| UC05.3 Mở khóa khu vực & Điểm dịch chuyển  | UC05.1  | Không  | Kích hoạt vùng đất mới hoặc sử dụng tính năng dịch chuyển tức thời  |
| UC05.4 Thu thập tài nguyên & Mở rương  | UC05.1  | Không  | Thêm tài nguyên nhặt được vào túi đồ sau tương tác  |

**Đặc tả UC05:**

| Mã Use Case | UC05  |
| :---- | :---- |
| Tên Use Case | Khám phá thế giới   |
| Mục đích | Cung cấp hệ thống tương tác không gian thế giới game, cho phép người chơi di chuyển, mở rộng bản đồ, tương tác NPC và thu thập vật phẩm.  |
| Mô tả | Use Case tổng quát quản lý luồng trải nghiệm môi trường 2D/3D của người chơi ngoài trạng thái chiến đấu cố định hoặc giao diện menu.  |
| Actor | **\+Chính:** Người chơi **\+Phụ:** Hệ thống Game (World Engine, Physics/Collision System, Inventory System)  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Diễn ra liên tục xuyên suốt quá trình trải nghiệm game  |

Trigger: Người chơi điều khiển nhân vật tiến vào bản đồ thế giới (World Map / Overworld Scene).

Tiền điều kiện: Nhân vật đã khởi tạo thành công và đang ở trạng thái còn sống (Alive).

Hậu điều kiện: Tọa độ nhân vật, trạng thái vật thể trong môi trường và tiến trình khám phá thế giới được lưu lại.

Luồng chính:

1. Người chơi tiến vào môi trường game và thực hiện điều khiển nhân vật di chuyển (Thực hiện UC05.1: Di chuyển & Điều hướng bản đồ).  
2. Khi đến gần các thực thể trong thế giới (NPC, cơ quan, điểm nhiệm vụ), người chơi kích hoạt tương tác (Thực hiện UC05.2: Tương tác với môi trường & NPC).  
3. Khi tiếp cận vùng đất mới hoặc Cột mốc dịch chuyển, hệ thống cập nhật mở rộng bản đồ (Thực hiện UC05.3: Mở khóa khu vực & Điểm dịch chuyển).  
4. Khi phát hiện tài nguyên/rương báu, người chơi tương tác để nhặt vật phẩm vào túi đồ (Thực hiện UC05.4: Thu thập tài nguyên & Mở rương).  
5. Hệ thống liên tục cập nhật vị trí, va chạm (Collision) và đồng bộ trạng thái môi trường.

Luồng thay thế:

* A1. Chuyển cảnh / Chuyển Map (Zone Transition):  
  * 1a. Nhân vật đi vào vùng dịch chuyển/cổng chuyển cảnh (Portal / Trigger Zone).  
  * 1b. Hệ thống lưu vị trí hiện tại, tải dữ liệu bản đồ mới và đưa nhân vật sang vùng đất mới.

Luồng ngoại lệ:

* E1. Nhân vật rơi khỏi bản đồ (Out of bounds / Bug va chạm): Hệ thống phát hiện bất thường về tọa độ và tự động đưa nhân vật trở về điểm an toàn gần nhất (Safe Checkpoint).  
* E2. Mất kết nối khi đang di chuyển: Hệ thống tạm dừng thế giới, hiển thị cảnh báo kết nối và lưu lại tọa độ an toàn trước khi ngắt phiên.

Business Rule / Quy tắc nghiệp vụ:

* BR1: Nhân vật không thể di chuyển qua các vùng vật thể có gán va chạm (Collider) hoặc vùng bị khóa theo tiến trình câu chuyện.  
* BR2: Tốc độ di chuyển, tầm nhìn bản đồ và phạm vi tương tác vật thể sẽ được cân bằng chi tiết ở giai đoạn Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

Include: UC05.1 (Di chuyển & Điều hướng), UC05.2 (Tương tác NPC/Môi trường), UC05.3 (Mở khóa khu vực & Dịch chuyển), UC05.4 (Thu thập tài nguyên & Mở rương).

Extend: Không.

Yêu cầu phi chức năng: Đảm bảo tải bản đồ và vật thể (World Streaming / Map Loading) mượt mà, hạn chế tối đa việc sụt giảm khung hình (FPS drop) khi di chuyển liên tục. *(Tuân thủ ghi mức nguyên tắc)*

Giao diện liên quan: Giao diện chơi game chính (HUD), Bản đồ thu nhỏ (Minimap), Bản đồ thế giới (World Map), Icon gợi ý tương tác (Interaction Prompt).

Ghi chú: Thống nhất với nhóm Dev/Art về góc nhìn camera (2D Top-down, Side-scroller hay 3D Third-person) để viết chi tiết các luồng di chuyển ở UC05.1.

| Mã Use Case | UC05.1  |
| :---- | :---- |
| Tên Use Case | Di chuyển & Điều hướng bản đồ  |
| Mục đích | Cho phép người chơi điều khiển nhân vật di chuyển trong không gian game, đồng thời sử dụng hệ thống Camera và Bản đồ để định vị, tìm đường.  |
| Mô tả | Hệ thống xử lý các thao tác nhập (input) từ người chơi để thay đổi tọa độ của nhân vật. Đi kèm với đó là việc cập nhật góc nhìn Camera và vị trí trên Minimap theo thời gian thực.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Input System, Physics/Collision Engine, Camera System)  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Liên tục khi người chơi không ở trong các giao diện (Menu/UI) toàn màn hình  |

**Trigger:** Người chơi sử dụng các phím điều hướng (WASD / Mũi tên / Joystick) hoặc click chuột lên bề mặt di chuyển trong game.

**Tiền điều kiện:** Nhân vật không ở trạng thái bị khống chế cứng (Choáng/Trói chân/Đóng băng) và không mở các giao diện khóa thao tác.

**Hậu điều kiện:** Tọa độ nhân vật được cập nhật; Góc nhìn Camera và Bản đồ thu nhỏ (Minimap) thay đổi tương ứng.

**Luồng chính:**

1. Người chơi giữ phím điều hướng hoặc click chuột để ra lệnh di chuyển.  
2. Hệ thống tiếp nhận lệnh và kiểm tra va chạm (Collision) trên hướng đi dự kiến.  
3. Nếu không có vật cản, hệ thống thay đổi tọa độ nhân vật theo hướng đã định và kích hoạt hoạt ảnh (Animation) di chuyển (Đi/Chạy).  
4. Hệ thống Camera tự động cuộn/di chuyển để giữ nhân vật trong khung hình.  
5. Hệ thống cập nhật biểu tượng định vị của nhân vật trên Bản đồ thu nhỏ (Minimap).  
6. Khi người chơi thả phím (hoặc tới điểm click chuột), hệ thống dừng cập nhật tọa độ và đưa nhân vật về hoạt ảnh đứng im (Idle).

**Luồng thay thế:**

* **A1. Chạy nước rút / Lướt (Sprint / Dash):**  
  * 1a. Người chơi nhấn giữ phím chạy nhanh (VD: Shift) cùng lúc với phím điều hướng.  
  * 1b. Hệ thống đổi sang hoạt ảnh chạy nhanh, gia tăng tốc độ cập nhật tọa độ và bắt đầu trừ điểm Thể lực (Stamina) theo thời gian.  
* **A2. Xem Bản đồ thế giới (World Map):**  
  * 1a. Người chơi nhấn phím tắt mở bản đồ tổng (VD: phím M).  
  * 1b. Hệ thống mở giao diện World Map, hiển thị vị trí hiện tại của nhân vật, sương mù bản đồ (Fog of War) và các biểu tượng điểm chú ý (POI).

**Luồng ngoại lệ:**

* **E1. Nhân vật gặp vật cản (Collision):** Hệ thống phát hiện va chạm với môi trường (tường, đá, vực sâu) hoặc NPC khác \-\> Hệ thống chặn di chuyển theo hướng đó, nhân vật có thể trượt dọc theo rìa vật cản hoặc đứng khựng lại.  
* **E2. Hết Thể lực (khi đang Sprint):** Hệ thống buộc nhân vật quay trở lại tốc độ di chuyển bình thường, khóa luồng thay thế A1 cho đến khi Thể lực hồi lại đủ mức tối thiểu.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Nhân vật tuyệt đối không được đi xuyên qua các đối tượng có thuộc tính cản trở (Solid Collider) trong môi trường.  
* **BR2:** Các chỉ số như Tốc độ di chuyển cơ bản (Walk speed), tốc độ chạy nước rút (Sprint speed) và tỷ lệ tiêu hao/hồi phục Thể lực sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** Không.

**Extend:** Không.

**Yêu cầu phi chức năng:** Cơ chế điều khiển cần có độ trễ cực thấp (No input lag) để tạo cảm giác phản hồi ngay lập tức. Camera di chuyển mượt mà, không giật lag (stuttering) làm hoa mắt người chơi. *(Tuân thủ mức nguyên tắc)*

**Giao diện liên quan:** Giao diện người dùng chính (HUD), Thanh Thể lực (Stamina Bar \- nếu có), Bản đồ thu nhỏ (Minimap), Bản đồ thế giới (World Map).

**Ghi chú:** Cần làm rõ với Coder và Designer về cơ chế Camera (Camera bám cứng/Rigid hay Camera có độ trễ mượt/Damping) để đảm bảo trải nghiệm nhìn tốt nhất.

| Mã Use Case | UC05.2  |
| :---- | :---- |
| Tên Use Case | Tương tác với môi trường & NPC  |
| Mục đích | Cho phép người chơi giao tiếp với NPC, nhận/trả nhiệm vụ, hoặc kích hoạt các vật thể/cơ quan trong môi trường thế giới.  |
| Mô tả | Khi nhân vật di chuyển vào phạm vi tương tác, hệ thống hiển thị biểu tượng gợi ý. Người chơi nhấn phím tương tác để mở hộp thoại, chọn các tùy chọn trò chuyện, nhận nhiệm vụ hoặc vận hành cơ quan giải đố.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Dialogue System, Quest System, World Object Engine)  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên trong quá trình khám phá và làm nhiệm vụ  |

**Trigger:** Người chơi nhấn phím tương tác (VD: phím F, E, Space hoặc nút Tương tác trên màn hình) khi nhân vật đứng trong tầm tương tác của NPC/vật thể.

**Tiền điều kiện:** Nhân vật ở trong khoảng cách tương tác cho phép (Interaction Range); Nhân vật không ở trạng thái bị khống chế hoặc bị khóa thao tác.

**Hậu điều kiện:** Khung đối thoại/Giao diện tương tác được mở; Trạng thái cơ quan môi trường thay đổi; Tiến trình nhiệm vụ được cập nhật trong Nhật ký (Quest Log).

**Luồng chính:**

1. Nhân vật di chuyển đến vị trí gần NPC hoặc vật thể môi trường (Thực hiện **UC05.1**).  
2. Hệ thống phát hiện khoảng cách và hiển thị biểu tượng gợi ý tương tác (VD: "Bấm \[F\] để Nói chuyện" hoặc "Bấm \[F\] để Kích hoạt").  
3. Người chơi nhấn phím tương tác.  
4. Hệ thống tạm khóa di chuyển tự do của nhân vật, quay góc nhìn Camera về phía đối tượng tương tác.  
5. Hệ thống hiển thị Giao diện đối thoại (hoặc kích hoạt hoạt ảnh của cơ quan).  
6. Người chơi click/bấm phím để chuyển qua các câu thoại hoặc chọn tùy chọn tương tác.  
7. Khi kết thúc hội thoại hoặc thao tác, hệ thống đóng giao diện tương tác và trả lại quyền di chuyển cho người chơi.

**Luồng thay thế:**

* **A1. Nhận hoặc Trả nhiệm vụ (Quest Interaction):**  
  * 1a. Người chơi nói chuyện với NPC có biểu tượng Nhiệm vụ (\! / ?).  
  * 1b. Hệ thống mở cửa sổ chi tiết Nhiệm vụ, hiển thị yêu cầu và phần thưởng.  
  * 1c. Người chơi bấm "Chấp nhận" hoặc "Hoàn thành" \-\> Hệ thống cập nhật trạng thái nhiệm vụ và trao thưởng (nếu có).  
* **A2. Kích hoạt cơ quan / Công tắc (Mechanism Trigger):**  
  * 1a. Người chơi bấm tương tác với công tắc/cơ quan trong bản đồ.  
  * 1b. Hệ thống chạy hoạt ảnh kích hoạt (mở cổng, hạ cầu, kích hoạt bẫy...) và thay đổi trạng thái của vật thể môi trường.

**Luồng ngoại lệ:**

* **E1. Bị ngắt tương tác (Do bị tấn công):** Nhân vật nhận sát thương từ kẻ địch trong lúc đang đối thoại \-\> Hệ thống tự động đóng hộp thoại và đưa nhân vật về trạng thái chiến đấu.  
* **E2. Cơ quan bị khóa / Chưa đủ điều kiện:** Người chơi tương tác với cơ quan chưa mở khóa \-\> Hệ thống hiển thị thông báo "Yêu cầu Chìa khóa" hoặc "Chưa đạt điều kiện kích hoạt" và giữ nguyên trạng thái.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Phạm vi nhận diện tương tác (Interactive Radius) phải được cố định rõ ràng xung quanh Collider của NPC/vật thể để tránh lỗi kích hoạt từ khoảng cách quá xa.  
* **BR2:** Điều kiện nhận/trả nhiệm vụ và logic giải đố của cơ quan sẽ được thiết kế chi tiết ở giai đoạn Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** **UC05.1** (Di chuyển & Điều hướng bản đồ \- yêu cầu nhân vật di chuyển đến tầm tương tác).

**Extend:** Không.

**Yêu cầu phi chức năng:** Chuyển cảnh góc nhìn từ di chuyển sang màn hình đối thoại phải diễn ra mượt mà, không giật khung hình. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Gợi ý tương tác (Interaction Prompt), Khung hộp thoại (Dialogue Box), Cửa sổ Nhận/Trả nhiệm vụ (Quest Window).

**Ghi chú:** Thống nhất với nhóm UI/UX về các tính năng phụ khi đối thoại như "Bỏ qua thoại" (Skip) hoặc "Tự động chạy thoại" (Auto Play).

| Mã Use Case | UC05.3 |
| :---- | :---- |
| Tên Use Case | Mở khóa khu vực & Điểm dịch chuyển  |
| Mục đích | Cho phép người chơi xóa sương mù bản đồ (Fog of War) và kích hoạt các điểm dịch chuyển nhanh (Fast Travel Waypoints) để di chuyển tức thời.  |
| Mô tả | Khi người chơi di chuyển đến vùng đất mới hoặc tương tác với Cột mốc dịch chuyển, hệ thống cập nhật trạng thái mở khóa trên World Map. Người chơi có thể sử dụng World Map để chọn vị trí và dịch chuyển ngay lập tức.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (World Map Engine, Fast Travel System, Progress Save System)  |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Thường xuyên trong quá trình khám phá thế giới game  |

**Trigger:** Người chơi tương tác với Cột mốc/Tượng dịch chuyển trên bản đồ; hoặc chọn một Điểm dịch chuyển đã kích hoạt từ World Map.

**Tiền điều kiện:** Nhân vật ở trạng thái an toàn (không trong trận chiến); Điểm dịch chuyển đích đã được mở khóa trước đó.

**Hậu điều kiện:** Sương mù khu vực trên bản đồ được làm sáng; Điểm dịch chuyển chuyển sang trạng thái khả dụng; Nhân vật được đưa đến tọa độ mới.

**Luồng chính:**

1. Người chơi di chuyển nhân vật đến vị trí Cột mốc / Điểm dịch chuyển chưa mở khóa (Thực hiện **UC05.1**).  
2. Người chơi nhấn phím tương tác với Cột mốc (Thực hiện **UC05.2**).  
3. Hệ thống kích hoạt hiệu ứng mở khóa (VFX/SFX), xóa sương mù (Fog of War) của vùng đất tương ứng trên World Map và chuyển biểu tượng mốc sang trạng thái "Đã mở khóa".  
4. Khi muốn dịch chuyển nhanh, người chơi mở Bản đồ thế giới World Map (Thực hiện **UC05.1**).  
5. Người chơi chọn một Điểm dịch chuyển đã mở khóa và nhấn "Dịch chuyển".  
6. Hệ thống hiển thị màn hình tải cảnh (Loading Screen) và chuyển tọa độ nhân vật đến điểm đã chọn.

**Luồng thay thế:**

* **A1. Tự động mở khóa khu vực theo vị trí (Boundary Discovery):**  
  * 1a. Nhân vật di chuyển qua ranh giới địa lý của một vùng đất mới.  
  * 1b. Hệ thống tự động xóa sương mù vùng xung quanh nhân vật và hiển thị thông báo "Đã khám phá: \[Tên vùng đất\]".

**Luồng ngoại lệ:**

* **E1. Đang trong trạng thái giao chiến (In-combat):** Người chơi chọn dịch chuyển trên bản đồ \-\> Hệ thống hiển thị thông báo "Không thể dịch chuyển khi đang giao chiến" và hủy thao tác.  
* **E2. Điểm dịch chuyển chưa được mở khóa:** Người chơi nhấp vào vị trí xám trên bản đồ \-\> Hệ thống hiển thị thông báo "Điểm dịch chuyển chưa được kích hoạt".

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Tuyệt đối không cho phép thực hiện dịch chuyển nhanh khi nhân vật đang ở trong phó bản cố định hoặc đang chịu sát thương.  
* **BR2:** Bán kính xóa sương mù bản đồ và chi phí dịch chuyển (nếu có) sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** **UC05.1** (Di chuyển & Điều hướng bản đồ), **UC05.2** (Tương tác với môi trường & NPC).

**Extend:** Không.

**Yêu cầu phi chức năng:** Thời gian chuyên cảnh và tải dữ liệu bản đồ khi dịch chuyển phải được tối ưu mượt mà, không gây đứng hình lâu. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Giao diện Bản đồ thế giới (World Map), Màn hình chờ tải cảnh (Loading Screen), Banner thông báo khám phá khu vực.

**Ghi chú:** Thống nhất với Game Designer xem việc dịch chuyển có tốn tài nguyên (như Thể lực/Vàng) hay hoàn toàn miễn phí.

| Mã Use Case | UC05.4 |
| :---- | :---- |
| Tên Use Case | Thu thập tài nguyên & Mở rương  |
| Mục đích | Cho phép người chơi tương tác với các điểm tài nguyên (thảo dược, quặng, gỗ...) và rương báu trong thế giới để thu thập vật phẩm vào túi đồ.  |
| Mô tả | Người chơi di chuyển đến vị trí rương hoặc điểm tài nguyên, thực hiện thao tác tương tác. Hệ thống kiểm tra điều kiện (dụng cụ, chìa khóa, dung lượng túi) và chuyển vật phẩm thu được vào úi đồ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Inventory System, World Object Engine, Loot Table System)  |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Thường xuyên trong quá trình khám phá thế giới game  |

**Trigger:** Người chơi bấm phím tương tác (VD: phím F/E hoặc nút Tương tác) khi đứng gần điểm tài nguyên hoặc rương báu.

**Tiền điều kiện:** Nhân vật ở trong phạm vi tương tác; Điểm tài nguyên hoặc Rương đang ở trạng thái khả dụng (chưa bị nhặt hoặc đã hồi lại/respawn).

**Hậu điều kiện:** Vật phẩm/tài nguyên được thêm vào Túi đồ (Inventory); Rương báu hoặc điểm tài nguyên chuyển sang trạng thái đã khai thác hoặc tạm thời biến mất.

**Luồng chính:**

1. Người chơi di chuyển nhân vật đến gần rương báu hoặc điểm tài nguyên (Thực hiện **UC05.1**).  
2. Hệ thống hiển thị biểu tượng gợi ý tương tác (VD: "Bấm \[F\] để Mở rương" hoặc "Bấm \[F\] để Thu thập").  
3. Người chơi nhấn phím tương tác.  
4. Hệ thống phát hoạt ảnh (Animation) thu thập hoặc mở rương (có thể đi kèm thanh tiến trình \- Progress Bar).  
5. Hệ thống tính toán danh sách vật phẩm nhận được theo bảng tỷ lệ rơi đồ (Loot Table).  
6. Hệ thống thêm vật phẩm vào Túi đồ và hiển thị thông báo nhận vật phẩm (Loot Popup) trên màn hình.

**Luồng thay thế:**

* **A1. Rương yêu cầu Chìa khóa / Dụng cụ chuyên dụng:**  
  * 1a. Người chơi tương tác với rương bị khóa hoặc điểm tài nguyên đặc biệt.  
  * 1b. Hệ thống kiểm tra và xác nhận trong Túi đồ có đủ Chìa khóa hoặc Dụng cụ phù hợp (VD: Cuốc, Liềm, Chìa vàng...).  
  * 1c. Hệ thống trừ dụng cụ (nếu là tiêu hao) và tiến hành mở rương/thu thập bình thường.

**Luồng ngoại lệ:**

* **E1. Túi đồ đã đầy (Inventory Full):** Hệ thống hiển thị thông báo "Túi đồ đã đầy, không thể thu thập" và giữ nguyên trạng thái rương/tài nguyên.  
* **E2. Thiếu Chìa khóa / Dụng cụ thu thập:** Hệ thống hiển thị thông báo "Yêu cầu \[Tên Chìa khóa / Dụng cụ\] để mở" và hủy thao tác.  
* **E3. Bị ngắt thao tác khi đang thu thập:** Nhân vật chịu sát thương hoặc di chuyển ra khỏi phạm vi khi thanh tiến trình đang chạy \-\> Thao tác bị hủy bỏ và không nhận được vật phẩm.

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Rương báu sau khi mở sẽ đổi sang trạng thái cố định (Đã mở / Mất đi); Điểm tài nguyên môi trường sẽ đếm ngược thời gian làm mới (Respawn Cooldown) nếu game thuộc dạng thế giới mở lặp lại.  
* **BR2:** Tỷ lệ rơi đồ (Drop Rate), số lượng tài nguyên thu hoạch và thời gian chờ thu thập (Channeling time) sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** **UC05.1** (Di chuyển & Điều hướng bản đồ).

**Extend:** Không.

**Yêu cầu phi chức năng:** Phản hồi nhận đồ và cập nhật dữ liệu vào Túi đồ phải diễn ra mượt mà, chính xác, không để xảy ra lỗi mất vật phẩm khi mạng chập chờn. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Gợi ý tương tác (Interaction Prompt), Thanh tiến trình thu thập (Progress Bar), Pop-up Thông báo nhận vật phẩm (Loot Notification).

**Ghi chú:** Thống nhất với nhóm Dev và Game Designer xem vật phẩm khi mở rương sẽ **bay thẳng vào túi đồ** hay **rơi ra mặt đất (Loot drop)** để người chơi tự nhặt.

**Cấu trúc Use Case của module:**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC06 | Quan hệ NPC  | Tổng quát |
| UC06.1 | Xem danh sách & Mức cảm tình NPC  | Được UC06 gọi; hiển thị danh sách NPC, cấp độ thân thiết và sở thích  |
| UC06.2 | Tương tác & Trò chuyện tăng cảm tình  | Được UC06 gọi; chọn câu thoại/chủ đề trò chuyện để tăng điểm thân thiết  |
| UC06.3 | Tặng quà NPC  | Được UC06 gọi; tiêu tốn vật phẩm đúng sở thích để gia tăng điểm cảm tình  |
| UC06.4 | Mở khóa Truyện ký & Phần thưởng NPC  | Được UC06 gọi; nhận quà mốc cảm tình, mở khóa tiểu sử, nhiệm vụ ẩn hoặc kỹ năng hỗ trợ  |

**Ma trận quan hệ Use Case:**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC06 Quan hệ NPC  | UC06.1, UC06.2, UC06.3, UC06.4  | Không  | Use Case cấp module  |
| UC06.1 Xem danh sách & Mức cảm tình NPC  | Không | Không  | Màn hình lưu trữ và tra cứu thông tin mối quan hệ NPC  |
| UC06.2 Tương tác & Trò chuyện tăng cảm tình  | UC06.1   | Không  | Cập nhật thanh điểm cảm tình sau tương tác thoại  |
| UC06.3 Tặng quà NPC  | UC06.1  | Không  | Trừ vật phẩm trong túi đồ và tính điểm cảm tình tương ứng  |
| UC06.4 Mở khóa Truyện ký & Phần thưởng NPC  | UC06.1  | Không  | Kích hoạt phần thưởng khi đạt mốc cấp độ cảm tình quy định  |

**Đặc tả UC06:**

| Mã Use Case | UC06 |
| :---- | :---- |
| Tên Use Case | Quan hệ NPC   |
| Mục đích | Cung cấp hệ thống tương tác tình cảm, cho phép người chơi xây dựng và quản lý mức độ thân thiết với các nhân vật NPC trong game để mở khóa cốt truyện và phần thưởng.  |
| Mô tả | Use Case tổng quát điều phối toàn bộ các luồng chức năng liên quan đến NPC Affection, bao gồm xem thông tin, trò chuyện, tặng quà và nhận thưởng mốc cảm tình.  |
| Actor | **\+Chính:** Người chơi **\+Phụ:** Hệ thống Game (NPC Relationship & Dialogue System)  |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Thường xuyên trong suốt quá trình chơi  |

**Trigger:** Người chơi tiến hành tương tác với NPC trong thế giới game hoặc mở giao diện "Sổ tay Quan hệ" từ Menu chính.

**Tiền điều kiện:** Người chơi đã hoàn thành nhiệm vụ hướng dẫn mở khóa tính năng Quan hệ; Gặp gỡ NPC có hỗ trợ hệ thống cảm tình.

**Hậu điều kiện:** Dữ liệu điểm thân thiết, lịch sử tặng quà và trạng thái phần thưởng của NPC được lưu đồng bộ vào tiến trình của người chơi.

**Luồng chính:**

1. Người chơi mở giao diện Quan hệ để kiểm tra danh sách NPC, sở thích và mức điểm thân thiết hiện tại (Thực hiện **UC06.1: Xem danh sách & Mức cảm tình NPC**).  
2. Người chơi tiếp cận NPC trong bản đồ và chọn các đoạn hội thoại đặc biệt để tăng điểm (Thực hiện **UC06.2: Tương tác & Trò chuyện tăng cảm tình**).  
3. Người chơi mở Menu tặng quà và chọn vật phẩm phù hợp để gia tăng nhanh điểm thân thiết (Thực hiện **UC06.3: Tặng quà NPC**).  
4. Khi mức độ thân thiết đạt mốc quy định, hệ thống thông báo mở khóa Truyện ký (Lore) hoặc cho phép nhận phần thưởng (Thực hiện **UC06.4: Mở khóa Truyện ký & Phần thưởng NPC**).  
5. Hệ thống cập nhật trạng thái mới nhất của NPC lên giao diện và lưu dữ liệu.

**Luồng thay thế:**

* **A1. Tương tác đa luồng:**  
  * 1a. Người chơi có thể liên tục tặng nhiều món quà (UC06.3) và nhận thưởng (UC06.4) ngay trong cùng một phiên trò chuyện với NPC mà không cần đóng mở lại Menu nhiều lần.

**Luồng ngoại lệ:**

* **E1. NPC đang bận (Busy State):** Nếu NPC đang dính líu đến một Nhiệm vụ chính tuyến (Main Quest) khác chưa hoàn thành \-\> Hệ thống tạm thời khóa các tùy chọn Trò chuyện tăng cảm tình / Tặng quà và hiển thị thông báo "NPC đang trong một sự kiện khác".

**Business Rule / Quy tắc nghiệp vụ:**

* **BR1:** Điểm thân thiết không thể vượt qua giới hạn của cấp độ hiện tại nếu người chơi chưa nhận phần thưởng mốc hoặc chưa xem xong đoạn Truyện ký tương ứng.  
* **BR2:** Công thức tính điểm khi tặng quà (đúng/sai sở thích) và bảng phần thưởng theo mốc sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** **UC06.1** (Xem danh sách & Mức cảm tình), **UC06.2** (Tương tác & Trò chuyện), **UC06.3** (Tặng quà NPC), **UC06.4** (Mở khóa Truyện ký & Phần thưởng).

**Extend:** Không.

**Yêu cầu phi chức năng:** Quá trình tính toán cộng điểm cảm tình và lưu trạng thái NPC phải diễn ra ngầm và mượt mà, không làm gián đoạn trải nghiệm của người chơi. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Menu Quan hệ NPC (NPC Relationship Window), Giao diện Tương tác NPC trực tiếp (NPC Dialogue UI).

**Ghi chú:** Cần làm rõ với Game Design xem giới hạn tặng quà NPC có bị tính theo "số lượt mỗi ngày" (Daily Limit) hay không để thiết kế thêm cảnh báo giới hạn vào luồng E.

| Mã Use Case | UC06.1 |
| :---- | :---- |
| Tên Use Case | Xem danh sách & Mức cảm tình NPC |
| Mục đích | Cho phép người chơi theo dõi danh sách các NPC đã gặp, mức độ thân thiết hiện tại, thông tin sở thích quà tặng và tiến trình mở khóa câu chuyện của NPC.  |
| Mô tả | Người chơi mở giao diện Quan hệ NPC để xem tổng quan cấp độ cảm tình, thanh tiến trình điểm, các mốc phần thưởng chưa nhận và danh sách món đồ NPC yêu thích/ghét.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (NPC Relationship System, Database)  |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Thường xuyên trong quá trình trải nghiệm game  |

**Trigger**

Người chơi chọn biểu tượng "Sổ tay NPC" / "Quan hệ" từ Menu chính hoặc chuyển sang tab NPC trong giao diện Sổ tay. 

**Tiền điều kiện**  
Người chơi đã gặp và kích hoạt tương tác với ít nhất 01 NPC trong thế giới. 

**Hậu điều kiện**  
Toàn bộ thông số cảm tình và trạng thái phần thưởng của NPC được hiển thị chính xác lên giao diện. 

**Luồng chính**

1. Người chơi mở giao diện Quản lý Quan hệ NPC.  
2. Hệ thống truy xuất dữ liệu tiến trình cảm tình của toàn bộ NPC đã mở khóa.  
3. Hệ thống hiển thị danh sách NPC dạng thẻ/danh sách kèm theo Cấp độ thân thiết (VD: Bằng hữu, Tri kỷ, Thân thiết...).  
4. Người chơi nhấp chọn một NPC cụ thể để xem thông tin chi tiết.  
5. Hệ thống hiển thị mô hình/hình ảnh 2D-3D của NPC, Thanh tiến trình điểm cảm tình, Bảng sở thích quà tặng (Yêu thích / Ghét) và các mốc Truyện ký (Lore) đã mở khóa.  
6. Người chơi xem xong và đóng giao diện.  
     
   

**Luồng thay thế**

A1. Xem NPC chưa mở khóa (Chưa gặp):

* 1a. Người chơi chọn một NPC hiển thị dưới dạng bóng đen (Silhouette) hoặc có dấu chấm hỏi \[?\].  
* 1b. Hệ thống hiển thị manh mối/vùng đất để gặp NPC đó (VD: "Gặp tại Thành Cổ khi đạt cấp 15").

**Luồng ngoại lệ**  
E1. Không tải được dữ liệu NPC: Hệ thống hiển thị thông báo "Không thể tải dữ liệu mối quan hệ" và cho phép người chơi nhấn nút \[Thử lại\]. 

**Business Rule / Quy tắc nghiệp vụ**  
BR1: Danh sách NPC phải được phân loại theo khu vực, phe phái hoặc vai trò để người chơi dễ tra cứu.  
BR2: Các mốc điểm cảm tình cần thiết để tăng cấp thân thiết sẽ được thống nhất ở giai đoạn cân bằng Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** Không.

**Extend:** Không.

**Yêu cầu phi chức năng:** Giao diện tải thông tin NPC và chuyển đổi giữa các NPC phải diễn ra phản hồi tức thì, giữ hình ảnh đồ họa mượt mà. *(Tuân thủ ghi mức nguyên tắc)*

**Giao diện liên quan:** Giao diện Quan hệ NPC (NPC Relationship Window), Tab Chi tiết NPC, Khung hiển thị sở thích (Favorites Grid).

**Ghi chú:** Thống nhất với nhóm UI/UX xem sở thích quà tặng của NPC có hiển thị ngay từ đầu hay phải tự mò/thử nghiệm mới mở khóa biểu tượng sở thích.

| Mã Use Case | UC06.2 |
| :---- | :---- |
| Tên Use Case | Tương tác & Trò chuyện tăng cảm tình  |
| Mục đích | Cho phép người chơi gia tăng điểm thân thiết với NPC thông qua việc lựa chọn các câu thoại phù hợp hoặc thực hiện chức năng hỏi thăm (Greeting) hàng ngày.  |
| Mô tả | Trong quá trình giao tiếp với NPC, hệ thống sẽ đưa ra các lựa chọn hội thoại. Dựa vào việc người chơi chọn câu trả lời đúng sở thích/tính cách của NPC, hệ thống sẽ tính toán và cộng (hoặc trừ) điểm cảm tình tương ứng.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Dialogue System, Affection System)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Thường xuyên khi người chơi tương tác với NPC  |

**Trigger**  
Người chơi đang trong cuộc hội thoại với NPC và xuất hiện các tùy chọn câu trả lời (Dialogue Choices), hoặc bấm vào nút "Hỏi thăm/Trò chuyện" trên menu NPC. 

**Tiền điều kiện**  
Người chơi đã kích hoạt hội thoại thành công với NPC (Đã qua bước UC05.2); NPC có hỗ trợ hệ thống cảm tình. 

**Hậu điều kiện**  
Điểm thân thiết của NPC được cập nhật vào cơ sở dữ liệu hệ thống; UI hiển thị phản hồi trực quan về mức điểm thay đổi. 

**Luồng chính**

1. Người chơi tương tác với NPC và kích hoạt luồng hội thoại có yếu tố cảm tình.  
2. Hệ thống hiển thị các tùy chọn câu trả lời (Choices) trên màn hình.  
3. Người chơi đọc và chọn một câu trả lời.  
4. Hệ thống đối chiếu lựa chọn với kịch bản (Dialogue Tree) để lấy trọng số điểm cảm tình.  
5. Lựa chọn hợp ý NPC: Hệ thống cộng thêm điểm thân thiết vào tiến trình hiện tại.  
6. Hệ thống hiển thị hiệu ứng phản hồi (VD: Biểu tượng trái tim bay lên, dòng chữ thả nổi "+10 Hảo cảm", hoặc thay đổi nét mặt NPC).  
7. Cuộc hội thoại tiếp tục diễn biến theo nhánh đã chọn hoặc kết thúc.

**Luồng thay thế**  
A1. Lựa chọn sai / Không hợp ý:

* 1a. Người chơi chọn câu thoại đi ngược lại tính cách/sở thích của NPC.  
* 1b. Hệ thống cộng \+0 điểm (hoặc trừ điểm tùy theo Business Rule) và hiển thị phản hồi/hiệu ứng NPC không hài lòng.

A2. Trò chuyện nhanh / Hỏi thăm hàng ngày (Daily Greeting):

* 1a. Tại Menu tương tác ban đầu của NPC, người chơi chọn nút "Hỏi thăm".  
* 1b. NPC phát một câu thoại chào hỏi ngẫu nhiên.  
* 1c. Hệ thống tự động cộng một lượng nhỏ điểm thân thiết quy định cho lần hỏi thăm đầu tiên trong ngày.


**Luồng ngoại lệ**  
E1. Đạt giới hạn tương tác điểm trong ngày: Nếu trò chơi có giới hạn số lần tăng điểm mỗi ngày (Daily Limit), khi người chơi trò chuyện vượt quá số lần này \-\> Các tùy chọn hội thoại vẫn diễn ra bình thường nhưng hệ thống không cộng thêm điểm và không hiện hiệu ứng.  
E2. Điểm cảm tình bị kẹt ở mức tối đa chưa đột phá (Cap Level): Điểm đang đầy thanh nhưng người chơi chưa làm "Nhiệm vụ đột phá" hoặc nhận thưởng mốc (UC06.4) \-\> Hệ thống hiển thị thông báo "Cảm tình đã đạt giới hạn hiện tại" và số điểm dư ra sẽ không được tính (hoặc bị ẩn đi).

**Business Rule / Quy tắc nghiệp vụ:**  
BR1: Trọng số điểm cộng/trừ của từng câu thoại phải được cấu hình cố định trong hệ thống quản lý kịch bản (Dialogue Data).  
BR2: Cơ chế tính điểm tối đa mỗi ngày (Daily Cap) và việc có áp dụng hình phạt "trừ điểm" khi chọn sai hay không sẽ được thống nhất ở giai đoạn Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** Không (Hội thoại cốt lõi mượn nền tảng giao diện từ UC05.2). 

**Extend:** Không. 

**Yêu cầu phi chức năng:** Hiệu ứng hình ảnh và âm thanh khi tăng/giảm cảm tình (Visual & Audio Feedback) phải đồng bộ khớp với lúc người chơi bấm chọn, không che khuất phần chữ hội thoại tiếp theo. *(Tuân thủ ghi mức nguyên tắc)* 

**Giao diện liên quan:** Khung hộp thoại (Dialogue Box), Nút lựa chọn (Choice Buttons), Hiệu ứng UI thả nổi (Floating Text / VFX cảm xúc). 

**Ghi chú:** Cần làm rõ với đội Biên kịch (Writer) và Game Designer về việc: Những lựa chọn hội thoại đã chọn rồi có được chọn lại để "cày" điểm hay không, hay mỗi câu hỏi chỉ được tính điểm 1 lần duy nhất trong toàn bộ game. 

| Mã Use Case | UC06.3 |
| :---- | :---- |
| Tên Use Case | Tặng quà NPC  |
| Mục đích | Cho phép người chơi tiêu hao vật phẩm từ Túi đồ để tặng cho NPC, qua đó gia tăng nhanh điểm cảm tình dựa trên độ hiếm của quà và sở thích riêng của từng NPC.  |
| Mô tả | Người chơi mở giao diện tặng quà khi đang tương tác với NPC, chọn vật phẩm và số lượng muốn tặng. Hệ thống kiểm tra kho đồ, trừ vật phẩm, tính toán điểm số dựa trên hệ số sở thích (Thích/Ghét/Bình thường) và cộng điểm vào tiến trình cảm tình.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Inventory System, Affection System)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Thường xuyên khi người chơi tích lũy đủ vật phẩm  |

**Trigger:**  
Người chơi nhấn chọn nút "Tặng quà" (Gift) trên Menu tương tác của NPC. 

**Tiền điều kiện:**  
Người chơi đang trong trạng thái tương tác với NPC; Túi đồ của người chơi có ít nhất 01 vật phẩm được phân loại là "Có thể tặng" (Giftable). 

**Hậu điều kiện**  
Vật phẩm bị trừ khỏi Túi đồ; Điểm thân thiết của NPC được cập nhật; Lượt tặng quà trong ngày (nếu có) bị trừ đi 1\. 

**Luồng chính**

1. Người chơi chọn nút "Tặng quà" tại màn hình tương tác NPC.  
2. Hệ thống mở cửa sổ Tặng quà, hiển thị danh sách các vật phẩm khả dụng đang có trong Túi đồ của người chơi (dạng Mini-Inventory).  
3. Người chơi chọn một vật phẩm và xác định số lượng muốn tặng, sau đó nhấn nút "Tặng" (Confirm).  
4. Hệ thống kiểm tra số lượng vật phẩm trong kho để đảm bảo tính hợp lệ.  
5. Hệ thống trừ vật phẩm tương ứng trong Túi đồ người chơi.  
6. Hệ thống đối chiếu vật phẩm đó với Bảng sở thích (Gift Preference Table) của NPC để tính toán số điểm thân thiết nhận được.  
7. Hệ thống cộng điểm vào thanh tiến trình cảm tình hiện tại.  
8. Hệ thống phát hiệu ứng hình ảnh/âm thanh (VFX/SFX) tương ứng, NPC hiển thị hoạt ảnh nhận quà và phát câu thoại cảm ơn.

**Luồng thay thế**  
A1. Tặng quà "Trúng sở thích" (Favorite Gift):

* 1a. Người chơi chọn đúng vật phẩm nằm trong danh mục "Đặc biệt yêu thích" của NPC.  
* 1b. Hệ thống áp dụng hệ số nhân (VD: x1.5 hoặc x2 điểm) so với vật phẩm thông thường.  
* 1c. NPC phát hoạt ảnh đặc biệt (VD: Mắt sáng lên, thả tim lớn) và câu thoại thể hiện sự vui mừng tột độ.

A2. Tặng quà bị ghét (Hated Gift):

* 1a. Người chơi tặng vật phẩm nằm trong danh sách "Ghét" của NPC.  
* 1b. Hệ thống chỉ cộng mức điểm tối thiểu (VD: \+1 điểm) hoặc trừ điểm cảm tình.  
* 1c. NPC hiển thị biểu cảm khó chịu/thất vọng và phát câu thoại từ chối khéo hoặc bực dọc.

**Luồng ngoại lệ:**  
E1. Hết lượt tặng quà trong ngày (Daily Limit Reached): Hệ thống hiển thị thông báo "Đã đạt giới hạn tặng quà hôm nay. Hãy quay lại vào ngày mai\!" và làm mờ (disable) nút Tặng quà.  
E2. Số lượng vật phẩm không hợp lệ: Người chơi nhập số lượng tặng lớn hơn số lượng đang có trong túi \-\> Hệ thống tự động đẩy giá trị về mức tối đa đang sở hữu (Max) hoặc báo lỗi "Không đủ vật phẩm".

**Business Rule / Quy tắc nghiệp vụ:**  
BR1: Điểm cảm tình đầu ra luôn bằng: \[Điểm gốc của vật phẩm (theo độ hiếm)\] x \[Hệ số sở thích của NPC\].  
BR2: Giới hạn số lượt tặng quà tối đa cho một NPC trong ngày và danh sách vật phẩm yêu thích/ghét của từng NPC sẽ được chốt tại tài liệu Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** UC06.1 (Xem danh sách & Mức cảm tình \- để hệ thống tự động cập nhật lại thanh UI điểm số sau khi tặng). 

**Extend:** Không. 

**Yêu cầu phi chức năng:** Giao diện chọn quà cần có bộ lọc (Filter) tự động đưa các vật phẩm NPC thích lên đầu danh sách để tối ưu trải nghiệm (UX). *(Tuân thủ ghi mức nguyên tắc)* 

**Giao diện liên quan:** Cửa sổ Tặng quà (Gift Window), Kho đồ thu nhỏ (Mini-Inventory), Khung phản hồi cảm xúc của NPC. 

**Ghi chú:** Cần thống nhất với Game Designer về Luồng A2: Liệu tặng quà sai sở thích có bị trừ điểm trực tiếp (gây ức chế cho người chơi) hay chỉ đơn giản là tăng rất ít điểm? 

| Mã Use Case | UC06.4  |
| :---- | :---- |
| Tên Use Case | Mở khóa Truyện ký & Phần thưởng NPC  |
| Mục đích | Cho phép người chơi nhận các phần thưởng đặc biệt (Vật phẩm, Danh hiệu, Kỹ năng bị động) và mở khóa các chương cốt truyện riêng (Truyện ký / Lore) khi đạt các mốc cảm tình quy định.  |
| Mô tả | Khi thanh tiến trình cảm tình của NPC đầy và đạt đến một mốc cấp độ mới (VD: Cấp 2, Cấp 3...), hệ thống sẽ hiển thị thông báo. Người chơi truy cập vào giao diện phần thưởng để đọc Truyện ký và nhấn nhận quà mốc.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Reward System, Lore/Quest System)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Không thường xuyên (Chỉ xảy ra khi người chơi "cày" đủ điểm lên cấp/mốc mới)  |

**Trigger**  
Điểm cảm tình của NPC đạt đủ số lượng yêu cầu để thăng cấp/đạt mốc mới. 

**Tiền điều kiện:**  
Điểm thân thiết của NPC đã chạm ngưỡng mốc nhận thưởng; Người chơi đang mở giao diện Quan hệ NPC hoặc đang trò chuyện trực tiếp với NPC đó. 

**Hậu điều kiện:**  
Cấp độ thân thiết của NPC tăng lên; Truyện ký được mở khóa trong Sổ tay; Vật phẩm thưởng được thêm vào Túi đồ người chơi. 

**Luồng chính:**

1. Điểm thân thiết của NPC vượt qua ngưỡng quy định (Thực hiện thông qua kết quả của UC06.2 hoặc UC06.3).  
2. Hệ thống hiển thị biểu tượng thông báo (Chấm đỏ / Dấu chấm than) tại biểu tượng của NPC đó trong Sổ tay Quan hệ.  
3. Người chơi mở giao diện Quan hệ NPC và chọn tab "Phần thưởng / Truyện ký".  
4. Hệ thống hiển thị danh sách các mốc phần thưởng, trong đó mốc mới đạt được sẽ sáng lên với nút "Nhận" (Claim).  
5. Người chơi nhấn "Nhận".  
6. Hệ thống cộng vật phẩm thưởng vào Túi đồ, kích hoạt Danh hiệu/Kỹ năng tương ứng (nếu có).  
7. Hệ thống hiển thị hiệu ứng chúc mừng thăng cấp thân thiết (VD: "Đạt mức: Tri kỷ") và đổi trạng thái nút thành "Đã nhận".

**Luồng thay thế:**  
A1. Mở khóa và xem Truyện ký (Lore Unlocking):

* 1a. Người chơi nhấn vào mục "Tiểu sử" hoặc "Truyện ký" đã được mở khóa ở mốc cảm tình tương ứng.  
* 1b. Hệ thống hiển thị giao diện đọc cốt truyện riêng của NPC (văn bản) hoặc phát một đoạn cắt cảnh (Cutscene) ngắn.

A2. Kích hoạt Nhiệm vụ Đột phá (Breakthrough Quest):

* 1a. Tại một số mốc quan trọng (VD: Từ Cấp 3 lên Cấp 4), thay vì nhận quà trực tiếp, hệ thống yêu cầu người chơi phải hoàn thành một Nhiệm vụ ẩn.  
* 1b. Nút "Nhận" được thay bằng nút "Nhận nhiệm vụ". Người chơi nhấn vào để tự động thêm Nhiệm vụ riêng của NPC vào Nhật ký nhiệm vụ (Quest Log).

**Luồng ngoại lệ:**  
E1. Túi đồ đã đầy khi nhận thưởng: Hệ thống hiển thị thông báo "Túi đồ đã đầy. Vui lòng dọn dẹp trước khi nhận thưởng" và giữ nguyên trạng thái nút "Nhận".  
E2. Chưa xem Truyện ký bắt buộc: Nếu Game Design bắt buộc người chơi phải xem xong đoạn hội thoại cốt truyện mới được thăng cấp \-\> Hệ thống khóa nút nhận thưởng và hiển thị thông báo "Yêu cầu hoàn thành Truyện ký Chương X".

**Business Rule / Quy tắc nghiệp vụ:**  
BR1: Mỗi mốc phần thưởng cảm tình của một NPC chỉ được nhận duy nhất 01 lần trên mỗi tài khoản/nhân vật.  
BR2: Các loại phần thưởng (Buff chỉ số, Vật phẩm độc quyền) và nội dung Truyện ký sẽ được quy định chi tiết trong file kịch bản của Game Design. *(Tuân thủ quy tắc chuẩn hóa)*

**Include:** Không. 

**Extend:** Không.

**Yêu cầu phi chức năng:** Đảm bảo hệ thống lưu trữ (Save Data) ghi nhận ngay lập tức trạng thái "Đã nhận quà" để tránh rủi ro người chơi lợi dụng lỗi mạng (dupe) nhận quà nhiều lần. *(Tuân thủ ghi mức nguyên tắc)* 

**Giao diện liên quan:** Tab Phần thưởng Cảm tình, Khung đọc Truyện ký (Lore Reader), Pop-up nhận vật phẩm (Reward Popup). 

**Ghi chú:** Đội kỹ thuật cần chuẩn bị sẵn cơ sở dữ liệu để lưu trữ biến trạng thái phần thưởng (0: Chưa đạt, 1: Có thể nhận, 2: Đã nhận) cho từng NPC tương ứng với từng người chơi. 

**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC07 | Quest (Nhiệm vụ)  | Tổng quát |
| UC07.1 | Quản lý Nhật ký nhiệm vụ (Quest Log)  | Được UC07 gọi; xem danh sách, phân loại và theo dõi (track) nhiệm vụ  |
| UC07.2 | Tiếp nhận nhiệm vụ  | Được UC07 gọi; tương tác với NPC hoặc Bảng thông báo để nhận nhiệm vụ mới  |
| UC07.3 | Cập nhật tiến trình nhiệm vụ  | Được UC07 gọi; hệ thống tự động ghi nhận số lượng quái hạ gục, vật phẩm thu thập  |
| UC07.4 | Trả nhiệm vụ & Nhận thưởng  | Được UC07 gọi; báo cáo hoàn thành cho NPC và nhận vật phẩm/EXP  |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC07 Quest (Nhiệm vụ)  | UC07.1, UC07.2, UC07.3, UC07.4  | Không  | Use Case cấp module quản lý vòng đời Quest  |
| UC07.1 Quản lý Nhật ký nhiệm vụ  | Không | Không  | Giao diện cốt lõi (UI) để tra cứu nhiệm vụ  |
| UC07.2 Tiếp nhận nhiệm vụ  | UC05.2   | Không  | Kế thừa cơ chế Tương tác NPC (UC05.2) để nhận việc  |
| UC07.3 Cập nhật tiến trình nhiệm vụ  | Không  | Không  | Luồng xử lý ngầm (Background) khi người chơi action  |
| UC07.4 Trả nhiệm vụ & Nhận thưởng  | UC05.2  | Không  | Kế thừa cơ chế Tương tác NPC (UC05.2) để trả việc  |

**Đặc tả UC07**

| Mã Use Case |  |
| :---- | :---- |
| Tên Use Case | Quest (Nhiệm vụ)  |
| Mục đích | Quản lý toàn bộ vòng đời của các nhiệm vụ trong game, từ định hướng mục tiêu, cung cấp thử thách cho đến khi hoàn thành và trao thưởng.  |
| Mô tả | Use Case tổng quát điều phối hệ thống Quest, bao gồm việc phân loại nhiệm vụ (Chính tuyến, Phụ tuyến, Hàng ngày, Sự kiện), quản lý giao diện theo dõi và tính toán tiến trình thực hiện của người chơi.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Quest Engine, Reward System)  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Liên tục xuyên suốt quá trình trải nghiệm game  |

Trigger  
Người chơi tương tác với NPC có biểu tượng giao nhiệm vụ (\! / ?) hoặc mở giao diện Nhật ký nhiệm vụ (Quest Log).   
Tiền điều kiện  
Nhân vật đã khởi tạo thành công; Cấp độ nhân vật hoặc tiến trình cốt truyện đạt đủ điều kiện mở khóa nhiệm vụ tương ứng.   
Hậu điều kiện  
Trạng thái của nhiệm vụ (Chưa nhận, Đang làm, Đã hoàn thành, Thất bại) được lưu đồng bộ vào cơ sở dữ liệu của người chơi.   
Luồng chính

1. Người chơi mở Nhật ký nhiệm vụ để kiểm tra các nhiệm vụ đang có hoặc nhiệm vụ có thể nhận (Thực hiện **UC07.1: Quản lý Nhật ký nhiệm vụ**).  
2. Người chơi di chuyển đến vị trí NPC / Bảng thông báo và tiến hành nhận nhiệm vụ mới (Thực hiện **UC07.2: Tiếp nhận nhiệm vụ**).  
3. Người chơi thực hiện các hành động theo yêu cầu (Đánh quái, Thu thập, Giải đố, Nói chuyện); hệ thống liên tục ghi nhận và hiển thị tiến độ (Thực hiện **UC07.3: Cập nhật tiến trình nhiệm vụ**).  
4. Khi tiến trình đạt 100%, người chơi quay lại gặp NPC chỉ định để báo cáo và nhận thưởng (Thực hiện **UC07.4: Trả nhiệm vụ & Nhận thưởng**).  
5. Hệ thống đóng nhiệm vụ, chuyển trạng thái sang "Đã hoàn thành" và mở khóa chuỗi nhiệm vụ tiếp theo (nếu có).

Luồng thay thế  
**A1. Hủy / Từ bỏ nhiệm vụ (Abandon Quest):**

* 1a. Người chơi mở Nhật ký nhiệm vụ, chọn một nhiệm vụ Phụ hoặc Hàng ngày đang làm dở.  
* 1b. Người chơi nhấn "Từ bỏ".  
* 1c. Hệ thống xóa tiến trình hiện tại, trả nhiệm vụ về trạng thái "Chưa nhận" tại NPC gốc.

**A2. Tự động trả nhiệm vụ (Auto-Complete):**

* 1a. Với một số nhiệm vụ hệ thống (như đạt cấp X, cường hóa vũ khí), ngay khi thỏa mãn điều kiện, hệ thống tự động đẩy thông báo.  
* 1b. Người chơi bấm "Nhận thưởng" trực tiếp trên giao diện UI mà không cần chạy đi tìm NPC.

Luồng ngoại lệ  
**E1. Xung đột nhiệm vụ (Quest Conflict):** NPC cần trả nhiệm vụ đang bị điều động bởi một sự kiện/cốt truyện khác \-\> Hệ thống tạm khóa biểu tượng trả nhiệm vụ và hiển thị thông báo "NPC đang bận ở một sự kiện khác".  
**E2. Thất bại nhiệm vụ (Quest Failed):** Người chơi thực hiện nhiệm vụ có giới hạn thời gian (Time-attack) hoặc bảo vệ mục tiêu nhưng hết giờ/mục tiêu chết \-\> Hệ thống đánh dấu nhiệm vụ Thất bại và yêu cầu nhận lại từ đầu.

Business Rule / Quy tắc nghiệp vụ

* **BR1:** Phân cấp bắt buộc: Tuyệt đối không cho phép "Từ bỏ" (Abandon) các Nhiệm vụ Chính tuyến (Main Quest).  
* **BR2:** Các loại tài nguyên nhiệm vụ (Quest Items) không chiếm ô đồ trong Túi đồ thông thường hoặc không thể vứt/bán. *(Tuân thủ quy tắc chuẩn hóa)*


Include  
**UC07.1** (Quản lý Nhật ký), **UC07.2** (Tiếp nhận), **UC07.3** (Cập nhật tiến trình), **UC07.4** (Trả nhiệm vụ).   
Extend  
Không.  
Yêu cầu phi chức năng  
Cơ chế theo dõi tiến trình (Tracker) trên màn hình chính phải cập nhật mượt mà theo thời gian thực (Real-time) ngay khi quái vật vừa nằm xuống, không có độ trễ. *(Tuân thủ ghi mức nguyên tắc)*   
Giao diện liên quan  
Giao diện Nhật ký nhiệm vụ (Quest Log UI), HUD Tracker (Bảng theo dõi góc màn hình), Biểu tượng trên đầu NPC (\! / ?).   
Ghi chú  
Thống nhất với Art và UI/UX về quy chuẩn màu sắc biểu tượng Quest: VD: Vàng \= Chính tuyến, Xanh dương \= Phụ tuyến, Tím \= Sự kiện/Hàng ngày. 

| Mã Use Case | UC07. |
| :---- | :---- |
| Tên Use Case | Quản lý Nhật ký nhiệm vụ (Quest Log)  |
| Mục đích | Cung cấp giao diện tập trung để người chơi tra cứu, phân loại, đọc chi tiết cốt truyện và quản lý việc hiển thị theo dõi (tracking) các nhiệm vụ đang thực hiện.  |
| Mô tả | Người chơi mở Nhật ký nhiệm vụ để xem danh sách toàn bộ quest. Giao diện chia thành các tab (Đang làm, Đã hoàn thành) và phân loại theo tính chất (Chính, Phụ, Sự kiện). Người chơi có thể đọc mục tiêu chi tiết, xem phần thưởng và bật/tắt theo dõi nhiệm vụ ra màn hình chính.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Quest UI System, Database)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Rất thường xuyên  |

**Trigger:**  
**Người chơi nhấn phím tắt mở nhiệm vụ (VD: phím J / phím Q) hoặc nhấp vào biểu tượng "Nhiệm vụ" trên Menu hệ thống / HUD.** 

**Tiền điều kiện:**  
**Người chơi đang ở trong trò chơi và không ở trong các trạng thái khóa giao diện (như đang xem Cutscene cốt truyện).** 

**Hậu điều kiện:**  
**Trạng thái bật/tắt theo dõi nhiệm vụ (Track/Untrack) được hệ thống ghi nhận và đồng bộ ngay lập tức ra bảng HUD trên màn hình chính.** 

**Luồng chính:**

1. **Người chơi thao tác mở Nhật ký nhiệm vụ.**  
2. **Hệ thống tải dữ liệu hiện tại và hiển thị giao diện Quest Log, mặc định mở ở tab "Nhiệm vụ đang làm" (Active Quests).**  
3. **Hệ thống phân loại danh sách nhiệm vụ thành các nhóm sổ dọc (Tree-view) như: Chính tuyến, Phụ tuyến, Hàng ngày.**  
4. **Người chơi nhấp chọn một nhiệm vụ bất kỳ trong danh sách.**  
5. **Hệ thống hiển thị thông tin chi tiết ở khung bên cạnh, bao gồm:**  
* **Tên nhiệm vụ**  
* **Đoạn văn mô tả cốt truyện**  
* **Tiến trình mục tiêu cần làm (VD: Tiêu diệt quái 5/10)**  
* **Danh sách phần thưởng dự kiến (EXP, Vàng, Vật phẩm)**  
*   
6. **Người chơi đọc thông tin, sau đó đóng giao diện để tiếp tục chơi.**   
     
   

**Luồng thay thế:**  
**A1. Bật/Tắt theo dõi nhiệm vụ trên HUD (Quest Tracking):**

* **1a. Tại khung chi tiết nhiệm vụ hoặc trong danh sách, người chơi đánh dấu (tick) hoặc bỏ đánh dấu vào ô "Theo dõi" (Track).**  
* **1b. Hệ thống cập nhật (thêm hoặc bớt) nhiệm vụ đó khỏi Bảng theo dõi (HUD Quest Tracker) nằm ở góc màn hình.**

**A2. Xem lại nhiệm vụ đã hoàn thành:**

* **1a. Người chơi chuyển sang tab "Đã hoàn thành" (Completed / Archive).**  
* **1b. Hệ thống hiển thị danh sách các nhiệm vụ đã làm xong để người chơi có thể tra cứu lại cốt truyện (Lore) nếu cần.**

**A3. Từ bỏ nhiệm vụ (Abandon Quest):**

* **1a. Người chơi chọn một nhiệm vụ Phụ/Hàng ngày và nhấn nút "Từ bỏ".**  
* **1b. Hệ thống bật Pop-up xác nhận: "Bạn có chắc chắn muốn hủy nhiệm vụ này? Tiến trình sẽ bị xóa."**  
* **1c. Người chơi xác nhận \-\> Hệ thống xóa nhiệm vụ khỏi danh sách và đưa trạng thái quest về "Chưa nhận" tại NPC giao nhiệm vụ.**

**Luồng ngoại lệ:**  
**E1. Bảng theo dõi (HUD Tracker) đã đầy: Người chơi chọn "Theo dõi" một nhiệm vụ mới khi giới hạn ghim trên màn hình đã đạt mức tối đa (VD: 5 nhiệm vụ) \-\> Hệ thống hiển thị thông báo "Bảng theo dõi đã đầy" và tự động thay thế nhiệm vụ cũ nhất (hoặc yêu cầu người chơi tự bỏ theo dõi nhiệm vụ khác trước).**  
**E2. Mất kết nối khi tải dữ liệu Quest: Hệ thống hiển thị thông báo "Đang đồng bộ dữ liệu..." và tự động tải lại khi kết nối mạng ổn định.**

**Business Rule / Quy tắc nghiệp vụ:**  
**BR1: Nhiệm vụ Chính tuyến (Main Quest) luôn được hệ thống tự động ghim (Auto-track) ở vị trí ưu tiên cao nhất trên HUD và tuyệt đối không có nút "Từ bỏ" (Abandon).**  
**BR2: Số lượng nhiệm vụ tối đa được phép nhận cùng lúc trong Nhật ký và giới hạn hiển thị trên HUD Tracker sẽ do Game Design quy định. *(Tuân thủ quy tắc chuẩn hóa)***

**Include:**   
**Không.**   
**Extend:**  
**Không.**   
**Yêu cầu phi chức năng:**  
**Bố cục chia cửa sổ phải trực quan (thường là danh sách bên trái, chi tiết bên phải). Việc chuyển đổi tab hoặc mở rộng/thu gọn các nhóm nhiệm vụ (Expand/Collapse) cần phản hồi mượt mà không có độ trễ. *(Tuân thủ ghi mức nguyên tắc)***   
**Giao diện liên quan:**  
**Nhật ký nhiệm vụ (Quest Log UI), Bảng theo dõi mục tiêu (HUD Quest Tracker), Nút chức năng Track/Abandon.**   
**Ghi chú:**  
**Thống nhất với team UI về việc có tích hợp tính năng "Dẫn đường" (Navigation/Pathfinding) vào nút Track luôn không (ví dụ: bấm theo dõi thì xuất hiện luôn mũi tên chỉ đường dưới chân nhân vật).** 

| Mã Use Case | UC07.2 |
| :---- | :---- |
| Tên Use Case | Tiếp nhận nhiệm vụ  |
| Mục đích | Cho phép người chơi bắt đầu một chuỗi thử thách hoặc cốt truyện mới bằng cách nhận nhiệm vụ từ NPC, bảng thông báo hoặc kích hoạt qua vật phẩm.  |
| Mô tả | Người chơi tương tác với đối tượng giao nhiệm vụ (có biểu tượng chỉ thị). Sau khi trải qua đoạn hội thoại giới thiệu, màn hình chi tiết nhiệm vụ xuất hiện. Người chơi xác nhận "Nhận", hệ thống sẽ đẩy nhiệm vụ vào Nhật ký (Quest Log) và bắt đầu theo dõi.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Quest Engine, Dialogue System)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Thường xuyên trong suốt quá trình chơi  |

**Trigger:**  
Người chơi nhấn phím tương tác với NPC, Bảng thông báo, hoặc sử dụng một "Vật phẩm kích hoạt nhiệm vụ" (Quest Starter Item).   
**Tiền điều kiện:**  
Người chơi thỏa mãn các điều kiện mở khóa nhiệm vụ (đạt Cấp độ yêu cầu, đã hoàn thành nhiệm vụ tiền đề); Nhật ký nhiệm vụ (Quest Log) chưa đạt giới hạn số lượng tối đa.   
**Hậu điều kiện:**  
Nhiệm vụ được thêm vào Quest Log với trạng thái "Đang làm" (Active); Biểu tượng nhiệm vụ trên đầu NPC thay đổi hoặc biến mất.   
**Luồng chính:**

1. Người chơi di chuyển đến gần NPC hoặc thực thể có biểu tượng giao nhiệm vụ (VD: Dấu \! trên đầu).  
2. Người chơi kích hoạt tương tác (Thực hiện UC05.2: Tương tác với môi trường & NPC).  
3. Hệ thống khóa góc nhìn và hiển thị Khung đối thoại cốt truyện (Dialogue Box) giữa nhân vật và NPC.  
4. Sau khi kết thúc đoạn thoại, hệ thống hiển thị Cửa sổ Tiếp nhận nhiệm vụ, bao gồm:  
* Mô tả mục tiêu cần thực hiện.  
* Phần thưởng dự kiến (Kinh nghiệm, Vàng, Vật phẩm).  
5. Người chơi nhấn nút "Nhận nhiệm vụ" (Accept).  
6. Hệ thống thêm nhiệm vụ vào Quest Log (Thực hiện UC07.1 ngầm).  
7. Hệ thống phát âm thanh/hiệu ứng thông báo nhận nhiệm vụ thành công và tự động ghim (Track) mục tiêu lên HUD.  
8. Hệ thống cập nhật lại biểu tượng trên đầu NPC (VD: Từ dấu \! chuyển thành dấu ? xám \- biểu thị đang chờ hoàn thành).

**Luồng thay thế:**  
A1. Nhận từ Bảng thông báo (Bounty Board) hoặc Vật phẩm (Item):

* 1a. Người chơi tương tác với Bảng thông báo hoặc bấm "Sử dụng" vật phẩm nhiệm vụ trong Túi đồ.  
* 1b. Hệ thống bỏ qua bước hội thoại cốt truyện (Bước 3\) và hiển thị trực tiếp Cửa sổ Tiếp nhận nhiệm vụ.

A2. Tự động nhận nhiệm vụ (Auto-accept Quest):

* 1a. Khi người chơi bước vào một khu vực sự kiện (Trigger Zone) hoặc vừa báo cáo xong một Nhiệm vụ Chính tuyến trước đó.  
* 1b. Hệ thống tự động đẩy Nhiệm vụ tiếp theo vào Quest Log và bật hiển thị mục tiêu lên màn hình mà không cần thông qua bước tương tác xác nhận.

**Luồng ngoại lệ:**  
E1. Nhật ký nhiệm vụ đã đầy (Quest Log Full): Người chơi bấm "Nhận nhiệm vụ" \-\> Hệ thống từ chối thao tác, hiển thị thông báo "Nhật ký nhiệm vụ đã đầy, vui lòng hoàn thành hoặc từ bỏ các nhiệm vụ cũ" và giữ nguyên trạng thái chưa nhận của NPC.  
E2. Hủy nhận nhiệm vụ: Tại Bước 5, nếu người chơi bấm "Từ chối" (Decline) hoặc đóng cửa sổ \-\> Hệ thống ngắt tương tác, nhiệm vụ vẫn ở trạng thái khả dụng để có thể nhận lại sau.  
**Business Rule / Quy tắc nghiệp vụ:**  
BR1: Biểu tượng chỉ thị trên đầu NPC phải được đồng bộ chính xác với hệ thống phân loại Quest (VD: Dấu \! Vàng cho Chính tuyến, Dấu \! Xanh cho Phụ tuyến).  
BR2: Đối với nhiệm vụ có đếm ngược thời gian (Time-limited Quest), bộ đếm giờ (Timer) sẽ bắt đầu chạy ngay lập tức ở background từ thời điểm người chơi bấm nút "Nhận nhiệm vụ". *(Tuân thủ quy tắc chuẩn hóa)*  
**Include:** UC05.2 (Tương tác với môi trường & NPC).   
**Extend:** Không.   
**Yêu cầu phi chức năng:** Quá trình chuyển tiếp từ hộp thoại (Dialogue) sang cửa sổ nhận nhiệm vụ (Quest Window) cần diễn ra trơn tru, không có độ trễ gây kẹt phím. *(Tuân thủ ghi mức nguyên tắc)*   
**Giao diện liên quan:** Giao diện đối thoại NPC, Cửa sổ chấp nhận nhiệm vụ, Biểu tượng trạng thái NPC (\! / ?).   
**Ghi chú:** Cần thống nhất với Game Designer về Giới hạn số lượng nhiệm vụ tối đa (Max Active Quests) trong sổ tay để kích hoạt luồng ngoại lệ E1 (Thường là 20 hoặc 30 nhiệm vụ cùng lúc). 

| Mã Use Case | UC07.3 |
| :---- | :---- |
| Tên Use Case | Cập nhật tiến trình nhiệm vụ  |
| Mục đích | Tự động ghi nhận, cập nhật số lượng/trạng thái của các mục tiêu nhiệm vụ (đánh quái, thu thập, di chuyển, giải đố...) và phản hồi trực quan cho người chơi theo thời gian thực.  |
| Mô tả | Use Case xử lý ngầm. Khi người chơi thực hiện các hành động trong game, hệ thống Quest Engine đối chiếu hành động đó với danh sách nhiệm vụ đang kích hoạt. Nếu trùng khớp, hệ thống sẽ tăng chỉ số tiến độ, phát thông báo lên màn hình và thay đổi trạng thái nhiệm vụ khi hoàn tất.  |
| Actor | Chính: Hệ thống Game (Quest Engine, Event System)  Phụ: Người chơi  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Liên tục ngầm trong suốt quá trình trải nghiệm game  |

Trigger:  
Người chơi thực hiện một hành động khớp với yêu cầu của ít nhất 01 nhiệm vụ đang có trong Quest Log (VD: Tiêu diệt quái vật chỉ định, nhặt vật phẩm nhiệm vụ, bước vào vùng sự kiện, tương tác vật thể).   
Tiền điều kiện:  
Nhiệm vụ tương ứng đang ở trạng thái "Đang làm" (Active) trong Nhật ký nhiệm vụ; Mục tiêu đó chưa đạt số lượng tối đa.   
Hậu điều kiện:  
Tiến trình mục tiêu được cập nhật trong Database; Bảng HUD Tracker cập nhật số liệu mới; Trạng thái nhiệm vụ chuyển sang "Chờ trả" (Ready to Turn In) nếu đạt 100% mục tiêu.   
Luồng chính:

1. Người chơi thực hiện một hành động trong thế giới game (VD: Hạ gục 1 Quái vật A).  
2. Hệ thống Sự kiện (Event Engine) phát tín hiệu (Event Trigger) kèm theo tham số thông tin (Mã đối tượng, số lượng, tọa độ).  
3. Quest Engine tiếp nhận tín hiệu và quét danh sách các Nhiệm vụ đang làm (Active Quests) của người chơi.  
4. Hệ thống xác nhận hành động trùng khớp với yêu cầu mục tiêu của nhiệm vụ.  
5. Hệ thống tăng chỉ số tiến độ tương ứng (VD: Cập nhật từ 4/10 lên 5/10 quái vật).  
6. Hệ thống hiển thị thông báo ngắn (Toast Notification/Banner) trên màn hình và cập nhật số liệu mới lên Bảng theo dõi (HUD Quest Tracker).  
7. Hệ thống tự động đồng bộ tiến độ mới vào dữ liệu tài khoản người chơi.

Luồng thay thế:  
A1. Hoàn thành toàn bộ mục tiêu nhiệm vụ (Quest Objective Complete):

* 1a. Chỉ số tiến độ đạt mức tối đa yêu cầu (VD: 10/10 quái vật).  
* 1b. Quest Engine chuyển trạng thái nhiệm vụ từ "Đang làm" sang "Chờ trả" (Ready to Turn In).  
* 1c. Hệ thống phát hiệu ứng hình ảnh/âm thanh hoàn thành (VFX/SFX "Objective Complete") và cập nhật biểu tượng NPC nhận trả nhiệm vụ trên Minimap từ ? xám sang ? vàng.

A2. Cập nhật mục tiêu đếm ngược thời gian (Time-limited Objective):

* 1a. Với nhiệm vụ có giới hạn thời gian, bộ đếm ngược (Timer) chạy lùi liên tục ở background.  
* 1b. Hệ thống đồng bộ thời gian còn lại lên HUD Tracker từng giây.

Luồng ngoại lệ:  
E1. Hết thời gian thực hiện (Time Expired): Đồng hồ đếm ngược về 00:00 trước khi người chơi hoàn thành đủ mục tiêu \-\> Quest Engine đánh dấu nhiệm vụ "Thất bại" (Failed), phát thông báo cảnh báo và yêu cầu người chơi hủy hoặc nhận lại nhiệm vụ.  
E2. Mất vật phẩm nhiệm vụ / Nhân vật tử vong: Nhân vật bị đánh bại trong vùng thử thách hoặc làm mất vật phẩm nhiệm vụ cố định \-\> Hệ thống tạm dừng tiến độ hoặc trừ lùi chỉ số (nếu logic game quy định) và hiển thị cảnh báo hướng dẫn xử lý.  
Business Rule / Quy tắc nghiệp vụ:  
BR1: Chỉ các hành động phát sinh sau khi nhận nhiệm vụ mới được ghi nhận vào tiến độ (không tính dồn các hành động đã làm trước đó, trừ vật phẩm nhiệm vụ đặc thù có sẵn trong kho đồ).  
BR2: Quy tắc chia sẻ tiến độ khi tham gia Tổ đội (Party/Co-op) — ví dụ: toàn đội cùng được cộng điểm hay chỉ người tung đòn kết liễu (Last Hit) mới được cộng — sẽ được chốt chi tiết trong tài liệu Game Design. *(Tuân thủ quy tắc chuẩn hóa)*  
Include:   
Không.   
Extend:  
Không.   
Yêu cầu phi chức năng:  
Quá trình quét và cập nhật tiến độ ở Background phải dùng cơ chế Lập trình sự kiện (Event-driven), đảm bảo tuyệt đối không gây sụt giảm khung hình (Frame Drop) khi người chơi tiêu diệt nhiều quái vật cùng lúc (AOE). *(Tuân thủ ghi mức nguyên tắc)*   
Giao diện liên quan:  
Bảng theo dõi góc màn hình (HUD Quest Tracker), Pop-up thông báo tiến độ thả nổi (Quest Progress Toast), Biểu tượng chỉ thị trên Minimap.   
Ghi chú:  
Đội kỹ thuật lưu ý kết nối chặt chẽ giữa Quest Engine với hệ thống Inventory (Túi đồ) và Combat (Chiến đấu) để đảm bảo không bị sót tín hiệu Event khi nhặt đồ hoặc tiêu diệt mục tiêu. 

| Mã Use Case | UC07.4 |
| :---- | :---- |
| Tên Use Case | Trả nhiệm vụ & Nhận thưởng  |
| Mục đích | Cho phép người chơi báo cáo hoàn thành nhiệm vụ với NPC (hoặc hệ thống) để nhận các phần thưởng tương ứng, kết thúc chuỗi sự kiện và mở khóa nhiệm vụ tiếp theo.  |
| Mô tả | Khi tiến trình đạt 100%, người chơi đến gặp NPC trả nhiệm vụ (có biểu tượng đặc trưng). Sau khi xem đoạn đối thoại kết thúc, màn hình tổng kết phần thưởng hiện ra. Người chơi xác nhận, hệ thống cộng tài nguyên vào tài khoản, cập nhật kho đồ và lưu tiến trình hoàn thành.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống Game (Quest Engine, Reward & Inventory System)  |
| Mức ưu tiên | Cao  |
| Tần suất sử dụng | Thường xuyên trong suốt quá trình chơi  |

Trigger:  
Người chơi tương tác với NPC trả nhiệm vụ (thường có biểu tượng dấu ? màu vàng/sáng) hoặc bấm nút "Hoàn thành" trên giao diện hệ thống với các nhiệm vụ tự động.   
Tiền điều kiện:  
Nhiệm vụ đang ở trạng thái "Chờ trả" (Tiến độ mục tiêu đạt 100%); Túi đồ của người chơi phải còn đủ ô trống nếu phần thưởng có chứa vật phẩm.   
Hậu điều kiện:  
Nhiệm vụ được chuyển sang danh mục "Đã hoàn thành" trong Quest Log; Phần thưởng được phân bổ thành công cho nhân vật; Vật phẩm nhiệm vụ (Quest Item) bị thu hồi; Mở khóa nhiệm vụ chuỗi tiếp theo (nếu có).   
Luồng chính:

1. Người chơi di chuyển đến vị trí NPC trả nhiệm vụ theo chỉ dẫn trên bản đồ/HUD.  
2. Người chơi kích hoạt tương tác (Thực hiện UC05.2: Tương tác với môi trường & NPC).  
3. Hệ thống hiển thị Khung đối thoại cốt truyện, tóm tắt lại kết quả việc người chơi vừa thực hiện.  
4. Sau khi hội thoại kết thúc, hệ thống mở Cửa sổ Tổng kết phần thưởng (Quest Reward Window), hiển thị rõ số lượng EXP, Vàng và Vật phẩm nhận được.  
5. Người chơi bấm nút "Hoàn thành" (Complete).  
6. Hệ thống cộng trực tiếp chỉ số (EXP, Vàng) và đẩy vật phẩm phần thưởng vào Túi đồ của người chơi.  
7. Hệ thống tự động xóa bỏ các "Vật phẩm nhiệm vụ" (Quest Items) yêu cầu ra khỏi Túi đồ.  
8. Hệ thống chuyển trạng thái nhiệm vụ trong Quest Log (UC07.1) thành "Đã hoàn thành".  
9. Hệ thống phát hiệu ứng chúc mừng (VD: Chữ "Quest Cleared" rực rỡ trên màn hình) và tự động cập nhật biểu tượng NPC nếu có nhiệm vụ nối tiếp.

Luồng thay thế:  
A1. Trả nhiệm vụ từ xa / Tự động trả (Auto Turn-in):

* 1a. Đối với nhiệm vụ Hàng ngày/Sự kiện không yêu cầu gặp NPC, khi tiến độ đạt 100%, hệ thống tự động hiển thị Pop-up hoặc làm sáng nút "Nhận thưởng" ngay trên giao diện HUD/Sổ tay.  
* 1b. Người chơi bấm "Nhận thưởng" trực tiếp trên UI \-\> Hệ thống thực hiện cộng quà bỏ qua bước hội thoại.

A2. Lựa chọn một trong nhiều phần thưởng (Selectable Rewards):

* 1a. Tại Bước 4 của Luồng chính, màn hình phần thưởng hiển thị nhiều tùy chọn (VD: Cho phép chọn 1 trong 3 vũ khí phù hợp với Class nhân vật).  
* 1b. Nút "Hoàn thành" bị khóa mờ (Disable). Người chơi buộc phải nhấp chọn 1 món đồ.  
* 1c. Nút "Hoàn thành" sáng lên, người chơi xác nhận và hệ thống chỉ trao món đồ đã chọn.

Luồng ngoại lệ:  
E1. Túi đồ đã đầy (Inventory Full): Khi người chơi bấm nút "Hoàn thành" nhưng phần thưởng chứa vật phẩm vượt quá số ô trống hiện tại của Túi đồ \-\> Hệ thống chặn thao tác nhận thưởng, hiển thị thông báo cảnh báo "Túi đồ đã đầy, vui lòng dọn dẹp trước khi nhận thưởng" và giữ nguyên trạng thái đối thoại của NPC.  
E2. Bị gián đoạn khi đang trả nhiệm vụ: Đang ở màn hình nhận thưởng thì nhân vật bị quái vật tấn công hoặc người chơi bấm phím Esc để đóng \-\> Hệ thống hủy tiến trình trả nhiệm vụ hiện tại. Nhiệm vụ vẫn giữ nguyên trạng thái "Chờ trả" để người chơi tương tác lại sau.  
Business Rule / Quy tắc nghiệp vụ:  
BR1: Lượng EXP, Vàng, và danh sách Item phần thưởng bắt buộc phải được ánh xạ chính xác từ bảng dữ liệu Cấu hình Nhiệm vụ (Quest Data Table) của Game Design để ngăn chặn hack/cheat thay đổi phần thưởng ở Client.  
BR2: Các nhiệm vụ có cơ chế "Thưởng theo thời gian hoàn thành" hoặc "Thưởng theo đánh giá" sẽ có thuật toán tính toán điểm thưởng riêng được quy định trong tài liệu Game Design. *(Tuân thủ quy tắc chuẩn hóa)*  
Include:   
UC05.2 (Tương tác với môi trường & NPC).   
Extend:  
Không.   
Yêu cầu phi chức năng:  
Cơ chế giao dịch ngầm (Transaction) ghi nhận dữ liệu hoàn thành quest và trao vật phẩm lên Server phải diễn ra nguyên tử (Atomic) – hoặc là thành công hết, hoặc là thất bại toàn bộ, tuyệt đối không được có độ trễ gây ra bug "Nhận đôi đồ" (Dupe Item). *(Tuân thủ ghi mức nguyên tắc)*   
Giao diện liên quan:  
Cửa sổ Tổng kết nhiệm vụ (Quest Complete UI), Pop-up chọn phần thưởng, Banner chúc mừng/Level Up.   
Ghi chú:  
Team Backend/Database cần lưu ý thiết lập hệ thống Ghi log (Log System) cho mọi sự kiện trả nhiệm vụ quan trọng nhằm đối soát dữ liệu khi có người chơi báo lỗi mất đồ hoặc cày cấp bất thường. 

| Mã Use Case | UC08 |
| :---- | :---- |
| Tên Use Case | Kinh doanh |
| Mục đích | Cho phép người chơi quản lý các hoạt động kinh doanh của cửa hàng/chi nhánh, từ mở rộng quy mô, mua nguyên liệu, sản xuất, định giá, quản lý tồn kho, thuê nhân viên, quảng cáo đến bán hàng.  |
| Mô tả | là nhóm chức năng kinh doanh. Người chơi sử dụng các chức năng con để vận hành cửa hàng và tạo doanh thu.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi mở menu/chức năng Kinh doanh.  
**Tiền điều kiện**

* Người chơi đã có dữ liệu phiên chơi hợp lệ.  
* Nhân vật/cửa hàng tồn tại theo thiết kế game.  
* Thông tin tiền, tài nguyên và trạng thái cửa hàng có thể đọc được.

**Hậu điều kiện**

* Trạng thái kinh doanh được hiển thị hoặc cập nhật theo chức năng được chọn.  
* Doanh thu, chi phí, tồn kho và các trạng thái liên quan được lưu khi thao tác thành công.

**Luồng chính**

1. Người chơi mở Kinh doanh.  
2. Hệ thống tải trạng thái cửa hàng/chi nhánh.  
3. Hệ thống hiển thị các chức năng kinh doanh.  
4. Người chơi chọn một chức năng.  
5. Hệ thống điều hướng đến Use Case tương ứng.  
6. Hệ thống cập nhật dữ liệu kinh doanh sau khi thao tác hoàn tất.

**Luồng thay thế**  
**A1 – Không đủ tiền/tài nguyên**

* Thông báo số lượng còn thiếu.  
* Không thực hiện giao dịch.

**A2 – Chưa mở chi nhánh**

* Hiển thị điều kiện mở chi nhánh.  
* Khóa chức năng phụ thuộc chi nhánh.

**Luồng ngoại lệ**  
Lỗi lưu dữ liệu kinh doanh: không làm mất trạng thái trước thao tác và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Mọi giao dịch phải kiểm tra tiền/tài nguyên trước khi thực hiện.  
* BR02: Không được tạo giao dịch vượt quá số lượng tồn kho.  
* BR03: Doanh thu và chi phí phải được cập nhật nhất quán.  
* BR04: Các hành động bị khóa phải có lý do/điều kiện rõ ràng.  
* BR05: Trạng thái kinh doanh phải được lưu sau giao dịch thành công.

**Include**  
Không  
**Extend**  
Không  
**Yêu cầu phi chức năng**  
Phản hồi giao dịch rõ ràng; dữ liệu tiền/tài nguyên phải nhất quán.  
**Giao diện liên quan**  
Menu Kinh doanh/Hệ thống kinh doanh.  
**Ghi Chú**  
Không.

| Mã Use Case | UC08.1 |
| :---- | :---- |
| Tên Use Case | Quản lý tồn kho |
| Mục đích | Cho phép người chơi theo dõi và quản lý số lượng nguyên liệu, sản phẩm và sức chứa kho.  |
| Mô tả | Người chơi xem tồn kho và thực hiện các thao tác được game cho phép như kiểm tra số lượng, sắp xếp hoặc xử lý hàng tồn.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi mở Quản lý tồn kho.  
**Tiền điều kiện**

* Có kho thuộc cửa hàng/chi nhánh.  
* Dữ liệu tồn kho đọc được.

**Hậu điều kiện**

* Trạng thái tồn kho được hiển thị hoặc cập nhật.  
* Dữ liệu tồn kho được lưu nếu có thay đổi.

**Luồng chính**

1. Người chơi mở kho.  
2. Hệ thống tải danh sách vật phẩm.  
3. Hệ thống hiển thị số lượng và sức chứa.  
4. Người chơi chọn thao tác.  
5. Hệ thống kiểm tra và cập nhật nếu cần.  
6. Hệ thống hiển thị kết quả.

**Luồng thay thế**  
**A1 – Kho đầy**

* Thông báo kho đầy.  
* Không nhận thêm nếu game không cho phép.

**A2 – Dữ liệu lỗi**

* Thông báo lỗi.  
* Không thực hiện cập nhật nguy hiểm.

**Luồng ngoại lệ**  
Lỗi cập nhật kho: giữ trạng thái an toàn gần nhất.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không vượt sức chứa kho.  
* BR02: Số lượng vật phẩm không âm.  
* BR03: Mọi giao dịch mua/sản xuất/bán phải phản ánh đúng tồn kho.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Tồn kho phải cập nhật nhất quán sau mọi giao dịch.  
**Giao diện liên quan**  
Màn hình Kho/Tồn kho.  
**Ghi Chú**  
Thuộc nhóm Quản lý sản xuất, đây là UC quan trọng để bảo vệ tính nhất quán dữ liệu kinh doanh.

| Mã Use Case | UC08.2 |
| :---- | :---- |
| Tên Use Case | Mua nguyên liệu |
| Mục đích | Cho phép người chơi mua nguyên liệu cần thiết cho hoạt động sản xuất.  |
| Mô tả | Người chơi chọn loại và số lượng nguyên liệu. Hệ thống kiểm tra tiền, sức chứa kho và điều kiện mua trước khi hoàn tất giao dịch.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Mua nguyên liệu.  
**Tiền điều kiện**

* Có cửa hàng/chi nhánh đủ điều kiện mua.  
* Kho có thể nhận thêm nguyên liệu hoặc có cơ chế nhập kho hợp lệ.  
* Đủ tiền.

**Hậu điều kiện**

* Tiền bị trừ và nguyên liệu được cộng vào kho nếu giao dịch thành công.  
* Không thay đổi nếu giao dịch thất bại.

**Luồng chính**

1. Người chơi chọn nguyên liệu.  
2. Hệ thống hiển thị giá và tồn kho.  
3. Người chơi nhập số lượng.  
4. Hệ thống kiểm tra tiền và sức chứa.  
5. Người chơi xác nhận.  
6. Hệ thống thực hiện giao dịch.  
7. Hệ thống cập nhật tiền và tồn kho.

**Luồng thay thế**  
**A1 – Thiếu tiền**

* Thông báo số tiền còn thiếu.  
* Không mua.

**A2 – Kho không đủ chỗ**

* Thông báo sức chứa.  
* Yêu cầu giảm số lượng hoặc nâng cấp kho.

**Luồng ngoại lệ**  
Lỗi giao dịch: không trừ tiền nếu nguyên liệu chưa được ghi nhận thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* **BR01: Số lượng mua phải lớn hơn 0\.**  
* **BR02: Không vượt sức chứa kho.**  
* **BR03: Giá mua được lấy từ dữ liệu hiện hành.**  
* **BR04: Tiền và nguyên liệu phải cập nhật đồng thời.**

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Không để xảy ra giao dịch trừ tiền nhưng không cộng nguyên liệu.  
**Giao diện liên quan**  
Màn hình Cửa hàng/Nhập nguyên liệu.  
**Ghi Chú**  
Thuộc nhóm Quản lý sản xuất, hoạt động độc lập và tùy theo BR.

| Mã Use Case | UC08.3 |
| :---- | :---- |
| Tên Use Case | Sản xuất |
| Mục đích | Cho phép người chơi sử dụng nguyên liệu để sản xuất sản phẩm kinh doanh.  |
| Mô tả | Người chơi chọn công thức/sản phẩm và số lượng. Hệ thống kiểm tra nguyên liệu, năng lực sản xuất và các điều kiện trước khi tạo sản phẩm.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Sản xuất.  
**Tiền điều kiện**

* Có chi nhánh/cơ sở sản xuất.  
* Có công thức sản phẩm hợp lệ.  
* Có đủ nguyên liệu.

**Hậu điều kiện**

* Nguyên liệu được trừ và sản phẩm được tạo/cộng vào kho.  
* Trạng thái sản xuất được cập nhật nếu game có thời gian sản xuất.

**Luồng chính**

1. Người chơi chọn sản phẩm.  
2. Hệ thống hiển thị nguyên liệu cần thiết.  
3. Người chơi chọn số lượng.  
4. Hệ thống kiểm tra nguyên liệu và điều kiện.  
5. Người chơi xác nhận.  
6. Hệ thống trừ nguyên liệu và tạo sản phẩm.  
7. Hệ thống cập nhật tồn kho/trạng thái sản xuất.

**Luồng thay thế**  
**A1 – Thiếu nguyên liệu**

* Thông báo nguyên liệu còn thiếu.  
* Không sản xuất.

**A2 – Không đủ công suất**

* Thông báo giới hạn sản xuất.  
* Điều chỉnh số lượng.

**Luồng ngoại lệ**  
Lỗi cập nhật sản xuất: không trừ nguyên liệu nếu sản phẩm chưa được tạo thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Công thức phải tồn tại.  
* BR02: Không sản xuất vượt số nguyên liệu/công suất.  
* BR03: Nguyên liệu chỉ bị trừ khi giao dịch hợp lệ.  
* BR04: Sản phẩm tạo ra phải được ghi nhận vào tồn kho/trạng thái sản xuất.

**Include**  
Include Kiểm tra nguyên liệu \-\> Quản lý tồn kho  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Không gây mất nguyên liệu khi thao tác thất bại.  
**Giao diện liên quan**  
Màn hình Sản xuất.  
**Ghi Chú**  
Thuộc nhóm Quản lý sản xuất, Include Kiểm tra nguyên liệu \-\> Quản lý tồn kho, để kiếm tra, quản lý cung cầu sản xuất hợp lý.

| Mã Use Case | UC08.4 |
| :---- | :---- |
| Tên Use Case | Kiểm tra nguyên liệu |
| Mục đích | Cho phép hệ thống kiểm tra số lượng và trạng thái nguyên liệu hiện có trong kho nhằm xác định người chơi có đủ nguyên liệu để thực hiện hoạt động sản xuất hoặc các hoạt động kinh doanh liên quan hay không.  |
| Mô tả | Khi người chơi thực hiện chức năng Sản xuất, hoặc truy cập các chức năng liên quan đến quản lý nguyên liệu, hệ thống sẽ kiểm tra số lượng nguyên liệu hiện có trong kho.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Thường xuyên sử dụng |

**Trigger**  
Người chơi thực hiện chức năng Sản xuất, hoặc các chức năng có liên quan để kiểm tra số lượng nguyên liệu.  
**Tiền điều kiện**

* Có nguyên liệu tồn tại trong hệ thống.  
* Người chơi đã có dữ liệu kinh doanh hợp lệ.   
* Dữ liệu tồn kho có thể truy cập.   
* Danh sách nguyên liệu cần kiểm tra đã được xác định. 

**Hậu điều kiện**

* Hệ thống xác nhận chính xác nguyên liệu  
* Kiểm tra kết quả và trả về Use Case gọi.

**Luồng chính**

1. Kích hoạt kiểm tra.  
2. Xác định nguyên liệu yêu cầu  
3. Kiểm tra hàng tồn kho  
4. Đối chiếu nguyên liệu  
5. Xác định kết quả  
6. Trả kết quả

**Luồng thay thế**  
**A1 – Không đủ nguyên liệu**

* Thông báo không đủ nguyên liệu.  
* Ngừng hành động

**A2 – Thiếu một loại nguyên liệu**

* Xác định nguyên liệu đang thiếu  
* Thông báo cho người chơi  
* Ngừng hoạt động

**A3 – Người chơi chưa có kho nguyên liệu** 

* Kho chưa được khởi tạo  
* Thông báo chưa có hoặc chưa mở khóa chức năng Quản lý kho  
* Không thực hiện kiểm tra

**A4 – Dữ liệu tồn kho thay đổi trong quá trình kiểm tra**

* Nhiều hoạt động tự động gây lỗi  
* Cập nhập lại dữ liệu nguyên liệu  
* Thực hiện kiểm tra lại trước khi xác nhận

**Luồng ngoại lệ**

* Không thể truy cập dữ liệu tồn kho: Thông báo lỗi, ngừng hoạt động   
* Dữ liệu nguyên liệu không hợp lệ: Không sử dụng dữ liệu lỗi, Ghi nhận lỗi, thông báo người chơi nếu cần, giữ trạng thái dữ liệu an toàn.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Kiểm tra trước khi sử dụng  
* BR02: Phải đủ tất cả nguyên liệu  
* BR03: Không được phép âm nguyên liệu  
* BR04: Kiểm tra chỉ xem chứ không được phép thay đổi dữ liệu  
* BR05: Dữ liệu phải được lấy từ trạng thái hiện tại

**Include**  
Include Quản lý tồn kho, kiểm tra số lượng nguyên liệu để phục vụ Sản xuất  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Hiệu suất nhanh chóng, tính chính xác cao, tính toàn vẹn dữ liệu và khả năng xử lí lỗi.  
**Giao diện liên quan**  
Không có giao diện riêng, được thực hiện trong giao diện Sản xuất hoặc giao diện Quản lý tồn kho  
**Ghi Chú**  
Thuộc nhóm Quản lý sản xuất, đây là UC phụ trợ, không phải là chức năng riêng để người chơi chọn, chỉ xem, kiểm tra chứ không được làm thay đổi dữ liệu.	

| Mã Use Case | UC08.5 |
| :---- | :---- |
| Tên Use Case | Định giá |
| Mục đích | Cho phép người chơi thiết lập hoặc điều chỉnh giá bán sản phẩm.  |
| Mô tả | Người chơi chọn sản phẩm và nhập giá. Hệ thống kiểm tra giới hạn/chiến lược giá theo luật game rồi cập nhật giá bán.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Định giá.  
**Tiền điều kiện**

* Sản phẩm tồn tại.  
* Người chơi có quyền định giá.  
* Dữ liệu sản phẩm hợp lệ.

**Hậu điều kiện**

* Giá bán mới được lưu nếu hợp lệ.  
* Giá cũ được giữ nếu thao tác thất bại.

**Luồng chính**

1. Người chơi chọn sản phẩm.  
2. Hệ thống hiển thị giá hiện tại.  
3. Người chơi nhập giá mới.  
4. Hệ thống kiểm tra giá.  
5. Người chơi xác nhận.  
6. Hệ thống lưu giá.  
7. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Giá không hợp lệ**

* Thông báo giới hạn.  
* Yêu cầu nhập lại.

**A2 – Hủy**

* Giữ giá cũ.

**Luồng ngoại lệ**  
Lỗi lưu giá: giữ giá cũ và thông báo lỗi.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Giá phải lớn hơn 0\.  
* BR02: Giá phải nằm trong giới hạn nếu game có giới hạn.  
* BR03: Giá mới chỉ áp dụng sau khi xác nhận/lưu thành công.

**Include**  
Include Bán hàng  
**Extend**  
Không xác định.  
**Yêu cầu phi chức năng**  
Giá phải được lưu nhất quán với sản phẩm.  
**Giao diện liên quan**  
Màn hình Định giá.  
**Ghi Chú**  
Thuộc nhóm Quản lý bán hàng, Định giá để Bán hàng.

| Mã Use Case | UC08.6 |
| :---- | :---- |
| Tên Use Case | Bán hàng |
| Mục đích | Cho phép người chơi bán sản phẩm cho khách hàng và tạo doanh thu.  |
| Mô tả | Người chơi thực hiện hoạt động bán sản phẩm. Hệ thống kiểm tra sản phẩm còn trong kho, giá bán và các điều kiện rồi cập nhật doanh thu và tồn kho.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Bán hàng hoặc game phát sinh lượt bán theo cơ chế gameplay.  
**Tiền điều kiện**

* Có sản phẩm có thể bán.  
* Sản phẩm còn trong tồn kho.  
* Giá bán hợp lệ.

**Hậu điều kiện**

* Sản phẩm được trừ khỏi tồn kho.  
* Tiền/doanh thu được cộng.  
* Thông tin giao dịch được ghi nhận.

**Luồng chính**

1. Người chơi mở Bán hàng.  
2. Hệ thống hiển thị sản phẩm và giá.  
3. Người chơi chọn sản phẩm/số lượng hoặc hệ thống xác định giao dịch.  
4. Hệ thống kiểm tra tồn kho.  
5. Hệ thống xác nhận giao dịch.  
6. Hệ thống trừ sản phẩm và cộng doanh thu.  
7. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Hết hàng**

* Thông báo hết hàng.  
* Không bán số lượng vượt tồn.

**A2 – Chi nhánh chưa hoạt động**

* Thông báo trạng thái.  
* Không thực hiện bán.

**Luồng ngoại lệ**  
Lỗi giao dịch: không được trừ hàng nếu doanh thu chưa được ghi nhận thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không bán vượt tồn kho.  
* BR02: Doanh thu \= giá bán × số lượng theo quy tắc game.  
* BR03: Tồn kho và tiền phải được cập nhật nhất quán.  
* BR04: Chỉ bán sản phẩm hợp lệ của chi nhánh.

**Include**   
Include với Quản lý tồn kho   
**Extend**  
Không xác định.  
**Yêu cầu phi chức năng**  
Thao tác bán phải đảm bảo tính toàn vẹn giao dịch.  
**Giao diện liên quan**  
Màn hình Bán hàng/Quầy bán hàng.  
**Ghi Chú**  
Thuộc nhóm Quản lý bán hàng, UC sẽ liên kết chặt chẽ với kiếm sát, dựa theo BR

| Mã Use Case | UC08.7 |
| :---- | :---- |
| Tên Use Case | Mở chi nhánh |
| Mục đích | Cho phép người chơi mở thêm một chi nhánh/cửa hàng kinh doanh khi đáp ứng điều kiện.  |
| Mô tả | Người chơi chọn khu vực/địa điểm hoặc yêu cầu mở chi nhánh. Hệ thống kiểm tra tiền, điều kiện và số lượng chi nhánh tối đa trước khi tạo chi nhánh.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Mở chi nhánh.  
**Tiền điều kiện**

* Người chơi sở hữu hệ thống kinh doanh hiện tại.  
* Đủ điều kiện mở chi nhánh theo luật game.  
* Đủ tiền/tài nguyên nếu có chi phí.

**Hậu điều kiện**

* Chi nhánh mới được tạo và lưu.  
* Tiền/tài nguyên được trừ nếu mở thành công.

**Luồng chính**

1. Người chơi chọn Mở chi nhánh.  
2. Hệ thống hiển thị điều kiện và chi phí.  
3. Người chơi chọn địa điểm/chi nhánh.  
4. Hệ thống kiểm tra điều kiện.  
5. Người chơi xác nhận.  
6. Hệ thống trừ chi phí và tạo chi nhánh.  
7. Hệ thống thông báo thành công và cập nhật danh sách chi nhánh.

**Luồng thay thế**  
**A1 – Không đủ tiền**

* Thông báo số tiền cần thiết.  
* Không mở chi nhánh.

**A2 – Đạt giới hạn chi nhánh**

* Thông báo đã đạt giới hạn.  
* Không thực hiện.

**A3 – Địa điểm không hợp lệ**

* Yêu cầu chọn địa điểm khác.

**Luồng ngoại lệ**  
Lỗi tạo/lưu chi nhánh: không trừ chi phí nếu giao dịch chưa thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Phải đáp ứng điều kiện mở chi nhánh.  
* BR02: Không vượt số lượng chi nhánh tối đa.  
* BR03: Chi phí chỉ được trừ khi mở thành công.  
* BR04: Chi nhánh mới phải có trạng thái khởi tạo hợp lệ.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Dữ liệu giao dịch phải toàn vẹn.  
**Giao diện liên quan**  
Màn hình Quản lý chi nhánh/Mở chi nhánh.  
**Ghi Chú**  
Thuộc nhóm Quản lý chi nhánh, hoạt động độc lập và theo BR

| Mã Use Case | UC08.8 |
| :---- | :---- |
| Tên Use Case | Thuê nhân viên |
| Mục đích | Cho phép người chơi tuyển nhân viên để hỗ trợ hoạt động kinh doanh.  |
| Mô tả | Người chơi xem danh sách nhân viên và lựa chọn nhân viên cần thuê. Hệ thống kiểm tra tiền, số lượng nhân viên tối đa và điều kiện liên quan.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Thuê nhân viên.  
**Tiền điều kiện**

* Có cửa hàng/chi nhánh.  
* Nhân viên có thể tuyển tồn tại trong dữ liệu.  
* Đủ tiền và điều kiện.

**Hậu điều kiện**

* Nhân viên được thêm vào cửa hàng/chi nhánh.  
* Tiền bị trừ nếu thuê thành công.

**Luồng chính**

1. Người chơi mở danh sách nhân viên.  
2. Hệ thống hiển thị thông tin và chi phí.  
3. Người chơi chọn nhân viên.  
4. Hệ thống kiểm tra điều kiện.  
5. Người chơi xác nhận.  
6. Hệ thống thêm nhân viên và trừ chi phí.  
7. Hệ thống cập nhật danh sách nhân viên.

**Luồng thay thế**  
**A1 – Thiếu tiền**

* Thông báo thiếu tiền.  
* Không thuê.

**A2 – Đạt giới hạn nhân viên**

* Thông báo giới hạn.  
* Không thuê.

**Luồng ngoại lệ**  
Lỗi giao dịch: không trừ tiền nếu nhân viên chưa được thêm thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không vượt giới hạn nhân viên.  
* BR02: Chi phí chỉ trừ khi thuê thành công.  
* BR03: Nhân viên phải được gán vào chi nhánh hợp lệ.  
* BR04: Nhân viên giỏi sẽ giúp doanh nghiệp phát triển mạnh

**Include**  
Không  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Không được tạo nhân viên trùng hoặc trừ tiền nhiều lần.  
**Giao diện liên quan**  
Màn hình Nhân viên/Tuyển dụng.  
**Ghi Chú**  
Thuộc nhóm Quản lý chi nhánh, hoạt động độc lập và nhân viên sẽ ảnh hưởng đến tốc độ kinh doanh của doanh nghiệp, được mô tả trong BR

| Mã Use Case | UC08.9 |
| :---- | :---- |
| Tên Use Case | Mở rộng cửa hàng |
| Mục đích | Cho phép người chơi tăng quy mô hoặc sức chứa của cửa hàng/chi nhánh.  |
| Mô tả | Người chơi lựa chọn hạng mục mở rộng. Hệ thống kiểm tra chi phí, điều kiện và giới hạn rồi cập nhật quy mô cửa hàng.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Mở rộng cửa hàng.  
**Tiền điều kiện**

* Có cửa hàng/chi nhánh cần mở rộng.  
* Đủ tiền/tài nguyên.  
* Đạt điều kiện mở rộng.

**Hậu điều kiện**

* Quy mô/capacity cửa hàng được tăng.  
* Chi phí được trừ nếu thành công.

**Luồng chính**

1. Người chơi chọn cửa hàng.  
2. Hệ thống hiển thị cấp hiện tại và lựa chọn mở rộng.  
3. Người chơi chọn hạng mục.  
4. Hệ thống kiểm tra điều kiện.  
5. Người chơi xác nhận.  
6. Hệ thống cập nhật quy mô và trừ chi phí.  
7. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Thiếu tiền**

* Thông báo thiếu tiền.  
* Không mở rộng.

**A2 – Đạt giới hạn**

* Thông báo mức tối đa.  
* Không thực hiện.

**Luồng ngoại lệ**  
Lỗi cập nhật: giữ quy mô cũ và không trừ tiền nếu thất bại.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Không vượt giới hạn mở rộng.  
* BR02: Chi phí chỉ trừ khi mở rộng thành công.  
* BR03: Quy mô mới phải được lưu.  
* BR04: Đủ điều kiện mới được mở rộng.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Không để cập nhật quy mô một phần.  
**Giao diện liên quan**  
Màn hình Nâng cấp/Mở rộng cửa hàng.  
**Ghi Chú**  
Thuộc nhóm Quản lý chi nhánh, được hoạt động theo BR

| Mã Use Case | UC08.10 |
| :---- | :---- |
| Tên Use Case | Quảng cáo |
| Mục đích | Cho phép người chơi thực hiện hoạt động quảng cáo để tăng khả năng tiếp cận/nhu cầu khách hàng theo cơ chế game.  |
| Mô tả | Người chơi chọn hình thức quảng cáo và ngân sách. Hệ thống kiểm tra chi phí và áp dụng hiệu quả quảng cáo.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Quảng cáo.  
**Tiền điều kiện**

* Có cửa hàng/chi nhánh hoạt động.  
* Đủ tiền nếu quảng cáo có chi phí.

**Hậu điều kiện**

* Chi phí được trừ và hiệu quả quảng cáo được cập nhật nếu thành công.  
* Không thay đổi nếu hủy/thất bại.

**Luồng chính**

1. Người chơi chọn hình thức quảng cáo.  
2. Hệ thống hiển thị chi phí và hiệu quả dự kiến.  
3. Người chơi chọn ngân sách/thời lượng.  
4. Hệ thống kiểm tra điều kiện.  
5. Người chơi xác nhận.  
6. Hệ thống thực hiện quảng cáo.  
7. Hệ thống cập nhật trạng thái và thông báo kết quả.

**Luồng thay thế**  
**A1 – Thiếu tiền**

* Thông báo thiếu tiền.  
* Không thực hiện quảng cáo.

**A2 – Chiến dịch đang chạy**

* Thông báo trạng thái.  
* Không tạo chiến dịch trùng nếu game không cho phép.

**Luồng ngoại lệ**  
Lỗi tạo chiến dịch: không trừ chi phí nếu chiến dịch không được tạo thành công.  
**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chi phí quảng cáo phải được kiểm tra trước khi thực hiện.  
* BR02: Hiệu quả quảng cáo phải tuân theo cơ chế game.  
* BR03: Không tạo chiến dịch trùng nếu có giới hạn.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**  
Thông tin chi phí và hiệu quả phải rõ ràng.  
**Giao diện liên quan**  
Màn hình Quảng cáo.  
**Ghi Chú**  
Thuộc nhóm Quản lý chi nhánh, tùy thuộc vào nhu cầu có muốn quảng cáo hay không, hoạt động theo BR

| Mã Use Case | UC09 |
| :---- | :---- |
| Tên Use Case | Inventory (Quản lý túi đồ) |
| Mục đích | Cho phép người chơi xem và quản lý các vật phẩm đang sở hữu trong túi đồ.  |
| Mô tả | Người chơi truy cập Inventory để xem danh sách vật phẩm và thực hiện các thao tác như sử dụng, bán, sắp xếp hoặc bỏ vật phẩm. Hệ thống kiểm tra điều kiện của từng thao tác và cập nhật dữ liệu túi đồ sau khi thực hiện thành công.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Túi đồ (Inventory).  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Dữ liệu túi đồ của người chơi đã được khởi tạo.  
* Người chơi có quyền truy cập chức năng Túi đồ.

**Hậu điều kiện**

* Thông tin túi đồ được hiển thị chính xác.  
* Dữ liệu vật phẩm được cập nhật nếu thao tác thành công.  
* Các thay đổi được lưu vào hệ thống.

**Luồng chính**

1. Người chơi chọn chức năng Túi đồ (Inventory).  
2. Hệ thống tải dữ liệu túi đồ của người chơi.  
3. Hệ thống hiển thị danh sách vật phẩm hiện có.  
4. Người chơi chọn vật phẩm hoặc chức năng quản lý.  
5. Hệ thống chuyển đến chức năng tương ứng.  
6. Người chơi thực hiện thao tác.  
7. Hệ thống kiểm tra điều kiện thực hiện.  
8. Hệ thống cập nhật dữ liệu túi đồ nếu thao tác thành công.  
9. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Túi đồ trống**

* Hệ thống thông báo túi đồ hiện không có vật phẩm.  
* Người chơi không thể chọn vật phẩm để thao tác.

**A2 – Người chơi hủy thao tác**

* Hệ thống hủy thao tác đang thực hiện.  
* Dữ liệu túi đồ được giữ nguyên.  
* Quay lại màn hình Túi đồ.

**Luồng ngoại lệ**  
**E1 – Lỗi tải dữ liệu túi đồ**

* Hệ thống thông báo không thể tải dữ liệu.  
* Không thực hiện thay đổi dữ liệu.

**E2 – Lỗi cập nhật dữ liệu**

* Hệ thống giữ nguyên dữ liệu trước khi cập nhật.  
* Hệ thống thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Người chơi chỉ được thao tác với vật phẩm đang sở hữu.  
* BR02: Số lượng vật phẩm không được nhỏ hơn 0\.  
* BR03: Dữ liệu túi đồ chỉ được cập nhật khi thao tác thành công.  
* BR04: Nếu thao tác thất bại, dữ liệu phải được giữ nguyên.  
* BR05: Mọi thay đổi vật phẩm phải được lưu đồng bộ.

**Include**  
UC09.1 – Sử dụng vật phẩm; UC09.2 – Xem túi đồ; UC09.3 – Bán vật phẩm; UC09.4 – Sắp xếp túi đồ; UC09.5 – Bỏ vật phẩm.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thông tin túi đồ phải được tải và hiể	n thị chính xác.  
* Không được xảy ra mất hoặc nhân bản vật phẩm khi cập nhật.  
* Hệ thống phải phản hồi rõ ràng khi thao tác thành công hoặc thất bại.

**Giao diện liên quan**  
Màn hình Túi đồ (Inventory); Màn hình Chi tiết vật phẩm; các màn hình thao tác vật phẩm.  
**Ghi Chú**  
UC09 là Use Case tổng quát của nhóm Inventory, bao gồm các Use Case con UC09.1 đến UC09.5.

| Mã Use Case | UC09.1 |
| :---- | :---- |
| Tên Use Case | Sử dụng sản phẩm |
| Mục đích | Cho phép người chơi sử dụng vật phẩm đang có trong túi đồ.  |
| Mô tả | Người chơi chọn một vật phẩm có thể sử dụng. Hệ thống kiểm tra số lượng và điều kiện sử dụng, sau đó áp dụng hiệu quả của vật phẩm và cập nhật lại số lượng.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Sử dụng vật phẩm.  
**Tiền điều kiện**

* Người chơi đang truy cập Túi đồ.  
* Vật phẩm được chọn đang tồn tại trong túi đồ.  
* Vật phẩm có thể sử dụng.  
* Số lượng vật phẩm lớn hơn 0\.

**Hậu điều kiện**

* Hiệu quả vật phẩm được áp dụng nếu sử dụng thành công.  
* Số lượng vật phẩm được giảm tương ứng.  
* Dữ liệu người chơi và túi đồ được cập nhật.

**Luồng chính**

1. Người chơi mở Túi đồ.  
2. Người chơi chọn vật phẩm cần sử dụng.  
3. Hệ thống hiển thị thông tin và hiệu quả của vật phẩm.  
4. Người chơi chọn Sử dụng.  
5. Hệ thống kiểm tra điều kiện sử dụng.  
6. Người chơi xác nhận sử dụng nếu cần.  
7. Hệ thống áp dụng hiệu quả vật phẩm.  
8. Hệ thống cập nhật số lượng vật phẩm.  
9. Hệ thống thông báo kết quả sử dụng.

**Luồng thay thế**  
**A1 – Vật phẩm không thể sử dụng**

* Hệ thống thông báo vật phẩm không hỗ trợ thao tác sử dụng.  
* Không thay đổi dữ liệu túi đồ.

**A2 – Số lượng vật phẩm bằng 0**

* Hệ thống thông báo không còn vật phẩm.  
* Không thực hiện sử dụng.

**A3 – Người chơi hủy**

* Hệ thống hủy thao tác.  
* Giữ nguyên trạng thái vật phẩm.

**Luồng ngoại lệ**  
**E1 – Lỗi áp dụng hiệu quả**

* Hệ thống không áp dụng hiệu quả vật phẩm.  
* Không giảm số lượng vật phẩm.  
* Thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ được sử dụng vật phẩm có trạng thái cho phép sử dụng.  
* BR02: Số lượng phải lớn hơn 0 trước khi sử dụng.  
* BR03: Mỗi lần sử dụng phải cập nhật đúng số lượng.  
* BR04: Chỉ giảm vật phẩm sau khi áp dụng hiệu quả thành công.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Không được giảm vật phẩm nếu hiệu quả chưa được áp dụng thành công.  
* Cập nhật số lượng phải đảm bảo tính nhất quán.

**Giao diện liên quan**  
Màn hình Túi đồ; Màn hình Chi tiết vật phẩm; Hộp thoại xác nhận sử dụng.  
**Ghi Chú**  
Áp dụng cho các vật phẩm có chức năng sử dụng trực tiếp.

| Mã Use Case | UC09.2 |
| :---- | :---- |
| Tên Use Case | Xem túi đồ |
| Mục đích | Cho phép người chơi xem danh sách và thông tin các vật phẩm đang sở hữu.  |
| Mô tả | Hệ thống tải và hiển thị các vật phẩm trong túi đồ, bao gồm thông tin cơ bản như tên, loại, số lượng và các thông tin liên quan.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Xem túi đồ.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Dữ liệu túi đồ đã được khởi tạo.

**Hậu điều kiện**

* Danh sách vật phẩm được hiển thị.  
* Không thay đổi dữ liệu túi đồ.

**Luồng chính**

1. Người chơi chọn chức năng Túi đồ.  
2. Hệ thống tải dữ liệu vật phẩm.  
3. Hệ thống kiểm tra trạng thái dữ liệu.  
4. Hệ thống hiển thị danh sách vật phẩm.  
5. Người chơi chọn một vật phẩm.  
6. Hệ thống hiển thị thông tin chi tiết của vật phẩm.

**Luồng thay thế**  
**A1 – Túi đồ trống**

* Hệ thống hiển thị thông báo Túi đồ trống.  
* Người chơi có thể quay lại màn hình trước.

**A2 – Không tìm thấy vật phẩm**

* Hệ thống thông báo vật phẩm không còn tồn tại.  
* Hệ thống tải lại dữ liệu túi đồ.

**Luồng ngoại lệ**  
**E1 – Lỗi tải dữ liệu**

* Hệ thống thông báo lỗi tải dữ liệu.  
* Cho phép người chơi thử tải lại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ hiển thị vật phẩm thuộc sở hữu của người chơi.  
* BR02: Thông tin hiển thị phải khớp với dữ liệu hiện tại.  
* BR03: Chức năng xem túi đồ không được tự ý thay đổi dữ liệu.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Dữ liệu hiển thị phải chính xác và dễ đọc.  
* Thời gian tải danh sách vật phẩm phải phù hợp với trải nghiệm người chơi.

**Giao diện liên quan**  
Màn hình Túi đồ; Màn hình Chi tiết vật phẩm.  
**Ghi Chú**  
Đây là chức năng nền tảng để người chơi thực hiện các thao tác khác trong UC09.

| Mã Use Case | UC09.3 |
| :---- | :---- |
| Tên Use Case | Bán vật phẩm |
| Mục đích | Cho phép người chơi bán vật phẩm trong túi đồ để nhận tiền hoặc tài nguyên theo quy định của trò chơi.  |
| Mô tả | Người chơi chọn vật phẩm có thể bán và số lượng muốn bán. Hệ thống kiểm tra điều kiện, tính giá trị nhận được, sau đó cập nhật số lượng vật phẩm và tài nguyên nếu giao dịch thành công.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Bán vật phẩm.  
**Tiền điều kiện**

* Người chơi đang truy cập Túi đồ.  
* Vật phẩm được chọn tồn tại trong túi đồ.  
* Vật phẩm được phép bán.  
* Số lượng bán hợp lệ.

**Hậu điều kiện**

* Số lượng vật phẩm được giảm tương ứng.  
* Người chơi nhận được tiền/tài nguyên theo giá bán.  
* Thông tin giao dịch được cập nhật.

**Luồng chính**

1. Người chơi chọn vật phẩm cần bán.  
2. Hệ thống hiển thị thông tin và giá trị bán.  
3. Người chơi nhập hoặc chọn số lượng cần bán.  
4. Hệ thống kiểm tra số lượng và điều kiện bán.  
5. Hệ thống hiển thị tổng giá trị nhận được.  
6. Người chơi xác nhận bán.  
7. Hệ thống cập nhật số lượng vật phẩm.  
8. Hệ thống cộng tiền/tài nguyên cho người chơi.  
9. Hệ thống thông báo giao dịch thành công.

**Luồng thay thế**  
**A1 – Số lượng bán không hợp lệ**

* Hệ thống thông báo số lượng không hợp lệ.  
* Người chơi nhập lại số lượng.

**A2 – Vật phẩm không thể bán**

* Hệ thống thông báo vật phẩm không được phép bán.  
* Không thực hiện giao dịch.

**A3 – Người chơi hủy giao dịch**

* Hệ thống hủy giao dịch.  
* Không thay đổi vật phẩm và tiền/tài nguyên.

**Luồng ngoại lệ**  
**E1 – Lỗi cập nhật giao dịch**

* Hệ thống hoàn tác hoặc giữ nguyên dữ liệu trước giao dịch.  
* Không được trừ vật phẩm nếu chưa cộng thành công tiền/tài nguyên.  
* Thông báo giao dịch thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ vật phẩm được phép bán mới có thể bán.  
* BR02: Số lượng bán phải lớn hơn 0 và không vượt quá số lượng sở hữu.  
* BR03: Giá trị nhận được phải tuân theo quy định của trò chơi.  
* BR04: Việc trừ vật phẩm và cộng tiền/tài nguyên phải được thực hiện nhất quán.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Giao dịch phải đảm bảo tính toàn vẹn dữ liệu.  
* Không được xảy ra trường hợp mất vật phẩm hoặc cộng tiền hai lần.

**Giao diện liên quan**  
Màn hình Túi đồ; Màn hình Bán vật phẩm; Hộp thoại xác nhận giao dịch.  
**Ghi Chú**  
Giá bán và loại tài nguyên nhận được phụ thuộc vào thiết kế kinh tế của trò chơi.

| Mã Use Case | UC09.4 |
| :---- | :---- |
| Tên Use Case | Sắp xếp vật phẩm |
| Mục đích | Cho phép người chơi thay đổi thứ tự hiển thị hoặc cách tổ chức vật phẩm trong túi đồ.  |
| Mô tả | Người chơi lựa chọn phương thức sắp xếp hoặc thực hiện thay đổi vị trí vật phẩm. Hệ thống cập nhật thứ tự hiển thị theo lựa chọn của người chơi.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Sắp xếp túi đồ.  
**Tiền điều kiện**

* Người chơi đang truy cập Túi đồ.  
* Túi đồ có ít nhất một vật phẩm.

**Hậu điều kiện**

* Thứ tự hiển thị vật phẩm được cập nhật.  
* Dữ liệu vật phẩm không bị thay đổi về số lượng hoặc thuộc tính.

**Luồng chính**

1. Người chơi mở Túi đồ.  
2. Người chơi chọn chức năng Sắp xếp.  
3. Hệ thống hiển thị các phương thức sắp xếp.  
4. Người chơi chọn phương thức hoặc thứ tự mong muốn.  
5. Hệ thống thực hiện sắp xếp vật phẩm.  
6. Hệ thống cập nhật giao diện Túi đồ.  
7. Hệ thống lưu tùy chọn sắp xếp nếu chức năng hỗ trợ.

**Luồng thay thế**  
**A1 – Túi đồ trống**

* Hệ thống thông báo không có vật phẩm để sắp xếp.  
* Không thực hiện thao tác.

**A2 – Người chơi hủy**

* Hệ thống hủy thao tác sắp xếp.  
* Giữ nguyên thứ tự trước đó nếu chưa xác nhận lưu.

**Luồng ngoại lệ**  
**E1 – Lỗi lưu thứ tự**

* Hệ thống giữ hoặc khôi phục thứ tự trước đó.  
* Thông báo thao tác sắp xếp thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Sắp xếp không được làm thay đổi số lượng vật phẩm.  
* BR02: Sắp xếp không được làm thay đổi thuộc tính vật phẩm.  
* BR03: Thứ tự hiển thị phải tuân theo phương thức người chơi lựa chọn.

**Include**  
UC09.2 – Xem túi đồ.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thao tác sắp xếp phải phản hồi nhanh.  
* Không được làm mất hoặc thay đổi dữ liệu vật phẩm.

**Giao diện liên quan**  
Màn hình Túi đồ; Menu hoặc bộ lọc sắp xếp.  
**Ghi Chú**  
Có thể mở rộng thêm các phương thức như theo loại, số lượng, độ hiếm hoặc thứ tự nhận vật phẩm.

| Mã Use Case | UC09.5 |
| :---- | :---- |
| Tên Use Case | Bỏ vật phẩm |
| Mục đích | Cho phép người chơi loại bỏ vật phẩm không còn muốn giữ trong túi đồ.  |
| Mô tả | Người chơi chọn vật phẩm và số lượng cần bỏ. Hệ thống yêu cầu xác nhận, kiểm tra điều kiện và cập nhật lại số lượng vật phẩm sau khi thao tác thành công.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Bỏ vật phẩm.  
**Tiền điều kiện**

* Người chơi đang truy cập Túi đồ.  
* Vật phẩm được chọn tồn tại trong túi đồ.  
* Số lượng bỏ hợp lệ.

**Hậu điều kiện**

* Số lượng vật phẩm được giảm hoặc vật phẩm bị xóa khỏi túi đồ nếu số lượng bằng 0\.  
* Dữ liệu túi đồ được cập nhật.

**Luồng chính**

1. Người chơi chọn vật phẩm cần bỏ.  
2. Hệ thống hiển thị thông tin vật phẩm.  
3. Người chơi chọn số lượng cần bỏ.  
4. Hệ thống yêu cầu xác nhận thao tác.  
5. Người chơi xác nhận.  
6. Hệ thống kiểm tra điều kiện.  
7. Hệ thống giảm số lượng hoặc xóa vật phẩm khỏi túi đồ.  
8. Hệ thống cập nhật dữ liệu.  
9. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Số lượng bỏ không hợp lệ**

* Hệ thống thông báo số lượng không hợp lệ.  
* Người chơi nhập lại số lượng.

**A2 – Người chơi hủy xác nhận**

* Hệ thống hủy thao tác.  
* Dữ liệu túi đồ được giữ nguyên.

**A3 – Vật phẩm bị khóa**

* Hệ thống thông báo vật phẩm không thể bỏ.  
* Không thực hiện thao tác.

**Luồng ngoại lệ**  
**E1 – Lỗi cập nhật dữ liệu**

* Hệ thống giữ nguyên dữ liệu trước khi thực hiện.  
* Không xóa hoặc giảm một phần số lượng.  
* Thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Số lượng bỏ phải lớn hơn 0\.  
* BR02: Số lượng bỏ không được vượt quá số lượng đang sở hữu.  
* BR03: Vật phẩm bị khóa hoặc không cho phép bỏ không được loại bỏ.  
* BR04: Nếu số lượng vật phẩm bằng 0 sau thao tác, vật phẩm phải được xóa khỏi danh sách.  
* BR05: Chỉ cập nhật dữ liệu sau khi xác nhận thành công.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Cần có bước xác nhận để hạn chế xóa nhầm.  
* Không được xảy ra tình trạng xóa một phần khi cập nhật thất bại.

**Giao diện liên quan**  
Màn hình Túi đồ; Hộp thoại xác nhận bỏ vật phẩm.  
**Ghi Chú**  
Thao tác bỏ vật phẩm có thể không thể hoàn tác tùy theo thiết kế trò chơi.

| Mã Use Case | UC10 |
| :---- | :---- |
| Tên Use Case | Shop |
| Mục đích | Cho phép người chơi xem thông tin hàng hóa và thực hiện các giao dịch mua, bán vật phẩm phục vụ hoạt động kinh doanh, nhu cầu yếu phẩm |
| Mô tả | Người chơi truy cập Shop để xem danh sách hàng hóa, xem giá, so sánh giá giữa các nguồn cung cấp, mua vật phẩm hoặc bán vật phẩm đang sở hữu. Hệ thống kiểm tra tiền, số lượng, điều kiện mở khóa, tồn kho và các quy tắc giao dịch trước khi cập nhật dữ liệu.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu; thường xuyên khi kinh doanh |

**Trigger**  
Người chơi chọn chức năng Shop hoặc tương tác với NPC, quầy hàng, cửa hàng trực tuyến hay nhà cung cấp trong phạm vi.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi và đang ở trạng thái có thể tương tác.  
* Dữ liệu nhân vật, tiền VND và túi đồ đã được khởi tạo.  
* Cửa hàng hoặc nguồn cung cấp tương ứng đã được mở khóa.  
* Hệ thống có thể truy cập dữ liệu hàng hóa, giá và trạng thái giao dịch.

**Hậu điều kiện**

* Danh sách hàng hóa và giá được hiển thị đúng theo nguồn cung cấp.  
* Nếu giao dịch thành công, tiền, vật phẩm, tồn kho và lịch sử giao dịch được cập nhật.  
* Nếu giao dịch thất bại hoặc bị hủy, dữ liệu trước giao dịch được giữ nguyên.  
* Các thay đổi được lưu đồng bộ vào hệ thống.

**Luồng chính**

1. Người chơi mở Shop.  
2. Hệ thống xác định cửa hàng/nguồn cung cấp và tải danh sách hàng hóa.  
3. Hệ thống hiển thị tên vật phẩm, loại, giá, số lượng còn lại và thông tin liên quan.  
4. Người chơi chọn xem giá, so sánh giá, mua hoặc bán vật phẩm.  
5. Hệ thống chuyển đến Use Case con tương ứng.  
6. Người chơi thực hiện thao tác và xác nhận nếu cần.  
7. Hệ thống kiểm tra điều kiện giao dịch.  
8. Hệ thống cập nhật tiền, vật phẩm, tồn kho và dữ liệu liên quan nếu thao tác thành công.  
9. Hệ thống thông báo kết quả và hiển thị dữ liệu mới nhất.

**Luồng thay thế**  
**A1 – Không có hàng hóa phù hợp**

* Hệ thống thông báo cửa hàng hiện không có vật phẩm phù hợp hoặc vật phẩm đã hết hàng.  
* Người chơi có thể xem lại danh mục, chuyển nguồn cung cấp hoặc quay lại màn hình trước.

**A2 – Người chơi hủy giao dịch**

* Hệ thống đóng hộp thoại xác nhận.  
* Không thay đổi tiền, vật phẩm hoặc tồn kho.  
* Quay lại màn hình Shop.

**A3 – Người chơi chỉ xem giá/so sánh giá**

* Hệ thống hiển thị thông tin giá mà không tạo giao dịch.  
* Dữ liệu tiền và túi đồ không thay đổi.

**Luồng ngoại lệ**  
**E1 – Lỗi tải dữ liệu Shop**

* Hệ thống thông báo không thể tải dữ liệu cửa hàng.  
* Không cho phép thực hiện giao dịch trên dữ liệu chưa xác nhận.

**E2 – Không đủ tiền hoặc vật phẩm**

* Hệ thống thông báo điều kiện còn thiếu.  
* Giao dịch bị từ chối và dữ liệu giữ nguyên.

**E3 – Vật phẩm hết hàng/không còn hợp lệ**

* Hệ thống thông báo trạng thái mới nhất.  
* Yêu cầu người chơi chọn lại số lượng hoặc vật phẩm khác.

**E4 – Lỗi cập nhật hoặc lưu dữ liệu**

* Hệ thống hủy toàn bộ giao dịch đang xử lý.  
* Khôi phục trạng thái trước giao dịch và thông báo thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Người chơi chỉ được mua vật phẩm tại nguồn cung cấp đã mở khóa.  
* BR02: Giá mua và giá bán được xác định theo cửa hàng, thời điểm và trạng thái thị trường trong game.  
* BR03: Không được mua khi số tiền hiện có nhỏ hơn tổng tiền phải trả.  
* BR04: Không được bán vật phẩm không thuộc sở hữu của người chơi.  
* BR05: Số lượng vật phẩm và tiền không được nhỏ hơn 0\.  
* BR06: Giao dịch chỉ được cập nhật khi kiểm tra và lưu thành công.  
* BR07: Khi giao dịch thất bại, tiền, vật phẩm và tồn kho phải giữ nguyên.  
* BR08: Mọi thay đổi giao dịch phải được lưu đồng bộ, tránh mất hoặc nhân bản vật phẩm.  
* BR09: Một số cửa hàng, vật phẩm hoặc mức giá có thể yêu cầu tiến độ, uy tín hoặc khu vực đã mở khóa.

**Include**  
UC10.1 – Mua vật phẩm; UC10.2 – Bán vật phẩm; UC10.3 – Xem giá; UC10.4 – So sánh giá.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thông tin giá và tồn kho phải chính xác, nhất quán với dữ liệu máy chủ/trạng thái game.  
* Giao dịch phải có tính nguyên tử: hoặc cập nhật toàn bộ, hoặc không cập nhật gì.  
* Thời gian phản hồi thao tác xem Shop và xem giá nên ngắn, không làm gián đoạn gameplay.  
* Thông báo lỗi phải rõ ràng, dễ hiểu với người chơi.  
* Không được xảy ra mất, nhân bản hoặc trừ tiền sai khi giao dịch.

**Giao diện liên quan**  
Màn hình Shop; màn hình danh mục hàng hóa; màn hình chi tiết vật phẩm; hộp thoại mua/bán; màn hình so sánh giá; thông báo giao dịch; màn hình túi đồ và số dư tiền.  
**Ghi chú**  
UC10 là Use Case tổng quát của nhóm Shop. Các Use Case con dưới đây mô tả từng thao tác cụ thể và có thể được gọi từ Shop hoặc từ NPC/cửa hàng tương ứng.

| Mã Use Case | UC10.1 |
| :---- | :---- |
| Tên Use Case | Mua vật phẩm |
| Mục đích | Cho phép người chơi mua nguyên liệu, thiết bị hoặc vật phẩm cần thiết cho hoạt động sinh tồn và kinh doanh.  |
| Mô tả | Người chơi sử dụng chức năng mua vật phẩm trong Shop. Hệ thống hiển thị và xử lý dữ liệu liên quan, kiểm tra điều kiện cần thiết, sau đó trả kết quả rõ ràng. Chức năng này không tự ý thay đổi dữ liệu nếu người chơi chưa xác nhận giao dịch.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn một vật phẩm và chọn chức năng Mua.  
**Tiền điều kiện**

* Người chơi đã mở Shop hợp lệ.  
* Vật phẩm đang được bán và nguồn cung cấp đã mở khóa.  
* Người chơi có đủ tiền dự kiến hoặc có thể chọn số lượng phù hợp.

**Hậu điều kiện**

* Giao dịch thành công thì tiền, vật phẩm và tồn kho được cập nhật.  
* Giao dịch thất bại/hủy thì dữ liệu giữ nguyên.  
* Kết quả được thông báo và lưu đồng bộ.

**Luồng chính**

1. Người chơi chọn vật phẩm cần mua.  
2. Hệ thống hiển thị giá, số lượng và tổng tiền.  
3. Người chơi nhập số lượng và xác nhận mua.  
4. Hệ thống kiểm tra tiền, tồn kho, giới hạn túi đồ và điều kiện mở khóa.  
5. Hệ thống trừ tiền và cộng vật phẩm.  
6. Hệ thống cập nhật tồn kho, lịch sử giao dịch và thông báo thành công.

**Luồng thay thế**  
**A1 – Người chơi hủy xác nhận**

* Hệ thống đóng hộp thoại.  
* Không cập nhật dữ liệu.

**Luồng ngoại lệ**  
**E1 – Không đủ tiền; E2 – Hết hàng; E3 – Vượt sức chứa túi đồ; E4 – Lỗi lưu giao dịch.**

* Hệ thống thông báo nguyên nhân phù hợp.  
* Không thực hiện thay đổi dữ liệu trái với điều kiện nghiệp vụ.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Tổng tiền \= đơn giá × số lượng.  
* BR02: Chỉ trừ tiền sau khi kiểm tra thành công.  
* BR03: Không mua vượt tồn kho hoặc sức chứa túi đồ.  
* BR04: Nếu lỗi, hoàn tác toàn bộ giao dịch.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Dữ liệu phải nhất quán và dễ đọc.  
* Thao tác phải phản hồi rõ ràng.  
* Không được thay đổi dữ liệu ngoài phạm vi của Use Case.

**Giao diện liên quan**  
Màn hình Shop; danh sách vật phẩm; chi tiết vật phẩm; hộp thoại xác nhận; bảng giá/so sánh giá; thông báo kết quả.  
**Ghi chú**  
UC độc lập, tập trung vào chức năng mua vật phẩm.

| Mã Use Case | UC10.2 |
| :---- | :---- |
| Tên Use Case | Bán vật phẩm |
| Mục đích | Cho phép người chơi bán vật phẩm đang sở hữu để nhận tiền, giải phóng túi đồ hoặc tối ưu dòng tiền.  |
| Mô tả | Người chơi sử dụng chức năng bán vật phẩm trong Shop. Hệ thống hiển thị và xử lý dữ liệu liên quan, kiểm tra điều kiện cần thiết, sau đó trả kết quả rõ ràng. Chức năng này không tự ý thay đổi dữ liệu nếu người chơi chưa xác nhận giao dịch.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn vật phẩm trong Shop hoặc túi đồ và chọn chức năng Bán.  
**Tiền điều kiện**

* Người chơi đã mở Shop hoặc túi đồ.  
* Vật phẩm thuộc sở hữu người chơi và được phép bán.

**Hậu điều kiện**

* Giao dịch thành công thì tiền, vật phẩm và tồn kho được cập nhật.  
* Giao dịch thất bại/hủy thì dữ liệu giữ nguyên.  
* Kết quả được thông báo và lưu đồng bộ.

**Luồng chính**

1. Người chơi chọn vật phẩm cần bán.  
2. Hệ thống hiển thị số lượng sở hữu và giá bán.  
3. Người chơi nhập số lượng và xác nhận bán.  
4. Hệ thống kiểm tra quyền sở hữu, số lượng và điều kiện bán.  
5. Hệ thống trừ vật phẩm và cộng tiền.  
6. Hệ thống cập nhật dữ liệu và thông báo thành công.

**Luồng thay thế**  
**A1 – Người chơi hủy xác nhận**

* Hệ thống đóng hộp thoại.  
* Không cập nhật dữ liệu.

**Luồng ngoại lệ**  
**E1 – Không sở hữu vật phẩm; E2 – Số lượng bán vượt quá số lượng có; E3 – Vật phẩm không được phép bán; E4 – Lỗi lưu giao dịch.**

* Hệ thống thông báo nguyên nhân phù hợp.  
* Không thực hiện thay đổi dữ liệu trái với điều kiện nghiệp vụ.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ bán vật phẩm đang sở hữu.  
* BR02: Số lượng bán không vượt số lượng hiện có.  
* BR03: Tiền nhận \= giá bán × số lượng.  
* BR04: Vật phẩm nhiệm vụ/đang sử dụng có thể bị khóa bán.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Dữ liệu phải nhất quán và dễ đọc.  
* Thao tác phải phản hồi rõ ràng.  
* Không được thay đổi dữ liệu ngoài phạm vi của Use Case.

**Giao diện liên quan**  
Màn hình Shop; danh sách vật phẩm; chi tiết vật phẩm; hộp thoại xác nhận; bảng giá/so sánh giá; thông báo kết quả.  
**Ghi chú**  
UC độc lập, tập trung vào chức năng bán vật phẩm.

| Mã Use Case | UC10.3 |
| :---- | :---- |
| Tên Use Case | Xem giá |
| Mục đích | Cho phép người chơi xem giá mua, giá bán và thông tin cơ bản của vật phẩm tại một nguồn cung cấp.  |
| Mô tả | Người chơi sử dụng chức năng xem giá trong Shop. Hệ thống hiển thị và xử lý dữ liệu liên quan, kiểm tra điều kiện cần thiết, sau đó trả kết quả rõ ràng. Chức năng này không tự ý thay đổi dữ liệu nếu người chơi chưa xác nhận giao dịch.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn vật phẩm hoặc danh mục cần xem giá.  
**Tiền điều kiện**

* Shop hoặc nguồn cung cấp tồn tại.  
* Dữ liệu vật phẩm và giá có thể được tải.

**Hậu điều kiện**

* Thông tin giá được hiển thị chính xác theo nguồn và thời điểm.  
* Không thay đổi tiền, vật phẩm hoặc tồn kho.

**Luồng chính**

1. Người chơi chọn vật phẩm.  
2. Hệ thống tải giá và thông tin từ nguồn cung cấp.  
3. Hệ thống hiển thị giá mua, giá bán nếu có, đơn vị, số lượng và điều kiện áp dụng.  
4. Người chơi đóng màn hình hoặc chuyển sang thao tác khác.

**Luồng thay thế**  
**A1 – Không có dữ liệu giá đầy đủ**

* Hệ thống hiển thị các nguồn có dữ liệu và ghi rõ nguồn chưa có giá.  
* Không đưa ra kết luận chắc chắn nếu dữ liệu không đủ.

**Luồng ngoại lệ**  
**E1 – Lỗi tải giá; E2 – Giá đã hết hiệu lực; E3 – Vật phẩm không tồn tại.**

* Hệ thống thông báo nguyên nhân phù hợp.  
* Không thực hiện thay đổi dữ liệu trái với điều kiện nghiệp vụ.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Giá phải gắn với nguồn cung cấp và thời điểm.  
* BR02: Không xem giá là một giao dịch.  
* BR03: Giá không tồn tại phải được hiển thị là chưa có dữ liệu.

**Include**  
Không.   
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Dữ liệu phải nhất quán và dễ đọc.  
* Thao tác phải phản hồi rõ ràng.  
* Không được thay đổi dữ liệu ngoài phạm vi của Use Case.

**Giao diện liên quan**  
Màn hình Shop; danh sách vật phẩm; chi tiết vật phẩm; hộp thoại xác nhận; bảng giá/so sánh giá; thông báo kết quả.  
**Ghi chú**  
UC độc lập, tập trung vào chức năng xem giá.

| Mã Use Case | UC10.4 |
| :---- | :---- |
| Tên Use Case | So sánh giá |
| Mục đích | Cho phép người chơi đối chiếu giá của cùng một vật phẩm giữa nhiều cửa hàng/nguồn cung cấp để chọn phương án có lợi.  |
| Mô tả | Người chơi sử dụng chức năng so sánh giá trong Shop. Hệ thống hiển thị và xử lý dữ liệu liên quan, kiểm tra điều kiện cần thiết, sau đó trả kết quả rõ ràng. Chức năng này không tự ý thay đổi dữ liệu nếu người chơi chưa xác nhận giao dịch.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng So sánh giá.  
**Tiền điều kiện**

* Có ít nhất hai nguồn cung cấp hợp lệ hoặc hệ thống có dữ liệu giá để đối chiếu.  
* Vật phẩm cần so sánh tồn tại trong danh mục.

**Hậu điều kiện**

* Thông tin giá được hiển thị chính xác theo nguồn và thời điểm.  
* Không thay đổi tiền, vật phẩm hoặc tồn kho.

**Luồng chính**

1. Người chơi chọn vật phẩm cần so sánh.  
2. Hệ thống lấy giá từ các nguồn cung cấp hợp lệ.  
3. Hệ thống chuẩn hóa đơn vị và số lượng để so sánh.  
4. Hệ thống hiển thị bảng giá, chênh lệch và nguồn có lợi hơn.  
5. Người chơi chọn nguồn cung cấp hoặc quay lại Shop.

**Luồng thay thế**  
**A1 – Không có dữ liệu giá đầy đủ**

* Hệ thống hiển thị các nguồn có dữ liệu và ghi rõ nguồn chưa có giá.  
* Không đưa ra kết luận chắc chắn nếu dữ liệu không đủ.

**Luồng ngoại lệ**  
**E1 – Không tìm thấy nguồn cung cấp; E2 – Giá giữa các nguồn không cùng đơn vị; E3 – Lỗi tải dữ liệu.**

* Hệ thống thông báo nguyên nhân phù hợp.  
* Không thực hiện thay đổi dữ liệu trái với điều kiện nghiệp vụ.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ so sánh cùng một vật phẩm và cùng đơn vị tính.  
* BR02: Phải hiển thị nguồn và thời điểm của giá.  
* BR03: Không tự động mua khi người chơi chỉ so sánh.

**Include**  
UC10.4 có thể \<\<include\>\> UC10.3 khi cần lấy giá từng nguồn.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Dữ liệu phải nhất quán và dễ đọc.  
* Thao tác phải phản hồi rõ ràng.  
* Không được thay đổi dữ liệu ngoài phạm vi của Use Case.

**Giao diện liên quan**  
Màn hình Shop; danh sách vật phẩm; chi tiết vật phẩm; hộp thoại xác nhận; bảng giá/so sánh giá; thông báo kết quả.  
**Ghi chú**  
UC riêng biệt, tập trung vào chức năng so sánh giá.

| Mã Use Case | UC11 |
| :---- | :---- |
| Tên Use Case | Quản lý Tiền |
| Mục đích | Cho phép người chơi xem, kiếm, chi tiêu và quản lý các hoạt động tài chính trong quá trình phát triển sự nghiệp.  |
| Mô tả | Người chơi sử dụng hệ thống Tiền để theo dõi số dư, nhận thu nhập, thanh toán chi phí, đầu tư, vay vốn và trả nợ. Hệ thống kiểm tra điều kiện của từng giao dịch, cập nhật số dư và lưu dữ liệu khi giao dịch thành công.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Tiền hoặc phát sinh một giao dịch làm thay đổi số dư.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Tài khoản và dữ liệu tài chính của người chơi đã được khởi tạo.  
* Người chơi có quyền truy cập chức năng Tiền.

**Hậu điều kiện**

* Số dư và lịch sử giao dịch được hiển thị chính xác.  
* Dữ liệu tiền được cập nhật nếu giao dịch thành công.  
* Các thay đổi được lưu vào hệ thống.  
* Nếu giao dịch thất bại, số dư trước giao dịch được giữ nguyên.

**Luồng chính**

1. Người chơi chọn chức năng Tiền.  
2. Hệ thống tải dữ liệu tài chính của người chơi.  
3. Hệ thống hiển thị số dư, các khoản thu/chi và các chức năng quản lý tiền.  
4. Người chơi chọn một chức năng quản lý tiền.  
5. Hệ thống chuyển đến chức năng tương ứng.  
6. Người chơi thực hiện thao tác.  
7. Hệ thống kiểm tra điều kiện giao dịch.  
8. Nếu hợp lệ, hệ thống cập nhật số dư và dữ liệu liên quan.  
9. Hệ thống lưu thay đổi và thông báo kết quả.

**Luồng thay thế**  
**A1 – Người chơi không thực hiện giao dịch**

* Hệ thống chỉ hiển thị thông tin tài chính.  
* Dữ liệu tiền được giữ nguyên.

**A2 – Người chơi hủy thao tác**

* Hệ thống hủy thao tác đang thực hiện.  
* Không thay đổi số dư hoặc dữ liệu tài chính.  
* Quay lại màn hình Tiền.

**Luồng ngoại lệ**  
**E1 – Lỗi tải dữ liệu tiền**

* Hệ thống thông báo không thể tải dữ liệu.  
* Không cho phép thực hiện giao dịch khi dữ liệu chưa được tải đầy đủ.

**E2 – Giao dịch không hợp lệ**

* Hệ thống thông báo lý do giao dịch không hợp lệ.  
* Không cập nhật số dư.

**E3 – Lỗi cập nhật hoặc lưu dữ liệu**

* Hệ thống giữ nguyên dữ liệu trước giao dịch.  
* Hệ thống thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ người chơi sở hữu dữ liệu tài chính mới được thực hiện giao dịch.  
* BR02: Số dư tiền không được nhỏ hơn 0, trừ trường hợp khoản nợ được hệ thống quản lý riêng.  
* BR03: Số dư chỉ được cập nhật sau khi giao dịch được xác nhận thành công.  
* BR04: Nếu giao dịch thất bại hoặc bị hủy, dữ liệu trước giao dịch phải được giữ nguyên.  
* BR05: Mọi thay đổi tiền phải được lưu đồng bộ và không được tạo giao dịch trùng.  
* BR06: Mọi khoản thu, chi, đầu tư, vay và trả nợ phải có nguồn phát sinh rõ ràng.

**Include**  
UC11.1 – Xem số dư; UC11.2 – Kiếm tiền; UC11.3 – Chi tiêu; UC11.4 – Đầu tư; UC11.5 – Vay vốn; UC11.6 – Trả nợ.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thông tin tiền phải được hiển thị chính xác và dễ hiểu.  
* Hệ thống phải tránh mất tiền, nhân bản tiền hoặc ghi nhận giao dịch hai lần.  
* Hệ thống phải phản hồi rõ ràng khi giao dịch thành công hoặc thất bại.  
* Dữ liệu tài chính phải được lưu bền vững.

**Giao diện liên quan**  
Màn hình Tiền; màn hình Số dư; màn hình Lịch sử giao dịch; các màn hình Kiếm tiền, Chi tiêu, Đầu tư, Vay vốn và Trả nợ.  
**Ghi chú**  
UC11 là Use Case tổng quát của nhóm quản lý tiền. Các Use Case con là những chức năng độc lập được truy cập từ màn hình Tiền. Không mặc định các chức năng này phải include lẫn nhau.

| Mã Use Case | UC11.1 |
| :---- | :---- |
| Tên Use Case | Xem số dư |
| Mục đích | Cho phép người chơi xem số tiền hiện có và các thông tin tài chính cơ bản.  |
| Mô tả | Người chơi mở chức năng Xem số dư. Hệ thống tải và hiển thị số dư tiền mặt, các khoản nợ hoặc nghĩa vụ tài chính đang tồn tại nếu có.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn Xem số dư trong màn hình Tiền.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Dữ liệu tài chính đã được khởi tạo.

**Hậu điều kiện**

* Số dư được hiển thị chính xác.  
* Không có dữ liệu tài chính bị thay đổi.

**Luồng chính**

1. Người chơi chọn Xem số dư.  
2. Hệ thống tải dữ liệu tài chính.  
3. Hệ thống hiển thị số dư hiện tại và thông tin liên quan.  
4. Người chơi xem thông tin hoặc quay lại màn hình Tiền.

**Luồng thay thế**  
**A1 – Không có khoản nợ**

* Hệ thống hiển thị số dư tiền mặt và thông báo không có khoản nợ.

**Luồng ngoại lệ**  
**E1 – Không thể tải số dư**

* Hệ thống thông báo lỗi tải dữ liệu.  
* Không cho phép chỉnh sửa dữ liệu tài chính.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Số dư phải phản ánh dữ liệu đã được lưu gần nhất.  
* BR02: Chức năng xem số dư không làm thay đổi tiền.  
* BR03: Nếu có khoản nợ, hệ thống phải hiển thị riêng, không trừ trực tiếp vào tiền mặt nếu chưa phát sinh thanh toán.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thời gian phản hồi phù hợp.  
* Thông tin rõ ràng, không gây nhầm giữa tiền mặt, tài sản và khoản nợ.

**Giao diện liên quan**  
Màn hình Tiền; bảng Số dư; khu vực Khoản nợ.  
**Ghi chú**  
Đây là chức năng chỉ đọc; không include Trả nợ.

| Mã Use Case | UC11.2 |
| :---- | :---- |
| Tên Use Case | Xem số dư |
| Mục đích | Cho phép người chơi xem số tiền hiện có và các thông tin tài chính cơ bản.  |
| Mô tả | Người chơi mở chức năng Xem số dư. Hệ thống tải và hiển thị số dư tiền mặt, các khoản nợ hoặc nghĩa vụ tài chính đang tồn tại nếu có.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi hoàn thành một hoạt động có phần thưởng tiền hoặc chọn chức năng Kiếm tiền.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Hoạt động tạo thu nhập đã được mở khóa.  
* Điều kiện nhận thưởng đã được đáp ứng.

**Hậu điều kiện**

* Tiền thu nhập được cộng đúng số lượng.  
* Nguồn thu được ghi nhận trong lịch sử giao dịch.  
* Dữ liệu được lưu thành công.

**Luồng chính**

1. Người chơi thực hiện công việc, bán hàng, hoàn thành nhiệm vụ hoặc nhận phần thưởng.  
2. Hệ thống xác định số tiền được nhận.  
3. Hệ thống kiểm tra điều kiện nhận thu nhập.  
4. Hệ thống cộng tiền vào số dư.  
5. Hệ thống ghi lịch sử giao dịch và thông báo kết quả.

**Luồng thay thế**  
**A1 – Thu nhập bằng 0**

* Hệ thống thông báo không phát sinh thu nhập.  
* Không thay đổi số dư.

**A2 – Thu nhập từ nhiều nguồn**

* Hệ thống ghi nhận từng khoản thu riêng biệt hoặc theo một giao dịch tổng hợp có nguồn rõ ràng.

**Luồng ngoại lệ**  
**E1 – Hoạt động chưa hoàn thành**

* Không cộng tiền.  
* Thông báo điều kiện chưa đạt.

**E2 – Lỗi cộng tiền hoặc lưu giao dịch**

* Hệ thống không cộng trùng tiền.  
* Khôi phục trạng thái trước giao dịch và thông báo thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ cộng tiền khi hoạt động tạo thu nhập hoàn thành hợp lệ.  
* BR02: Không được nhận thưởng nhiều lần cho cùng một lần hoàn thành.  
* BR03: Khoản thu phải có nguồn phát sinh.  
* BR04: Thu nhập từ kinh doanh phải phù hợp với kết quả hoạt động và dữ liệu game.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Kết quả thu nhập phải phản hồi rõ ràng.  
* Không được cộng tiền trùng hoặc mất tiền khi lưu.

**Giao diện liên quan**  
Màn hình Tiền; màn hình nghề/nghiệp vụ; màn hình nhiệm vụ; lịch sử giao dịch.  
**Ghi chú**  
Kiếm tiền là chức năng độc lập, không bắt buộc phải thực hiện Đầu tư hoặc Chi tiêu.

| Mã Use Case | UC11.3 |
| :---- | :---- |
| Tên Use Case | Chi tiêu |
| Mục đích | Cho phép người chơi sử dụng tiền để mua hàng hóa, nguyên liệu, thiết bị, dịch vụ, thuê mặt bằng hoặc thanh toán các chi phí trong game.  |
| Mô tả | Người chơi chọn một khoản mua hoặc thanh toán. Hệ thống kiểm tra giá trị giao dịch và số dư, sau đó trừ tiền và cập nhật dữ liệu liên quan nếu giao dịch hợp lệ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn một hoạt động hoặc vật phẩm cần thanh toán.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Sản phẩm, dịch vụ hoặc khoản phí tồn tại hợp lệ.  
* Giá giao dịch đã được xác định.

**Hậu điều kiện**

* Số dư bị trừ đúng số tiền.  
* Vật phẩm, dịch vụ hoặc trạng thái liên quan được cập nhật.  
* Giao dịch được lưu vào lịch sử.

**Luồng chính**

1. Người chơi chọn nội dung cần mua hoặc thanh toán.  
2. Hệ thống hiển thị giá và thông tin giao dịch.  
3. Người chơi xác nhận.  
4. Hệ thống kiểm tra số dư và điều kiện.  
5. Hệ thống trừ tiền và cập nhật dữ liệu.  
6. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Người chơi hủy thanh toán**  
Giao dịch bị hủy.  
Không trừ tiền.  
**A2 – Có chi phí định kỳ**  
Hệ thống thông báo khoản phí đến hạn và yêu cầu xác nhận nếu thiết kế game cần xác nhận.  
**Luồng ngoại lệ**  
**E1 – Không đủ tiền**

* Hệ thống thông báo số dư không đủ.  
* Không cập nhật dữ liệu.

**E2 – Lỗi cập nhật vật phẩm/dịch vụ**

* Không trừ tiền hoặc hoàn tác giao dịch nếu đã tạm giữ tiền.  
* Thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Người chơi phải có đủ tiền để thực hiện chi tiêu.  
* BR02: Giá giao dịch phải được xác định trước khi xác nhận.  
* BR03: Không được trừ tiền hai lần cho một giao dịch.  
* BR04: Nếu không nhận được vật phẩm/dịch vụ, giao dịch phải được hoàn tác hoặc không ghi nhận thành công.  
* BR05: Chi tiêu không đồng nghĩa với đầu tư; chỉ các giao dịch được xác định là đầu tư mới thuộc UC11.4.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Giá và tổng tiền phải hiển thị rõ.  
* Hệ thống phải đảm bảo tính nhất quán giữa tiền bị trừ và vật phẩm/dịch vụ nhận được.

**Giao diện liên quan**  
Màn hình Shop; màn hình mua thiết bị/nguyên liệu; màn hình thuê mặt bằng; màn hình xác nhận thanh toán.  
**Ghi chú**  
Chi tiêu có thể được phát sinh từ Shop hoặc các hoạt động khác, nhưng vẫn được quản lý theo quy tắc giao dịch tiền.

| Mã Use Case | UC11.4 |
| :---- | :---- |
| Tên Use Case | Đầu tư |
| Mục đích | Cho phép người chơi sử dụng một phần vốn để đầu tư và theo dõi kết quả đầu tư trong game.  |
| Mô tả | Người chơi chọn hình thức đầu tư được mở khóa, nhập số vốn và xác nhận. Hệ thống kiểm tra điều kiện, ghi nhận khoản đầu tư và cập nhật tiền hoặc tài sản đầu tư theo cơ chế của game.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Trung bình đến cao |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Đầu tư.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Hình thức đầu tư đã được mở khóa.  
* Người chơi có đủ vốn theo điều kiện đầu tư.

**Hậu điều kiện**

* Khoản đầu tư được ghi nhận chính xác.  
* Số dư hoặc tài sản đầu tư được cập nhật.  
* Kết quả đầu tư được lưu khi có phát sinh.

**Luồng chính**

1. Người chơi chọn hình thức đầu tư.  
2. Hệ thống hiển thị thông tin, vốn yêu cầu và rủi ro nếu có.  
3. Người chơi nhập số vốn và xác nhận.  
4. Hệ thống kiểm tra điều kiện.  
5. Hệ thống ghi nhận khoản đầu tư và trừ vốn theo quy định.  
6. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Người chơi không xác nhận**

* Không tạo khoản đầu tư.  
* Không trừ tiền.

**A2 – Không có hình thức đầu tư khả dụng**

* Hệ thống thông báo chưa có lựa chọn đầu tư phù hợp.

**Luồng ngoại lệ**  
**E1 – Không đủ vốn**

* Không tạo khoản đầu tư.  
* Thông báo số dư không đủ.

**E2 – Lỗi ghi nhận đầu tư**

* Không trừ vốn hoặc hoàn tác giao dịch.  
* Thông báo thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ đầu tư vào hình thức đã được hệ thống mở khóa.  
* BR02: Vốn đầu tư không được vượt quá số tiền người chơi có thể sử dụng.  
* BR03: Đầu tư phải được ghi nhận thành một giao dịch riêng.  
* BR04: Lợi nhuận hoặc thua lỗ chỉ được cập nhật theo quy tắc đầu tư của game.  
* BR05: Đầu tư không bắt buộc phải phát sinh từ Vay vốn.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Thông tin vốn, trạng thái và kết quả đầu tư phải rõ ràng.  
* Không được tạo hoặc ghi nhận khoản đầu tư trùng.

**Giao diện liên quan**  
Màn hình Tiền; màn hình Đầu tư; màn hình danh mục đầu tư; lịch sử giao dịch.  
**Ghi chú**  
Không suy diễn cơ chế cổ phiếu, lãi suất hay tỷ lệ lợi nhuận cụ thể nếu game chưa quy định.

| Mã Use Case | UC11.5 |
| :---- | :---- |
| Tên Use Case | Vay vốn |
| Mục đích | Cho phép người chơi vay tiền từ nguồn vay được hệ thống cung cấp để phục vụ hoạt động kinh doanh hoặc mục đích hợp lệ.  |
| Mô tả | Người chơi chọn khoản vay, xem điều kiện và xác nhận. Hệ thống kiểm tra khả năng vay, tạo khoản nợ, cộng tiền vay vào số dư và lưu nghĩa vụ trả nợ.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Vay vốn.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Chức năng vay vốn đã được mở khóa.  
* Nguồn vay và điều kiện vay tồn tại.

**Hậu điều kiện**

* Tiền vay được cộng đúng số lượng.  
* Khoản nợ được tạo và lưu.  
* Điều kiện trả nợ được hiển thị rõ nếu có.

**Luồng chính**

1. Người chơi chọn khoản vay.  
2. Hệ thống hiển thị số tiền, điều kiện và nghĩa vụ trả nợ.  
3. Người chơi xác nhận.  
4. Hệ thống kiểm tra điều kiện vay.  
5. Hệ thống cộng tiền và tạo khoản nợ.  
6. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Người chơi hủy vay**

* Không cộng tiền.  
* Không tạo khoản nợ.

**A2 – Không có gói vay phù hợp**

* Hệ thống thông báo không có khoản vay khả dụng.

**Luồng ngoại lệ**  
**E1 – Không đủ điều kiện vay**

* Hệ thống từ chối yêu cầu.  
* Không thay đổi số dư hoặc khoản nợ.

**E2 – Lỗi tạo khoản nợ**

* Không cộng tiền vay.  
* Thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ vay trong phạm vi và điều kiện do game quy định.  
* BR02: Vay vốn phải tạo nghĩa vụ trả nợ tương ứng.  
* BR03: Tiền vay và khoản nợ phải được ghi nhận trong cùng giao dịch logic.  
* BR04: Vay vốn không bắt buộc phải dùng cho Đầu tư.  
* BR05: Không được tạo khoản vay trùng khi người chơi xác nhận nhiều lần.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Điều kiện vay và nghĩa vụ trả nợ phải dễ hiểu.  
* Hệ thống phải bảo đảm tính nhất quán giữa tiền được cộng và khoản nợ được tạo.

**Giao diện liên quan**  
Màn hình Tiền; màn hình Vay vốn; màn hình chi tiết khoản vay.  
**Ghi chú**  
Không tự ý xác định lãi suất, kỳ hạn hoặc hạn mức cụ thể nếu chưa có trong thiết kế game.

| Mã Use Case | UC11.6 |
| :---- | :---- |
| Tên Use Case | Trả nợ |
| Mục đích | Cho phép người chơi thanh toán một phần hoặc toàn bộ khoản nợ đã phát sinh.  |
| Mô tả | Người chơi chọn khoản nợ cần thanh toán và xác nhận số tiền trả. Hệ thống kiểm tra số dư, số tiền phải trả và cập nhật khoản nợ cùng số dư khi thanh toán thành công.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống; NPC liên quan |
| Mức ưu tiên | Trung bình  |
| Tần suất sử dụng | Theo kỳ hạn hoặc Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Trả nợ hoặc chọn một khoản nợ đang tồn tại.  
**Tiền điều kiện**

* Người chơi đã vào trò chơi.  
* Người chơi có ít nhất một khoản nợ hợp lệ.  
* Dữ liệu khoản nợ được tải đầy đủ.

**Hậu điều kiện**

* Số dư bị trừ đúng số tiền trả.  
* Khoản nợ được giảm hoặc tất toán.  
* Giao dịch trả nợ được lưu.

**Luồng chính**

1. Người chơi chọn khoản nợ.  
2. Hệ thống hiển thị số nợ và số tiền cần trả.  
3. Người chơi nhập số tiền hoặc chọn trả toàn bộ.  
4. Hệ thống kiểm tra số dư và điều kiện.  
5. Hệ thống trừ tiền, cập nhật khoản nợ.  
6. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Không có khoản nợ**

* Hệ thống thông báo không có khoản nợ cần trả.  
* Không thay đổi số dư.

**A2 – Người chơi trả một phần**

* Hệ thống giảm dư nợ theo số tiền đã thanh toán.  
* Khoản nợ vẫn tồn tại nếu chưa tất toán.

**A3 – Người chơi hủy**

* Không trừ tiền và không cập nhật khoản nợ.

**Luồng ngoại lệ**  
**E1 – Không đủ tiền trả nợ**

* Hệ thống thông báo số dư không đủ.  
* Không cập nhật khoản nợ.

**E2 – Lỗi cập nhật khoản nợ**

* Không trừ tiền hoặc hoàn tác giao dịch.  
* Thông báo thao tác thất bại.

**Business Rule / Quy tắc nghiệp vụ**

* BR01: Chỉ trả nợ đối với khoản nợ đang tồn tại của người chơi.  
* BR02: Số tiền trả không được vượt quá số nợ phải trả, trừ trường hợp hệ thống cho phép xử lý phần dư.  
* BR03: Trả nợ phải cập nhật đồng thời số dư và dư nợ.  
* BR04: Trả nợ không phải là chức năng bắt buộc của Xem số dư.  
* BR05: Không được ghi nhận một khoản trả nợ nhiều lần.

**Include**  
Không.  
**Extend**  
Không.  
**Yêu cầu phi chức năng**

* Số nợ, số tiền trả và số dư sau giao dịch phải hiển thị rõ.  
* Hệ thống phải bảo đảm không mất tiền hoặc giảm nợ sai.

**Giao diện liên quan**  
Màn hình Tiền; màn hình Khoản nợ; màn hình xác nhận trả nợ; lịch sử giao dịch.  
**Ghi chú**  
Trả nợ là chức năng độc lập. Xem số dư chỉ hiển thị thông tin khoản nợ và không tự động gọi Trả nợ.  
**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC12 | Quản lý công ty | Tổng quát |
| UC12.1 | Mở công ty  | Gọi UC12.3, UC12.6; được gọi bởi UC12.5 |
| UC12.2 | Quản lý nhân viên | Gọi UC12.3, UC12.4, UC12.5  |
| UC12.3 | Thuê nhân viên  | Được gọi bởi UC12.1, UC12.2.  |
| UC12.4 | Sa thải | Được gọi bởi UC12.2. |
| UC12.5 | Trả lương | Được gọi bởi UC12.1, UC12.2 |
| UC12.6 | Nâng cấp công ty | Được gọi bởi UC12.1 |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC12.1 (Mở công ty) | UC12.3, UC12.6  | Không  | Mở công ty tự động gọi quy trình thuê nhân viên đầu tiên và mở khóa Khung nâng cấp |
| UC12.2 (Quản lý nhân viên)  | UC12.3, UC12.4, UC12.5 | Không  | Màn hình quản lý bao hàm trực tiếp các tác vụ Tuyển, Sa thải và Trả lương |
| UC12.3 (Thuê nhân viên)  | Không  | Không  |   |
| UC12.4 (Sa thải)  | Không  | Không  |  |
| UC12.5 (Trả lương) | Không | UC12.1 | Kích hoạt định kỳ (hàng tháng) chèn vào luồng hoạt động của Công ty. Nếu không đủ tiền \-\> Cảnh báo trả lương / Đình công. |
| UC12.6 (Nâng cấp công ty) | Không | Không |  |

**Đặc tả UC12**

| Mã Use Case | UC12 |
| :---- | :---- |
| Tên Use Case | Quản lý công ty |
| Mục đích | Cho phép người chơi thành lập, mở rộng doanh nghiệp, điều hành nhân sự, tối ưu hóa quy trình trả lương và cơ sở vật chất để tự động hóa nguồn thu nhập hướng tới cột mốc \$1M. |
| Mô tả |  |
| Actor | Người chơi  |
| Mức ưu tiên | ?? |
| Tần suất sử dụng | ?? |

Trigger  
Người chơi tương tác với Toà nhà Văn phòng hoặc mở ứng dụng “Quản Lý Công Ty” trên Laptop/Điện thoại in-game.  
Tiền điều kiện

* Đã hoàn thành Tutorial (ngày 1).  
* Tích lũy đủ số vốn tối thiểu trong Tài khoản Ngân hàng và có Kỹ năng Quản trị tiền đề. 

Hậu điều kiện

* Doanh nghiệp được thành lập/cập nhật trạng thái.  
* Các biến số tài chính, số lượng nhân viên, quỹ lương định kỳ và chỉ số Stress của nhân vật chính được lưu lại.

Luồng chính

1. Người chơi chọn Mở công ty (UC13.1) khi đạt đủ điều kiện vốn và kỹ năng.  
2. Hệ thống khởi tạo doanh nghiệp, tự động gọi Thuê nhân viên (UC13.3) để tuyển nhân sự ban đầu và Nâng cấp công ty (UC13.6) để cấp không gian làm việc mặc định.  
3. Người chơi truy cập màn hình Quản lý nhân viên (UC13.2) để theo dõi danh sách, năng suất, độ trung thành và quỹ lương của công ty.  
4. Từ bảng điều hành nhân sự, người chơi tùy chỉnh đội ngũ thông qua việc Thuê nhân viên mới (UC13.3) hoặc Sa thải (UC13.4) các cá nhân kém hiệu quả.  
5. Định kỳ hàng tháng, hệ thống kích hoạt luồng mở rộng Trả lương (UC13.5) để tự động khấu trừ quỹ lương từ tài khoản doanh nghiệp/cá nhân.  
6. Người chơi thực hiện Nâng cấp công ty (UC13.6) để mở rộng văn phòng, mua sắm thiết bị, tăng sức chứa nhân sự tối đa và nâng cao hiệu suất làm việc.

Luồng phụ 1 (Rủi ro tài chính và đình công)

1. Đến kỳ Trả lương (UC13.5) nhưng tài khoản công ty/cá nhân không đủ số dư.  
2. Hệ thống phát thông báo cảnh báo nợ lương. Chỉ số Trung thành của toàn bộ nhân viên giảm 50%.  
3. Nếu trễ lương quá 3 ngày $\rightarrow$ Nhân viên đồng loạt Sa thải (UC13.4) bản thân (tự nghỉ việc) hoặc đình công $\rightarrow$ Công ty ngừng hoạt động, nhân vật chính bị cộng trực tiếp \+30% Stress.

Luồng phụ 2 (Extend Flow \- Mở khóa từ giao diện xem):

1. Trong quá trình vận hành, người chơi chọn tùy chọn *"Báo cáo tài chính ma / Trốn thuế"* để tăng 30% lợi nhuận net.  
2. Hệ thống cộng tiền nhưng đồng thời tăng chỉ số Risk\_Factor.  
3. Khi bị Cơ quan Thuế/Thanh tra phát hiện $\rightarrow$ Khấu trừ 200% tiền trốn thuế, nếu không đủ tiền thanh toán $\rightarrow$ Công ty bị cưỡng chế phá sản $\rightarrow$ Kích hoạt Bad Ending "Chung Thân Unlocked" (UC16) với background phòng giam u tối, ẩm mốc.

Luồng thay thế / ngoại lệ (A: luồng thay thế, B: Luồng ngoại lệ):  
A1: Người chơi không thực hiện UC13.1 (Mở công ty) \-\> Bỏ qua toàn bộ phân hệ quản trị doanh nghiệp, chỉ tập trung vào công việc tự do và đầu tư tài chính cá nhân.   
B1: Thoát game giữa chừng khi công ty đang khủng hoảng / đình công: Hệ thống ghi nhận cờ Flag\_RageQuitWork \= True. Khi bạn tải game ở lượt sau, nhận thư phạt sa thải / giải thể và có Thành tựu Ẩn “Đột Ngột Bốc Hơi” (UC15).  
Quy tắc nghiệp vụ:  
Giới hạn nhân sự: Số lượng nhân viên tối đa bị giới hạn bởi Cấp độ Văn phòng hiện tại trong UC13.6 (Nâng cấp công ty).  
Tác động của Kỹ năng (UC14): Cấp độ Kỹ năng Quản trị của người chơi (UC14) giúp giảm 1% \- 15% chi phí vận hành văn phòng và tăng 5% \- 20% năng suất tổng của nhân viên.  
Độc lập tài chính: Tài khoản công ty chỉ được phép âm nếu người chơi sử dụng Hạn mức Tín dụng/Vay nóng (UC11).

| Mã Use Case | UC12.1  |
| :---- | :---- |
| Tên Use Case | Mở công ty  |
| Mục đích | Tạo dựng doanh nghiệp ban đầu khi người choi có đủ vốn tích lũy.  |
| Mô tả | Cho phép người chơi đăng ký thành lập doanh nghiệp mới, lựa chọn ngành nghề kinh doanh, khởi tạo văn phòng ban đầu và tuyển dụng nhân sự khởi nghiệp.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống |
| Mức ưu tiên  | Trung bình |
| Tần suất sử dụng | Theo nhu cầu |

   
**Tiền điều kiện**

* Nhân vật chưa sở hữu công ty nào (hoặc công ty cũ bị giải thể hoặc phá sản).  
* Tài khoản ngân hàng có đủ số vốn đăng ký doanh nghiệp tối thiểu.  
* Nhân vật đạt cấp độ Kỹ năng Quản trị tối thiểu.

**Hậu điều kiện**

* Doanh nghiệp được khởi tạo thành công trên hệ thống.  
* Trừ số tiền phí thành lập doanh nghiệp từ tài khoản cá nhân.  
* Tự động mở khóa các tính năng và giao diện quản trị doanh nghiệp.

**Luồng chính**

1. Người chơi tương tác với Tòa nhà Văn phòng hoặc Laptop, chọn chức năng **"Mở công ty"**.  
2. Hệ thống kiểm tra điều kiện (Số dư ngân hàng, Cấp độ kỹ năng quản trị, Trạng thái sở hữu công ty).  
3. Hệ thống hiển thị biểu mẫu Đăng ký thành lập doanh nghiệp.  
4. Người chơi nhập tên công ty và chọn ngành nghề kinh doanh (IT, Marketing, Logistics,...).  
5. Người chơi xác nhận đăng ký thành lập.  
6. Hệ thống khấu trừ vốn đăng ký và phí thành lập từ tài khoản ngân hàng của người chơi.  
7. Hệ thống tự động gọi (`<<include>>`) **UC12.3: Thuê nhân sự** để tuyển chọn nhân sự ban đầu.  
8. Hệ thống tự động gọi (`<<include>>`) **UC12.6: Cấp văn phòng cơ bản** để gán địa điểm làm việc ban đầu.  
9. Hệ thống lưu dữ liệu công ty mới vào Database và hiển thị thông báo "Thành lập công ty thành công".

Luồng thay thế:   
**A1: Tên công ty không hợp lệ hoặc đã tồn tại**

1. Tại bước 4, người chơi nhập tên công ty bị trùng hoặc chứa ký tự đặc biệt/từ cấm.  
2. Hệ thống hiển thị cảnh báo: *"Tên công ty không hợp lệ hoặc đã được sử dụng. Vui lòng nhập tên khác."*  
3. Người chơi nhập lại tên mới và tiếp tục từ bước 5\.

**A2: Người chơi hủy quá trình thành lập**

1. Tại bất kỳ thời điểm nào trước bước 5, người chơi nhấn nút "Hủy" hoặc đóng giao diện.  
2. Hệ thống đóng màn hình đăng ký, không trừ tiền và giữ nguyên trạng thái ban đầu.

Luồng ngoại lệ:  
**E1: Không đủ điều kiện vốn hoặc kỹ năng**

1. Tại bước 2, nếu số dư ngân hàng không đủ hoặc cấp độ kỹ năng quản trị chưa đạt.  
2. Hệ thống thông báo lý do cụ thể (Ví dụ: *"Bạn cần tối thiểu \$50,000 và Kỹ năng Quản trị Cấp 3 để mở công ty"*).  
3. Hệ thống khóa nút "Xác nhận" và kết thúc Use Case.

**E2: Mất kết nối mạng / Lỗi lưu dữ liệu server**

1. Tại bước 6-9, nếu xảy ra sự cố gián đoạn kết nối hoặc lỗi cơ sở dữ liệu.  
2. Hệ thống thực hiện Rollback (hoàn trả giao dịch, không trừ tiền).  
3. Hiển thị thông báo: *"Lỗi kết nối máy chủ. Thao tác mở công ty chưa hoàn tất, vui lòng thử lại sau."*

Quy tắc nghiệp vụ:   
**Quy tắc đặt tên:** Tên công ty phải từ 3–30 ký tự, không chứa từ ngữ vi phạm thuần phong mỹ tục hoặc ký tự đặc biệt không cho phép. Tên công ty là duy nhất trong toàn bộ Server.

**Số dư tối thiểu:** Tài khoản ngân hàng phải đảm bảo tính đúng: $Số\ Dư\geq Phí\ Thành\ Lập+Vốn\ Điều\ Lệ\ Tối\ Thiểu$. Không cho phép số dư bị âm.

**Giới hạn sở hữu:** Mỗi người chơi chỉ được sở hữu tối đa **01 công ty active** tại một thời điểm.

**Tính nhất quán dữ liệu:** Mọi giao dịch trừ tiền thành lập và khởi tạo công ty đều phải được ghi lại lịch sử giao dịch tài chính (Log).

**Include**  
UC12.3, UC12.6.  
**Extend**  
Không.  
Ghi chú: 

- Về actor phụ: Chịu trách nhiệm kiểm tra số dư, xác thực và thực hiện giao dịch trừ tiền từ tài khoản cá nhân người chơi  
- Hệ thống: Lưu trữ thông tin doanh nghiệp, gán ID công ty cho nhân vật và đồng bộ hóa trạng thái tài khoản

| Mã Use Case | UC12.2  |
| :---- | :---- |
| Tên Use Case | Quản lý nhân viên  |
| Mục đích | Hiển thị danh sách, chỉ số hài lòng, năng suất và tổng quỹ lương nhân sự.  |
| Mô tả | Cung cấp giao diện tổng quan về đội ngũ nhân sự của công ty; hiển thị trạng thái làm việc, hiệu suất, mức độ hài lòng/stress và chi phí lương; đồng thời là điểm truy cập chính để điều hướng đến các tác vụ quản trị nhân sự khác (Thuê, Sa thải, Trả lương, Đào tạo).  |
| Actor | Chính: Người chơi  Phụ: Hệ thống |
| Mức ưu tiên  | Trung bình \- Cao |
| Tần suất sử dụng | Thường xuyên |

   
**Tiền điều kiện**

* UC12.1 đã được thực hiện thành công.  
* Nhân vật đang ở trong giao diện điều hành doanh nghiệp.

**Hậu điều kiện**

* Hiển thị chính xác các chỉ số thời gian thực (năng suất, mức lương, độ trung thành, stress nhân sự)  
* Cho phép người chơi điều hướng sang các tác vụ UC12.3, UC12.4, UC12.5..

**Luồng chính**

1. Người chơi truy cập tab "Nhân sự" trong giao diện Quản lý công ty \[source: 3\].  
2. Hệ thống tải danh sách nhân viên hiện tại kèm các thông số: Mức lương, Năng suất, Stress, Độ trung thành.  
3. Từ giao diện này, hệ thống tích hợp sẵn các thao tác **UC12.3 (Thuê)**, **UC12.4 (Sa thải)** và **UC12.5 (Trả lương)**.  
4. Người chơi theo dõi thông số hoặc chọn 1 tác vụ tương ứng để tiếp tục quản lý.

Luồng phụ:   
**A1: Tìm kiếm hoặc Lọc danh sách nhân viên**

1. Tại bước 2, người chơi sử dụng thanh tìm kiếm hoặc bộ lọc (lọc theo Ngành nghề, Cấp độ, Mức lương, Trạng thái Stress).  
2. Hệ thống cập nhật danh sách hiển thị theo các tiêu chí được chọn.

**A2: Sắp xếp danh sách nhân viên**

1. Tại bước 2, người chơi chọn sắp xếp theo Năng suất (Cao/Thấp), Mức lương, hoặc Độ trung thành.  
2. Hệ thống tái sắp xếp danh sách nhân sự theo thứ tự mong muốn.

Luồng ngoại lệ: 

**E1: Danh sách nhân viên trống (Chưa có nhân viên nào)**

1. Tại bước 2, nếu công ty chưa có nhân viên (hoặc vừa giải thể toàn bộ đội ngũ).  
2. Hệ thống hiển thị màn hình trống kèm thông báo: *"Công ty chưa có nhân viên nào. Hãy tuyển dụng nhân sự mới\!"*  
3. Hệ thống làm nổi bật nút **"Tuyển dụng"** (UC12.3) để gợi ý người chơi thao tác.

**E2: Mất kết nối máy chủ khi đang xem dữ liệu**

1. Tại bước 2, nếu kết nối mạng bị gián đoạn khi đang truy xuất thông số thời gian thực.  
2. Hệ thống hiển thị thông báo: *"Không thể tải dữ liệu nhân sự. Vui lòng kiểm tra lại kết nối mạng."*  
3. Cho phép người chơi nhấn nút "Tải lại" (Reload).

Quy tắc nghiệp vụ:

**BR1: Cập nhật dữ liệu thời gian thực (Real-time Sync):** Các chỉ số Năng suất, Stress và Độ trung thành phải được hệ thống tính toán và cập nhật liên tục (theo chu kỳ gian game, ví dụ: mỗi ngày/tuần trong game).

**BR2: Cảnh báo chỉ số nguy hiểm:**

* Nếu chỉ số **Stress \> 80%** hoặc **Độ trung thành \< 20%**, hệ thống phải hiển thị biểu tượng cảnh báo màu đỏ cạnh nhân viên đó.  
* Nhân viên có chỉ số Stress kéo dài ở mức 100% có tỷ lệ tự động nộp đơn xin nghỉ việc.

**BR3: Quy tắc Tổng quỹ lương:** Tổng quỹ lương hiển thị ở màn hình chung phải bằng tổng chính xác tất cả mức lương cố định \+ phụ cấp (nếu có) của toàn bộ nhân viên đang active.

**BR4: Bảo mật & Phân quyền:** Chỉ người sở hữu công ty (hoặc nhân vật được cấp quyền quản trị) mới có thể truy cập giao diện này.

**Include**  
UC12.3, UC12.4, UC12.5.  
**Extend**  
Không.  
Ghi chú: 

1. **Về Actor phụ:**  
* **Hệ thống lưu trữ/Cơ sở dữ liệu game (Server/DB):** Đóng vai trò cập nhật, tính toán các biến số thời gian thực (Stress, Năng suất, Lương) và truyền dữ liệu hiển thị lên giao diện UI của người chơi.  
2. **Thiết kế UX/UI khuyến nghị:** Nên bổ sung thanh trạng thái dạng đồ thị (Progress Bar) màu sắc (Xanh \- Vàng \- Đỏ) cho chỉ số Stress và Độ trung thành để người chơi dễ dàng quan sát trực quan.

| Mã Use Case | UC12.3  |
| :---- | :---- |
| Tên Use Case | Thuê nhân viên  |
| Mục đích | Tuyển dụng nhân sự mới để gia tăng sản lượng / năng suất công ty..  |
| Mô tả | Cho phép người chơi bỏ ra một khoản ngân sách tuyển dụng để hệ thống tìm kiếm danh sách ứng viên (CV), từ đó lựa chọn nhân sự phù hợp về kỹ năng và mức lương để ký hợp đồng lao động.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống |
| Mức ưu tiên  | Trung bình \- Cao |
| Tần suất sử dụng | Theo nhu cầu |

   
**Tiền điều kiện**

* UC12.1 (Mở công ty) đã kích hoạt.  
* Công ty chưa đạt giới hạn sức chứa nhân sự tối đa (tùy theo quy mô văn phòng hiện tại).  
* Tài khoản có đủ ngân sách cho gói nâng cấp được chọn.

**Hậu điều kiện**

* Nhân viên mới được thêm vào danh sách nhân sự của công ty.  
* Trừ chi phí tuyển dụng từ tài khoản ngân hàng  
* Tăng chỉ số hiệu suất/năng suất chung cho toàn bộ công ty  
* Tổng năng suất của công ty sẽ được tính toán tăng lên tương ứng.

**Luồng chính**

5. Người chơi truy cập tab "Nhân sự" và nhấn nút **"Đăng tuyển"**.  
6. Người chơi chọn gói ngân sách săn nhân tài (Ví dụ: Đăng tuyển phổ thông, Chiêu mộ cao cấp, Headhunter).  
7. Hệ thống trừ phí đăng tuyển tương ứng với gói đã chọn.  
8. Hệ thống tạo ngẫu nhiên (Generate) và hiển thị danh sách các hồ sơ ứng viên (CV) dựa trên mức ngân sách, bao gồm: Họ tên, Chuyên môn, Cấp kỹ năng, Mức lương đòi hỏi, Mức độ trung thành ban đầu.  
9. Người chơi duyệt danh sách và chọn ứng viên mong muốn, nhấn **"Ký Hợp Đồng"**.  
10. Hệ thống kiểm tra sức chứa văn phòng (sự liên quan từ UC12.6).  
11. Hệ thống thêm nhân viên mới vào danh sách công ty, cập nhật lại chỉ số tổng năng suất và hiển thị thông báo "Tuyển dụng thành công".

Luồng phụ:   
**A1: Làm mới (Refresh) danh sách ứng viên**

1. Tại bước 4, nếu không chọn được ứng viên ưng ý, người chơi nhấn nút **"Làm mới danh sách"**.  
2. Hệ thống trừ một khoản phí làm mới nhỏ và hiển thị dàn ứng viên (CV) mới.  
3. Quay lại bước 5 của luồng chính.

**A2: Người chơi bỏ qua / Không tuyển ai**

1. Tại bước 4, người chơi xem danh sách nhưng nhấn **"Đóng"** hoặc **"Hủy"**.  
2. Hệ thống hủy danh sách ứng viên tạm thời, giữ nguyên phí đăng tuyển đã trừ trước đó và kết thúc Use Case.

Luồng ngoại lệ: 

**E1: Văn phòng đã đầy (Đạt giới hạn nhân sự)**

1. Tại bước 1 hoặc bước 6, hệ thống phát hiện số lượng nhân viên hiện tại đã đạt sức chứa tối đa của văn phòng (UC12.6).  
2. Hệ thống hiển thị thông báo: *"Văn phòng đã hết chỗ ngồi. Vui lòng mở rộng/nâng cấp văn phòng (UC12.6) trước khi tuyển thêm nhân sự\!"*  
3. Hệ thống vô hiệu hóa nút "Ký Hợp Đồng" và kết thúc Use Case.

**E2: Không đủ tiền trả phí đăng tuyển**

1. Tại bước 2, người chơi chọn gói đăng tuyển nhưng số dư tài khoản không đủ.  
2. Hệ thống hiển thị thông báo: *"Số dư tài khoản không đủ để thực hiện đăng tuyển gói này."*  
3. Người chơi chọn lại gói rẻ hơn hoặc hủy thao tác.

**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC12.4 |
| :---- | :---- |
| Tên Use Case | Sa thải  |
| Mục đích | Loại bỏ nhân viên có năng suất kém hoặc để cắt giảm chi phí vận hành.  |
| Mô tả | Cho phép người chơi chấm dứt hợp đồng lao động với một nhân sự cụ thể. Hệ thống sẽ tính toán mức phí đền bù (nếu có), giải phóng vị trí làm việc và cập nhật lại quỹ lương cùng năng suất chung của doanh nghiệp.  |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng | Theo nhu cầu |

   
**Tiền điều kiện**

* Công ty có ít nhất 1 nhân viên trong danh sách.  
* Người chơi đã chọn 1 nhân sự cụ thể trong giao diện Quản lý nhân viên.

**Hậu điều kiện**

* Nhân sự được chọn bị xóa khỏi danh sách công ty.  
* Trừ tiền đền bù hợp đồng (nếu có) từ tài khoản công ty.  
* Tổng quỹ lương định kỳ và tổng năng suất của công ty giảm tương ứng.

**Luồng chính**

12. Tại giao diện Quản lý nhân viên (UC12.2), người chơi chọn một nhân viên cụ thể và nhấn nút **"Sa thải"**.  
13. Hệ thống tính toán phí đền bù hợp đồng (dựa trên mức lương hiện tại và số ngày còn lại trong hợp đồng/độ trung thành) và hiển thị hộp thoại xác nhận kèm số tiền đền bù.  
14. Người chơi xác nhận đồng ý sa thải.  
15. Hệ thống kiểm tra số dư ngân hàng và thực hiện trừ tiền đền bù hợp đồng từ tài khoản.  
16. Hệ thống xóa nhân viên khỏi danh sách công ty, giải phóng 01 vị trí sức chứa văn phòng.  
17. Hệ thống tự động tính toán lại và giảm quỹ lương định kỳ, giảm tổng năng suất công ty tương ứng.  
18. Hiển thị thông báo *"Đã sa thải nhân viên \[Tên nhân viên\] thành công"* và cập nhật lại giao diện UC12.2.

Luồng phụ: 

**A1: Người chơi hủy thao tác sa thải**

1. Tại bước 2, sau khi nhìn thấy mức phí đền bù hợp đồng, người chơi chọn **"Hủy"** hoặc đóng hộp thoại.  
2. Hệ thống hủy thao tác, giữ nguyên trạng thái nhân viên và quay lại giao diện UC12.2.

Luồng ngoại lệ: 

**E1: Không đủ tiền trả phí đền bù hợp đồng**

1. Tại bước 4, số dư tài khoản ngân hàng của công ty/người chơi ít hơn khoản phí đền bù bắt buộc.  
2. Hệ thống hiển thị cảnh báo: *"Không đủ tiền trong tài khoản để trả phí đền bù sa thải (\$\[Số tiền\]). Thao tác bị hủy."*  
3. Hệ thống giữ nguyên trạng thái nhân viên và dừng Use Case.

**E2: Nhân viên đang thực hiện nhiệm vụ đặc biệt không thể sa thải**

1. Tại bước 1, nhân viên được chọn đang trực tiếp tham gia một dự án/nhiệm vụ quan trọng chưa hoàn thành.  
2. Hệ thống hiển thị thông báo: *"Nhân viên đang phụ trách dự án. Cần hủy dự án hoặc chờ hoàn thành trước khi sa thải\!"*  
3. Thao tác bị hủy.

***Quy tắc nghiệp vụ:***

1. **Quy tắc phí đền bù:**  
* Nếu sa thải nhân viên trước thời hạn hợp đồng hoặc khi chỉ số Độ trung thành/Sự hài lòng còn cao, công ty phải trả phí đền bù:

* $Phí\ Đền\ Bù=Mức\ Lương\ Tháng\times Hệ\ Số\ Đền\ Bù(ví\ dụ:1.5-2.0)$  
* Nếu nhân viên có chỉ số Stress \= 100% hoặc vi phạm quy định (nếu game có cơ chế này), phí đền bù có thể bằng $0$.  
2. **Không âm tài khoản:** Giao dịch trừ phí đền bù sa thải tuân thủ quy tắc không cho phép số dư bị âm.  
3. **Lịch sử giao dịch:** Mọi thao tác sa thải và biến động tài chính liên quan đều phải ghi lại lịch sử (Log). 

**Include**  
Không.  
**Extend**  
Không.

***Ghi chú:***  
**Về Actor phụ:**

* **Hệ thống ngân hàng/Tài chính:** Xác thực và thực hiện trừ tiền đền bù sa thải từ tài khoản của người chơi.  
* **Hệ thống quản lý dữ liệu (Server/Database):** Thực hiện xóa ID nhân viên, giải phóng slot sức chứa văn phòng và cập nhật lại chỉ số tổng năng suất / tổng quỹ lương.

**Hiệu ứng tâm lý tập thể (Gợi ý mở rộng gameplay):** Có thể thiết lập quy tắc phụ: Việc sa thải nhân viên liên tục trong thời gian ngắn sẽ làm giảm nhẹ độ trung thành của các nhân viên còn lại trong công ty.

| Mã Use Case | UC12.5 |
| :---- | :---- |
| Tên Use Case | Trả lương |
| Mục đích | Chi trả tiền lương định kỳ để duy trì sự hài lòng và năng suất nhân viên  |
| Mô tả | Hệ thống tự động hoặc cho phép người chơi chủ động thực hiện chi trả quỹ lương định kỳ (cuối tháng/cuối kỳ in-game) cho toàn bộ nhân sự. Xử lý các kịch bản duy trì động lực làm việc khi trả đủ lương hoặc gánh chịu hậu quả (giảm độ trung thành, tăng stress, đình công/nghỉ việc) khi nợ lương.  |
| Actor | Chính: Người chơi Phụ: Hệ thống quản lý dữ liệu game, ngân hàng/tài chính, lịch/thời gian in-game  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Định kỳ (theo chu kỳ thời gian in-game) |

   
**Tiền điều kiện**

* Kích hoạt đến chu kỳ/thời điểm trả lương định kỳ (cuối tháng in-game).  
* Công ty đang có ít nhất 01 nhân viên.

**Hậu điều kiện**

* **Trường hợp thành công:** Số dư tài khoản bị trừ tương ứng với tổng quỹ lương; chỉ số Trung thành của nhân viên giữ nguyên hoặc tăng.  
* **Trường hợp thất bại (Không đủ tiền):** Ghi nhận nợ lương; chỉ số Trung thành nhân viên giảm mạnh; kích hoạt cảnh báo nguy cơ đình công/nghỉ việc hàng loạt và chỉ số Stress tăng mạnh.

**Luồng chính**

19. Đến thời điểm trả lương định kỳ (cuối kỳ/tháng in-game), Hệ thống Thời gian kích hoạt sự kiện **Chi trả lương**.  
20. Hệ thống tính toán **Tổng quỹ lương** từ danh sách nhân sự hiện tại (UC12.2).  
21. Hệ thống kiểm tra số dư tài khoản ngân hàng của công ty/người chơi.  
22. Hệ thống thực hiện trừ tiền tương ứng với Tổng quỹ lương từ tài khoản.  
23. Hệ thống cập nhật trạng thái đã thanh toán lương cho tất cả nhân viên.  
24. Chỉ số **Độ trung thành** của nhân viên giữ nguyên (hoặc tăng nếu có thưởng thêm).  
25. Hệ thống hiển thị thông báo/báo cáo tài chính: *"Đã chi trả thành công \$\[Số tiền\] tiền lương cho \[Số lượng\] nhân viên"* và ghi lịch sử giao dịch.

Luồng thay thế: 

**A1: Trả lương thủ công trước hạn / Tăng thưởng (Bonus)**

1. Người chơi chủ động truy cập giao diện UC12.2 và chọn nút **"Thanh toán/Thưởng thêm"** trước ngày chốt sổ.  
2. Người chơi chọn mức thưởng thêm (%) cho nhân viên.  
3. Hệ thống trừ tiền tài khoản và lập tức cộng thêm chỉ số **Độ trung thành (+10% đến \+20%)** cho đội ngũ.

Luồng ngoại lệ: 

**E1: Không đủ tiền thanh toán (Nợ lương lần 1 \- Trễ 1 chu kỳ)**

1. Tại bước 3, số dư tài khoản ngân hàng ít hơn Tổng quỹ lương cần trả.  
2. Hệ thống không thể trừ đủ tiền và đánh dấu trạng thái **"Trễ lương"**.  
3. Chỉ số **Độ trung thành** của toàn bộ nhân viên giảm 50%, chỉ số **Stress** tăng lên.  
4. Hệ thống phát màn hình cảnh báo đỏ: *"Tài khoản không đủ tiền trả lương\! Nhân viên đang bất mãn và có nguy cơ nghỉ việc."*

**E2: Nợ lương kéo dài (Trễ lương quá 3 ngày/chu kỳ in-game)**

1. Nếu trạng thái trễ lương kéo dài quá 3 ngày/chu kỳ mà người chơi vẫn không nạp đủ tiền thanh toán.  
2. Toàn bộ hoặc đa số nhân viên đồng loạt **Đình công / Nộp đơn nghỉ việc** (xóa khỏi danh sách nhân sự).  
3. Hệ thống áp phạt: Nhân vật chính (người chơi) nhận ngay **\+30% Stress**.  
4. Mọi hoạt động kinh doanh/sản xuất của công ty bị ngưng trệ hoàn toàn.

**Include**  
Không.  
**Extend**  
UC12.1.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Ưu tiên trừ tiền:** Tiền lương được tự động trừ từ Tài khoản Ngân hàng Công ty trước, nếu không đủ sẽ cấn trừ tiếp sang Tài khoản Ngân hàng Cá nhân của người chơi (nếu cài đặt chế độ liên thông).  
2. **Nguyên tắc không âm tài khoản:** Nếu cả 2 tài khoản không đủ thanh toán 100% quỹ lương, hệ thống dừng giao dịch và chuyển sang luồng ngoại lệ E1/E2 (không được trừ tiền về số âm).  
3. **Lưu lịch sử giao dịch:** Mọi khoản chi trả lương hoặc nợ lương đều phải được ghi lại lịch sử giao dịch tài chính (Log).  
4. **Cơ chế tính điểm đền bù:** Nếu trả bù tiền nợ lương kèm phạt muộn trước 3 ngày, chỉ số Độ trung thành sẽ hồi phục một phần (khoảng 50% lượng bị sụt giảm).

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống Lịch/Thời gian in-game (Time Manager):** Theo dõi chu kỳ thời gian trong game để đếm ngược và kích hoạt sự kiện trả lương định kỳ.  
  * **Hệ thống ngân hàng/Tài chính:** Xác thực số dư, xử lý lệnh trừ quỹ lương và ghi lại log giao dịch.  
  * **Hệ thống dữ liệu (Server/DB):** Cập nhật chỉ số Trung thành, Stress của nhân viên và Stress của Nhân vật chính.  
* **Lưu ý quan hệ Extend:** Trong mô tả có đề cập `Extend UC12.1`, điều này có nghĩa là khi công ty đã được thành lập (UC12.1) thì cơ chế trả lương (UC12.5) mới được kích hoạt đính kèm theo vòng đời hoạt động của doanh nghiệp.

| Mã Use Case | UC12.6 |
| :---- | :---- |
| Tên Use Case | Nâng cấp công ty |
| Mục đích | Đầu tư cơ sở vật chất để mở rộng quy mô tuyển dụng và tăng hiệu suất  |
| Mô tả | Cho phép người chơi bỏ ra một khoản vốn đầu tư để nâng cấp văn phòng, mua sắm máy móc thiết bị mới hoặc bổ sung tiện ích (Pantry, phòng nghỉ...). Hệ thống sẽ tính toán cộng thêm sức chứa nhân sự tối đa và buff hiệu suất/giảm stress cho toàn bộ nhân viên.  |
| Actor | Chính: Người chơi  Phụ: Hệ thống ngân hàng, cơ sở dữ liệu game |
| Mức ưu tiên | Trung bình |
| Tần suất sử dụng | Theo nhu cầu |

   
**Tiền điều kiện**

* **UC12.1 (Mở công ty)** đã hoàn tất thành công và công ty đang hoạt động.  
* Cấp độ văn phòng / trang thiết bị hiện tại chưa đạt cấp tối đa (Max Level).  
* Tài khoản ngân hàng công ty/cá nhân có đủ số tiền chi trả cho gói nâng cấp được chọn.

**Hậu điều kiện**

* Trừ số tiền chi phí nâng cấp từ tài khoản ngân hàng.  
* Cấp độ văn phòng / cơ sở vật chất của công ty được cập nhật lên cấp mới.  
* Tăng giới hạn sức chứa nhân sự tối đa (giúp phục vụ cho **UC12.3: Thuê nhân viên**).  
* Tăng chỉ số hiệu suất làm việc chung (+10% hoặc tùy theo gói) và/hoặc giảm tốc độ tăng Stress cho nhân viên..

**Luồng chính**

1. Tại giao diện Quản lý công ty, người chơi chọn mục **"Nâng cấp văn phòng / Máy móc"**.  
2. Hệ thống hiển thị danh sách các danh mục/gói nâng cấp khả dụng, bao gồm:  
* **Mở rộng văn phòng:** Tăng sức chứa nhân viên tối đa.  
* **Nâng cấp trang thiết bị (Máy tính, bàn ghế):** Tăng % hiệu suất làm việc chung.  
* **Tiện ích nội bộ (Pantry cà phê, phòng giải trí):** Giảm tỷ lệ tăng Stress của nhân sự.  
3. Người chơi chọn gói nâng cấp mong muốn và nhấn **"Xác nhận thanh toán"**.  
4. Hệ thống kiểm tra điều kiện số dư tài khoản ngân hàng và cấp độ tối đa.  
5. Hệ thống thực hiện trừ chi phí nâng cấp từ tài khoản ngân hàng.  
6. Hệ thống cập nhật cấp độ mới cho cơ sở vật chất, tự động gia tăng giới hạn nhân sự tối đa (UC12.3) và cộng \+10% hiệu suất làm việc chung (hoặc giảm Stress tương ứng).  
7. Hiển thị thông báo *"Nâng cấp thành công\!"* và thay đổi diện mạo/giao diện văn phòng mới (nếu có).

##### **Luồng phụ / Luồng thay thế**

* **A1: Người chơi thay đổi ý định / Hủy nâng cấp**  
  1. Tại bước 3, người chơi xem các gói nâng cấp nhưng nhấn **"Hủy"** hoặc đóng cửa sổ giao diện.  
  2. Hệ thống đóng danh mục nâng cấp, không trừ tiền và giữ nguyên trạng thái công ty.

##### **Luồng ngoại lệ**

* **E1: Không đủ tiền thanh toán gói nâng cấp**  
  1. Tại bước 4, số dư tài khoản ngân hàng của người chơi ít hơn chi phí của gói nâng cấp đã chọn.  
  2. Hệ thống hiển thị cảnh báo: *"Số dư tài khoản không đủ để thực hiện nâng cấp này (Thiếu \$\[Số tiền\])."*  
  3. Hệ thống vô hiệu hóa nút thanh toán của gói đó và giữ nguyên trạng thái.  
* **E2: Đã đạt cấp độ nâng cấp tối đa (Max Level)**  
  1. Tại bước 1 hoặc 2, danh mục nâng cấp đã đạt cấp độ cao nhất trong hệ thống.  
  2. Hệ thống hiển thị nhãn **"Đã tối đa (MAX)"** và vô hiệu hóa nút mua.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Không cho phép số dư âm:** Thao tác nâng cấp bắt buộc phải tuân thủ quy tắc số dư tài khoản $\geq Chi\ Phí\ Nâng\ Cấp$, không được trừ về số âm.  
2. **Cộng dồn chỉ số (Stacking Buffs):** Các chỉ số cộng thêm từ việc nâng cấp (sức chứa, hiệu suất) được cộng dồn vĩnh viễn vào thuộc tính của công ty, ngoại trừ trường hợp công ty bị giải thể hoặc phá sản.  
3. **Lịch sử giao dịch:** Mọi khoản chi phí nâng cấp đều phải được ghi lại lịch sử giao dịch tài chính (Log).

**Include**  
Không.  
**Extend**  
UC12.1.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống ngân hàng/Tài chính:** Xác thực số dư và thực hiện lệnh chuyển/trừ tiền chi phí nâng cấp.  
  * **Hệ thống quản lý dữ liệu (Server/Database):** Cập nhật thuộc tính cấp độ văn phòng, tính toán lại giới hạn nhân sự tối đa và hiệu suất toàn công ty.  
* **Mối liên hệ với các UC khác:** Kết quả nâng cấp của UC12.6 sẽ nới rộng giới hạn sức chứa cho **UC12.3 (Thuê nhân viên)**, đồng thời tác động tích cực đến chỉ số năng suất hiển thị tại **UC12.2 (Quản lý nhân viên)**.

**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC13 | Nâng cấp kỹ năng | Tổng quát |
| UC13.1 | Xem kỹ năng  | Base UC (Gọi UC13.2, UC13.3 và UC13.4) |
| UC13.2 | Học kỹ năng | Được gọi bởi UC13.1  |
| UC13.3 | Nâng cấp kỹ năng | Gọi UC13.2.  |
| UC13.4 | Trang bị kỹ năng | Được gọi bởi UC13.3. |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC13.1 (Xem kỹ năng) | UC13.2, UC13.3, UC13.4  | Không  | Base Use Case: Khi mở giao diện Xem kỹ năng, hệ thống tự động tải và hiển thị tích hợp cả 3 chức năng: Học, Nâng cấp và Trang bị  |
| UC13.2 (Học kỹ năng)  | Không  | Không  |  |
| UC13.3 (Nâng cấp kỹ năng)  | Không  | UC13.2  | Khi người chơi chọn Nâng cấp một kỹ năng (UC14.3), nếu kỹ năng đó chưa học hoặc đạt mốc yêu cầu, hệ thống sẽ mở rộng/chèn luồng UC14.2 (Học kỹ năng) để người chơi hoàn thành điều kiện trước   |
| UC13.4 (Trang bị kỹ năng)  | UC13.3  | Không  | Khi người chơi thao tác trên ô Trang bị kỹ năng, hệ thống tự động gọi/kiểm tra cấp độ kỹ năng từ UC14.3 để áp dụng đúng thông số buff tương ứng  |

**Đặc tả UC13**

| Mã Use Case | UC13 |
| :---- | :---- |
| Tên Use Case | Nâng cấp kỹ năng |
| Mục đích | Cho phép người chơi sử dụng Điểm Kỹ Năng (Skill Points/SP) hoặc tiền/thời gian học tập để nâng cấp các nhóm chỉ số kỹ năng, hỗ trợ trực tiếp khả năng kiếm tiền và sinh tồn. |
| Mô tả | Khi người chơi mở mục Kỹ năng, người chơi sẽ sử dụng điểm kỹ năng để nâng cấp hoặc phải dùng tiền và thời gian để có kỹ năng nhằm cải thiện chỉ số, khả năng kiếm tiền,  |
| Actor | Người chơi  |
| Mức ưu tiên | ?? |
| Tần suất sử dụng | Mỗi lần mở mục cây kỹ năng |

Trigger  
Người chơi chọn biểu tượng “Kỹ năng / Cây Kỹ năng” trên giao diện điện thoại/màn hình cá nhân hoặc tương tác với Tủ sách/Máy tính.  
Tiền điều kiện

* Đã hoàn thành Tutorial (ngày 1).  
* Có đủ điểm Kỹ năng (nhận từ Level Up, Làm việc hay mở khóa thành tựu) hoặc có đủ tiền để tham gia khóa học. 

Hậu điều kiện

* Cấp độ kỹ năng mới được ghi nhận.  
* Các hiệu ứng bổ trợ như tăng lương, giảm tiêu hao Stress, tăng tỷ lệ đầu tư được kích hoạt ngay lập tức.

Luồng chính

1. Người chơi mở giao diện Cây Kỹ Năng (Skill Tree).  
2. Hệ thống hiển thị sơ đồ kỹ năng, cấp độ hiện tại, số Điểm Kỹ Năng (SP) đang có và điều kiện để nâng cấp tiếp theo.  
3. Người chơi chọn một kỹ năng mong muốn và nhấn nút "Nâng Cấp".  
4. Hệ thống kiểm tra điều kiện (Đủ SP, đủ cấp độ tiền đề).  
5. Hệ thống trừ số Điểm Kỹ Năng tương ứng, tăng cấp kỹ năng và kích hoạt hiệu ứng bổ trợ (Buff).  
6. Hệ thống lưu dữ liệu và hiển thị thông báo nâng cấp thành công.  
   

Luồng phụ 1 (Include Flow \- Mở khóa thành tựu)

1. Người chơi tương tác với Laptop/Điện thoại và chọn "Đăng ký Khóa học Online".  
2. Hệ thống kiểm tra Tài khoản ngân hàng.  
3. Nếu đủ tiền: Trừ tiền khóa học $\rightarrow$ Nhân vật tốn một khoảng thời gian in-game (ví dụ: 4 tiếng) để học $\rightarrow$ Tăng điểm kỹ năng tương ứng \+ Tăng nhẹ Stress.

Luồng phụ 2 (Extend Flow \- Mở khóa từ giao diện xem):

1. Khi mở khóa các Thành tựu đặc biệt trong UC15, hệ thống gọi hàm trao thưởng.  
2. Tự động cộng Điểm Kỹ Năng Thưởng hoặc mở khóa thẳng một Node Kỹ năng Ẩn (ví dụ: Kỹ năng “Lội Ngược Dòng” giúp tăng 20% thu nhập khi tiền mặt \<1 000\$).

Luồng thay thế / ngoại lệ (A: luồng thay thế, B: Luồng ngoại lệ):  
A1: Không đủ điểm kỹ năng / Chưa đủ tiền: Nút “Nâng Cấp” bị làm mờ. Hệ thống hiển thị gợi ý cách kiếm thêm SP.   
A2: Lối chơi “Thất nghiệp”: Người chơi tập trung nâng tối đa Nhánh Sinh Tồn & Tài Chính \-\> Mở khóa kỹ năng đặc biệt “Đội Đồ Ngủ Kiếm Triệu Đô” (tăng 25% doanh thu Freelance tại nhà)  
B1: Nhân vật trong trạng thái sốc thuốc / kiệt sức (Stress 100% / Health 0%) \-\> Hệ thống khóa giao diện Nâng cấp kỹ năng, buộc người chơi phải cấp cứu / hồi phục trước khi học kỹ năng mới.

| Mã Use Case | UC13.1  |
| :---- | :---- |
| Tên Use Case | Xem kỹ năng  |
| Mục đích | Hiển thị toàn bộ sơ đồ kỹ năng, cấp độ hiện tại, số Điểm Kỹ Năng (SP) khả dụng và các ô (Slots) kỹ năng đang trang bị.  |
| Mô tả | Cho phép người chơi truy cập màn hình quản lý kỹ năng nhân vật để theo dõi tiến trình phát triển, kiểm tra số điểm kỹ năng tích lũy, các ô trang bị kỹ năng kích hoạt, đồng thời làm giao diện trung tâm để điều hướng tới các thao tác học, nâng cấp và trang bị kỹ năng.  |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu |

   
**Tiền điều kiện**

* Người chơi đã đăng nhập vào game và hoàn thành khởi tạo nhân vật (UC03).  
* Người chơi truy cập vào Menu Nhân vật hoặc ứng dụng Kỹ năng trên Điện thoại/UI in-game.

**Hậu điều kiện**

* Giao diện cây kỹ năng, điểm SP khả dụng và trạng thái các ô trang bị (Slots) được hiển thị chính xác theo thời gian thực.  
* Sẵn sàng cho phép người chơi điều hướng và thực hiện các tác vụ con (`<<include>>` UC13.2, UC13.3, UC13.4).

**Luồng chính**

1. Người chơi nhấn chọn biểu tượng **"Kỹ Năng"** trên giao diện người dùng (UI / Menu / Điện thoại).  
2. Hệ thống truy xuất và tải dữ liệu kỹ năng của nhân vật từ Save File / Database.  
3. Hệ thống hiển thị giao diện chính bao gồm:  
* **Thông tin chung:** Số Điểm Kỹ Năng (SP) khả dụng, Cấp độ nhân vật.  
* **Cây kỹ năng (Skill Tree):** Phân chia theo 4 nhánh chuyên môn (ví dụ: Quản trị, Kinh doanh, Sáng tạo, Kỹ thuật).  
* **Bảng Ô trang bị (Equip Slots):** Hiển thị các kỹ năng đang được gắn vào ô kích hoạt.  
4. Hệ thống tích hợp và tải sẵn dữ liệu hiển thị cho các tác vụ con:  
* Trạng thái các khóa học / kỹ năng mở khóa (`<<include>>` **UC13.2: Học kỹ năng**).  
* Cấp độ kỹ năng hiện tại và điều kiện nâng cấp (`<<include>>` **UC13.3: Nâng cấp kỹ năng**).  
* Danh sách kỹ năng đang gán vào các ô Slot (`<<include>>` **UC13.4: Trang bị kỹ năng**).  
5. Người chơi xem thông tin chi tiết hoặc chọn tương tác với các nút chức năng.  
6. Người chơi chọn nút **"Đóng"** hoặc bấm phím tắt quay lại để thoát giao diện.

##### **Luồng phụ / Luồng thay thế (Alternative Flow)**

* **A1: Xem chi tiết một kỹ năng cụ thể**  
  1. Tại bước 3, người chơi nhấp/rê chuột vào một biểu tượng kỹ năng bất kỳ trên Cây kỹ năng.  
  2. Hệ thống hiển thị bảng thông báo nhỏ (Tooltip/Pop-up) chứa thông tin: Tên kỹ năng, Mô tả tác dụng, Cấp độ hiện tại/Tối đa, Chi phí nâng cấp (SP/Tiền) và Điều kiện tiên quyết.  
* **A2: Chuyển đổi giữa các nhánh Cây kỹ năng**  
  1. Tại bước 3, người chơi chuyển tab giữa 4 nhánh kỹ năng khác nhau.  
  2. Hệ thống cập nhật sơ đồ hiển thị tương ứng với nhánh kỹ năng được chọn.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Lỗi tải dữ liệu Save File / Mất kết nối máy chủ**  
  1. Tại bước 2, hệ thống không thể đọc được dữ liệu kỹ năng từ Save File hoặc gặp sự cố kết nối Server.  
  2. Hệ thống hiển thị thông báo lỗi: *"Không thể tải dữ liệu kỹ năng. Vui lòng thử lại\!"*  
  3. Màn hình quay lại trạng thái Menu trước đó.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Đồng bộ dữ liệu (Real-time Sync):** Số điểm SP và trạng thái các ô Slot hiển thị phải luôn chính xác và đồng bộ hoàn toàn với Save File / Database tại thời điểm mở giao diện.  
2. **Quy tắc hiển thị ô trang bị (Slots):** Số lượng ô trang bị hiển thị (Slots) phải thể hiện rõ trạng thái: *Đã mở khóa*, *Đang khóa (Yêu cầu cấp độ/tiền để mở)*, hoặc *Đã gán kỹ năng*.  
3. **Phân nhánh kỹ năng:** Các kỹ năng thuộc cấp cao hơn trong Cây kỹ năng chỉ hiển thị trạng thái khả dụng khi các kỹ năng rễ/tiền đề đã đạt cấp độ tối thiểu.

**Include**  
UC13.2, UC13.3, UC13.4.  
**Extend**  
Không.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống quản lý dữ liệu game (Server/Save File Database):** Chịu trách nhiệm cung cấp dữ liệu cấu trúc kỹ năng, điểm SP, level hiện tại và lưu giữ trạng thái giao diện khi người chơi đóng màn hình.

| Mã Use Case | UC13.2  |
| :---- | :---- |
| Tên Use Case | Học kỹ năng  |
| Mục đích | Cho phép người chơi bỏ tiền (UC11) hoặc thời gian in-game để học và mở khóa các node kỹ năng mới..  |
| Mô tả | Cho phép người chơi chọn và đăng ký các khóa học/node kỹ năng chưa từng sở hữu. Quá trình học sẽ tiêu tốn học phí, thể lực, thời gian in-game và làm tăng chỉ số Stress tùy thuộc vào độ khó của khóa học. Khi hoàn tất, kỹ năng sẽ chính thức mở khóa ở Cấp 1\.  |
| Actor | Chính: Người chơi Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng  | Theo nhu cầu |

   
Tiền điều kiện

* Nhân vật đạt cấp độ và điều kiện rễ/tiền đề của cây kỹ năng (nếu có).  
* Đủ điều kiện tài chính (Số dư tài khoản $\geq$ Học phí khóa học).  
* Nhân vật có đủ Thể lực (Energy) để bắt đầu khóa học.

Hậu điều kiện

* Node kỹ năng chuyển trạng thái từ **Đã khóa (Locked)** $\rightarrow$ **Đã học (Unlocked \- Cấp 1\)**.  
* Trừ tiền học phí từ tài khoản (UC11) và trừ Thể lực (Energy) của nhân vật.  
* Thời gian in-game được tua nhanh tương ứng với thời lượng khóa học.  
* Chỉ số **Stress** của nhân vật tăng thêm tùy theo độ khó của khóa học.

Luồng chính

1. Từ giao diện Xem kỹ năng (UC13.1), người chơi chọn một node kỹ năng chưa mở khóa và nhấn **"Đăng Ký Học"**.  
2. Hệ thống kiểm tra điều kiện số dư ngân hàng (UC11), Thể lực (Energy) và Stress hiện tại của nhân vật.  
3. Hệ thống trừ chi phí khóa học từ tài khoản ngân hàng và trừ \$20\\% \- 40\\%\$ Thể lực (Energy).  
4. Hệ thống tua nhanh một lượng thời gian in-game (ví dụ: $4$ tiếng in-game).  
5. Chỉ số Stress của nhân vật tăng thêm từ \$15\\% \- 30\\%\$ (phụ thuộc vào độ khó của khóa học).  
6. Kỹ năng chính thức được mở khóa ở Cấp 1 (Level 1).  
7. Hệ thống hiển thị thông báo "Học kỹ năng thành công\!" và cập nhật giao diện Cây kỹ năng (UC13.1).

Luồng mở rộng (`<<extend>>` từ UC13.3):

* Khi người chơi nhấn "Nâng cấp kỹ năng" (UC13.3) cho một kỹ năng chưa từng được học, hệ thống chèn luồng UC13.2 để yêu cầu người chơi thanh toán chi phí đăng ký học ban đầu trước khi cho phép tăng Level. 

Luồng thay thế:

**A1: Học khi cơ thể mệt mỏi (Health \< 20%)**

1. Tại bước 2, hệ thống phát hiện chỉ số Sức khỏe (Health) của nhân vật \<20%.  
2. Hệ thống hiển thị cảnh báo: *"Cơ thể đang suy nhược, việc học sẽ tốn gấp đôi thời gian và tích tụ nhiều Stress hơn\!"*  
3. Nếu người chơi tiếp tục: Thời gian học kéo dài gấp 2 lần (ví dụ: $8$ tiếng in-game) và lượng Stress gánh chịu tăng thêm 50% so với mức cơ sở.  
4. Tiếp tục bước 3 của luồng chính.

**A2: Luồng mở rộng từ UC13.3 (Nâng cấp kỹ năng)**

1. Khi người chơi nhấn "Nâng cấp" (UC13.3) cho một kỹ năng chưa từng được học (Level 0).  
2. Hệ thống tự động kích hoạt luồng UC13.2 để yêu cầu người chơi thanh toán chi phí đăng ký học ban đầu trước khi cho phép tăng Level.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Quy tắc tính tổn hại (Penalty Rules):**  
   * **Tốn Thể lực:** Tiêu hao \-20% đến \-40% Energy per course.  
   * **Tăng Stress:** \+15% đến \+30% Stress per course.  
   * **Phạt Mệt mỏi (Health \< 20%):** Thời gian học $\times 2$, Lượng Stress \+50%.  
2. **Ngưỡng an toàn (Burnout Threshold):** Ngăn chặn học kỹ năng mới khi Stress \> 80%. Đưa nhân vật vào trạng thái cần can thiệp y tế.  
3. **Quy tắc tài chính:** Tiền học phí không được trừ về số âm và mọi giao dịch thanh toán khóa học phải lưu vào lịch sử tài chính.

Include  
Không.  
Extend  
Không.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống quản lý chỉ số (Health/Energy/Stress Manager):** Chịu trách nhiệm kiểm tra ngưỡng, tính toán lượng hao hụt Energy, gia tăng Stress và áp dụng hiệu ứng tiêu cực (Burnout/Cấp cứu).  
  * **Hệ thống thời gian in-game:** Thực hiện cộng dồn/tua nhanh thời gian tương ứng với thời lượng khóa học.

| Mã Use Case | UC13.3  |
| :---- | :---- |
| Tên Use Case | Nâng cấp kỹ năng  |
| Mục đích | Sử dụng Điểm Kỹ Năng (SP) để tăng Level kỹ năng đã học, gia tăng chỉ số hiệu ứng bổ trợ (Buffs)..  |
| Mô tả | Cho phép người chơi tăng cấp độ các kỹ năng đã sở hữu nhằm tối ưu hóa các chỉ số bổ trợ (buff) cho nhân vật. Trong trường hợp kỹ năng chưa được học (Cấp 0), hệ thống sẽ điều hướng người chơi thực hiện đăng ký học ban đầu (UC13.2) trước khi cho phép nâng cấp.  |
| Actor | Chính: Người chơiPhụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng  | Theo nhu cầu |

   
Tiền điều kiện

* Kỹ năng đã ở trạng thái **Đã học** (Level $\geq 1$).  
* Người chơi tích lũy đủ Điểm Kỹ Năng (SP) và/hoặc Tiền theo yêu cầu của cấp độ tiếp theo.  
* Cấp độ kỹ năng hiện tại chưa đạt mức tối đa (Max Level).

Hậu điều kiện

* Cấp độ kỹ năng (Skill Level) tăng lên $1$ cấp.  
* Trừ số điểm SP và/hoặc Tiền tương ứng khỏi tài khoản/nhân vật.  
* Các chỉ số hiệu ứng bổ trợ (Buffs/Passives) của kỹ năng được cập nhật ngay lập tức vào thuộc tính nhân vật.

Luồng chính

1. Từ màn hình Cây kỹ năng (UC13.1), người chơi chọn một node kỹ năng đã học và nhấn nút **"Nâng Cấp"**.  
2. Hệ thống kiểm tra điều kiện nâng cấp (Số điểm SP khả dụng, Tiền, Cấp độ tối đa, Cấp độ nhân vật yêu cầu).  
3. Hệ thống thực hiện trừ số điểm SP (và Tiền) yêu cầu từ tài khoản/nhân vật.  
4. Hệ thống tăng Cấp độ (Level) kỹ năng lên $+1$.  
5. Hệ thống tính toán và cập nhật lại chỉ số hiệu ứng bổ trợ (Buffs) mới cho nhân vật.  
6. Hệ thống hiển thị hiệu ứng tăng cấp thành công và cập nhật lại thông số trên giao diện UC13.1.

Luồng mở rộng (`<<extend>>` từ UC13.3):

* Khi người chơi nhấn "Nâng cấp kỹ năng" (UC13.3) cho một kỹ năng chưa từng được học, hệ thống chèn luồng UC13.2 để yêu cầu người chơi thanh toán chi phí đăng ký học ban đầu trước khi cho phép tăng Level

##### **Luồng phụ / Luồng thay thế**

* **A1: Nâng cấp khi kỹ năng chưa được học (Mở rộng từ UC13.2)**  
  1. Tại bước 1, người chơi chọn một node kỹ năng chưa từng được học (Level 0\) và nhấn **"Nâng Cấp"**.  
  2. Hệ thống phát hiện kỹ năng chưa được khởi tạo và kích hoạt luồng mở rộng `<<extend>>` gọi **UC13.2: Học kỹ năng**.  
  3. Người chơi thực hiện thanh toán học phí và học kỹ năng ở Level 1 theo quy trình UC13.2.  
  4. Sau khi học xong thành công, hệ thống quay trở lại giao diện để người chơi tiếp tục thực hiện nâng cấp lên các level tiếp theo (nếu đủ điều kiện).

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Không đủ Điểm Kỹ Năng (SP) hoặc Tiền**  
  1. Tại bước 2, số điểm SP hoặc Tiền hiện có của người chơi ít hơn chi phí nâng cấp yêu cầu.  
  2. Hệ thống hiển thị thông báo: *"Không đủ Điểm Kỹ Năng (SP) hoặc Tiền để nâng cấp\!"*  
  3. Hệ thống vô hiệu hóa nút "Nâng Cấp" và giữ nguyên trạng thái.  
* **E2: Kỹ năng đã đạt Cấp độ tối đa (Max Level)**  
  1. Tại bước 2, kỹ năng đã ở cấp độ giới hạn cao nhất.  
  2. Hệ thống hiển thị nhãn **"Cấp tối đa (MAX)"** và vô hiệu hóa nút bấm.  
* **E3: Chưa đạt điều kiện Cấp độ Nhân vật (Player Level)**  
  1. Tại bước 2, cấp độ nhân vật chưa đạt mốc yêu cầu để mở khóa Level tiếp theo của kỹ năng.  
  2. Hệ thống hiển thị thông báo: *"Yêu cầu Nhân vật đạt Cấp \[X\] để nâng cấp tiếp\!"*

#### ***Quy tắc nghiệp vụ (Business Rules)***

1. **Công thức chi phí nâng cấp:** Chi phí SP và Tiền để nâng cấp tăng dần theo cấp độ kỹ năng:

2. $ChiphíSP(LevelN)=Chiphícơbản\times N$  
3. **Nguyên tắc không âm:** Không được phép trừ SP hay Tiền về số âm.  
4. **Cập nhật Chỉ số ngay lập tức (Real-time Buff Update):** Các chỉ số Buff/Passive cộng thêm sau khi nâng cấp phải có hiệu lực ngay lập tức với nhân vật mà không cần khởi động lại game.  
5. **Lưu dữ liệu:** Mọi thay đổi về Level kỹ năng và điểm SP còn lại phải được tự động ghi vào Save File / Database.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống quản lý dữ liệu game (Server/Save File Database):** Chịu trách nhiệm kiểm tra số dư SP, thực hiện trừ điểm và lưu trạng thái Level kỹ năng mới.  
* **Mối liên hệ hệ thống:** Kết quả nâng cấp của UC13.3 sẽ trực tiếp tác động đến các kỹ năng có thể gán tại **UC13.4 (Trang bị kỹ năng)**.

Include  
Không.  
Extend  
UC13.2.

| Mã Use Case | UC13.4  |
| :---- | :---- |
| Tên Use Case | Trang bị kỹ năng  |
| Mục đích | Kéo/thả hoặc gán các kỹ năng đã học vào các ô trang bị để kích hoạt hiệu ứng thực tế trong gameplay..  |
| Mô tả | Cho phép người chơi kích hoạt các kỹ năng đã sở hữu bằng cách gán chúng vào các ô trang bị khả dụng. Hệ thống sẽ đọc cấp độ hiện tại của kỹ năng (thông qua UC13.3) để tính toán chính xác giá trị hiệu ứng bổ trợ (Buffs) tác động trực tiếp lên nhân vật.  |
| Actor | Chính: Người chơiPhụ: Hệ thống |
| Mức ưu tiên | Cao |
| Tần suất sử dụng  | Theo nhu cầu |

   
Tiền điều kiện

* Có ít nhất 1 kỹ năng đã học và còn ô trang bị trống (hoặc thay thế ô cũ).  
* Có ít nhất 01 ô trang bị kỹ năng (Equip Slot) đang trống, hoặc người chơi chấp nhận gán đè/thay thế vào ô đã có kỹ năng. 

Hậu điều kiện

* Kỹ năng nằm trong Slot Active, các chỉ số / hiệu ứng Buff tác động trực tiếp vào nhân vật.  
* Lưu trạng thái cấu hình ô trang bị (Equip Layout) vào Save File / Database. 

Luồng chính 

1. Tại giao diện Cây kỹ năng (UC13.1), người chơi chọn một kỹ năng đã mở khóa và nhấn nút **"Trang Bị"** (hoặc kéo-thả biểu tượng kỹ năng vào ô Slot mong muốn).  
2. Hệ thống bắt buộc gọi (`<<include>>`) **UC13.3 (Nâng cấp kỹ năng)** để đọc chính xác Cấp độ (Level) hiện tại của kỹ năng đó.  
3. Hệ thống gán kỹ năng vào ô trang bị (Equip Slot) được chọn.  
4. Hệ thống cập nhật và áp dụng các chỉ số/hiệu ứng bổ trợ của kỹ năng lên nhân vật (Ví dụ: Giảm 20% Stress khi ngủ, Tăng 10% tốc độ làm việc...).  
5. Hiển thị hiệu ứng kích hoạt kỹ năng thành công trên giao diện.

##### **Luồng phụ / Luồng thay thế (Alternative Flow)**

* **A1: Gán đè lên ô đã có kỹ năng (Thay thế kỹ năng)**  
  1. Tại bước 1, ô Slot được chọn đã chứa một kỹ năng khác.  
  2. Hệ thống thực hiện tháo (Unequip) kỹ năng cũ, hủy bỏ các chỉ số Buff của kỹ năng cũ khỏi nhân vật.  
  3. Hệ thống gán kỹ năng mới vào ô Slot và áp dụng hiệu ứng Buff mới (tiếp tục bước 2-5 của luồng chính).  
* **A2: Tháo kỹ năng khỏi ô trang bị (Unequip)**  
  1. Người chơi nhấp vào một ô kỹ năng đang active và chọn **"Tháo"** (hoặc kéo kỹ năng ra ngoài bảng Slot).  
  2. Hệ thống xóa kỹ năng khỏi ô Slot và loại bỏ hoàn toàn các hiệu ứng Buff tương ứng khỏi nhân vật.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Tất cả các ô trang bị đều bị khóa (Locked Slots)**  
  1. Tại bước 1, người chơi cố gắng gán kỹ năng vào ô Slot chưa được mở khóa (yêu cầu level nhân vật hoặc tiền tệ để mở).  
  2. Hệ thống hiển thị thông báo: *"Ô trang bị đang bị khóa\! Vui lòng mở khóa ô trang bị trước."*  
  3. Thao tác bị hủy.  
* **E2: Trang bị trùng lặp kỹ năng đã có trong ô khác**  
  1. Tại bước 1, người chơi cố gắng gán một kỹ năng đã nằm ở Slot A vào tiếp Slot B.  
  2. Hệ thống hiển thị cảnh báo: *"Kỹ năng này đã được trang bị\!"*  
  3. Hệ thống tự động di chuyển kỹ năng sang vị trí Slot B mới và bỏ trống Slot A (hoặc hủy thao tác tùy thiết kế UX).

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Giới hạn ô trang bị (Slot Capacity):** Số lượng ô trang bị tối đa phụ thuộc vào Cấp độ nhân vật hoặc trạng thái mở khóa ô của người chơi (Ví dụ: Ban đầu 2 slots, mở tối đa 4 slots).  
2. **Nguyên tắc không cộng dồn trùng lặp (Unique Equip):** Mỗi kỹ năng chỉ được phép trang bị vào **01 ô duy nhất** tại một thời điểm. Không cho phép gán trùng 1 kỹ năng vào nhiều ô để nhân bản hiệu ứng Buff.  
3. **Áp dụng hiệu ứng lập tức (Instant Buff Calculation):** Hiệu ứng bổ trợ từ Cấp độ kỹ năng (kết nối từ UC13.3) phải được tính toán và áp dụng/gỡ bỏ ngay lập tức ngay khi kỹ năng được gán hoặc tháo khỏi Slot.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống quản lý chỉ số nhân vật (Character Stats Manager):** Chịu trách nhiệm trực tiếp nhận giá trị Buff/Passive từ kỹ năng active để cộng/trừ vào các thuộc tính nhân vật thời gian thực.  
  * **Hệ thống lưu trữ/Cơ sở dữ liệu game:** Lưu lại sơ đồ ô trang bị (Equip Layout) để giữ nguyên trạng thái khi người chơi thoát game hoặc chuyển cảnh.  
* **Ý nghĩa quan hệ Include UC13.3:** Mối quan hệ bắt buộc này đảm bảo hệ thống không lấy giá trị mặc định (Level 1\) mà luôn đọc đúng thuộc tính Level hiện tại (đã được nâng cấp qua UC13.3) để trả về đúng sức mạnh thực sự của kỹ năng.

Include  
UC13.3.  
Extend.  
Không.

**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC14 | Mini Game | Tổng quát |
| UC14.1 | Pha chế | Không |
| UC14.2 | Debug Code | Không  |
| UC14.3 | Chạy quảng cáo | Không |
| UC14.4 | Chụp ảnh | Không |
| UC14.5 | Chế biến món ăn  | Không |
| UC14.6 | Sửa máy tính | Không |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC14.1 (Pha chế) | Không  | Không  |  |
| UC14.2 (Debug Code)  | Không  | Không  |  |
| UC14.3 (Chạy quảng cáo)  | Không  | Không  |  |
| UC14.4 (Chụp ảnh)  | Không  | Không  |  |
| UC14.5 (Chế biến món ăn) | Không | Không |  |
| UC14.6 (Sửa máy tính) | Không | Không |  |

**Đặc tả UC14**

| Mã Use Case | UC14 |
| :---- | :---- |
| Tên Use Case | Mini game |
| Mục đích | Cung cấp cơ chế chơi các trò chơi nhỏ để người chơi tích lũy tiền mặt và tài nguyên, phục vụ mục tiêu đạt 1 triệu đô trong thời hạn quy định |
| Mô tả | Người chơi chọn và hoàn thành 1 trong các hoạt động mini game kỹ năng (Pha chế, Debug, chạy QC…) để nhận phần thưởng tiền mặt và điểm kinh nghiệm dựa trên hiệu suất chơi. |
| Actor | Người chơi  |
| Mức ưu tiên | ?? |
| Tần suất sử dụng | Cao |

Trigger  
Người chơi tương tác với điểm làm việc / nhiệm vụ trên bản đồ hoặc chọn mini game từ danh sách công việc.  
Tiền điều kiện

* Nhân vật còn đủ chỉ số thể lực / năng lượng và thời gian trong ngày để thực hiện công việc.  
* Đã mở khóa mini game tương ứng (nếu có yêu cầu về cấp độ / dụng cụ).

Hậu điều kiện

* Thành công: Tài khoản người chơi tăng tiền thưởng, điểm kinh nghiệm; các chỉ số thể lực / thời gian bị trừ tương ứng.  
* Thất bại: Trừ thể lực/ thời gian nhưng nhận ít tiền hoặc không nhận được tiền

Luồng chính

1. Người chơi chọn bắt đầu một mini game cụ thể từ giao diện game.  
2. Hệ thống kiểm tra điều kiện tiên quyết (thể lực, thời gian) và khởi tạo giao diện mini game tương ứng (giao diện Pha chế, Debug, Chạy QC...).  
3. Hệ thống hiển thị hướng dẫn ngắn, mục tiêu và đếm ngược thời gian.  
4. Người chơi thực hiện các thao tác tương tác (click, kéo thả, gõ phím, chọn đáp án...) theo yêu cầu riêng của mini game.  
5. Người chơi hoàn thành mục tiêu trước khi hết giờ.  
6. Hệ thống tính toán điểm số dựa trên thời gian còn lại và độ chính xác.  
7. Hệ thống hiển thị màn hình kết quả, cộng tiền thưởng vào tài khoản và cập nhật tiến trình mục tiêu 1 triệu đô.  
8. Người chơi xác nhận và quay trở lại màn hình chính.

Luồng phụ 1 (Include Flow \- Mở khóa thành tựu)  
*A1: Hoàn thành xuất sắc (Perfect Score):*

* Tại bước 5, người chơi đạt độ chính xác 100% hoặc hoàn thành cực nhanh.  
* Hệ thống thưởng thêm tiền Combo (Bonus cash) và hiển thị danh hiệu/hiệu ứng đặc biệt.  
  *A2: Tạm dừng mini game:*  
* Trong lúc chơi, người chơi bấm "Pause".  
* Hệ thống đóng đóng băng thời gian và hiển thị menu: Tự động chơi tiếp (Resume), Chơi lại (Restart), hoặc Thoát (Quit).

Luồng ngoại lệ:   
*B1: Hết thời gian hoặc làm sai quá số lần quy định (Game Over):*

* Tại bước 4-5, thời gian đếm ngược về 0 hoặc người chơi phạm lỗi tối đa cho phép.  
* Hệ thống dừng mini game, hiển thị thông báo "Thất bại".  
* Hệ thống trả phần thưởng tối thiểu (hoặc 0 đồng) và vẫn trừ năng lượng/thời gian của nhân vật.

*B2: Không đủ thể lực/thời gian để bắt đầu:*

* Tại bước 2, hệ thống phát hiện nhân vật kiệt sức hoặc đã hết giờ làm việc trong ngày.  
* Hệ thống hiển thị thông báo "Không đủ năng lượng/Thời gian" và hủy thao tác, đưa người chơi về màn hình trước.

Luồng thay thế:   
*R1: Sử dụng vật phẩm hỗ trợ / Tự động hoàn thành (Auto-complete):*

* Tại bước 1, người chơi chọn tiêu thụ một vật phẩm hỗ trợ (như "Thẻ bỏ qua", "Tăng tốc").  
* Hệ thống bỏ qua bước 3, 4, 5 (không cần chơi mini game) và trực tiếp tính kết quả thành công ở bước 6 để trả thưởng.

| Mã Use Case | UC14.1  |
| :---- | :---- |
| Tên Use Case | Pha chế  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Người chơi truy cập vào giao diện mini game và chọn công việc pha chế |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Pha chế từ giao diện in-game.

**Tiền điều kiện**

* Bắt đầu ca làm việc tại quán cà phê hoặc mua máy cà phê

**Hậu điều kiện**

* Hoàn thành tốt: Nhận thù lao, giảm 5-15% Stress cho nhân vật.  
* Pha sai/thất bại: Stress tăng gấp đôi so với hoàn thành tốt 

**Luồng chính**

1. Người chơi kích hoạt Mini game “pha chế”  
2. Màn hình hiển thị đơn hàng gồm tỷ lệ: Cà phê, nước, đường, sữa và thời gian đếm ngược (30 giây)   
3. Người chơi thao tác chọn đúng thứ tự và đong đếm số lượng nguyên liệu chuẩn xác.  
4. Hệ thống đánh giá kết quả (*Perfect / Good / Pass*).  
5. Nhân vật nhận tiền công, chỉ số Stress giảm từ 5% \- 15%, tích lũy điểm Kỹ năng.

**Luồng phụ**  
**A1. Pha sai cách**

- **Tại bước 3, nếu chọn sai công thức hoặc hết giờ \-\> món ăn/thức uống bị hỏng**  
- **Hệ thống trừ 5% thể lực, tăng 10 \- 20% Stress do áp lực từ khách hàng, không nhận tiền thù lao.**

**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC14.2  |
| :---- | :---- |
| Tên Use Case | Sửa lỗi (Debug code)  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Trò chơi nhỏ dành cho công việc lập trình viên ở công ty IT. |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Debug Code từ giao diện in-game.

**Tiền điều kiện**

* Đã nhận công việc lập trình và có kỹ năng IT.

**Hậu điều kiện**

* Thắng: Hoàn thành dự án, nhận thù lao cao và cộng điểm kỹ năng lập trình.  
* Thua: Dự án bị trễ hạn \-\> \+20% Stress, \-20% thể lực, trừ thù lao. 

**Luồng chính**

1. Màn hình hiển thị giao diện mô phỏng IDE với các đoạn code có vệt đỏ đánh dấu lỗi.  
2. Người chơi hoàn thành chuỗi thao tác gõ phím đúng ký tự bị thiếu hoặc giải đố sắp xếp thuật toán trong thời gian quy định.  
3. Hệ thống xác nhận Debug thành công 100%.  
4. Dự án hoàn tất: Nhận thù lao hợp đồng lớn, cộng điểm Kỹ năng Lập trình.

**Luồng phụ**  
**A1. Hết giờ mà vẫn chưa hết lỗi \-\> Dự án bị trễ hạn.**  
**Hệ thống trừ tiền phạt hợp đồng, \+20% stress và \-20% thể lực. Nếu stress \>80% \-\> kích hoạt trạng thái kiệt sức.**  
**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC14.3  |
| :---- | :---- |
| Tên Use Case | Chạy quảng cáo  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Trò chơi nhỏ tối ưu hóa ngân sách và đối tượng truyền thông cho việc Marketing. |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Chạy quảng cáo từ giao diện in-game.

**Tiền điều kiện**

* Nhận hợp đồng Marketing hoặc kích hoạt chiến dịch quảng cáo cho công ty.

**Hậu điều kiện**

* Tăng chỉ số Doanh thu / Uy tín công ty, nhận tiền thưởng dự án.

**Luồng chính**

1. Màn hình hiển thị bảng cân bằng 3 tham số: Budget (Ngân sách), Target Audience (Tệp khách hàng) và Content (Nội dung).  
2. Người chơi canh nhịp thanh trượt (Timing Clicker) để dừng đúng "Điểm Vàng" (Green Zone).  
3. Hệ thống tính toán chỉ số Click-Through Rate (CTR) đạt mức cao.  
4. Chiến dịch bùng nổ: Tăng 20% Doanh thu công ty hoặc nhận tiền thưởng dự án Freelance xuất sắc.

**Luồng phụ**

- **Bấm trượt vào vùng Đỏ (Red Zone) \-\> Ngân sách bị lãng phí nhưng không mang lại chuyển đổi.**  
- **Hệ thống trừ ngân sách chạy Ads, chỉ số Uy tín công ty bị sụt giảm.**  
- **Bonus: Nếu bạn làm sai quy trình quá nhiều lần (5 lần liên tiếp) khiến người xem khi nhìn thấy quảng cáo hiểu nhầm thành spam, bạn sẽ có thành tựu ẩn “Chúa tể Seeding”.**

**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC14.4  |
| :---- | :---- |
| Tên Use Case | Chụp ảnh  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Trò chơi nhỏ căn nét và bắt khoảnh khắc dành cho công việc Nhiếp ảnh / Media. |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Chụp ảnh từ giao diện in-game.

**Tiền điều kiện**

* Nhận công việc chụp ảnh sự kiện/người mẫu hoặc sở hữu Máy ảnh.

**Hậu điều kiện**

* Bức ảnh đạt chất lượng cao nhận thêm tiền tip, \-10% stress nhờ tính chất nghệ thuật.

**Luồng chính**

1. Màn hình hiển thị khung ngắm camera (Focus Frame) di chuyển liên tục đuổi theo chủ thể chuyển động.  
2. Người chơi căn chỉnh tiêu cự (Focus) và bấm bấm chụp đúng khoảnh khắc khung hình chuyển sang màu xanh lá.  
3. Bức ảnh đạt độ nét và bố cục hoàn hảo.  
4. Hệ thống cộng tiền thù lao \+ tiền Tip từ khách hàng, giảm **10% Stress**.

**Luồng phụ**

- **Bấm chụp sai thời điểm làm ảnh bị nhòe/mờ.**  
- **Khách hàng không hài lòng: Chỉ nhận 50% thù lao, không được giảm Stress.**

**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC14.5 |
| :---- | :---- |
| Tên Use Case | Chế biến món ăn  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Trò chơi nhỏ nấu nướng khi làm bếp trưởng/phụ bếp hoặc tự nấu ăn ở phòng trọ để tiết kiệm tiền.. |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Chế biến món ăn từ giao diện in-game.

**Tiền điều kiện**

* Có bếp ăn tại nhà hoặc làm việc tại nhà hàng.

**Hậu điều kiện**

* Nấu tại nhà: \+30% thể lực, tốn ít tiền hơn mua đồ ăn ngoài.  
* Nấu tại nhà hàng: Nhận lương ca làm, cộng điểm kỹ năng bếp.

**Luồng chính**

1. Hệ thống đưa ra quy trình 4 bước: Thái nguyên liệu \-\> Tẩm ướp \-\> Xào/Nấu \-\> Trình bày.  
2. Người chơi thực hiện nhanh các thao tác vuốt/nhấn phím theo đúng nhịp đếm.  
3. Món ăn hoàn thành đạt chất lượng *Masterchef*.  
4. **Nấu tại nhà:** Tăng ngay **\+30% Thể lực (Energy)** với chi phí rẻ hơn mua đồ ăn ngoài.  
5. **Nấu tại nhà hàng:** Nhận thù lao ca làm và cộng điểm Kỹ năng Nấu nướng.

**Luồng phụ**

- **Để quá lửa hoặc thao tác quá chậm \-\> Món ăn bị cháy đen.**  
- **Mất nguyên liệu, không tăng Thể lực (nếu tự nấu) hoặc bị nhà hàng trừ lương phạt (nếu làm thuê).**

**Bonus: Đạt thành tựu “Gordon Ramsay\!?” nếu người chơi để món ăn bị cháy/hỏng món ăn 5 lần trở lên (chỉ tính khi bạn làm ở nhà hàng).**   
**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC14.6 |
| :---- | :---- |
| Tên Use Case | Sửa máy tính  |
| Mục đích | Cho phép người chơi làm một trong số công việc để kiếm tiền |
| Mô tả | Trò chơi nhỏ chẩn đoán và thay thế linh kiện phần cứng máy tính. |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**

- Người chơi chọn chức năng Mini game \-\> Sửa máy tính từ giao diện in-game.

**Tiền điều kiện**

* Nhận công việc nhận sửa chữa máy tính / kỹ thuật viên.

**Hậu điều kiện**

* Sửa hỏng (chập cháy): Phải đền bù tiền linh kiện cho khách, \+15% stress và trừ tiền đền bù.

**Luồng chính**

1. Màn hình hiển thị case máy tính hỏng (lỗi dây nguồn, hỏng RAM, cháy Card đồ họa).  
2. Người chơi thực hiện nối các đường dây mạch điện bị đứt (Wiring Puzzle) và lắp đặt linh kiện đúng vị trí.  
3. Máy tính khởi động thành công.  
4. Nhận tiền công sửa chữa, cộng điểm Kỹ năng Kỹ thuật (UC14). Nếu hoàn thành trong dưới 10 giây \-\> Kích hoạt Thành tựu Ẩn **"Bàn Tay Vàng Kỹ Thuật"**

**Luồng phụ**

- **Nối sai dây điện hoặc cắm ngược linh kiện \$\\rightarrow\$ Phát nổ/chập cháy case máy tính.**  
- **Người chơi phải đền bù chi phí linh kiện hỏng cho khách hàng, nhân vật bị giật điện cộng \+15% Stress và mất 10% Thể lực.**

**Bonus: Người chơi sẽ đạt thành tựu ẩn “Bàn Tay Vàng Kỹ Thuật” nếu hoàn thành một công việc trong dưới 10 giây.**  
**Include**  
Không.  
**Extend**  
Không.

**Cấu trúc Use Case của module**

| Mã | Tên UC | Quan hệ |
| :---- | :---- | :---- |
| UC15 | Quản lý thành tựu | Tổng quát |
| UC15.1 | Xem danh sách thành tựu | UC cơ sở cho extend |
| UC15.2 | Mở khóa thành tựu | Gọi UC15.1 / Được gọi bởi UC15.3 |
| UC15.3 | Nhận danh hiệu và phần thưởng | Gọi UC15.2  |
| UC15.4 | Xem bộ sưu tập và kết cục | Sub-component của UC15 |

**Ma trận quan hệ Use Case**

| Use Case | Include | Extend | Ghi chú |
| :---- | :---- | :---- | :---- |
| UC15.1 Xem thành tựu | Không  | UC15.2  | Kích hoạt khi: Người chơi thực hiện thao tác UI/UX đặc biệt trực tiếp trên màn hình xem   |
| UC15.2 (Mở khóa thành tựu)  | UC15.3  | Không  | Bắt buộc: Mọi thành công khi mở khóa thành tựu đều tự động bao hàm việc gán danh hiệu/kích hoạt phần thưởng tương ứng  |
| UC15.3 (Nhận danh hiệu và phần thưởng)  | Không  | Không  | Được gọi bởi UC15.2. Mỗi khi thành tựu được mở khóa, UC15.3 sẽ thực thi việc trao thưởng và gán danh hiệu cho nhân vật.  |
| UC15.4 (Xem Gallery)  | Không  | Không  | Phân hệ xem riêng biệt, đọc dữ liệu từ Save FIle / Global Profile |

**Đặc tả UC15**

| Mã Use Case | UC15 |
| :---- | :---- |
| Tên Use Case | Thành tựu |
| Mục đích | Ghi nhận tiến trình, theo dõi các cột mốc/chỉ số sinh tồn, mở khóa danh hiệu/phần thưởng, và kích hoạt các kết cục (Endings) cho người chơi. |
| Mô tả | Khi người chơi mở game, hệ thống khởi tạo môi trường trò chơi, kiểm tra dữ liệu cần thiết, tải tài nguyên và hiển thị giao diện để người chơi thực hiện các chức năng tiếp theo.  |
| Actor | Người chơi  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Mỗi lần mở mục thành tựu |

Trigger  
Người chơi chủ động mở giao diện thành tựu, hoặc hệ thống tự động kích hoạt khi người chơi thỏa mãn điều kiện ẩn/cột mốc/Game Over.  
Tiền điều kiện

* Đã tạo nhân vật và tham gia vào vòng lặp gameplay.

Hậu điều kiện

* Tiến trình thành tựu, danh hiệu, phần thưởng (tiền/điểm kỹ năng) và album kết cục (Ending Gallery) được lưu lại. 

Luồng chính

1. Người chơi truy cập vào giao diện Thành tựu từ Menu chính  
2. Hệ thống hiển thị danh sách các thành tựu: Đã hoàn thành, Chưa hoàn thành và Thành tựu ẩn (dạng ???)  
3. Người chơi chọn một thành tựu đã đạt điều kiện để nhận phần thưởng (Tiền, Điểm kỹ năng UC13) hoặc trang bị Danh hiệu.  
4. Hệ thống cập nhật trạng thái “Đã nhận”, cộng phần thưởng và cập nhật và hồ sơ người chơi (Profile).

Luồng phụ 1 (Include Flow \- Mở khóa thành tựu)

1. Trong quá trình chơi (In-game), hệ thống liên tục kiểm tra các sự kiện/chỉ số (Doanh thu, Stress, Health, AFK, Easter Eggs UI/UX, thoát game giữa chừng).  
2. Khi điều kiện của một thành tựu được đáp ứng \-\> Hệ thống tự động kích hoạt hàm “Mở khóa thành tựu”.  
3. Hệ thống hiển thị thông báo Popup nổ thành tựu kèm dòng “cà khịa” tương ứng.  
4. Hệ thống tự động trao Danh hiệu tương ứng cho người chơi (Bắt buộc bao gồm trong bước này).

Luồng phụ 2 (Extend Flow \- Mở khóa từ giao diện xem):

1. Người chơi đang thực hiện hành vi tương tác ngay trên giao diện danh sách thành tựu.  
2. Hệ thống phát hiện thao tác UI đặc biệt và mở khóa ngay thành tựu ẩn.

Luồng phụ kích hoạt Endings (Kịch bản đặc biệt):  
1\. Khi chạm mốc \$1 000 000 / Hết thời gian / Đột tử: Hệ thống quét toàn bộ chỉ số Lifetime Stats (Độ nghiện, Stress, Health, doanh thu).  
2\. Hệ thống đối chiếu ma trận ưu tiên để kích hoạt kịch bản kết cục tương ứng.  
3\. Mở khóa thành tựu ending tương ứng và lưu vào bộ sưu tập kết cục (Ending Gallery) ở Menu chính.

| Mã Use Case | UC15.1  |
| :---- | :---- |
| Tên Use Case | Xem danh sách thành tựu  |
| Mục đích | Hiển thị tiến trình, danh sách các thành tựu đã đạt, chưa đạt và các cột mốc ẩn để người chơi theo dõi.  |
| Mô tả | Người chơi truy cập vào giao diện thành tựu để xem danh sách. Khi một thành tựu mở khóa, hệ thống tự động xuất hiện đồ vật/cúp tương ứng tại vị trí tọa độ quy định trong phòng trọ/văn phòng của nhân vật.   |
| Actor | Chính: Người chơi  |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**  
Người chơi chọn chức năng Thành tựu từ giao diện khởi động/in-game.   
**Tiền điều kiện**

* Người chơi đang ở màn hình chính (Main menu), menu tạm dừng (Pause Menu)

**Hậu điều kiện**

* Giao diện thành tựu hiển thị đầy đủ danh sách, thanh tiến trình và trạng thái thực tế.  
* Ghi nhận trạng thái xem thành tựu (xóa các thông báo "New" nếu có).  
* Đảm bảo các đồ vật/cúp thành tựu đã mở khóa được load đúng tại vị trí không gian tương ứng trong phòng trọ/văn phòng.

**Luồng chính**

1. Người chơi chọn biểu tượng **"Thành tựu"** trên giao diện UI.  
2. Hệ thống tải dữ liệu tiến trình thành tựu của người chơi từ Save File / Profile chung.  
3. Hệ thống hiển thị giao diện danh sách gồm 2 tab phân loại chính:  
* **3.1. Tab Thường:** Hiển thị các thành tựu tiến trình công khai (Doanh thu, Sức khỏe, Stress, Cấp độ,...), kèm thanh phần trăm (%) hoàn thành.  
* **3.2. Tab Ẩn (???):** Hiển thị các thành tựu Easter Eggs, AFK, Quit Game giữa chừng... (mô tả và tên bị che bằng dấu `???`, chỉ hiển thị câu gợi ý mờ).  
4. Hệ thống kiểm tra các thành tựu đã đạt và tải/hiển thị các vật phẩm, cúp trưng bày tương ứng vào khung cảnh phòng trọ/văn phòng của nhân vật.  
5. Người chơi xem danh sách và nhấn nút **"Đóng"** để quay lại menu trước đó.

**Luồng phụ**  
**A1: Kích hoạt Easter Egg trên UI (Gọi mở rộng UC15.2)**

1. Tại giao diện xem thành tựu, người chơi nhấp chuột / chạm (tap) liên tục 10 lần vào Logo game hoặc biểu tượng trang trí.  
2. Hệ thống phát hiện sự kiện tương tác đặc biệt và tự động kích hoạt luồng `<<extend>>` gọi **UC15.2: Mở khóa thành tựu**.  
3. Hệ thống trao thành tựu ẩn *"Kẻ thù của Logo"*, phát hiệu ứng mở khóa thành công ngay trên màn hình.  
   **A2: Lọc / Tìm kiếm thành tựu**  
1. Người chơi chuyển đổi bộ lọc: *Tất cả*, *Đã hoàn thành*, *Chưa hoàn thành*.  
2. Hệ thống cập nhật danh sách hiển thị tương ứng.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Lỗi đọc file lưu dữ liệu (Save File Corrupted)**  
  1. Tại bước 2, hệ thống không thể đọc được dữ liệu thành tựu từ Save File hoặc kết nối Profile bị gián đoạn.  
  2. Hệ thống hiển thị thông báo: *"Không thể tải dữ liệu thành tựu. Vui lòng kiểm tra lại kết nối\!"*  
  3. Màn hình duy trì ở giao diện Menu ban đầu.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Bảo mật thành tựu ẩn:** Các thành tựu thuộc tab Ẩn tuyệt đối không hiển thị tên điều kiện chi tiết cho đến khi người chơi chính thức đạt được, trừ câu gợi ý (Hint) ngắn.  
2. **Đồng bộ vật phẩm môi trường (Physical Trophy Sync):** Mỗi mã thành tựu được mở khóa bắt buộc phải gắn liền với một ID prefab/đồ vật tương ứng trong scene (Phòng trọ/Văn phòng). Khi thành tựu đạt True, đồ vật đó bắt buộc phải hiển thị tại đúng tọa độ $(X,Y,Z)$ đã thiết lập sẵn.  
3. **Tiến trình toàn cục (Global Profile):** Dữ liệu thành tựu được lưu ở cấp độ Profile chung (Global Save), có thể tích lũy hoặc giữ nguyên ngay cả khi người chơi tạo nhân vật mới (Tùy thuộc vào thiết kế game).

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống lưu trữ (Save File / Profile Server):** Cung cấp và lưu giữ trạng thái tiến trình thành tựu.  
  * **Hệ thống hiển thị không gian (Environment / Scene Manager):** Đảm nhận việc spawn/kích hoạt hiển thị các cúp và đồ vật kỷ niệm bên trong phòng trọ hay văn phòng làm việc của nhân vật.  
* **Mã Use Case:** Đã giữ nguyên mã **UC15.1** theo chuỗi danh mục điều chỉnh của bạn.

**Include**  
Không.  
**Extend**  
UC15.2

| Mã Use Case | UC15.2  |
| :---- | :---- |
| Tên Use Case | Mở khóa thành tựu  |
| Mục đích | Tự động kiểm tra điều kiện, ghi nhận việc hoàn thành thành tựu, hiển thị thông báo popup và gọi hàm trao thưởng.  |
| Mô tả | Hệ thống chạy ngầm để theo dõi các sự kiện in-game. Khi người chơi thỏa mãn điều kiện của một thành tựu cụ thể, hệ thống sẽ tự động chuyển trạng thái thành tựu sang Mở khóa, hiển thị thông báo chúc mừng/cà khịa ở góc màn hình, đồng thời tự động trao phần thưởng và xuất hiện vật phẩm kỷ niệm tương ứng.  |
| Actor | Chính: Hệ thống (System trigger)Phụ: Người chơi (khi thao tác UI), CSDL |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Tự động / Thường xuyên trong quá trình chơi |

**Trigger**  
Người chơi thỏa mãn các điều kiện của Thành tựu trong quá trình chơi.  
**Tiền điều kiện**

* Thành tựu đó đang ở trạng thái **Chưa mở khóa (IsUnlocked \= False)**.  
* Xảy ra một sự kiện in-game (biến động chỉ số, hoàn thành nhiệm vụ, kịch bản kết thúc, hành vi UI...) thỏa mãn đúng \$100\\%\$ điều kiện của thành tựu.

**Hậu điều kiện**

* Trạng thái thành tựu chuyển sang **Đã mở khóa (IsUnlocked \= True)** kèm mốc thời gian hoàn thành (Timestamp).  
* Hiển thị thông báo Pop-up/Banner "Nổ thành tựu" ở góc màn hình.  
* Nhận phần thưởng tương ứng (Tiền, Điểm thưởng, Danh hiệu, Đồ vật trang trí phòng trọ/văn phòng).

**Luồng chính**

1. Hệ thống (System Event Listener) phát hiện một sự kiện in-game thỏa mãn điều kiện mở khóa thành tựu (Ví dụ: Tài sản \>1,000,000\$, Stress \= 100%, hoặc thoát game khi nhân vật đang tăng ca).  
2. Hệ thống cập nhật thuộc tính IsUnlocked \= True và ghi nhận mốc thời gian mở khóa vào Save File / Profile của người chơi.  
3. Hệ thống kích hoạt giao diện hiển thị Banner/Pop-up thông báo nổ thành tựu ở góc màn hình kèm tên thành tựu, biểu tượng và câu thoại "cà khịa" / hài hước.  
4. Hệ thống phát âm thanh hiệu ứng (SFX) chúc mừng.  
5. Hệ thống bắt buộc gọi (\<\<include\>\>) **UC15.3 (Nhận thưởng thành tựu)** để tự động cộng phần thưởng đi kèm (Tiền, Danh hiệu, Đồ trang trí) vào tài khoản người chơi.  
6. Banner thông báo tự động ẩn sau một khoảng thời gian quy định (ví dụ: $3-5$ giây).

##### **Luồng phụ / Luồng thay thế (Alternative Flow)**

* **A1: Mở khóa nhiều thành tựu cùng lúc (Multi-unlock Queue)**  
  1. Người chơi thực hiện một hành động thỏa mãn điều kiện của $2$ hoặc nhiều thành tựu đồng thời.  
  2. Hệ thống đưa các thông báo thành tựu vào Hàng chờ (Queue).  
  3. Hệ thống lần lượt hiển thị từng Pop-up banner nối tiếp nhau cho đến khi hết hàng chờ.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Mất kết nối lưu dữ liệu (Save File Lock / Offline Mode)**  
  1. Tại bước 2, hệ thống không thể ghi trạng thái `IsUnlocked = True` vào Save File do lỗi bộ nhớ hoặc đĩa cứng bị khóa.  
  2. Hệ thống lưu tạm dữ liệu mở khóa vào bộ nhớ đệm (Cache) và phát thông báo Pop-up như bình thường.  
  3. Hệ thống sẽ cố gắng ghi lại (Retry Sync) vào Save File ngay khi tiến trình lưu dữ liệu khả dụng trở lại.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Mở khóa một lần (Once-Only Unlock):** Mỗi thành tựu chỉ được kích hoạt mở khóa **01 lần duy nhất** trong suốt vòng đời của Profile/Save File. Mọi sự kiện thỏa mãn điều kiện sau đó sẽ bị hệ thống bỏ qua.  
2. **Không làm gián đoạn Gameplay (Non-blocking UI):** Pop-up thông báo thành tựu xuất hiện dưới dạng lớp phủ (Overlay) ở góc màn hình, không Pause game và không chặn thao tác điều khiển của người chơi.  
3. **Đồng bộ phần thưởng (Instant Reward Dispatch):** Phần thưởng đi kèm (gọi qua UC15.3) phải được chuyển giao ngay lập tức ngay khi Pop-up xuất hiện.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống lưu trữ (Save File / Profile Server):** Lưu giữ vĩnh viễn biến `IsUnlocked` và thời gian mở khóa.  
* **Thiết kế trải nghiệm (UX/UI):** Đảm bảo câu thoại "cà khịa" trong Pop-up mang phong cách hài hước đặc trưng của game để tăng tính giải trí khi người chơi vô tình "ăn" các thành tựu ẩn tiêu cực (như phá sản, kiệt sức, làm vỡ đồ...).

**Include**  
UC15.3  
**Extend**  
Không.

| Mã Use Case | UC15.3 |
| :---- | :---- |
| Tên Use Case | Nhận danh hiệu và phần thưởng.  |
| Mục đích | Trao các phần thưởng vật chất (Tiền hay điểm kỹ năng ở UC13) và gán danh hiệu cho người chơi sau khi mở khóa thành tựu.  |
| Mô tả | Sau khi người chơi đã đạt danh hiệu, hệ thống sẽ mở khóa thành tựu và xử lý phần thưởng đi kèm (nếu có). |
| Actor | Hệ thống (được gọi bởi UC15.2) |
| Mức ưu tiên | Trung bình \- Cao |
| Tần suất sử dụng  | Tự động / Theo tần suất mở khóa thành tựu |

**Trigger**  
Sau khi người chơi thỏa mãn các điều kiện của Thành tựu trong quá trình chơi.  
**Tiền điều kiện**

* **UC15.2 (Mở khóa thành tựu)** đã thực thi mở khóa thành công (`IsUnlocked = True`).  
* Thành tựu đó đang ở trạng thái **Chưa nhận thưởng (`IsRewardClaimed = False`)**.

**Hậu điều kiện**

* Tài sản (Tiền) hoặc Điểm Kỹ Năng (SP \- UC13) của người chơi được cộng trực tiếp và chính xác.  
* Danh hiệu mới (Title) được mở khóa và hiển thị trong Kho trang bị / Hồ sơ nhân vật.  
* Trạng thái nhận thưởng chuyển thành **`IsRewardClaimed = True`** và được lưu cố định vào Save File.

**Luồng chính**

1. Hệ thống đọc dữ liệu bảng phần thưởng (Reward Matrix) tương ứng với Mã Thành Tựu vừa mở khóa từ UC15.2.  
2. Hệ thống tự động mở khóa và gán danh hiệu mới vào hồ sơ người chơi (Ví dụ: *"Chúa tể treo máy"*, *"Kẻ đi ngược hệ thống"*, *"Thánh Nợ"*...).  
3. Hệ thống kiểm tra các phần thưởng tài sản/chỉ số đi kèm:  
* **Nếu thưởng Tiền:** Hệ thống gọi module Tài chính cộng trực tiếp vào Tài khoản Ngân hàng/Tiền mặt.  
* **Nếu thưởng Điểm Kỹ Năng (SP):** Hệ thống gửi dữ liệu cộng điểm SP sang module Kỹ năng (**UC13**).  
* **Nếu thưởng Vật phẩm/Đồ trang trí:** Hệ thống mở khóa item tương ứng trong kho/môi trường phòng.  
4. Hệ thống cập nhật thuộc tính `IsRewardClaimed = True` và ghi mốc thời gian trao thưởng.  
5. Hệ thống hiển thị dòng thông báo nhận thưởng nhỏ (Toast Notification) trên giao diện (Ví dụ: *"+\$50,000 & \+2 SP đã được thêm vào tài khoản\!"*).  
6. Tự động lưu (Auto-save) dữ liệu phần thưởng mới vào Save File.

##### **Luồng phụ / Luồng thay thế (Alternative Flow)**

* **A1: Thành tựu không có phần thưởng vật chất (Chỉ trao Danh hiệu)**  
  1. Tại bước 1, bảng dữ liệu xác định thành tựu chỉ chứa phần thưởng Danh hiệu (không có Tiền hoặc SP).  
  2. Hệ thống bỏ qua bước 3, thực hiện gán Danh hiệu ở bước 2 và chuyển thẳng đến bước 4 để cập nhật trạng thái `IsRewardClaimed = True`.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Lỗi đồng bộ dữ liệu với Module Kỹ năng (UC13) hoặc Ngân hàng**  
  1. Tại bước 3, hệ thống gặp sự cố khi đang cộng SP hoặc Tiền (ví dụ: tràn số hoặc mất kết nối bộ nhớ tạm).  
  2. Hệ thống đưa giá trị phần thưởng vào danh sách **Phần thưởng chờ (Pending Rewards Queue)**.  
  3. Hệ thống hiển thị thông báo: *"Phần thưởng sẽ được tự động cập nhật trong lần lưu kế tiếp\!"*  
  4. Hệ thống thực hiện cộng lại thưởng ngay khi kết nối/trạng thái module khôi phục bình thường.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Chống nhận thưởng trùng lặp (Idempotency / Anti-duplication):** Một phần thưởng gắn liền với Mã Thành Tựu chỉ được phát **01 lần duy nhất**. Kiểm tra chặt chẽ điều kiện `IsRewardClaimed == False` trước khi cộng tài sản.  
2. **Cộng thưởng tức thì (Instant Balance Update):** Mọi khoản tiền hay điểm SP thưởng phải có hiệu lực ngay lập tức trong giao diện người dùng mà không cần phải chuyển cảnh hay tải lại game.  
3. **An toàn dữ liệu tài chính:** Không để xảy ra lỗi âm/tràn số khi cộng tiền tệ hoặc SP vào tài khoản. Mọi biến động tài chính từ phần thưởng thành tựu đều phải được ghi log sự kiện (`Reward Log`).

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống quản lý kỹ năng (UC13):** Tiếp nhận dữ liệu cộng điểm SP thưởng để người chơi sử dụng cho việc học/nâng cấp kỹ năng (UC13.2, UC13.3).  
  * **Hệ thống ngân hàng/Tài chính:** Tiếp nhận dữ liệu cộng tiền thưởng vào số dư tài khoản.  
  * **Hệ thống lưu trữ (Save File / Profile Server):** Lưu trữ thuộc tính IsRewardClaimed và danh sách danh hiệu đã mở khóa.  
* **Mối liên hệ giữa UC15.2 và UC15.3:** Mối quan hệ giữa UC15.2 và UC15.3 là dạng UC15.2 \<\<include\>\> UC15.3. Điều này đảm bảo quy trình luôn diễn ra khép kín: *Thỏa điều kiện $\rightarrow$ Mở khóa thành tựu (UC15.2) $\rightarrow$ Tự động trao thưởng & gán danh hiệu (UC15.3)*.

**Include**  
Không.  
**Extend**  
Không.

| Mã Use Case | UC15.4 |
| :---- | :---- |
| Tên Use Case | Xem bộ sưu tập kết cục (Gallery).  |
| Mục đích | Cho phép người chơi xem lại Album lưu trữ tất cả các Bad/Good/Secret Endings đã từng mở khóa qua các lượt chơi.  |
| Mô tả | Chuyển đổi giao diện Album dạng lưới truyền thống thành Giao diện bức tường tranh ảnh (Memory Wall). Đọc dữ liệu từ Global Profile để hiển thị ảnh tương ứng  |
| Actor | Chính: Người chơi Phụ: Hệ thống lưu trữ toàn cục |
| Mức ưu tiên | Cao |
| Tần suất sử dụng  | Theo nhu cầu |

**Trigger**  
Người chơi truy cập vào phần Ending Gallery từ Menu chính.  
**Tiền điều kiện**

* Người chơi ở màn hình chính

**Hậu điều kiện**

* Màn hình Memory Wall hiển thị đầy đủ danh sách và trạng thái các Endings.  
* Người chơi xem được hình ảnh bưu thiếp/kỷ niệm và kịch bản/bức thư chi tiết của các Ending đã đạt được.

**Luồng chính**

1. Người chơi chọn mục **"Bộ sưu tập kết cục"** (Gallery / Memory Wall) trên giao diện Menu chính.  
2. Hệ thống tải dữ liệu tiến trình Ending của người chơi từ Global Profile.  
3. Hệ thống hiển thị giao diện Bức tường tranh ảnh (Memory Wall) dưới dạng lưới/khung ảnh ($12+$ ô Endings):  
* **Nếu đã mở khóa:** Hiển thị ảnh minh họa có màu, tên Ending và ngày đạt được.  
* **Nếu chưa mở khóa:** Hiển thị dạng ảnh xám/khung trống kèm gợi ý mờ (Hint) điều kiện đạt được.  
4. Người chơi nhấp vào một tấm ảnh Ending đã mở khóa.  
5. Hệ thống phóng to bức ảnh, hiển thị chi tiết bức thư kỷ niệm/kịch bản kết cục và nội dung tổng kết của Ending đó.  
6. Người chơi đóng xem chi tiết và nhấn nút **"Quay lại"** để quay về Menu chính.

##### **Luồng phụ / Luồng thay thế (Alternative Flow)**

* **A1: Phân loại / Lọc loại Ending**  
  1. Tại bước 3, người chơi sử dụng bộ lọc giao diện: *Tất cả*, *Good Endings*, *Bad Endings*, *Secret Endings*.  
  2. Hệ thống cập nhật hiển thị các khung ảnh trên Bức tường tranh theo loại đã chọn.

##### **Luồng ngoại lệ (Exception Flow)**

* **E1: Lỗi đọc file lưu toàn cục (Global Profile Error)**  
  1. Tại bước 2, hệ thống không thể truy xuất dữ liệu Global Profile (do file bị hỏng hoặc lỗi bộ nhớ).  
  2. Hệ thống hiển thị thông báo: *"Không thể tải dữ liệu Bức tường kỷ niệm. Vui lòng thử lại\!"*  
  3. Màn hình duy trì ở giao diện Menu chính.

#### **Quy tắc nghiệp vụ (Business Rules)**

1. **Lưu trữ toàn cục (Global Save Persistence):** Dữ liệu các Ending đã mở khóa phải được ghi nhận vào **Global Profile** (Hồ sơ toàn cục). Khi người chơi bắt đầu lượt chơi mới (New Game) hoặc xóa file Save game tạm thời, danh sách Ending trong Gallery vẫn được giữ nguyên không bị mất.  
2. **Quy tắc hiển thị thông tin:**  
   * **Ending đã đạt:** Hiển thị đầy đủ 100% hình ảnh màu chất lượng cao, tên đầy đủ, ngày giờ mở khóa và kịch bản/bức thư kỷ niệm.  
   * **Ending chưa đạt:** Ảnh bị phủ màu xám/bóng ma (Grayscale/Silhouette), ẩn tên chi tiết, chỉ hiển thị câu gợi ý ngắn (Hint) để định hướng người chơi tìm kiếm trong các lượt chơi sau.  
3. **An toàn trải nghiệm (Spoil-Free Policy):** Không hiển thị các chi tiết kịch bản quan trọng của các Secret Endings chưa mở khóa trên giao diện gợi ý.

#### **Ghi chú**

* **Về Actor phụ:**  
  * **Hệ thống lưu trữ toàn cục (Global Profile / Database Server):** Chịu trách nhiệm lưu giữ mảng dữ liệu boolean và ngày tháng đạt được của từng ID Ending độc lập với các file Save state in-game.  
* **Thiết kế UI/UX Memory Wall:** Nên thiết kế theo dạng khung tranh treo trên tường gạch/gỗ, với các hiệu ứng ánh sáng hoặc bưu thiếp kỷ niệm để tăng tính hoài niệm và hấp dẫn thị giác cho người chơi khi sưu tầm đầy đủ bộ kết cục.

**Include**  
Không.  
**Extend**  
Không

