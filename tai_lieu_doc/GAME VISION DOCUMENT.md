## Lời dẫn và nguyên tắc xây dựng tài liệu

Game Vision không đơn thuần là tài liệu mô tả một trò chơi. Đây là tài liệu xác định Start Again muốn trở thành game như thế nào, muốn mang lại trải nghiệm gì cho người chơi và cần dựa vào những nguyên tắc nào để đưa ra quyết định phát triển nhất quán.  
Tài liệu này được xây dựng nhằm trở thành điểm tham chiếu chung cho Game Designer, Programmer, Artist, UI/UX Designer, QA và Project Manager trong suốt quá trình phát triển dự án.  
Vì vậy, đây là bản Game Vision v0.1 có định hướng thiết kế và có thể dùng làm cơ sở thảo luận, không phải bản tổng hợp đã được đối chiếu đầy đủ với toàn bộ tài liệu gốc, cũng chưa phải tài liệu đã được nhóm phê duyệt.

## **1.1. Thông tin tài liệu**

| Thuộc tính | Nội dung |
| ----- | ----- |
| Tên tài liệu | Game Vision Document — Start Again |
| Phiên bản | 0.1 |
| Trạng thái | Draft — Đang xây dựng |
| Mục đích | Định hướng sản phẩm, trải nghiệm người chơi và quyết định thiết kế |
| Phạm vi | Tầm nhìn sản phẩm và nguyên tắc phát triển game |
| Đối tượng sử dụng | Game Designer, Programmer, Artist, UI/UX Designer, QA, Project Manager |
| Công nghệ | Godot — game 2D |
| Người phê duyệt | CẦN XÁC NHẬN |
| Ngày phê duyệt | Chưa có |
| Tài liệu đầu vào | Các tài liệu dự án được liệt kê trong mục kiểm kê |

## **1.2. Game Vision khác gì với các tài liệu khác?**

### **Game Vision — WHY & WHAT FOR**

Trả lời: Game được phát triển vì điều gì? Trải nghiệm cốt lõi là gì? Điều gì cần được giữ vững?

### **Game Core — WHAT & HOW IT FEELS**

Xác định trải nghiệm cốt lõi, các vòng lặp gameplay và những hoạt động chính mà người chơi thực hiện.

### **Game Design Document (GDD) — HOW**

Đặc tả cơ chế, luật chơi, thông số, hệ thống, tương tác và hành vi gameplay.

### **Story Bible — WHAT HAPPENS**

Quản lý cốt truyện, nhân vật, thế giới, sự kiện, quan hệ và tính nhất quán của nội dung kể chuyện.

### **Art Vision — HOW IT LOOKS & SOUNDS**

Xác định ngôn ngữ thị giác, màu sắc, hình khối, phong cách nhân vật, môi trường, UI và định hướng âm thanh.

### **Technical Design Document — HOW IT IS BUILT**

Đặc tả kiến trúc, cấu trúc scene, hệ thống script, dữ liệu, giao tiếp giữa các thành phần và giải pháp kỹ thuật.

### **Roadmap — WHEN & IN WHAT ORDER**

Xác định thứ tự thực hiện, các mốc phát triển, phụ thuộc, nguồn lực và tiêu chí hoàn thành.  
Nguyên tắc: Game Vision không thay thế các tài liệu trên. Nó cung cấp tiêu chuẩn để đánh giá liệu các tài liệu và quyết định bên dưới có cùng hướng tới một sản phẩm nhất quán hay không.

## **2.1. Vision Statement**

# **“Start Again — mỗi khởi đầu mở ra một hành trình, mỗi lựa chọn tạo nên câu chuyện của riêng bạn.”**

Câu Vision trên được đề xuất vì kết nối ba ý tưởng có khả năng phù hợp với định hướng dự án:

* Start Again: gợi mở chủ đề về sự khởi đầu, nhưng ý nghĩa chính thức của tên game vẫn cần xác nhận.  
* Hành trình: tạo không gian cho khám phá và progression.  
* Lựa chọn: gợi mở sự tham gia chủ động của người chơi và khả năng tạo ra những kết quả khác nhau.

Nếu cốt truyện chính thức không xoay quanh sự khởi đầu mới hoặc nếu lựa chọn không phải yếu tố trọng tâm của gameplay, câu này cần được điều chỉnh thay vì ép nội dung dự án phải phù hợp với khẩu hiệu.

## **2.2. Tầm nhìn sản phẩm**

Start Again hướng tới một trò chơi 2.5D mang màu sắc Fantasy, trong đó gameplay, thế giới và quá trình phát triển nhân vật được thiết kế để hỗ trợ một trải nghiệm có tiến triển rõ ràng và mang lại cảm giác người chơi đang chủ động tham gia vào hành trình của mình.  
Thay vì chỉ cung cấp một chuỗi nhiệm vụ cần hoàn thành, trò chơi nên tạo mối liên hệ dễ hiểu giữa hành động của người chơi, kết quả nhận được và những khả năng mới được mở ra. Nếu lựa chọn là một phần cốt lõi của thiết kế, các lựa chọn cần thể hiện được giá trị thông qua phản hồi hoặc hệ quả phù hợp với quy mô sản xuất.  
Tầm nhìn này chỉ trở thành định hướng chính thức khi được đối chiếu với cốt truyện, Game Core và phạm vi tính năng đã thống nhất.

## **2.3. Experience Promise — Lời hứa trải nghiệm**

ĐỀ XUẤT ba lời hứa:

1. Dễ hiểu để bắt đầu: người chơi hiểu mình đang làm gì, vì sao hành động đó có ý nghĩa và có thể tiếp tục như thế nào.  
2. Có tiến triển để theo đuổi: hoạt động chơi tạo ra kết quả có thể nhận biết, dù là phát triển nhân vật, mở rộng khả năng hay tiến triển nội dung.  
3. Có ý nghĩa trong hành động: các hệ thống quan trọng không tồn tại độc lập mà hỗ trợ cùng một trải nghiệm.

Đây không phải cam kết rằng game sẽ có nhiều nhánh kết thúc, thế giới mở hay hệ thống lựa chọn phức tạp. Các hình thức thể hiện cụ thể phụ thuộc vào tài liệu đã được xác nhận.

## **2.4. Giá trị người chơi nhận được**

| Giá trị | Biểu hiện mong muốn | Cách kiểm chứng |
| ----- | ----- | ----- |
| Dễ tiếp cận | Hiểu cách chơi và mục tiêu gần nhất | Playtest người mới |
| Cảm giác làm chủ | Hiểu mối quan hệ giữa hành động và kết quả | Quan sát hành vi, phỏng vấn |
| Tiến triển | Nhận ra sự thay đổi sau khi chơi | Kiểm thử các mốc progression |
| Gắn kết | Muốn tiếp tục hành trình | Phỏng vấn sau phiên chơi |
| Nhất quán | Nhận thấy gameplay và thế giới hỗ trợ cùng một trải nghiệm | Playtest và đánh giá thiết kế |

