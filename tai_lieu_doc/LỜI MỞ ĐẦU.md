Tài liệu này trình bày đặc tả hệ thống cho dự án game 2D **START AGAIN**. Mục đích của tài liệu là mô tả một cách có hệ thống các chức năng, tác nhân, phạm vi và quy trình tương tác giữa người chơi với hệ thống, làm cơ sở cho quá trình phân tích, thiết kế, lập trình và kiểm thử sản phẩm.  
Tài liệu tập trung mô tả hệ thống dưới góc nhìn của người chơi, trong đó Người chơi là Actor chính thực hiện các thao tác và tương tác với những chức năng được cung cấp trong trò chơi.  
Nội dung tài liệu được tổ chức thành các phần chính gồm: giới thiệu, tổng quan hệ thống, danh sách Use Case và đặc tả chi tiết từng Use Case. Trong quá trình phát triển dự án, tài liệu có thể tiếp tục được cập nhật khi các chức năng, quy tắc nghiệp vụ và yêu cầu của trò chơi được xác định rõ hơn.  
Đối với những thông tin chưa được xác định trong phạm vi dữ liệu hiện tại, tài liệu sử dụng các ký hiệu **\[CẦN BỔ SUNG\]** hoặc **\[CẦN XÁC NHẬN\]** nhằm tránh đưa các giả định chưa được thống nhất vào đặc tả chính thức

**START AGAIN** là một game 2D trong đó người chơi điều khiển hoặc định hướng nhân vật trong thế giới game, tương tác với các chức năng của hệ thống và phát triển nhân vật thông qua quá trình chơi.  
Trò chơi tập trung vào các hoạt động liên quan đến lựa chọn, tùy chỉnh và phát triển nhân vật. Trong đó, chức năng Quản lý nghề cho phép người chơi truy cập thông tin về nghề, kiểm tra trạng thái và điều kiện liên quan, lựa chọn nghề và thực hiện các thao tác liên quan theo quy tắc của trò chơi.  
**Các mục tiêu cụ thể khác của trò chơi:**

* Mở rộng phạm vi khu vực hoạt động để mở khóa thêm nghề mới  
* Tương tác với các nhân vật khác để có thể mở cốt truyện ẩn hoặc nhiệm vụ ẩn dẫn đến quá khứ của nhân vật chính  
* Mở rộng các bản đồ khu vực, bản đồ rộng nhất là 5x5, với bản đồ mở đầu là ở giữa trung tâm

Tài liệu đặc tả được xây dựng nhằm:

* Mô tả phạm vi và tổng quan của hệ thống START AGAIN.  
* Xác định Actor tương tác với hệ thống.  
* Xác định các Use Case đã được phân tích.  
* Mô tả mục đích và phạm vi của từng Use Case.  
* Chuẩn hóa cách mô tả luồng tương tác giữa Người chơi và hệ thống.  
* Làm cơ sở cho quá trình thiết kế và phát triển chức năng.  
* Hỗ trợ lập trình viên hiểu đúng yêu cầu chức năng.  
* Hỗ trợ thiết kế game và thiết kế giao diện dựa trên các hành vi đã được đặc tả.  
* Hỗ trợ kiểm thử xây dựng các trường hợp kiểm thử dựa trên luồng chính, luồng thay thế và luồng ngoại lệ.  
* Làm cơ sở để các thành viên trong nhóm thống nhất cách hiểu về chức năng của hệ thống.

START AGAIN là một game 2D cho phép Người chơi điều khiển hoặc định hướng nhân vật trong thế giới game và tương tác với các chức năng được hệ thống cung cấp.  
Trong phạm vi thông tin hiện tại, đã xác định chức năng ở mục 2.3 Các nhóm chức năng chính  
Các chức năng khác của hệ thống:  
**Sẽ bổ sung thêm (nếu có)**  
Actor chính của hệ thống là:  
**Người chơi (Player)**  
Người chơi thực hiện các thao tác trực tiếp với hệ thống game thông qua giao diện và các chức năng được cung cấp.  
Bên cạnh đó, có các **nhân vật phụ (NPC)** hỗ trợ trong quá trình chơi

Dựa trên thông tin hiện có, phạm vi đặc tả tập trung vào:

