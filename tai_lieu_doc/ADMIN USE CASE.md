Admin \- Người quản trị nội dung / dữ liệu game  
với vai trò:

- Là Actor được đề xuất để quản lý các **dữ liệu nội dung và cấu hình gameplay** được hệ thống sử dụng  
- Admin sẽ không trực tiếp chơi game thay cho người chơi

**Admin có thể được phép:**

* Xem dữ liệu nội dung.  
* Tạo dữ liệu mới.  
* Chỉnh sửa dữ liệu.  
* Ngừng sử dụng dữ liệu.  
* Thiết lập điều kiện.  
* Thiết lập phần thưởng.  
* Thiết lập các tham số gameplay được phép cấu hình.  
* Kiểm tra tính hợp lệ của dữ liệu.

**Phân chia công việc cho Actor**

| Công việc | Actor phù hợp |
| :---- | :---- |
| Viết code Godot  | Developer  |
| Sửa GDScript  | Developer  |
| Sửa Scene  | Developer / Game Designer |
| Thiết kế UI  | Developer  |
| Debug code  | Developer  |
| Quản lý Git  | Developer  |
| Build game  | Developer  |
| Thiết kế gameplay  | Game Designer |
| Cân bằng gameplay  | Game Designer |
| Quản lý dữ liệu nội dung  | Admin |
| Quản lý cấu hình dữ liệu  | Admin |
| Quản lý tài khoản Admin  | Admin / System |

**Danh sách Admin Use Case**

| Mã | Use Case | Nhóm  | Mức độ | Trạng thái |
| :---- | :---- | :---- | :---- | :---- |
| AUC01  | Đăng nhập Admin  | Tài khoản/quyền  | SHOULD HAVE  | Có cơ sở rõ |
| AUC02 | Quản lý dữ liệu nghề  | Nghề  | MUST HAVE  | Có cơ sở rõ  |
| AUC03 | Quản lý dữ liệu NPC & nội dung quan hệ  | NPC | SHOULD HAVE  | Có cơ sở rõ  |
| AUC04 | Quản lý Quest & nội dung nhiệm vụ  | Quest  | SHOULD HAVE  | Có cơ sở rõ |
| AUC05 | Quản lý vật phẩm & Shop  | Item/Shop  | MUST HAVE  | Có cơ sở rõ  |
| AUC06 | Quản lý dữ liệu thế giới  | World  | SHOULD HAVE  | Có cơ sở rõ  |
| AUC07 | Quản lý kỹ năng & thành tựu  | Progression  | SHOULD HAVE  | Có cơ sở rõ  |
| AUC08 | Quản lý Mini Game  | Mini Game  | FUTURE  | Chưa đủ dữ liệu  |
| AUC09 | Quản lý người chơi/progress  | Player  | FUTURE  | Phụ thuộc vào Backend |
| AUC10 | Thống kê/báo cáo  | Analytics  | NOT NEEDED hiện tại  | Chưa có yêu cầu |

| Mã Use Case | AUC01 |
| :---- | :---- |
| Tên Use Case | Đăng nhập Admin |
| Mục đích | Cho phép Admin đăng nhập tài khoản quản lý 1 số dữ liệu |
| Mô tả | Admin truy cập với vai trò người quan sát hoạt động của hệ thống, từ đó có thể điều chỉnh 1 số điều cần thiết cho phù hợp hoặc khắc phục lỗi |
| Actor | Chính: Admin Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Tùy nhu cầu |

| Mã Use Case | AUC02 |
| :---- | :---- |
| Tên Use Case | Quản lý dữ liệu nghề  |
| Mục đích | Cho phép Admin quản lý dữ liệu nghề được sử dụng bởi hệ thống Gameplay  |
| Mô tả | Admin xem, thêm, chỉnh sửa, cấu hình điều kiện và ngừng sử dụng dữ liệu nghề  |
| Actor | Chính: Admin Phụ: Hệ thống  |
| Mức ưu tiên | Cao |
| Tần suất sử dụng | Theo nhu cầu quản trị  |

**Trigger**  
Admin truy cập chức năng quản lý nghề.  
**Tiền điều kiện**

* Admin đã được xác thực nếu hệ thống có cơ chế xác thực Admin.  
* Hệ thống có quyền truy cập dữ liệu nghề.  
* Dữ liệu hiện tại có thể đọc được.

**Hậu điều kiện**  
Nếu thành công:

* Dữ liệu nghề được cập nhật.  
* Dữ liệu hợp lệ có thể được Gameplay sử dụng.

Nếu thất bại:

* Dữ liệu cũ được giữ nguyên.  
* Hệ thống thông báo lỗi.

**Luồng chính**

1. Admin mở Quản lý dữ liệu nghề.  
2. Hệ thống tải danh sách nghề.  
3. Admin chọn nghề cần quản lý.  
4. Hệ thống hiển thị thông tin nghề.  
5. Admin thêm hoặc chỉnh sửa dữ liệu.  
6. Hệ thống kiểm tra tính hợp lệ.  
7. Admin xác nhận lưu.  
8. Hệ thống cập nhật dữ liệu.  
9. Hệ thống thông báo kết quả.

**Luồng thay thế**  
**A1 – Dữ liệu không hợp lệ**

* Hệ thống phát hiện dữ liệu không hợp lệ.  
* Hệ thống thông báo trường dữ liệu cần chỉnh sửa.  
* Không cập nhật dữ liệu chính thức.

**A2 – Admin hủy**

* Không lưu thay đổi.  
* Giữ dữ liệu trước đó.

**A3 – Ngừng sử dụng nghề**