## **3.1. Khái niệm tổng thể**

Start Again là dự án game 2D sử dụng Godot, được định hướng phát triển từ các yếu tố Fantasy, RPG, Life Simulation, Choice-driven Gameplay và Progression. Tầm nhìn sản phẩm cần làm rõ cách kết hợp những yếu tố này thành một trải nghiệm thống nhất, thay vì chỉ tập hợp nhiều thể loại và hệ thống trong cùng một trò chơi.  
Điểm cần quyết định không phải là game có bao nhiêu tính năng, mà là: người chơi dành phần lớn thời gian để làm gì, điều gì khiến họ muốn tiếp tục và những hệ thống nào thực sự cần thiết để hỗ trợ hành vi đó.

## **3.2. Elevator Pitch**

Start Again là một trò chơi 2D mang định hướng Fantasy, kết hợp các yếu tố nhập vai, phát triển nhân vật và mô phỏng đời sống. Trò chơi hướng tới việc tạo ra một hành trình có tiến triển rõ ràng, nơi hoạt động gameplay, khám phá thế giới và những lựa chọn của người chơi cùng góp phần hình thành trải nghiệm.

## **3.3. Định hướng thể loại**

| Yếu tố | Vai trò tiềm năng | Trạng thái |
| ----- | ----- | ----- |
| Fantasy | Xây dựng bối cảnh, không khí và các khả năng của thế giới | Đã có trong định hướng; vai trò cụ thể cần xác nhận |
| RPG | Hỗ trợ phát triển nhân vật, năng lực và tiến trình | Đã có trong định hướng; hệ thống thực tế cần xác nhận |
| Life Simulation | Tạo hoạt động đời sống và sự gắn kết với thế giới nếu được triển khai | Cần xác nhận phạm vi |
| Choice-driven Gameplay | Kết nối quyết định của người chơi với kết quả | Cần xác nhận mức độ quan trọng |
| Progression | Tạo cảm giác tiến bộ qua thời gian chơi | Đã có trong định hướng; cấu trúc cần xác nhận |

### **3.4. Bản sắc cốt lõi và yếu tố bổ trợ**

Khi phân loại các hệ thống, nhóm nên dùng ba câu hỏi:

* Nếu bỏ hệ thống này, trải nghiệm đặc trưng của Start Again có mất đi không?  
* Hệ thống này có trực tiếp hỗ trợ core loop hay chỉ tạo thêm nội dung?  
* Chi phí xây dựng, kiểm thử và bảo trì có tương xứng với giá trị mang lại không?

Một hệ thống không trở thành yếu tố cốt lõi chỉ vì nó thuộc một thể loại được nhắc đến trong phần giới thiệu game.  
Ví dụ, một hệ thống nghề nghiệp chỉ nên được xem là trọng tâm nếu nó thực sự ảnh hưởng đáng kể đến hành động, mục tiêu hoặc tiến trình của người chơi. Đây là nguyên tắc đánh giá, không phải xác nhận rằng Start Again đã có hệ thống nghề nghiệp.

## **3.5. Vai trò của người chơi và tiền đề cốt truyện**

| Câu hỏi | Trạng thái |
| ----- | ----- |
| Người chơi nhập vai ai? | CẦN XÁC NHẬN |
| Nhân vật bắt đầu hành trình trong hoàn cảnh nào? | CẦN XÁC NHẬN |
| Mục tiêu chính của nhân vật là gì? | CẦN XÁC NHẬN |
| Thế giới có quy tắc hoặc xung đột đặc biệt nào? | CẦN XÁC NHẬN |
| Lựa chọn tác động đến câu chuyện ở mức nào? | CẦN XÁC NHẬN |
| Điều gì làm Start Again khác biệt so với các game cùng định hướng? | CẦN KIỂM CHỨNG |

Các câu hỏi này cần được giải quyết bằng tài liệu cốt truyện và Game Core hiện có, không nên trả lời bằng cách sáng tác thêm nội dung mới.

## **4.1. Nhóm người chơi mục tiêu**

Dựa vào khảo sát thị trường (khoảng 47 người), chủ yếu ở độ tuổi 18-22 và tần suất chơi game 3-4 lần / tuần

### **Nhóm chính tiềm năng**

Người chơi thích khám phá một thế giới Fantasy, phát triển nhân vật theo thời gian và trải nghiệm những hoạt động có mục tiêu rõ ràng.  
Động lực tiềm năng:

* Muốn thấy nhân vật trở nên mạnh hơn hoặc có nhiều khả năng hơn.  
* Thích khám phá môi trường và tìm hiểu các hệ thống.  
* Muốn nhận được phản hồi rõ ràng từ hành động của mình.  
* Thích nhịp chơi có thể cân bằng giữa hoạt động chính và các hoạt động bổ trợ.

### **Nhóm phụ tiềm năng**

Người chơi yêu thích mô phỏng đời sống, tiến trình dài hạn hoặc những trò chơi có quyết định ảnh hưởng đến trải nghiệm.  
Nhóm này chỉ thực sự phù hợp nếu các yếu tố mô phỏng, lựa chọn và hậu quả được triển khai đủ rõ trong phiên bản thực tế.

## **4.2. Động lực và yếu tố duy trì người chơi**

| Động lực giả thuyết | Yếu tố hỗ trợ | Nguy cơ mất hứng thú |
| ----- | ----- | ----- |
| Muốn tiến bộ | Cột mốc và phản hồi tiến triển dễ nhận biết | Tiến triển không tạo ra thay đổi đáng kể |
| Muốn khám phá | Thông tin hoặc nội dung mới có giá trị | Khám phá chỉ mang tính lặp lại |
| Muốn tự quyết | Lựa chọn có hệ quả dễ hiểu | Lựa chọn chỉ thay đổi câu chữ |
| Muốn thư giãn | Nhịp chơi và giao diện dễ tiếp cận | Quá nhiều thao tác hoặc áp lực không cần thiết |
| Muốn hiểu thế giới | Nội dung nhất quán, có liên kết | Câu chuyện và gameplay rời rạc |

Không phải mọi động lực trên đều cần được đáp ứng ở cùng mức độ. Nhóm cần chọn một nhóm người chơi ưu tiên để tập trung nguồn lực.

## **4.3. Nhóm không phải trọng tâm của phiên bản đầu**

ĐỀ XUẤT: Nếu nguồn lực còn hạn chế, không nên tối ưu ngay cho các nhu cầu đòi hỏi quy mô sản xuất lớn như:

* Thế giới có hàng trăm hoạt động và NPC với hành vi độc lập.  
* Nhiều tuyến cốt truyện phân nhánh sâu, tạo ra khối lượng nội dung lớn.  
* Hệ thống mô phỏng nhiều biến số tương tác phức tạp.  
* Các cơ chế multiplayer hoặc hệ thống vận hành trực tuyến, nếu không thuộc mục tiêu đã chốt.

Đây không phải tuyên bố loại bỏ vĩnh viễn các khả năng trên. Chúng chỉ nên được cân nhắc khi có lý do sản phẩm rõ ràng và nguồn lực phù hợp.

