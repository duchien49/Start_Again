1. **Kiến trúc dữ liệu tổng thể:**  
   *Phần này định nghĩa các cấu trúc dữ liệu cốt lõi sẽ được dựng trong Godot (dưới dạng Global/Autoload hoặc Resource).*

   #### 1.1. Hệ thống Quản lý Biến toàn cục (GameManager / Autoload):

   Định nghĩa các biến trạng thái chạy xuyên suốt trò chơi, áp dụng cơ chế bảo vệ dữ liệu (chống số âm):  
* Tài chính & Chỉ số nhân vật:  
  * wallet\_cash (Int): Tiền mặt hiện có. Quy tắc: max(0, value).  
  * skill\_points (Int \- SP): Điểm kỹ năng dùng để nâng cấp cây kỹ năng. Quy tắc: max(0, value).  
  * health / energy / stress (Float: $0-100$). Quy tắc giới hạn biên độ min/max nghiêm ngặt.  
* Hệ thống Quản lý Thời gian (TimeManager / Autoload):  
  * current\_day (Int), current\_hour (Int), current\_minute (Int).  
  * Quy đổi thời gian thực sang game: *Ví dụ: 1 giây thực tế \= 1 phút trong game*.  
  * Chu kỳ sự kiện: Phát tín hiệu định kỳ mỗi khi qua ngày mới (day\_changed) để kích hoạt các cơ chế như: tính chi phí vận hành công ty, reset món hàng giới hạn ở Shop, hoặc trừ lương/ngày nợ lương nhân sự.

  #### 1.2. Kiến trúc Dữ liệu Tĩnh (Data-Driven Design với Custom Resource):

  Sử dụng hệ thống Resource của Godot để tách biệt hoàn toàn dữ liệu game ra khỏi mã nguồn (giúp Game Designer dễ dàng cân chỉnh số liệu trên Inspector mà không cần sửa code):

* SkillData.tres: Lưu ID, tên, mô tả, cấp độ tối đa, chi phí SP và hệ số buff.  
* ItemData.tres: Lưu ID, tên, giá mua/bán, hiệu ứng hồi phục thể lực/stress, giới hạn stack.  
* AchievementData.tres: Lưu mã thành tựu, điều kiện kích hoạt, phần thưởng đi kèm và tọa độ đặt cúp trong phòng.

**2\. Đặc tả chi tiết các core systems:**  
*Phần này chuyển hóa các Use Case thành sơ đồ logic hoặc quy tắc kỹ thuật để bạn (và team) nhìn vào là biết phải code như thế nào:*   
*Trong đó:*   
*\- Dữ liệu đầu vào/đầu ra: Liệt kê các biến động chạm.*   
*\- Quy tắc và thuật toán: điều kiện kiểm tra, công thức, hành vi khi thất bại.*   
*\- Tín hiệu liên thông: Gửi/nhận tín hiệu gì với hệ thống.*  
*\- Yêu cầu lưu trữ: Có cần lưu vào file save không?*

**2.1. Module khởi động game (UC01):**

1. *Dữ liệu đầu vào/đầu ra:*  
- has\_save\_file (boolean): Kiểm tra xem thư mục user:// có file lưu game hợp lệ hay không.  
- current\_game\_version (string): Kiểm tra phiên bản game để tương thích dữ liệu cũ.   
2. *Quy tắc và thuật toán:*   
- Khi mở game, hệ thống chạy màn hình Splash Screen \-\> Chuyển sang Main Menu.  
- Nếu has\_save\_file \== true, kích hoạt hiển thị “Tiếp tục”; ngược lại, vô hiệu hóa nút này và chỉ hiển thị “Chơi mới”.  
3. *Tín hiệu liên thông:* game\_initialized, save\_file\_checked.  
4. *Yêu cầu lưu trữ:* Khởi tạo cấu trúc thư mục lưu trữ cục bộ và tệp cấu hình mặc định khi bấm “Chơi mới”.

   **2.2. Module cài đặt (UC02):**

   1. *Dữ liệu đầu vào/đầu ra:*  
- Master\_volume, sfx\_volume, bgm\_volume (float từ 0.0 đến 1.0).  
- Fullscreen\_mode (boolean), resolution\_scale (Vector2).  
  2. *Quy tắc và thuật toán:*   