* Admin chọn nghề cần ngừng sử dụng.  
* Hệ thống yêu cầu xác nhận.  
* Hệ thống chuyển nghề sang trạng thái không hoạt động.  
* Không xóa dữ liệu nếu Gameplay còn tham chiếu đến nghề.

**Luồng ngoại lệ**  
**E1 – Không thể lưu dữ liệu**

* Hệ thống báo lỗi.  
* Dữ liệu cũ được giữ nguyên.

**E2 – Dữ liệu đang được Gameplay tham chiếu**

* Hệ thống không cho phép xóa trực tiếp.  
* Chỉ cho phép ngừng sử dụng hoặc yêu cầu xử lý tham chiếu.

**Business Rules / Nguyên tắc nghiệp vụ**

* BR01: Dữ liệu nghề phải hợp lệ trước khi được sử dụng.  
* BR02: Điều kiện mở khóa phải nhất quán với Gameplay.  
* BR03: Không được tạo nghề có mã định danh trùng.  
* BR04: Không được xóa dữ liệu đang được tham chiếu nếu có nguy cơ làm lỗi Gameplay.  
* BR05: Thay đổi dữ liệu nghề phải được lưu nhất quán.

**Include**  
Không.  
**Extend**  
Không.  
**Ghi chú**  
Không.

| Use Case | MUST HAVE | SHOULD HAVE | FUTURE | NOT NEEDED | Lý do |
| :---- | ----- | ----- | ----- | ----- | :---- |
| AUC01 Đăng nhập Admin  |  | ✓  |  |  | Chưa xác định Admin chính thức  |
| AUC02 Quản lý nghề  | ✓  |  |  |  | UC03 phụ thuộc dữ liệu nghề  |
| AUC03 Quản lý NPC  |  | ✓  |  |  | UC06 có nhiều dữ liệu nội dung  |
| AUC04 Quản lý Quest  |  | ✓  |  |  | UC07 chưa được đặc tả đầy đủ  |
| AUC05 Quản lý Item/Shop  | ✓  |  |  |  | UC09/UC10 cần dữ liệu Item/Shop  |
| AUC06 Quản lý World  |  | ✓  |  |  | UC05 có nhiều dữ liệu cấu hình  |
| AUC07 Quản lý Skill/Achievement  |  | ✓  |  |  | UC13/UC15 có dữ liệu cấu hình  |
| AUC08 Quản lý Mini Game  |  |  | ✓  |  | Chưa đủ yêu cầu quản trị  |
| AUC09 Quản lý Player  |  |  | ✓  |  | Phụ thuộc Account/Server  |
| AUC10 Analytics  |  |  |  | ✓  | Không có yêu cầu thống kê hiện tại  |

| Admin Use Case  | Dữ liệu quản lý  | Hệ thống sử dụng  | Player Use Case  |
| :---- | :---- | :---- | :---- |
| AUC02 Quản lý nghề  | Nghề, điều kiện, cấp độ, chi phí  | Career System  | UC03  |
| AUC03 Quản lý NPC  | NPC, sở thích, thoại, mốc cảm tình, phần thưởng  | NPC Relationship  | UC06  |
| AUC04 Quản lý Quest  | Quest, điều kiện, phần thưởng  | Quest System  | UC07, UC05.2  |
| AUC05 Quản lý Item/Shop  | Item, giá, loại, điều kiện  | Inventory/Shop  | UC09, UC10  |
| AUC06 Quản lý World  | Khu vực, tài nguyên, rương, waypoint, loot  | World System  | UC05  |
| AUC07 Quản lý Skill  | Skill, điều kiện, cấp độ, buff  | Skill System  | UC13  |
| AUC07 Quản lý Achievement  | Thành tựu, điều kiện, reward  | Achievement System  | UC15  |
| AUC08 Mini Game  | Dữ liệu Mini Game  | Mini Game System  | UC14  |
| Player Management  | Account/progress  | Account/Save/Server  | UC01, UC04...  |

Ghi chú: AUC07 quản lý chung Skill và Achievement nhưng mapping riêng biệt vì sử dụng UC khác nhau cho các hướng đến khác nhau. Quản lý chung vì nó có chung luồng xử lý

- [x] ~~Actor Admin đã được **đề xuất**~~  
- [x] ~~Quyền Admin đã được xác định ở mức đề xuất~~   
- [x] ~~Đã phân biệt Admin và Developer~~   
- [x] ~~xác định các nhóm dữ liệu có khả năng cần quản lý~~   
- [x] ~~đặc tả Use Case quan trọng~~   
- [x] ~~mapping Admin ↔ Player~~  
- [ ] mapping Admin ↔ Gameplay   
- [x] ~~kiểm tra dữ liệu nghề~~  
- [x] ~~kiểm tra NPC~~    
- [x] ~~kiểm tra Quest~~   
- [x] ~~kiểm tra Item/Shop~~   
- [x] ~~kiểm tra World~~   
- [x] ~~kiểm tra Skill/Achievement~~   
- [x] ~~phân biệt dữ liệu gameplay với dữ liệu Player~~   
- [x] ~~kiểm tra khả năng triển khai với Godot~~   
- [x] ~~phân loại MUST HAVE~~   
- [x] ~~phân loại SHOULD HAVE~~   
- [x] ~~phân loại FUTURE~~  
- [x] ~~loại Analytics khỏi phạm vi hiện tại~~   
- [x] ~~đề xuất cây Use Case Admin~~   
- [x] ~~Admin có phải Actor chính thức hay không~~   
- [ ] Có xây Admin Tool thật hay chỉ quản lý data nội bộ   
- [ ] Kiến trúc Server/Database   
- [ ] Cơ chế Login online/offline   
- [ ] Phạm vi quản lý Quest  
- [ ] Có cho Admin chỉnh dữ liệu Player hay không 