## **4.4. Cách xác nhận nhóm người chơi**

Nên tiến hành theo ba bước:

1. Viết mô tả ngắn về nhóm người chơi giả định.  
2. Cho người chơi phù hợp thử prototype thể hiện core loop.  
3. Quan sát hành vi, hỏi về điều họ hiểu, điều họ thích và lý do họ muốn hoặc không muốn tiếp tục.

Không cần khẳng định nhóm người chơi bằng số liệu thị trường khi chưa có nghiên cứu. Hãy xây dựng mức cơ sở từ những phiên thử nghiệm đầu tiên.

Phần này mô tả hành trình trải nghiệm mong muốn ở mức định hướng. Nó không thay thế sơ đồ gameplay thực tế của Game Core.

| Giai đoạn | Mục tiêu của người chơi | Trải nghiệm mong muốn | Cách kiểm chứng |
| ----- | ----- | ----- | ----- |
| 1\. Lần đầu tiếp xúc | Hiểu game và lý do bắt đầu | Tò mò, dễ tiếp cận | Hỏi người chơi mô tả game sau phần mở đầu |
| 2\. Làm quen | Hiểu mục tiêu và thao tác cơ bản | Không bị quá tải | Quan sát số lần cần trợ giúp |
| 3\. Làm chủ | Hiểu mối liên hệ giữa hành động và kết quả | Chủ động, có năng lực | Cho người chơi tự hoàn thành một mục tiêu |
| 4\. Phát triển | Nhận ra tiến triển | Có động lực tiếp tục | Kiểm tra người chơi có nhận ra thay đổi |
| 5\. Đưa ra lựa chọn | Hiểu các phương án | Cảm thấy quyết định có ý nghĩa | Hỏi lý do chọn phương án |
| 6\. Nhận kết quả | Nhận biết tác động từ hành động | Thấy được mối liên hệ nguyên nhân – kết quả | Kiểm tra khả năng giải thích kết quả |
| 7\. Tiếp tục hành trình | Có mục tiêu tiếp theo | Muốn khám phá hoặc đạt mốc mới | Hỏi người chơi muốn làm gì tiếp theo |

Lưu ý: Giai đoạn lựa chọn và hậu quả chỉ áp dụng ở mức tương ứng với cơ chế đã được xác nhận. Không nên tạo nhiều nhánh nội dung chỉ để đáp ứng bảng này.

## **Tiêu chuẩn cho trải nghiệm tốt**

Một phiên chơi thử nên giúp nhóm trả lời:

* Người chơi có hiểu mục tiêu trước mắt không?  
* Người chơi có biết hành động tiếp theo là gì không?  
* Phản hồi của game có giúp họ hiểu điều vừa xảy ra không?  
* Người chơi có nhận ra tiến triển sau khi hoàn thành mục tiêu không?  
* Người chơi có thể giải thích tại sao họ chọn một phương án không?  
* Người chơi có biết mình muốn làm gì tiếp theo không?

Nếu người chơi không hiểu mục tiêu, không nhận ra tiến triển hoặc không thể giải thích các lựa chọn quan trọng, nhóm cần kiểm tra lại thiết kế trước khi mở rộng nội dung.

Design Pillars là các nguyên tắc cốt lõi dùng để đánh giá quyết định thiết kế. Một pillar tốt phải đủ cụ thể để trả lời câu hỏi: Trong hai phương án đều có vẻ hợp lý, phương án nào phù hợp với Start Again hơn?

## **Pillar 1 — Progress With Purpose: Tiến triển có ý nghĩa**

Định nghĩa: Các hoạt động quan trọng cần đóng góp vào tiến trình mà người chơi có thể nhận biết, hiểu và cảm nhận được.

* Lời hứa: Thời gian người chơi bỏ ra giúp họ đạt được điều gì đó có ý nghĩa.  
* Biểu hiện: Mục tiêu, phản hồi, cột mốc hoặc khả năng mới được thể hiện rõ.  
* Quyết định phù hợp: Xây dựng một mốc tiến triển nhỏ nhưng có tác động rõ ràng đến trải nghiệm.  
* Quyết định không phù hợp: Thêm một chỉ số hoặc cấp độ chỉ để tạo cảm giác game có nhiều hệ thống.  
* Kiểm chứng: Người chơi có thể giải thích họ đã tiến bộ ở điểm nào và điều đó giúp ích gì.

## **Pillar 2 — Agency Matters: Hành động và lựa chọn có giá trị**

Định nghĩa: Người chơi cần hiểu các hành động hoặc quyết định quan trọng có thể dẫn đến kết quả nào.

* Lời hứa: Người chơi cảm nhận được vai trò chủ động trong trải nghiệm.  
* Biểu hiện: Phản hồi dễ hiểu; các lựa chọn quan trọng có khác biệt thực tế tương xứng.  
* Quyết định phù hợp: Cho phép người chơi lựa chọn giữa những phương án có ưu điểm, hạn chế hoặc kết quả khác nhau.  
* Quyết định không phù hợp: Tạo lựa chọn trông có vẻ quan trọng nhưng không mang lại khác biệt đáng kể.  
* Kiểm chứng: Người chơi có thể nêu lý do lựa chọn và mô tả kết quả mà họ nhận thấy.

Pillar này không bắt buộc mọi lựa chọn phải phân nhánh cốt truyện. Một lựa chọn có thể có ý nghĩa thông qua cách tiếp cận, tài nguyên, tiến trình hoặc các kết quả khác nếu những cơ chế đó thuộc thiết kế thực tế.

## **Pillar 3 — A Coherent World: Thế giới nhất quán**

Định nghĩa: Môi trường, nhân vật, hoạt động và phản hồi của game cần tạo cảm giác thuộc về cùng một thế giới.

* Lời hứa: Người chơi có thể hiểu và tin vào những quy tắc cơ bản của thế giới.  
* Biểu hiện: Hành vi, nội dung, hình ảnh và âm thanh hỗ trợ cùng một bối cảnh.  
* Quyết định phù hợp: Tạo một khu vực nhỏ nhưng có bản sắc và tương tác nhất quán.  
* Quyết định không phù hợp: Thêm nội dung không phục vụ trải nghiệm chỉ vì muốn thế giới trông rộng hơn.  
* Kiểm chứng: Người chơi có thể mô tả đặc điểm của khu vực và hiểu các tương tác chính.

## **Pillar 4 — Systems Work Together: Các hệ thống hỗ trợ lẫn nhau**

Định nghĩa: Những hệ thống được giữ lại cần có quan hệ rõ ràng với trải nghiệm cốt lõi, thay vì hoạt động như các tính năng tách rời.