- Khi mở game, hệ thống chạy màn hình Splash Screen \-\> Chuyển sang Main Menu.  
- Nếu has\_save\_file \== true, kích hoạt hiển thị “Tiếp tục”; ngược lại, vô hiệu hóa nút này và chỉ hiển thị “Chơi mới”.  
  3. *Tín hiệu liên thông:* settings\_updated.  
  4. *Yêu cầu lưu trữ:* Lưu vào file cấu hình riêng biệt (user://settings.cfg) bằng lớp ConfigFile của Godot để giữ nguyên khi tắt game.

  **2.3. Module quản lý nghề (UC03):**

1. *Dữ liệu đầu vào/đầu ra:*

   current\_job\_id (string), base\_salary (int), work\_hours (array), job\_level (int). 

2. *Quy tắc và thuật toán:*  
- Xác định nguồn thu nhập cố định định kỳ (theo ngày/tuần in-game) cho nhân vật dựa trên công việc hiện tại.  
- Điều kiện thăng tiến công việc phụ thuộc vào Cấp độ kỹ năng (liên kết chéo với module Kỹ năng \- UC13).  
3. *Tín hiệu liên thông:* job\_changed, salary\_earned.   
4. *Yêu cầu lưu trữ:* Lưu vào tệp Save State của lượt chơi hiện tại.

   **2.4. Module quản lý nhân vật (UC04):**

1. *Dữ liệu đầu vào/đầu ra:*

   Character\_name (string), health (int: 0-100), energy (int: 0-100), stress (int: 0-100).

2. *Quy tắc và thuật toán:*  
- Các chỉ số dao động trong ngưỡng giới hạn \[0, 100\].  
- Ngưỡng nguy hiểm: Khi Stress \>= 80, nhân vật rơi vào trạng thái cảnh báo; nếu chạm 100, kích hoạt trạng thái Burnout (chặn học tập/làm việc). Khi health \<= 0, kích hoạt sự kiện ngất xỉu/nhập viện.  
3. *Tín hiệu liên thông:* stats\_changed, health\_depleted, stress\_threshold\_reached.   
4. *Yêu cầu lưu trữ:* Lưu trạng thái chỉ số tức thời vào Save State.

   **2.5. Module khám phá thế giới (UC05):**

   *a. Dữ liệu đầu vào/Đầu ra (Variables):*

* current\_location\_id (String): ID khu vực hiện tại (Ví dụ: khu\_tro, quan\_ca\_phe, cong\_ty).  
* unlocked\_locations (Array): Danh sách các khu vực đã được mở khóa để di chuyển.

  *b. Quy tắc & Thuật toán (Logic/Rules):*

* Tiêu hao thời gian & thể lực: Việc di chuyển giữa các địa điểm tiêu tốn một lượng thời gian in-game nhất định và tiêu hao chỉ số energy của nhân vật (UC04).  
* Điều kiện mở khóa: Khu vực mới chỉ được mở khóa khi người chơi đạt cấp độ nhân vật hoặc hoàn thành một nhiệm vụ cốt truyện tương ứng (UC07).

  *c. Tín hiệu liên thông (Signals):*

* location\_changed(new\_location\_id), location\_unlocked(location\_id).

  *d. Yêu cầu lưu trữ (Persistence):*

* Lưu vị trí hiện tại và mảng danh sách các khu vực đã mở khóa vào Save State.

  **2.6. Module quan hệ NPC (UC06):**

  a. Dữ liệu đầu vào/Đầu ra (Variables):

  * npc\_id (String), friendship\_points (Float: Điểm thiện cảm từ 0 \- 100).  
  * npc\_status (Enum: Người lạ, Bạn bè, Người yêu, Kẻ thù).  
    b. Quy tắc & Thuật toán (Logic/Rules):  
  * Tăng giảm thiện cảm: Tương tác hàng ngày, tặng quà đúng sở thích hoặc hoàn thành nhiệm vụ phụ của NPC sẽ làm tăng điểm friendship\_points. Hành vi xúc phạm hoặc phản bội làm giảm điểm.  
  * Ngưỡng cấp bậc quan hệ: Khi điểm đạt mốc (Ví dụ: $\geq 50$), trạng thái NPC chuyển từ Người lạ sang Bạn bè, mở ra các hội thoại hoặc sự kiện độc quyền.

  c. Tín hiệu liên thông (Signals):

  * npc\_friendship\_changed(npc\_id,new\_points), relationship\_tier\_up(npc\_id, new\_tier).

  d. Yêu cầu lưu trữ (Persistence):

  * Lưu toàn bộ chỉ số thiện cảm và trạng thái quan hệ của tất cả NPC vào Save State.

  **2.7. Module nhiệm vụ (UC07):**

    a. Dữ liệu đầu vào/Đầu ra (Variables):

* quest\_id (String), quest\_status (Enum: Chưa nhận, Đang thực hiện, Hoàn thành, Thất bại).  
* quest\_objectives (Dictionary): Danh sách mục tiêu (Ví dụ: Tiêu diệt/Thu thập X món đồ, Gặp NPC Y).

  b. Quy tắc & Thuật toán (Logic/Rules):

* Theo dõi tiến trình: Hệ thống liên tục lắng nghe các sự kiện in-game (như nhặt item, tăng tiền, gặp NPC). Khi mục tiêu đạt giá trị yêu cầu, tự động cập nhật trạng thái mục tiêu lên hoàn thành.  
* Trả thưởng: Khi tất cả mục tiêu hoàn thành, người chơi bấm nhận thưởng để gọi module tiền tệ (UC11) hoặc Inventory (UC09) cấp phần thưởng.

  c. Tín hiệu liên thông (Signals):

* quest\_accepted(quest\_id), quest\_progress\_updated(quest\_id), quest\_completed(quest\_id).

  d. Yêu cầu lưu trữ (Persistence):

* Lưu trạng thái nhiệm vụ và tiến trình các mục tiêu vào Save State.

  **2.8. Module kinh doanh (UC08):**

1. *Số liệu đầu vào/đầu ra:*  
- business\_type\_id (string): loại hình kinh doanh (VD: Cửa hàng tiện lợi, quán cà phê, công ty phần mềm…).  
- operating\_cost (int): chi phí vận hành hằng ngày/tháng/năm.  
- daily\_revenue (int): doanh thu tính toán theo ngày in-game.  
- market\_trend (float): hệ số biến động thị trường (ảnh hưởng đến doanh thu).  
2. *Quy tắc và thuật toán:*  
- Công thức lợi nhuận: 

  Doanh thu \=tiền thu sản phẩm \* số lượng;

  Chi phí vận hành \= tiền chi sản phẩm \* số lượng \+ tiền thuê mặt bằng \+ tiền thuê nhân viên \+ thuế 

  Lợi nhuận thực tế \= (Doanh thu gốc \* Market Trend) \- Chi phí vận hành.

- Xử lý thua lỗ: Nếu số dư tài khoản không đủ bù đắp chi phí vận hành, hệ thống cảnh báo nợ tài chính và tự động ghi nhận vào lịch sử giao dịch (UC11).  
3. *Tín hiệu liên thông:* revenue\_generated (amount), business\_status\_changed (is\_active).   
4. *Yêu cầu lưu trữ:* Lưu loại hình kinh doanh, mức vốn đầu tư và lịch sử doanh thu vào Save State của lượt chơi hiện tại.

   **2.9. Module inventory (UC09):**

1. *Dữ liệu đầu vào/đầu ra:*  
- Inventory\_slots (array): Lưu danh sách các vật phẩm (item ID, số lượng, loại vật phẩm).  
- Max\_slots (int): Sức chứa tối đa của túi đồ/kho.  
2. *Quy tắc và thuật toán:*  
- Xếp đống: Nếu vận phẩm cùng loại có thuộc tính is\_stackable \= True, cộng dồn số lượng cho đến khi đạt max\_stack\_size (VD: 99 slots).  
- Kiểm tra giỏ đồ: Khi thêm vật phẩm mới, nếu kho đã đầy (inventory\_slots.size() \>= max\_slots), hiển thị thông báo “Túi đồ đã đầy\!” và hủy thao tác nhận vật phẩm.  
- Sử dụng vật phẩm: Khi tiêu thụ một item (VD: nước tăng lực), gọi module Nhân vật (UC04) để hồi Thể lực/giảm Stress, sau đó giảm số lượng vật phẩm đi 1\.  
3. *Tín hiệu liên thông: inventory\_updated, item\_used(item\_id), item\_added(item\_id, amount).*  
4. *Yêu cầu lưu trữ:* Lưu mảng danh sách vật phẩm và số lượng tương ứng vào Save State.

   **2.10. Module cửa hàng (UC10):**

1. *Dữ liệu đầu vào/đầu ra:*

   shop\_item\_list (array): danh sách các vật phẩm được bán (item ID, giá mua, giá bán lại, số lượng tồn kho).

2. *Quy tắc và thuật toán:*  
- Quy trình mua:   
+ B1: Kiểm tra tiền mặt/ngân hàng (UC11) \>= Giá vật phẩm \* số lượng.  
+ B2: Kiểm tra túi đồ (UC09) còn chỗ trống.  
+ B3: Nếu thỏa mãn: Trừ tiền \-\> Thêm vật phẩm vào Inventory \-\> Giảm số lượng tồn kho của Shop (nếu có giới hạn).  
- Quy trình bán: Trừ vật phẩm khỏi Inventory \-\> cộng 50% \- 70% giá trị gốc vào tài khoản người chơi.  
3. *Tín hiệu liên thông:* item\_purchased(item\_id, total\_cost), item\_sold(item\_id, total\_earned).  
4. *Yêu cầu lưu trữ:* Lưu trạng thái các món đồ giới hạn (Limited items) đã mua trong ngày vào Save State (reset theo chu kỳ ngày in-game).

   **2.11. Module quản lý tiền (UC11):** 

1. *Dữ liệu đầu vào/đầu ra:*

   wallet\_cash (tiền mặt), bạnk\_balance (tiền trong ngân hàng), transaction\_history (array chứa lịch sử thu/chi).

2. *Quy tắc thuật toán:*  
- Quy tắc chống số âm: Số dư tài khoản tuyệt đối không được nhỏ hơn 0 (max(0, value)).  
3. *Tín hiệu liên thông:*

   money\_changed (phát đi số dư mới để UI các màn hình tự động cập nhật).

4. *Yêu cầu liên thông: Lưu toàn bộ tiền tệ và lịch sử giao dịch vào Save State.*

   **2.12. Module công ty và nhân sự (UC12):**

1. *Dữ liệu đầu vào/đầu ra:*  
- company\_name (string), office\_level (int).  
- office\_capacity (int).  
- employee\_list (array/list chứa ID, tên, mức lương, độ trung thành, năng suất).  
- unpaid\_days (int): số ngày trễ trong tích lũy.  
- loyalty (int): độ trung thành của nhân viên.   
2. *Quy tắc và tính toán:*  
- Sức chứa văn phòng (UC12.6): Không cho phép tuyển thêm nhân viên mới nếu employee\_list.size() \>= office\_capacity. Muốn tăng sức chứa phải nâng cấp văn phòng.  
- Quy tắc trễ/nợ lương (UC12.5):   
+ Nếu đến kỳ trả lương mà số dư ngân hàng (UC11) ít hơn tổng quỹ lương: unpaid\_days \+= 1\.   
+ Khi unpaid\_days \>= 3 hoặc loyalty \<= 0, kích hoạt sự kiện Đình công / Nhân viên hàng loạt nghỉ việc.  
- Phí sa thải (UC12.4): Trừ phí đền bù hợp đồng \= 1.5 \* Mức lương hiện tại.  
3. *Tín hiệu liên thông:* payroll\_processed (total\_paid), employee\_hired(employee\_id)  
4. *Yêu cầu lưu trữ:* danh sách nhân viên, cấp độ văn phòng và số ngày nợ lương vào Save State. 

   **2.13. Module cây kỹ năng và trang bị (UC13):**

   **a. Dữ liệu đầu vào/Đầu ra (Variables):**

* skill\_id (String), current\_level (Int), max\_level (Int), sp\_cost (Int).  
* active\_slots (Array): Các ô trang bị kỹ năng hoạt động ngoài gameplay (UC13.4).

  **b. Quy tắc & Thuật toán (Logic/Rules):**

* **Điều kiện học/nâng cấp:** Cần đủ điểm kỹ năng SP và Tiền (UC11). Nếu nhân vật quá mệt (Health \< 20% hoặc Stress \> 80%), hệ thống chặn hành động nâng cấp hoặc tăng gấp đôi thời gian học (hình phạt Burnout).  
* **Trang bị độc lập (Unique Equip):** Một kỹ năng chỉ được gán vào 01 ô trang bị duy nhất tại một thời điểm để tránh cộng dồn buff ảo.

  **c. Tín hiệu liên thông (Signals):**

* skill\_unlocked(skill\_id), skill\_level\_up(skill\_id, new\_level), skill\_equipped(slot\_index, skill\_id).

  **d. Yêu cầu lưu trữ (Persistence):**

* Lưu cấp độ của toàn bộ kỹ năng và danh sách các kỹ năng đang được đặt trong ô trang bị vào Save State.

	  
**2.14. Module Mini Game (UC14):**  
		a. Dữ liệu đầu vào/Đầu ra (Variables):

* minigame\_id (String), score (Int), time\_limit (Float), reward\_multiplier (Float).  
  b. Quy tắc & Thuật toán (Logic/Rules):  
* Luồng chạy Mini Game: Khi kích hoạt từ cốt truyện hoặc tương tác công việc, tạm dừng luồng game chính (Pause Main Game) $\rightarrow$ Tải scene Mini Game $\rightarrow$ Nhận kết quả điểm số (score) sau khi kết thúc.  
* Quy đổi phần thưởng: Dựa vào điểm số đạt được, áp dụng hệ số nhân để trả thưởng Tiền (UC11), tăng kỹ năng hoặc cải thiện chỉ số stress (UC04).  
  c. Tín hiệu liên thông (Signals):  
* minigame\_started(minigame\_id), minigame\_finished(minigame\_id, final\_score).  
  d. Yêu cầu lưu trữ (Persistence):  
* Mini Game thường mang tính chất tức thời, chỉ lưu điểm cao nhất (High Score) nếu hệ thống có tính năng kỷ lục cá nhân vào Save State.

  **2.15. Module thành tựu và kết cục (UC15):**

  **a. Dữ liệu đầu vào/Đầu ra (Variables):**

* achievement\_list (Dictionary / Array): Danh sách tất cả thành tựu với các thuộc tính: id, is\_unlocked (Boolean), unlocked\_timestamp (String), is\_reward\_claimed (Boolean).  
* unlocked\_endings (Array): Mảng chứa các mã Ending đã đạt được qua các lượt chơi (Ví dụ: \["GOOD\_01", "BAD\_03", "SECRET\_02"\]).

  **b. Quy tắc & Thuật toán (Logic/Rules):**

* **Cơ chế theo dõi ngầm (UC15.2):** Hệ thống lắng nghe các sự kiện in-game liên tục. Khi điều kiện thỏa mãn (\$100\\%\$), tự động chuyển is\_unlocked \= true, hiển thị Pop-up banner "Nổ thành tựu" ở góc màn hình (không làm gián đoạn game) kèm câu thoại hài hước.  
* **Trao thưởng tự động (UC15.3):** Ngay sau khi mở khóa, gọi hàm kiểm tra is\_reward\_claimed \== false để cộng trực tiếp tiền mặt, điểm kỹ năng (SP) hoặc gán danh hiệu mới vào hồ sơ nhân vật, sau đó đánh dấu is\_reward\_claimed \= true để chống nhận trùng lặp.  
* **Đồng bộ vật phẩm môi trường & Gallery (UC15.1, UC15.4):** Khi thành tựu hoặc kết cục được mở khóa, hệ thống tự động tải các cúp trưng bày ra đúng tọa độ trong phòng trọ/văn phòng, hoặc chuyển bức ảnh tương ứng trên *Memory Wall* từ trạng thái xám (Grayscale) sang ảnh màu kèm nội dung thư kỷ niệm.

  **c. Tín hiệu liên thông (Signals):**

* achievement\_unlocked(achievement\_id), reward\_claimed(achievement\_id), ending\_discovered(ending\_id).

  **d. Yêu cầu lưu trữ (Persistence):**

* **Đặc thù quan trọng:** Dữ liệu thành tựu và Gallery Ending bắt buộc phải được lưu trữ vĩnh viễn trong **Global Profile** (user://global\_profile.json). Các dữ liệu này được giữ nguyên ngay cả khi người chơi tạo lượt chơi mới (New Game).

**3\. Luồng dữ liệu và giao tiếp:**

#### **3.1. Sơ đồ Luồng Tín hiệu Trung tâm (SignalBus.gd)**

* Nhóm Tín hiệu Tài nguyên & Chỉ số:  
  * money\_changed(new\_amount) $\rightarrow$ Lắng nghe bởi UI hiển thị tiền (Top Bar HUD).  
  * sp\_changed(new\_sp) $\rightarrow$ Lắng nghe bởi giao diện Cây kỹ năng (UC13).  
  * stats\_changed(stat\_name, current\_val) $\rightarrow$ Lắng nghe bởi UI thanh thể lực/stress (UC04).  
* Nhóm Tín hiệu Tiến trình & Tương tác:  
  * skill\_unlocked(skill\_id) $\rightarrow$ Lắng nghe bởi hệ thống tính toán hiệu ứng nhân vật (UC13).  
  * achievement\_unlocked(achievement\_id) $\rightarrow$ Lắng nghe bởi AchievementManager để gọi Pop-up banner (UC15.2) và phần thưởng (UC15.3).  
  * item\_purchased(item\_id, count) $\rightarrow$ Lắng nghe bởi Inventory (UC09) và Shop (UC10).

  #### **3.2. Ví dụ về một Luồng xử lý khép kín (Event Sequence)**

  *Khi người chơi bấm nút nâng cấp kỹ năng (UC13.3):*

1. SkillUI gọi hàm GameManager.try\_upgrade\_skill(skill\_id).  
2. GameManager kiểm tra: if GameManager.skill\_points \>= skill.sp\_cost.  
3. Nếu đủ $\rightarrow$ Trừ điểm (GameManager.skill\_points \-= cost), tăng level kỹ năng trong Resource.  
1. GameManager phát tín hiệu SignalBus.sp\_changed.emit() và SignalBus.skill\_unlocked.emit().  
2. Các UI đang lắng nghe tự động cập nhật giao diện ngay lập tức mà không cần gọi hàm thủ công chéo giữa các màn hình.

   

**4\. Quy chuẩn lưu trữ:**  
*Quy định cấu trúc file lưu game (`.json` hoặc định dạng của Godot):*

#### **4.1. Phân tách Cấu trúc Lưu trữ**

* **A. Lưu trữ Trạng thái Lượt chơi (`Save State` – File: `user://save_game.json` hoặc `.tres`):**  
  * *Phạm vi:* Lưu toàn bộ tiến trình của lần chơi hiện tại. Khi người chơi chọn "Chơi mới" (New Game), file này sẽ bị ghi đè hoặc xóa sạch.  
  * *Nội dung:* Tiền mặt, vị trí hiện tại (`UC05`), danh sách nhân viên & cấp độ văn phòng (`UC12`), túi đồ (`UC09`), cấp độ các kỹ năng hiện tại (`UC13`), tiến trình các Quest đang làm (`UC07`).  
* **B. Lưu trữ Hồ sơ Toàn cục (`Global Profile` – File: `user://global_profile.json`):**  
  * *Phạm vi:* Lưu vĩnh viễn độc lập với file Save game. Ngay cả khi người chơi xóa file Save để chơi lại từ đầu, dữ liệu trong Global Profile vẫn được bảo toàn.  
  * *Nội dung:* Danh sách các thành tựu đã mở khóa (`is_unlocked = true` của `UC15`), danh sách các Ending đã đạt được trong bộ sưu tập Gallery (`UC15.4`), và các thiết lập cài đặt cấu hình game (`user://settings.cfg` của `UC02`).

  #### **4.2. Cơ chế Thực thi Save / Load**

* **Save Manager (`SaveManager.gd`):**  
  * Cung cấp hai hàm tĩnh chung: `save_game_state()` và `save_global_profile()`.  
  * Sử dụng lớp `FileAccess` và định dạng `JSON` của Godot để đóng gói các Dictionary dữ liệu thành chuỗi văn bản mã hóa an toàn trước khi ghi xuống ổ cứng.  
  * Tự động gọi lưu game định kỳ (Auto-save) khi kết thúc ngày trong vận hành hoặc khi hoàn thành các mốc quan trọng (như nhận thành tựu).