1. Người chơi.  
2. Nhân vật trong game.  
3. Chức năng Nghề.  
4. Các thao tác liên quan đến lựa chọn và quản lý nghề.  
5. Trạng thái mở khóa và điều kiện liên quan đến nghề.  
6. Các chức năng phát triển nhân vật được xác định trong quá trình phân tích.  
7. Thành tựu  
8. Chức năng Tiền  
9. Chức năng Quan Hệ  
10. Chức năng Kỹ năng  
11. Minigame  
12. Inventory

Các thành phần khác:  
**Công ty**  
**Shop**  
**Kinh doanh**  
chưa có thông tin :v 

1. Player / Người chơi: Người sử dụng và tương tác trực tiếp với trò chơi START AGAIN.   
2. Character / Nhân vật: Đối tượng do người chơi điều khiển hoặc định hướng trong thế giới game. (NPC)  
3. Actor: Đối tượng bên ngoài tương tác với hệ thống để thực hiện một Use Case.   
4. Use case: Một chức năng hoặc nhóm hành vi mà Actor thực hiện với hệ thống nhằm đạt được một mục tiêu cụ thể.   
5. Nghề: Chức năng cho phép người chơi xem, lựa chọn và thực hiện các thao tác liên quan đến nghề của nhân vật.   
6. Kỹ năng: Các khả năng hoặc chức năng có liên quan đến nhân vật/nghề. **Cơ chế Kỹ Năng sẽ được bổ sung sau**  
7. Vật phẩm: Đối tượng trong game có thể liên quan đến quá trình chơi.   
8. Nhiệm vụ: Hoạt động hoặc mục tiêu mà người chơi có thể thực hiện trong game. Sẽ có nhiệm vụ từ NPC để mở ra thêm nhiều hướng đi khác, gợi mở thêm ký ức đã trải qua  
9. Level: Cấp độ của nhân vật hoặc một đối tượng trong game.   
10. EXP: Kinh nghiệm được sử dụng trong cơ chế phát triển/cấp độ của game.   
11. HP: Chỉ số điểm sinh lực của nhân vật  
12. MP: Chỉ số năng lượng của nhân vật.   
13. UI: Giao diện người dùng mà người chơi sử dụng để tương tác với hệ thống.   
14. Game state: Trạng thái hiện tại của hệ thống hoặc trò chơi. **CHƯA THỐNG NHẤT CÁC TRẠNG THÁI CỦA HỆ THỐNG**  
15. Unlock/Mở khóa: Trạng thái cho phép người chơi sử dụng một chức năng hoặc đối tượng sau khi đáp ứng điều kiện tương ứng.   
16. Điều kiện mở khóa: Điều kiện mà người chơi phải đáp ứng để một nghề hoặc chức năng có thể được mở khóa. **Điều kiện cụ thể sẽ được thống nhất sau khi có MVP**  
17. Game 2D: Trò chơi điện tử sử dụng cách thể hiện và tương tác trong không gian hai chiều. 