* Lời hứa: Các hoạt động trong game bổ trợ cho nhau.  
* Biểu hiện: Gameplay, progression, nội dung và giao diện có mối liên hệ dễ hiểu.  
* Quyết định phù hợp: Ưu tiên một cơ chế có thể phục vụ nhiều mục tiêu thiết kế mà không làm hệ thống phức tạp quá mức.  
* Quyết định không phù hợp: Thêm một hệ thống lớn chỉ vì nó phổ biến trong các game cùng thể loại.  
* Kiểm chứng: Nhóm có thể giải thích mỗi hệ thống đóng góp gì cho core loop và giá trị của người chơi.

## **Pillar 5 — Small Scope, Finished Experience: Phạm vi nhỏ, trải nghiệm hoàn chỉnh**

Định nghĩa: Ưu tiên hoàn thiện một trải nghiệm có thể chơi được, thay vì mở rộng nhiều tính năng nhưng không thể tích hợp thành sản phẩm hoàn chỉnh.

* Lời hứa: Người chơi được trải nghiệm một vòng gameplay hoàn chỉnh, không chỉ những tính năng rời rạc.  
* Biểu hiện: Các thành phần cần thiết được tích hợp, kiểm thử và có thể hoàn thành.  
* Quyết định phù hợp: Hoàn thiện một lát cắt gameplay đại diện trước khi xây thêm nội dung.  
* Quyết định không phù hợp: Mở rộng bản đồ hoặc hệ thống trong khi các luồng chơi cơ bản chưa hoạt động ổn định.  
* Kiểm chứng: Nhóm có thể bàn giao một bản build chạy được và hoàn thành mục tiêu thử nghiệm.

## **Thứ tự ưu tiên khi các pillar xung đột**

Đối với phiên bản đầu, có thể dùng thứ tự tạm thời sau:

1. Khả năng hoàn thành trải nghiệm trong nguồn lực hiện có.  
2. Tiến triển có ý nghĩa và gameplay dễ hiểu.  
3. Hành động, lựa chọn có giá trị.  
4. Tính nhất quán của thế giới và nội dung.  
5. Mức độ phong phú của hệ thống và nội dung bổ trợ.

Đây là thứ tự gợi ý cho các quyết định liên quan đến MVP, không phải khẳng định rằng giá trị nghệ thuật hoặc cốt truyện kém quan trọng hơn trong toàn bộ tầm nhìn dài hạn.

## **7.1. Mục tiêu**

Gameplay Vision xác định cách trải nghiệm chơi thực hiện lời hứa của sản phẩm. Nó không phải nơi tự tạo một core loop mới khi Game Core chưa được đối chiếu.  
Với thông tin hiện tại, chưa thể khẳng định vòng lặp chính xác của Start Again. Do đó, phần này xác lập các tiêu chuẩn mà core loop hiện có cần đáp ứng.

## **7.2. Đánh giá các cấp độ gameplay loop**

| Cấp độ | Cần xác định | Trạng thái |
| ----- | ----- | ----- |
| Moment-to-moment | Hành động người chơi lặp lại thường xuyên nhất | Cần Game Core |
| Short-term loop | Mục tiêu gần và kết quả trong một phiên chơi | Cần Game Core |
| Mid-term loop | Cách các hoạt động tạo ra tiến triển lớn hơn | Cần Game Core |
| Long-term loop | Mục tiêu dài hạn, các cột mốc và cách duy trì động lực | Cần Game Core |

Các vòng lặp không nhất thiết phải tồn tại dưới dạng bốn hệ thống độc lập. Chúng là các cấp độ phân tích khác nhau của cùng một trải nghiệm.

## **7.3. Nguyên tắc gameplay**

1. Người chơi phải hiểu hành động đang phục vụ mục tiêu nào.  
2. Hệ thống phải phản hồi đủ rõ để người chơi hiểu kết quả.  
3. Các cơ chế phát triển cần tạo ra thay đổi có ý nghĩa đối với hành vi hoặc lựa chọn.  
4. Hoạt động bổ trợ cần hỗ trợ trải nghiệm cốt lõi, không mặc nhiên được giữ lại chỉ vì phù hợp với thể loại.  
5. Độ phức tạp chỉ nên tăng khi người chơi đã có đủ kiến thức để hiểu và sử dụng các cơ chế mới.  
6. Mỗi hệ thống mới cần được đánh giá cùng chi phí tích hợp, cân bằng, kiểm thử và bảo trì.

## **7.4. Mối quan hệ giữa gameplay và các hệ thống**

Mục tiêu của người chơi \-\> Hành động / tương tác \-\> Kết quả và phản hồi \-\> Tiến triển hoặc thay đổi trạng thái \-\> Mục tiêu tiếp theo

## **7.5. Các vấn đề cần đối chiếu với Game Core**

- [ ] Hành động chính của người chơi đã được xác định rõ.  
- [ ] Core loop đã có điểm bắt đầu, hành động, phản hồi và điều kiện tiếp tục.  
- [ ] Có mục tiêu ngắn hạn và cách đánh giá hoàn thành.  
- [ ] Progression gắn với gameplay thực tế.  
- [ ] Các lựa chọn quan trọng có quy tắc và hệ quả xác định.  
- [ ] Các hệ thống phụ không tạo ra vòng lặp tách rời thiếu mục đích.  
- [ ] Phạm vi của core loop phù hợp với khả năng hiện tại của nhóm.  
- [ ] Có thể xây dựng một prototype để kiểm tra giả thuyết chính.

## **8.1. Vai trò của cốt truyện**

Cốt truyện nên hỗ trợ trải nghiệm gameplay và giúp người chơi hiểu bối cảnh, mục tiêu hoặc ý nghĩa của các hoạt động chính. Tuy nhiên, mức độ ưu tiên giữa kể chuyện và gameplay phải được xác định dựa trên ý đồ thực tế của dự án.  
Narrative Vision không yêu cầu game phải có cốt truyện tuyến tính, phân nhánh sâu hay nhiều kết thúc. Nó yêu cầu những nội dung được triển khai phải có vai trò rõ ràng.

## **8.2. Nguyên tắc kể chuyện**

| Thành phần | Nguyên tắc định hướng | Điều cần xác nhận |
| ----- | ----- | ----- |
| Nhân vật chính | Mục tiêu và hành động cần có lý do trong bối cảnh | Danh tính, động lực và hành trình chính thức |
| NPC | Vai trò tương xứng với chức năng trong gameplay hoặc câu chuyện | Danh sách và chức năng NPC |
| Thế giới | Quy tắc và bối cảnh nhất quán | Worldbuilding đã chốt |
| Hội thoại | Cung cấp thông tin, thể hiện nhân vật hoặc hỗ trợ quyết định | Vai trò và cấu trúc hội thoại |
| Lựa chọn | Chỉ rõ sự khác biệt ở mức cần thiết | Cơ chế và phạm vi hậu quả |
| Tiến trình cốt truyện | Liên kết với trạng thái game khi phù hợp | Mốc truyện và điều kiện mở khóa |

## **8.3. Kết nối Narrative và Gameplay**

Một nội dung kể chuyện nên được đánh giá qua ba câu hỏi:

1. Nội dung này cung cấp thông tin hoặc giá trị gì cho người chơi?  
2. Nó có liên hệ với hành động, mục tiêu hay trạng thái gameplay không?  
3. Chi phí sản xuất và kiểm thử có tương xứng với giá trị mang lại không?

Không phải mọi câu chuyện đều cần gắn với cơ chế gameplay. Một đoạn hội thoại có thể tồn tại để xây dựng cảm xúc hoặc bối cảnh. Tuy nhiên, nếu mục tiêu là làm cho người chơi cảm nhận thế giới có phản hồi, những nội dung được quảng bá là có ảnh hưởng cần thể hiện tác động tương ứng.

## **8.4. Quy tắc bảo vệ canon**

* Không tự ý thêm nhân vật, sự kiện, địa điểm, tổ chức hoặc kết thúc.  
* Không thay đổi động lực nhân vật để giải thích cho một tính năng mới.  
* Không thêm nhánh truyện nếu chưa đánh giá chi phí nội dung và kiểm thử.  
* Nếu gameplay yêu cầu thay đổi canon, ghi nhận thành một đề xuất cần người có thẩm quyền phê duyệt.  
* Phân biệt nội dung chính thức, nội dung thử nghiệm và nội dung chưa được xác nhận.

## **9.1. Mục tiêu**

Tạo cảm giác thế giới có quy luật, có bản sắc và có đủ tương tác để hỗ trợ hoạt động chơi chính.  
Sự nhập vai không chỉ đến từ số lượng bản đồ, NPC hay hiệu ứng. Nó còn đến từ cách thế giới phản hồi, sự nhất quán giữa các thành phần và khả năng giúp người chơi hiểu mình đang ở đâu, làm gì và tại sao.

## **9.2. Nguyên tắc xây dựng thế giới**

| Thành phần | Định hướng | Ưu tiên ban đầu |
| ----- | ----- | ----- |
| Môi trường | Dễ nhận diện và hỗ trợ mục tiêu gameplay | Một khu vực đại diện được hoàn thiện tốt |
| NPC | Có vai trò và hành vi rõ ràng | Ít NPC nhưng phục vụ trải nghiệm |
| Tương tác | Phản hồi rõ, tránh tạo kỳ vọng sai | Hoàn thiện các tương tác bắt buộc |
| Âm thanh | Hỗ trợ không khí và thông tin gameplay | Những âm thanh cần thiết cho bản chơi thử |
| Âm nhạc | Hỗ trợ cảm xúc và tính nhất quán | Một số đoạn phù hợp với phạm vi MVP |
| Hiệu ứng | Giúp hành động và kết quả dễ nhận biết | Ưu tiên phản hồi gameplay trước trang trí |
| Chi tiết thế giới | Bổ sung chiều sâu khi có giá trị | Chỉ mở rộng sau khi luồng chơi chính ổn định |

Các ưu tiên trên là đề xuất về quy mô sản xuất. Chúng không xác nhận rằng game đã có bản đồ, NPC hoặc hệ thống âm thanh cụ thể nào.

## **9.3. Phân biệt World Vision và Art Vision**

World & Immersion Vision tập trung vào câu hỏi: người chơi cảm nhận thế giới như thế nào?  
Art Vision sẽ trả lời các câu hỏi khác:

* Sử dụng ngôn ngữ hình khối nào?  
* Bảng màu, ánh sáng và độ tương phản ra sao?  
* Nhân vật và môi trường có tỷ lệ thế nào?  
* Phong cách pixel art, hand-drawn hay một phương pháp khác?  
* UI, animation và hiệu ứng cần tuân theo quy chuẩn gì?

Các quyết định cụ thể về phong cách nghệ thuật cần chờ tài liệu Art Vision hoặc quyết định chính thức của nhóm.

## **10.1. Điểm khác biệt hiện có và giả thuyết**

| Nội dung | Trạng thái | Nhận định |
| ----- | ----- | ----- |
| Kết hợp định hướng Fantasy, RPG, Life Simulation, Choice-driven Gameplay và Progression | ĐÃ XÁC NHẬN là định hướng đã được sử dụng | Chưa đủ để chứng minh khác biệt trên thị trường |
| Tên Start Again gợi liên tưởng đến một khởi đầu mới | SUY LUẬN | Chỉ là liên tưởng ngôn ngữ, không phải bằng chứng về cốt truyện |
| Lựa chọn và tiến triển có thể là trọng tâm trải nghiệm | SUY LUẬN | Cần đối chiếu Game Core |
| Thế giới và gameplay có sự kết nối chặt chẽ | ĐỀ XUẤT | Là mục tiêu thiết kế, chưa phải lợi thế đã chứng minh |
| Start Again có điểm độc đáo so với game tương tự | CẦN KIỂM CHỨNG | Chưa có phân tích cạnh tranh và playtest |

## **10.2. Hướng định vị để xem xét**

ĐỀ XUẤT: Thay vì định vị game chỉ bằng một danh sách thể loại, nhóm nên diễn đạt sản phẩm thông qua tổ hợp:

* Người chơi làm gì thường xuyên nhất?  
* Điều gì khiến hành động đó thú vị hoặc có ý nghĩa?  
* Trải nghiệm này khác gì so với những lựa chọn thay thế?  
* Game thực hiện lời hứa đó bằng những hệ thống nào?

Một hướng định vị chỉ nên được giữ lại khi có thể chứng minh bằng gameplay, nội dung thực tế và phản hồi của người chơi.

## **10.3. Kế hoạch kiểm chứng khác biệt**

1. Chọn một nhóm nhỏ game có cấu trúc hoặc trải nghiệm tương đồng.  
2. So sánh core loop, progression, lựa chọn, nhịp chơi và cách trình bày.  
3. Xác định điểm tương đồng, khoảng trống và giả thuyết khác biệt.  
4. Xây dựng prototype thể hiện rõ nhất giả thuyết đó.  
5. Cho người chơi thử mà không giải thích trước điều nhóm muốn họ nhận ra.  
6. Kiểm tra xem họ có tự mô tả được điểm đặc trưng đó không.

Không sử dụng các tuyên bố như “độc nhất”, “đột phá” hoặc “vượt trội” khi chưa có bằng chứng đủ mạnh.

## **11.1. Phân biệt tầm nhìn dài hạn và MVP**

Tầm nhìn sản phẩm mô tả trải nghiệm mà Start Again muốn hướng tới. MVP là phiên bản nhỏ nhất có thể kiểm chứng một cách có ý nghĩa liệu hướng thiết kế đó có hoạt động hay không.  
MVP không đồng nghĩa với một bản game có thật ít tính năng. Một MVP tốt phải có đủ các thành phần để người chơi trải nghiệm được một luồng gameplay có đầu vào, hành động, kết quả và mục tiêu tiếp theo.

## **11.2. Ma trận ưu tiên**