**TÀI LIỆU CỦA NHÓM**  
Phản hồi khảo sát: [Start Again: Story and Core \- Google Biểu mẫu](https://docs.google.com/forms/d/179p1sRNoKAW7FHVpDw1gZDeEhrJ1OTClPvyl9gnryo0/edit#responses)   
Bài khảo sát: [Start Again: Story, Game Core and Gameplay](https://docs.google.com/forms/d/e/1FAIpQLScJOa1q1ZJ9b371uYQmBTMkcS_s-_LtBPoOQZAdqB_QGAjQbQ/viewform)   
Project Status: [Project Status \- Google Trang tính](https://docs.google.com/spreadsheets/d/1eQaj4cksV0rW5Nl-6W104rwSF9tgUoezbfpFwOY8QUs/edit?gid=1386834576#gid=1386834576)   
Admin UseCase: [ADMIN USE CASE \- Google Tài liệu](https://docs.google.com/document/d/1CzuaDGDTJyjtn0gk-3EZz7leqLkHouMrcf3s6hPL8fE/edit?tab=t.0)   
Đặc tả Use Case: [ĐẶC TẢ USE CASE \- Google Tài liệu](https://docs.google.com/document/d/1noFjEOHw4BTnydBE1hYmyxxj_iC0BOaCaG6oIr_70xo/edit?tab=t.ahbexf20bzyd) 

**TÀI LIỆU KHÁC**

**START AGAIN** là một game 2D trong đó Người chơi tương tác với thế giới game thông qua nhân vật và các chức năng được hệ thống cung cấp.  
Người chơi giữ vai trò chính trong quá trình trải nghiệm game. Người chơi có thể thực hiện các thao tác liên quan đến nhân vật và sử dụng những chức năng được mở ra trong quá trình chơi.  
Một chức năng đã được xác định là Quản lý nghề. Thông qua chức năng này, người chơi có thể truy cập danh sách nghề, kiểm tra trạng thái mở khóa và điều kiện liên quan, lựa chọn nghề và thực hiện các thao tác liên quan đến nghề theo quy tắc của trò chơi.  
Vòng lặp chơi tổng quát hiện có thể xác định ở mức:  
Người chơi truy cập game → tương tác với nhân vật/hệ thống → lựa chọn hoặc thực hiện các chức năng → hệ thống kiểm tra điều kiện → hệ thống cập nhật trạng thái tương ứng.  
Các hoạt động khác trong vòng lặp chơi:  
**\[CẦN XÁC NHẬN\]**  
**Mục tiêu trải nghiệm chính**  
Dựa trên thông tin hiện tại, trò chơi tập trung vào:

* Lựa chọn.  
* Tùy chỉnh.  
* Phát triển nhân vật.  
* Tương tác với các chức năng của hệ thống.  
* Quản lý và lựa chọn nghề.  
* Quản lý quan hệ  
* Xây dựng luồng kinh tế/kinh doanh để đạt mục tiêu  
* Quản lý kỹ năng của nhân vật  
* Quest cốt truyện

Mục tiêu cụ thể của trò chơi:

* Chạy theo nhiệm vụ chính của cốt truyện  
* Tương tác với các NPC để mở khóa thêm các nhiệm vụ ẩn, cốt truyện ẩn  
* Xây dựng hệ thống và kiếm được 30 tỷ VNĐ

Người chơi (Player) là Actor chính của START AGAIN.  
Người chơi tương tác trực tiếp với hệ thống để:

* Truy cập các chức năng được cung cấp.  
* Xem thông tin.  
* Kiểm tra trạng thái.  
* Thực hiện lựa chọn.  
* Tùy chỉnh nhân vật theo các chức năng được hỗ trợ.  
* Quản lý nghề.  
* Thực hiện các hành động khác được hệ thống cho phép.

Các Actor khác sẽ bao gồm NPC, Admin, Server/hệ thống  
Các Actor này sẽ song hành cùng với người chơi khi làm nhiệm vụ hoặc sử dụng 1 số chức năng cần thiết của người chơi  
**NPC:**

* Hỗ trợ Nhiệm vụ, Khám phá thế giới, Nghề, Dịch vụ, Kinh tế và 1 số chức năng khác

**Admin:**

* Hỗ trợ người chơi khi người chơi sử dụng 1 số chức năng  
* Đóng vai trò là người quan sát, theo dõi quá trình hành động của người chơi khi thực hiện hành động  
* Quản lý các chức năng lớn khi xảy ra sai sót hay luồng ngoại lệ

**Server/Hệ thống:**

* Với vai trò là nền tảng thực hiện các chức năng  
* Yêu cầu Kỹ thuật cứng để thực hiện và có luồng thay thế thay cho luồng chính khi sự kiện xảy ra ko theo dự định

| STT | Nhóm chức năng | Trạng thái |
| :---- | :---- | :---- |
| 1 | Quản lý nghề  | đã chốt |
| 2 | Quản lý nhân vật  | chốt |
| 3 | Kỹ năng  | chốt |
| 4 | Vật phẩm  | chốt |
| 5 | Nhiệm vụ  | chốt |
| 6 | Tương tác NPC  | chốt |
| 7 | Di chuyển/khám phá  | chốt |
| 8 | Chiến đấu  | chốt |
| 9 | Lưu/đọc dữ liệu  | chốt |
| 10 | Cài đặt  | chốt |

Quy trình có thể xác định từ thông tin hiện tại:

1. Người chơi khởi động trò chơi.	  
2. Người chơi truy cập vào hệ thống game.  
3. Người chơi điều khiển hoặc định hướng nhân vật.  
4. Người chơi truy cập các chức năng được hệ thống cung cấp.  
5. Người chơi lựa chọn hoặc thực hiện một thao tác.  
6. Hệ thống kiểm tra trạng thái và các điều kiện liên quan.  
7. Hệ thống xử lý thao tác.  
8. Hệ thống cập nhật hoặc hiển thị kết quả tương ứng.  
9. Người chơi tiếp tục tương tác với hệ thống.

Các bước liên quan đến tạo/chọn nhân vật, lưu tiến trình, kết thúc phiên chơi hoặc các hoạt động khác:  
**\[CẦN XÁC NHẬN\]**  
**Thông tin cần xác nhận**

1. Mục tiêu chính của người chơi trong START AGAIN.  
2. Vòng lặp gameplay đầy đủ.  
3. Các chức năng chính ngoài Quản lý nghề.  
4. Có hay không hệ thống tạo/chọn nhân vật.  
5. Có hay không hệ thống lưu/đọc tiến trình.  
6. Có hay không NPC, chiến đấu, nhiệm vụ, vật phẩm.  
7. Các trạng thái chính của game.

1. Cấu trúc tài liệu  
- [x] ~~hoàn thành phần Lời mở đầu.~~  
- [x] ~~hoàn thành phần 1\. Giới thiệu.~~  
- [x] ~~hoàn thành phần 1.1 Mục đích.~~  
- [x] ~~hoàn thành phần 1.2 Phạm vi ở mức thông tin hiện có.~~  
- [x] ~~xây dựng phần 1.3 Thuật ngữ.~~  
- [x] ~~xây dựng phần 1.4 Tài liệu tham khảo.~~  
- [x] ~~xây dựng phần 2\. Tổng quan hệ thống.~~  
- [x] ~~xây dựng phần 2.1 Tổng quan hệ thống.~~  
- [x] ~~xây dựng phần 2.2 Tổng quan hệ thống.~~  
- [x] ~~xây dựng phần 2.3 Tổng quan hệ thống.~~  
- [x] ~~xây dựng phần 2.4 Tổng quan hệ thống.~~  
- [x] ~~Checklist hoàn thiện~~  
2. Use Case  
- [x] ~~Hoàn thiện UC01.~~  
- [x] ~~Hoàn thiện UC02.~~  
- [x] ~~Hoàn thiện UC03~~  
- [x] ~~Hoàn thiện UC04.~~  
- [x] ~~Hoàn thiện UC05.~~  
- [x] ~~Hoàn thiện UC06.~~  
- [x] ~~Hoàn thiện UC07.~~  
- [x] ~~Hoàn thiện UC08.~~  
- [x] ~~Hoàn thiện UC09.~~  
- [x] ~~Hoàn thiện UC010.~~  
- [x] ~~Hoàn thiện UC011.~~  
- [x] ~~Hoàn thiện UC012.~~  
- [x] ~~Hoàn thiện UC013.~~  
- [x] ~~Hoàn thiện UC014.~~  
- [x] ~~Hoàn thiện UC015.~~  
- [x] ~~Kiểm tra toàn bộ mã Use Case sau khi có danh sách chính thức.~~  
- [x] ~~Actor chính "Người chơi" đã được thống nhất.~~  
3. Thông tin dự án còn thiếu  
- [x] ~~Mục tiêu/trải nghiệm chính của START AGAIN.~~  
- [ ] Gameplay loop đầy đủ.  
- [x] ~~Danh sách Use Case chính thức.~~  
- [ ] Danh sách nghề.  
- [ ] Quy tắc nghề.  
- [ ] Điều kiện mở khóa nghề.  
- [ ] Quy tắc thay đổi nghề.  
- [ ] Các chức năng phát triển nhân vật.  
- [ ] Hệ thống kỹ năng.  
- [ ] Hệ thống vật phẩm.  
- [ ] Hệ thống nhiệm vụ.  
- [ ] Hệ thống NPC.  
- [ ] Hệ thống chiến đấu.  
- [ ] Hệ thống lưu/đọc dữ liệu.  
- [ ] Công nghệ/framework.  
- [ ] Các tài liệu tham khảo chính thức.