| Mức ưu tiên | Tiêu chí | Ví dụ ở mức định hướng |
| ----- | ----- | ----- |
| MUST HAVE | Không có thì không thể kiểm chứng trải nghiệm cốt lõi | Luồng chơi chính, các tương tác bắt buộc, phản hồi, điều kiện hoàn thành |
| SHOULD HAVE | Tăng đáng kể độ rõ ràng hoặc chất lượng trải nghiệm | Hướng dẫn, UI hỗ trợ, nội dung đại diện cho một pillar |
| COULD HAVE | Có giá trị nhưng có thể trì hoãn | Nội dung phụ, hiệu ứng bổ sung, các biến thể không thiết yếu |
| OUT OF SCOPE | Không phục vụ mục tiêu MVP hoặc vượt nguồn lực hiện tại | Hệ thống quy mô lớn chưa có căn cứ về giá trị và khả năng thực hiện |

Những ví dụ này mô tả cách áp dụng phương pháp MoSCoW, không xác nhận các hệ thống tương ứng đang tồn tại trong Start Again.

## **11.3. Đề xuất phạm vi MVP theo lớp năng lực**

**MUST HAVE \-** Một luồng chơi hoàn chỉnh  
Một người chơi có thể bắt đầu, thực hiện hoạt động chính, nhận phản hồi và hoàn thành mục tiêu thử nghiệm.

**SHOULD HAVE \-** Đủ thông tin để hiểu trải nghiệm  
Giao diện, hướng dẫn, phản hồi và nội dung giúp người chơi hiểu mục tiêu, thao tác và kết quả.

**COULD HAVE \-** Chiều sâu bổ sung  
Những nội dung nâng cao chỉ được thêm sau khi luồng chơi chính hoạt động ổn định.

**OUT OF SCOPE \-** Mở rộng chưa có căn cứ  
Các hệ thống lớn không cần thiết để kiểm chứng giả thuyết sản phẩm hoặc chưa có người phụ trách đủ năng lực.

## **11.4. Cách đánh giá từng tính năng**

Mỗi tính năng cần có ít nhất các thông tin sau:

| Trường thông tin | Câu hỏi cần trả lời |
| ----- | ----- |
| Mục đích | Tính năng giải quyết vấn đề gì? |
| Giá trị Vision | Pillar nào được hỗ trợ? |
| Phụ thuộc | Cần hệ thống hoặc nội dung nào trước? |
| Chi phí | Mất bao nhiêu thời gian thiết kế, lập trình, nghệ thuật và kiểm thử? |
| Rủi ro | Điều gì có thể khiến tính năng thất bại? |
| Mức ưu tiên | Có thực sự cần cho MVP không? |
| Tiêu chí hoàn thành | Bằng chứng nào cho thấy tính năng hoạt động đúng? |
| Trạng thái | Đã thống nhất, đề xuất hay cần xác nhận? |

## **11.5. Nguyên tắc chống phình phạm vi**

* Không thêm tính năng chỉ vì một game cùng thể loại có tính năng đó.  
* Không xây dựng hệ thống trước khi xác định được giá trị người chơi nhận được.  
* Không bắt đầu nhiều hệ thống phụ khi các hệ thống nền tảng chưa ổn định.  
* Không mở rộng nội dung khi chưa có cách tái sử dụng hoặc quản lý nội dung hợp lý.  
* Không coi tính năng chạy được là tính năng đã hoàn thành.  
* Mọi thay đổi làm ảnh hưởng đến core loop, nguồn lực hoặc mốc bàn giao phải được đánh giá lại.

## **12.1. Nguyên tắc đo lường**

Vision chỉ có giá trị khi có thể chuyển thành những giả thuyết kiểm chứng được.  
Trong giai đoạn chưa có dữ liệu thử nghiệm, không nên đặt KPI tùy ý. Nhóm cần xây dựng mức cơ sở, sau đó đặt ngưỡng chấp nhận dựa trên mục tiêu sản phẩm và kết quả thực tế.

## **12.2. Bộ tiêu chí thành công đề xuất**

| Tiêu chí | Phương pháp đo | Thời điểm |
| ----- | ----- | ----- |
| Hiểu mục tiêu | Yêu cầu người chơi mô tả mục tiêu hiện tại | Sau phần hướng dẫn |
| Hiểu core loop | Quan sát người chơi tự thực hiện một vòng gameplay | Trong prototype |
| Hiểu phản hồi | Hỏi người chơi giải thích kết quả của một hành động | Sau tương tác quan trọng |
| Nhận ra tiến triển | So sánh nhận thức trước và sau khi đạt một mốc | Sau một vòng chơi |
| Nhận thấy giá trị lựa chọn | Hỏi lý do lựa chọn và nhận thức về hệ quả | Sau tình huống có lựa chọn |
| Nhận diện bản sắc | Hỏi người chơi mô tả điểm đáng nhớ của game | Cuối phiên chơi |
| Khả năng hoàn thành | Kiểm tra build, lỗi và luồng chơi từ đầu đến cuối | Mỗi mốc tích hợp |
| Khả năng sản xuất | Theo dõi thời gian thực hiện, lỗi tồn đọng và công việc bị chặn | Hằng tuần hoặc mỗi sprint |

Không phải mọi tiêu chí đều áp dụng ngay từ prototype đầu tiên. Chỉ đo những điều bản build hiện tại đủ khả năng kiểm chứng.

## **12.3. Quy trình xác lập KPI**

1. Xác định giả thuyết cần kiểm chứng.  
2. Xác định hành vi hoặc kết quả quan sát được.  
3. Thu thập dữ liệu từ các phiên playtest ban đầu.  
4. Ghi nhận mức cơ sở và các vấn đề lặp lại.  
5. Thống nhất ngưỡng chấp nhận cho giai đoạn tiếp theo.  
6. Thực hiện thử nghiệm lại sau khi thay đổi thiết kế.

Ví dụ, thay vì đặt mục tiêu tùy ý rằng mọi người chơi phải hiểu core loop trong một khoảng thời gian cố định, nhóm có thể bắt đầu bằng việc quan sát họ cần bao nhiêu hướng dẫn, mắc lỗi nào và có thể tự hoàn thành vòng chơi hay không. Sau đó mới đặt ngưỡng dựa trên mục tiêu thực tế.

## **12.4. Definition of Done cho một bản prototype**

* Có thể khởi chạy và bắt đầu chơi.  
* Người chơi có thể thực hiện hoạt động đại diện cho giả thuyết cần kiểm chứng.  
* Các trạng thái và phản hồi quan trọng hoạt động đúng.  
* Có điều kiện kết thúc phiên thử nghiệm.  
* Có thể thu thập phản hồi hoặc dữ liệu quan sát.  
* Các lỗi nghiêm trọng đã được ghi nhận và xử lý theo mức độ cần thiết.  
* Nhóm biết kết quả thử nghiệm sẽ ảnh hưởng đến quyết định thiết kế nào.

## **13.1. Non-Goals — Những điều không phải mục tiêu hiện tại**

Các mục sau là đề xuất để bảo vệ phạm vi MVP, không phải quyết định loại bỏ vĩnh viễn.

* Không cố gắng triển khai toàn bộ khả năng của mọi thể loại được nhắc đến.  
* Không tối đa hóa số lượng hệ thống hoặc nội dung.  
* Không tạo nhiều nhánh truyện trước khi hiểu rõ chi phí sản xuất và kiểm thử.  
* Không ưu tiên polish hình ảnh khi luồng chơi cốt lõi chưa được kiểm chứng.  
* Không xây dựng kiến trúc kỹ thuật quá phức tạp cho các nhu cầu chưa xuất hiện.  
* Không đánh giá thành công chỉ dựa trên số lượng tính năng hoàn thành.  
* Không mở rộng phạm vi chỉ vì nhóm đã đầu tư thời gian vào một tính năng chưa chứng minh được giá trị.

## **13.2. Design Guardrails — Hàng rào thiết kế**

Một quyết định mới nên bị xem xét lại nếu có một trong các dấu hiệu:

1. Không giải thích được nó phục vụ pillar nào.  
2. Tạo thêm hệ thống phụ nhưng không cải thiện trải nghiệm cốt lõi.  
3. Tạo phụ thuộc kỹ thuật lớn mà chưa có kế hoạch kiểm thử.  
4. Làm tăng đáng kể khối lượng nội dung, UI hoặc cân bằng.  
5. Mâu thuẫn với cốt truyện hoặc cơ chế đã thống nhất.  
6. Làm chậm khả năng tạo ra một bản chơi thử hoàn chỉnh.  
7. Không có tiêu chí để đánh giá liệu tính năng có thành công hay không.

## **13.3. Quy trình thay đổi thiết kế**

Đề xuất ý tưởng hoặc thay đổi \-\> Đánh giá giá trị đối với Vision \-\> Đánh giá chi phí, phụ thuộc và rủi ro \-\> Thử nghiệm, điều chỉnh hoặc từ chối \-\> Ghi nhận quyết định và cập nhật tài liệu liên quan

Đối với thay đổi ảnh hưởng đến cốt truyện chính, core loop, phạm vi MVP hoặc kiến trúc nền tảng, cần có sự đồng thuận của những người được nhóm giao quyền quyết định. Quyền phê duyệt cụ thể cần được xác định trong quy trình quản lý dự án.

## **14.1. Bảng rủi ro**

Mức độ ảnh hưởng dưới đây là đánh giá sơ bộ. Khả năng xảy ra chưa được gán điểm số vì chưa có đủ dữ liệu về nhóm và tiến độ.

| Vấn đề | Ảnh hưởng | Biện pháp giảm thiểu | Phụ trách đề xuất |
| ----- | ----- | ----- | ----- |
| Chưa đối chiếu Game Core | Rất cao: Vision có thể không phản ánh gameplay thực tế | Đối chiếu core loop và các tài liệu gốc | Game Designer |
| Nhiều yếu tố thể loại | Cao: Phạm vi dễ mở rộng quá mức | Xác định một trải nghiệm chính và vai trò của các yếu tố phụ | Game Director / Designer |
| Chưa xác nhận phạm vi MVP | Rất cao: Khó ưu tiên và lập kế hoạch | Chốt mục tiêu MVP và Definition of Done | Producer / PM |
| Thiếu dữ liệu về người chơi | Cao: Các giả thuyết trải nghiệm chưa được kiểm chứng | Prototype và playtest | Designer / QA |
| Năng lực Godot đang phát triển | Cao: Rủi ro kỹ thuật và tiến độ | Chia nhỏ hệ thống, làm prototype độc lập và tích hợp từng bước | Programmer |
| Cốt truyện và gameplay không đồng bộ | Cao: Trải nghiệm thiếu nhất quán | Đối chiếu Story Bible và Game Core | Narrative Designer / Game Designer |
| Hệ thống phụ tăng dần | Cao: Khối lượng sản xuất vượt khả năng | Áp dụng quy trình duyệt thay đổi và đánh giá chi phí | Producer |
| Thiếu tiêu chí nghiệm thu | Cao: Không xác định được khi nào hoàn thành | Định nghĩa tiêu chí kiểm thử cho mỗi mốc | QA / PM |
| Tài liệu không được cập nhật đồng bộ | Trung bình đến cao | Quản lý phiên bản và ghi lại quyết định | Document Owner |

## **14.2. Các câu hỏi cần nhóm thống nhất**

Các câu hỏi sau cần được ưu tiên vì có khả năng ảnh hưởng đến toàn bộ thiết kế.  
Q1. Start Again muốn người chơi làm gì thường xuyên nhất?  
Cần trả lời bằng hành động gameplay cụ thể, không chỉ bằng tên thể loại.  
Q2. Ý nghĩa chính thức của tên Start Again là gì?  
Tên game có gắn trực tiếp với chủ đề, biến cố hoặc hành trình của nhân vật không?  
Q3. Yếu tố nào là trọng tâm: RPG, Life Simulation, Choice-driven hay một tổ hợp cụ thể?  
Không nhất thiết phải bỏ các yếu tố còn lại, nhưng cần xác định yếu tố nào định hình phần lớn trải nghiệm.  
Q4. MVP cần chứng minh điều gì?  
Mục tiêu là kiểm chứng core loop, một hệ thống progression, trải nghiệm kể chuyện hay một tổ hợp đã xác định?  
Q5. Nhóm có nguồn lực và mốc bàn giao nào?  
Cần xác nhận nhân sự, thời gian, mức độ thành thạo Godot và phạm vi nội dung có thể hoàn thành.

## **14.3. Cách xử lý mâu thuẫn giữa tài liệu**

Hiện chưa thể xác định mâu thuẫn thực tế do thiếu nội dung gốc. Khi có tài liệu, mỗi mâu thuẫn cần được ghi lại theo cấu trúc:

| Trường | Nội dung cần ghi |
| ----- | ----- |
| Mã vấn đề | ID duy nhất |
| Tài liệu A | Tên, phiên bản, vị trí |
| Tài liệu B | Tên, phiên bản, vị trí |
| Nội dung mâu thuẫn | Mô tả chính xác hai quan điểm |
| Ảnh hưởng | Tác động đến Vision, gameplay, kỹ thuật và tiến độ |
| Phương án | Các cách giải quyết cùng ưu, nhược điểm |
| Người quyết định | Người hoặc nhóm có thẩm quyền |
| Trạng thái | Chưa xử lý / Đang xem xét / Đã quyết định |

Không tự ý chọn một tài liệu làm nguồn ưu tiên nếu nhóm chưa thống nhất quy tắc quản lý tài liệu.

Traceability giúp truy vết mối liên hệ giữa tầm nhìn, hệ thống, nội dung, kỹ thuật và công việc sản xuất. Mục đích là tránh tình trạng mỗi nhóm xây dựng một phần tốt riêng lẻ nhưng tổng thể không tạo ra trải nghiệm mà dự án mong muốn.

## **15.1. Design Pillar → Gameplay System → Biểu hiện → Kiểm chứng**

| Pillar đề xuất | Hệ thống liên quan | Biểu hiện mong muốn | Kiểm chứng |
| ----- | ----- | ----- | ----- |
| Progress With Purpose | Progression và phản hồi tiến triển | Người chơi nhận biết thay đổi sau hành động | Quan sát và phỏng vấn |
| Agency Matters | Hệ thống lựa chọn nếu có | Người chơi hiểu khác biệt giữa các phương án | Kiểm tra lý do lựa chọn |
| A Coherent World | Môi trường, NPC, tương tác | Các thành phần nhất quán | Playtest và đánh giá nội dung |
| Systems Work Together | Core loop và các hệ thống phụ | Các hệ thống hỗ trợ cùng mục tiêu | Rà soát phụ thuộc và gameplay |
| Small Scope, Finished Experience | Pipeline sản xuất và tích hợp | Có bản build chơi được | Kiểm thử từ đầu đến cuối |

Các hệ thống trong bảng là nhóm hệ thống liên quan về mặt khái niệm, không phải xác nhận về kiến trúc hoặc chức năng đã triển khai.

## **15.2. Vision → Game Core → Art Vision → Technical Design → Roadmap**

### **Game Vision**

Trải nghiệm và nguyên tắc sản phẩm  
↓  
**Game Core**			\+ 	**Art Vision**  
Gameplay và vòng lặp 	   Ngôn ngữ thị giác và cảm xúc  
↓  
**Technical Design**  
Cách triển khai bằng Godot và cấu trúc hệ thống  
↓  
**Roadmap & Production**  
Thứ tự thực hiện, tích hợp và kiểm thử

Đây là sơ đồ quan hệ và truy vết đề xuất, không có nghĩa mọi quyết định phải được thực hiện theo một chiều tuyệt đối.

### **Cách sử dụng sơ đồ**

* Game Vision cung cấp mục tiêu và nguyên tắc.  
* Game Core xác định trải nghiệm đó được thực hiện bằng gameplay như thế nào.  
* Art Vision thể hiện trải nghiệm qua hình ảnh, chuyển động và ngôn ngữ nghệ thuật.  
* Technical Design xác định cách triển khai phù hợp với Godot và nguồn lực.  
* Roadmap chuyển các quyết định thành công việc, mốc bàn giao và tiêu chí nghiệm thu.

Nếu một quyết định kỹ thuật buộc nhóm phải thay đổi gameplay đáng kể, cần phản hồi ngược lên Game Core và đánh giá xem Vision có bị ảnh hưởng hay không.

## **15.3. Feature → Vision Value → Priority → Status**

| Tính năng hoặc nhóm tính năng | Giá trị dự kiến | Ưu tiên | Trạng thái |
| ----- | ----- | ----- | ----- |
| Luồng gameplay chính | Kiểm chứng trải nghiệm cốt lõi | MUST HAVE cho MVP nếu thuộc phạm vi đã chốt | Cần đối chiếu Game Core |
| Phản hồi và điều kiện hoàn thành | Giúp hiểu hành động và kết quả | MUST HAVE cho luồng chơi đại diện | Đề xuất |
| Progression | Thể hiện tiến triển | Theo Game Core | Chưa xác nhận chi tiết |
| Lựa chọn có hệ quả | Thể hiện tính chủ động nếu đây là trọng tâm | Theo thiết kế thực tế | Chưa xác nhận chi tiết |
| Nội dung thế giới | Hỗ trợ khám phá và bối cảnh | Chỉ ưu tiên phần cần cho MVP | Cần Story Bible |
| Hiệu ứng và nội dung trang trí | Tăng chất lượng trình bày | COULD HAVE nếu không thiết yếu | Đề xuất |
| Các hệ thống mở rộng lớn | Mở rộng chiều sâu | Chưa xác định | Cần đánh giá phạm vi |

## **15.4. Checklist đánh giá một tính năng mới**

## **Feature Review Checklist**

**Giá trị sản phẩm**

- [ ] Giải quyết một nhu cầu rõ ràng của người chơi.  
- [ ] Hỗ trợ ít nhất một Design Pillar đã được nhóm thống nhất.  
- [ ] Có thể mô tả giá trị bằng một câu cụ thể.

**Thiết kế**

- [ ] Có hành vi, quy tắc và kết quả mong đợi rõ ràng.  
- [ ] Không mâu thuẫn với Game Core hoặc canon đã chốt.  
- [ ] Có tiêu chí để kiểm chứng hiệu quả.

**Khả thi**

- [ ] Đã đánh giá chi phí lập trình, nghệ thuật và kiểm thử.  
- [ ] Đã xác định phụ thuộc và rủi ro kỹ thuật.  
- [ ] Không làm mất khả năng hoàn thành MVP.

**Quản lý**

- [ ] Có người phụ trách.  
- [ ] Đã xác định mức ưu tiên.  
- [ ] Đã ghi nhận quyết định và cập nhật tài liệu liên quan.

## **Tóm tắt điều hành**

Start Again là dự án game 2D phát triển bằng Godot, với định hướng thể loại đã được sử dụng trong quá trình xây dựng gồm Fantasy, RPG, Life Simulation, Choice-driven Gameplay và Progression.  
Nhiệm vụ của Game Vision là kết nối những hướng thể loại này thành một định hướng sản phẩm nhất quán. Nhóm cần xác định rõ hoạt động chơi chính, động lực khiến người chơi tiếp tục, giá trị của progression và lựa chọn, đồng thời bảo đảm quy mô thiết kế phù hợp với nguồn lực thực tế.

Vision Statement được đề xuất trong bản v0.1 là:  
> “Start Again — mỗi khởi đầu mở ra một hành trình, mỗi lựa chọn tạo nên câu chuyện của riêng bạn.”  
Câu này cần được đối chiếu với cốt truyện và Game Core trước khi chính thức thông qua.

Năm Design Pillars được đề xuất gồm:

1. Progress With Purpose — Tiến triển có ý nghĩa.  
2. Agency Matters — Hành động và lựa chọn có giá trị.  
3. A Coherent World — Thế giới nhất quán.  
4. Systems Work Together — Các hệ thống hỗ trợ lẫn nhau.  
5. Small Scope, Finished Experience — Phạm vi nhỏ, trải nghiệm hoàn chỉnh.

Đối với phiên bản đầu, định hướng sản xuất được đề xuất là ưu tiên một luồng gameplay hoàn chỉnh, có thể chơi và kiểm chứng, trước khi mở rộng các hệ thống và nội dung bổ trợ.  
Thành công của Vision không nên được đánh giá bằng số lượng tính năng. Các tiêu chí cần tập trung vào khả năng người chơi hiểu gameplay, nhận biết tiến triển, hiểu các lựa chọn quan trọng, nhận diện bản sắc game và việc nhóm có thể hoàn thành trải nghiệm trong nguồn lực hiện có hay không.

Trạng thái cuối cùng: Game Vision v0.1 là bản dự thảo định hướng. Chưa đủ căn cứ để tuyên bố rằng toàn bộ Vision đã phản ánh chính xác các quyết định trong tài liệu gốc hoặc đã được nhóm phê duyệt.  
