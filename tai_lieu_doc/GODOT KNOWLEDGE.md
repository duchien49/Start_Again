**Mục đích:** Đây là Godot Knowledge, tài liệu dùng để hướng dẫn lập trình API, thiết kế hệ thống và định nghĩa mã nguồn GDScript cho dự án Game Start Again trên Godot Engine. Tài liệu này được sử dụng làm kim chỉ nam cho Main Developer và đội ngũ phát triển.   
**Lưu ý:** Tài liệu này vẫn đang trong quá trình phát triển và sẽ được hoàn thiện dần trong quá trình phát triển dự án.   
Hệ thống core của game vận hành dựa trên các Singleton (Autoload) đóng vai trò làm “bộ não” xử lý dữ liệu và luồng truyền tín hiệu trung tâm.  
res://  
├── global/  
│   ├── GameManager.gd     \# Quản lý tài chính, chỉ số nhân vật & trạng thái chính  
│   ├── TimeManager.gd       \# Quản lý vòng lặp thời gian in-game  
│   ├── SignalBus.gd              \# Tổng đài phát/nhận tín hiệu toàn cục  
│   └── SaveManager.gd       \# Xử lý Mã hóa, Lưu & Tải dữ liệu (Save/Load)  
├── scripts/  
│   ├── resources/                    \# Custom Resources (SkillData, ItemData, AchievementData...)  
│   └── managers/                 \# Các Manager cấp Module (Company, Quest, Shop, Minigame...)  
└── scenes/                  \# Giao diện UI & Cảnh game (.tscn)

**2.1. SignalBus.gd \- Tổng Đài Tín Hiệu Trung Tâm**  
\# res://global/SignalBus.gd  
extends Node

\# \--- Nhóm Tín Hiệu Tài Nguyên & Chỉ Số \---  
signal money\_changed(new\_wallet: int, new\_bank: int)  
signal sp\_changed(new\_sp: int)  
signal stats\_changed(stat\_name: String, new\_value: float)  
signal health\_depleted()  
signal stress\_threshold\_reached(current\_stress: float)

\# \--- Nhóm Tín Hiệu Thời Gian \---  
signal time\_ticked(hour: int, minute: int)  
signal day\_changed(new\_day: int)

\# \--- Nhóm Tín Hiệu Tiến Trình & Module \---  
signal job\_changed(new\_job\_id: String)  
signal salary\_earned(amount: int)  
signal location\_changed(new\_location\_id: String)  
signal location\_unlocked(location\_id: String)  
signal npc\_friendship\_changed(npc\_id: String, new\_points: float)  
signal relationship\_tier\_up(npc\_id: String, new\_tier: String)

\# \--- Nhóm Tín Hiệu Nhiệm Vụ & Kinh Doanh \---  
signal quest\_accepted(quest\_id: String)  
signal quest\_progress\_updated(quest\_id: String, objective\_id: String, current: int, target: int)  
signal quest\_completed(quest\_id: String)  
signal revenue\_generated(amount: int)  
signal business\_status\_changed(business\_id: String, is\_active: bool)

\# \--- Nhóm Tín Hiệu Túi Đồ & Cửa Hàng \---  
signal inventory\_updated()  
signal item\_used(item\_id: String)  
signal item\_added(item\_id: String, amount: int)  
signal item\_purchased(item\_id: String, total\_cost: int)  
signal item\_sold(item\_id: String, total\_earned: int)

\# \--- Nhóm Tín Hiệu Nhân Sự Công Ty \---  
signal payroll\_processed(total\_paid: int)  
signal employee\_hired(employee\_id: String)  
signal employee\_fired(employee\_id: String)  
signal office\_upgraded(new\_level: int)

\# \--- Nhóm Tín Hiệu Kỹ Năng & Mini Game \---  
signal skill\_unlocked(skill\_id: String)  
signal skill\_level\_up(skill\_id: String, new\_level: int)  
signal skill\_equipped(slot\_index: int, skill\_id: String)  
signal minigame\_started(minigame\_id: String)  
signal minigame\_finished(minigame\_id: String, final\_score: int)

\# \--- Nhóm Tín Hiệu Thành Tựu & Kết Cục \---  
signal achievement\_unlocked(achievement\_id: String)  
signal reward\_claimed(achievement\_id: String)  
signal ending\_discovered(ending\_id: String)

\# \--- Nhóm System & Settings \---  
signal settings\_updated()  
signal game\_initialized()  
signal save\_file\_checked(exists: bool)

**2.2. GameManager.gd \- Quản Lý Trạng Thái và Chỉ Số Nhân Vật**  
\# res://global/SignalBus.gd  
extends Node

\# \--- Nhóm Tín Hiệu Tài Nguyên & Chỉ Số \---  
signal money\_changed(new\_wallet: int, new\_bank: int)  
signal sp\_changed(new\_sp: int)  
signal stats\_changed(stat\_name: String, new\_value: float)  
signal health\_depleted()  
signal stress\_threshold\_reached(current\_stress: float)

\# \--- Nhóm Tín Hiệu Thời Gian \---  
signal time\_ticked(hour: int, minute: int)  
signal day\_changed(new\_day: int)

\# \--- Nhóm Tín Hiệu Tiến Trình & Module \---  
signal job\_changed(new\_job\_id: String)  
signal salary\_earned(amount: int)  
signal location\_changed(new\_location\_id: String)  
signal location\_unlocked(location\_id: String)  
signal npc\_friendship\_changed(npc\_id: String, new\_points: float)  
signal relationship\_tier\_up(npc\_id: String, new\_tier: String)

\# \--- Nhóm Tín Hiệu Nhiệm Vụ & Kinh Doanh \---  
signal quest\_accepted(quest\_id: String)  
signal quest\_progress\_updated(quest\_id: String, objective\_id: String, current: int, target: int)  
signal quest\_completed(quest\_id: String)  
signal revenue\_generated(amount: int)  
signal business\_status\_changed(business\_id: String, is\_active: bool)

\# \--- Nhóm Tín Hiệu Túi Đồ & Cửa Hàng \---  
signal inventory\_updated()  
signal item\_used(item\_id: String)  
signal item\_added(item\_id: String, amount: int)  
signal item\_purchased(item\_id: String, total\_cost: int)  
signal item\_sold(item\_id: String, total\_earned: int)

\# \--- Nhóm Tín Hiệu Nhân Sự Công Ty \---  
signal payroll\_processed(total\_paid: int)  
signal employee\_hired(employee\_id: String)  
signal employee\_fired(employee\_id: String)  
signal office\_upgraded(new\_level: int)

\# \--- Nhóm Tín Hiệu Kỹ Năng & Mini Game \---  
signal skill\_unlocked(skill\_id: String)  
signal skill\_level\_up(skill\_id: String, new\_level: int)  
signal skill\_equipped(slot\_index: int, skill\_id: String)  
signal minigame\_started(minigame\_id: String)  
signal minigame\_finished(minigame\_id: String, final\_score: int)

\# \--- Nhóm Tín Hiệu Thành Tựu & Kết Cục \---  
signal achievement\_unlocked(achievement\_id: String)  
signal reward\_claimed(achievement\_id: String)  
signal ending\_discovered(ending\_id: String)

\# \--- Nhóm System & Settings \---  
signal settings\_updated()  
signal game\_initialized()  
signal save\_file\_checked(exists: bool)

**2.3. TimeManager.gd \- Vòng Lặp Thời Gian In-Game**  
\# res://global/TimeManager.gd  
extends Node

var current\_day: int \= 1  
var current\_hour: int \= 8  
var current\_minute: int \= 0  
var time\_scale: float \= 1.0 \# 1 giây thực \= 1 phút in-game

var \_timer: Timer

func \_ready() \-\> void:  
	\_timer \= Timer.new()  
	\_timer.wait\_time \= 1.0 / time\_scale  
	\_timer.autostart \= true  
	\_timer.timeout.connect(\_on\_tick)  
	add\_child(\_timer)

func \_on\_tick() \-\> void:  
	current\_minute \+= 1  
	if current\_minute \>= 60:  
		current\_minute \= 0  
		current\_hour \+= 1  
		if current\_hour \>= 24:  
			current\_hour \= 0  
			current\_day \+= 1  
			SignalBus.day\_changed.emit(current\_day)  
	SignalBus.time\_ticked.emit(current\_hour, current\_minute)

func advance\_time(hours: int, minutes: int \= 0\) \-\> void:  
	current\_minute \+= minutes  
	current\_hour \+= hours  
	while current\_minute \>= 60:  
		current\_minute \-= 60  
		current\_hour \+= 1  
	while current\_hour \>= 24:  
		current\_hour \-= 24  
		current\_day \+= 1  
		SignalBus.day\_changed.emit(current\_day)  
	SignalBus.time\_ticked.emit(current\_hour, current\_minute)

**2.4. SaveManager.gd \- Mã Hóa và Lưu Trữ Dữ Liệu (Save/Load)**  
\# res://global/SaveManager.gd  
extends Node

const SAVE\_PATH \= "user://save\_game.json"  
const GLOBAL\_PROFILE\_PATH \= "user://global\_profile.json"  
const SETTINGS\_PATH \= "user://settings.cfg"

\# \--- Kiểm tra & Khởi tạo (UC01) \---  
func check\_save\_file() \-\> bool:  
	var exists \= FileAccess.file\_exists(SAVE\_PATH)  
	SignalBus.save\_file\_checked.emit(exists)  
	return exists

\# \--- Save/Load State (Lượt chơi hiện tại) \---  
func save\_game\_state(extra\_data: Dictionary \= {}) \-\> bool:  
	var save\_dict \= {  
		"version": "1.0.0",  
		"player": {  
			"name": GameManager.character\_name,  
			"wallet": GameManager.wallet\_cash,  
			"bank": GameManager.bank\_balance,  
			"sp": GameManager.skill\_points,  
			"health": GameManager.health,  
			"energy": GameManager.energy,  
			"stress": GameManager.stress,  
			"history": GameManager.transaction\_history  
		},  
		"time": {  
			"day": TimeManager.current\_day,  
			"hour": TimeManager.current\_hour,  
			"minute": TimeManager.current\_minute  
		},  
		"modules": extra\_data  
	}  
	  
	var file \= FileAccess.open(SAVE\_PATH, FileAccess.WRITE)  
	if not file:  
		return false  
	var json\_string \= JSON.stringify(save\_dict, "\\t")  
	file.store\_string(json\_string)  
	file.close()  
	return true

func load\_game\_state() \-\> Dictionary:  
	if not FileAccess.file\_exists(SAVE\_PATH):  
		return {}  
	var file \= FileAccess.open(SAVE\_PATH, FileAccess.READ)  
	var json\_string \= file.get\_as\_text()  
	file.close()  
	  
	var json \= JSON.new()  
	if json.parse(json\_string) \== OK:  
		var data \= json.data  
		GameManager.character\_name \= data\["player"\]\["name"\]  
		GameManager.wallet\_cash \= data\["player"\]\["wallet"\]  
		GameManager.bank\_balance \= data\["player"\]\["bank"\]  
		GameManager.skill\_points \= data\["player"\]\["sp"\]  
		GameManager.health \= data\["player"\]\["health"\]  
		GameManager.energy \= data\["player"\]\["energy"\]  
		GameManager.stress \= data\["player"\]\["stress"\]  
		GameManager.transaction\_history \= data\["player"\]\["history"\]  
		  
		TimeManager.current\_day \= data\["time"\]\["day"\]  
		TimeManager.current\_hour \= data\["time"\]\["hour"\]  
		TimeManager.current\_minute \= data\["time"\]\["minute"\]  
		return data.get("modules", {})  
	return {}

\# \--- Global Profile (Lưu vĩnh viễn: Thành tựu & Gallery UC15) \---  
func save\_global\_profile(unlocked\_achievements: Array, unlocked\_endings: Array) \-\> void:  
	var profile \= {  
		"achievements": unlocked\_achievements,  
		"endings": unlocked\_endings  
	}  
	var file \= FileAccess.open(GLOBAL\_PROFILE\_PATH, FileAccess.WRITE)  
	if file:  
		file.store\_string(JSON.stringify(profile, "\\t"))  
		file.close()

func load\_global\_profile() \-\> Dictionary:  
	if not FileAccess.file\_exists(GLOBAL\_PROFILE\_PATH):  
		return {"achievements": \[\], "endings": \[\]}  
	var file \= FileAccess.open(GLOBAL\_PROFILE\_PATH, FileAccess.READ)  
	var json \= JSON.new()  
	if json.parse(file.get\_as\_text()) \== OK:  
		file.close()  
		return json.data  
	return {"achievements": \[\], "endings": \[\]}

\# \--- Cài Đặt (UC02) \---  
func save\_settings(master\_vol: float, sfx\_vol: float, bgm\_vol: float, fullscreen: bool) \-\> void:  
	var config \= ConfigFile.new()  
	config.set\_value("audio", "master", master\_vol)  
	config.set\_value("audio", "sfx", sfx\_vol)  
	config.set\_value("audio", "bgm", bgm\_vol)  
	config.set\_value("video", "fullscreen", fullscreen)  
	config.save(SETTINGS\_PATH)  
	SignalBus.settings\_updated.emit()

\# res://scripts/resources/SkillData.gd  
extends Resource  
class\_name SkillData

@export var skill\_id: String \= ""  
@export var skill\_name: String \= ""  
@export\_multiline var description: String \= ""  
@export var current\_level: int \= 0  
@export var max\_level: int \= 5  
@export var sp\_cost: int \= 2  
@export var money\_cost: int \= 500  
@export var icon: Texture2D

\# res://scripts/resources/ItemData.gd  
extends Resource  
class\_name ItemData

@export var item\_id: String \= ""  
@export var item\_name: String \= ""  
@export var buy\_price: int \= 100  
@export var sell\_price: int \= 50  
@export var is\_stackable: bool \= true  
@export var max\_stack\_size: int \= 99  
@export var energy\_restore: float \= 20.0  
@export var stress\_reduce: float \= 10.0  
@export var icon: Texture2D

\# res://scripts/resources/AchievementData.gd  
extends Resource  
class\_name AchievementData

@export var achievement\_id: String \= ""  
@export var title: String \= ""  
@export\_multiline var description: String \= ""  
@export var reward\_sp: int \= 5  
@export var reward\_money: int \= 1000  
@export var trophy\_icon: Texture2D  
@export var trophy\_position: Vector2 \= Vector2.ZERO

**4.1. UC01: Khởi Động Game và UC02: Cài Đặt**  
\# res://scripts/managers/MainMenuManager.gd  
extends Node

func \_ready() \-\> void:  
	var has\_save \= SaveManager.check\_save\_file()  
	\$UI/ContinueButton.disabled \= not has\_save  
	SignalBus.game\_initialized.emit()

func on\_new\_game\_pressed() \-\> void:  
	GameManager.wallet\_cash \= 10000  
	GameManager.bank\_balance \= 50000  
	GameManager.health \= 100.0  
	GameManager.energy \= 100.0  
	GameManager.stress \= 0.0  
	get\_tree().change\_scene\_to\_file("res://scenes/MainGame.tscn")

func on\_continue\_pressed() \-\> void:  
	SaveManager.load\_game\_state()  
	get\_tree().change\_scene\_to\_file("res://scenes/MainGame.tscn")

func apply\_settings(master: float, sfx: float, bgm: float, fullscreen: bool) \-\> void:  
	AudioServer.set\_bus\_volume\_db(AudioServer.get\_bus\_index("Master"), linear\_to\_db(master))  
	AudioServer.set\_bus\_volume\_db(AudioServer.get\_bus\_index("SFX"), linear\_to\_db(sfx))  
	AudioServer.set\_bus\_volume\_db(AudioServer.get\_bus\_index("BGM"), linear\_to\_db(bgm))  
	DisplayServer.window\_set\_mode(DisplayServer.WINDOW\_MODE\_FULLSCREEN if fullscreen else DisplayServer.WINDOW\_MODE\_WINDOWED)  
	SaveManager.save\_settings(master, sfx, bgm, fullscreen)

**4.2. UC03: Quản Lý Nghề**  
\# res://scripts/managers/JobManager.gd  
extends Node

var current\_job\_id: String \= "UNEMPLOYED"  
var base\_salary: int \= 0  
var job\_level: int \= 1

func promote\_job(new\_job\_id: String, new\_salary: int, required\_skill\_level: int) \-\> bool:  
	\# Kiểm tra cấp độ kỹ năng từ Module UC13  
	if SkillManager.get\_skill\_level("SL\_WORK") \>= required\_skill\_level:  
		current\_job\_id \= new\_job\_id  
		base\_salary \= new\_salary  
		job\_level \+= 1  
		SignalBus.job\_changed.emit(current\_job\_id)  
		return true  
	return false

func earn\_daily\_salary() \-\> void:  
	if current\_job\_id \!= "UNEMPLOYED":  
		GameManager.add\_money(base\_salary, true, "Lương hàng ngày: " \+ current\_job\_id)  
		SignalBus.salary\_earned.emit(base\_salary)  
**4.3. UC04: Quản Lý Nhân Vật**  
**Module này để quản lý các chỉ số sinh tồn và trạng thái tâm lý của nhân vật với các ngưỡng giới hạn nghiêm ngặt \[0, 100\] và cơ chế phát tín hiệu khi chạm mốc nguy hiểm**  
extends Node  
class\_name CharacterManager

signal stats\_changed(stat\_name: String, current\_val: float)  
signal health\_depleted()  
signal stress\_threshold\_reached(is\_burnout: bool)

@export var character\_name: String \= "Main Character"

var health: float \= 100.0:  
	set(value):  
		health \= clamp(value, 0.0, 100.0)  
		emit\_signal("stats\_changed", "health", health)  
		if health \<= 0.0:  
			emit\_signal("health\_depleted")

var energy: float \= 100.0:  
	set(value):  
		energy \= clamp(value, 0.0, 100.0)  
		emit\_signal("stats\_changed", "energy", energy)

var stress: float \= 0.0:  
	set(value):  
		stress \= clamp(value, 0.0, 100.0)  
		emit\_signal("stats\_changed", "stress", stress)  
		if stress \>= 80.0:  
			\# stress \>= 80: cảnh báo; stress \>= 100: Burnout chặn học tập/làm việc  
			emit\_signal("stress\_threshold\_reached", stress \>= 100.0)

func modify\_stat(stat\_name: String, amount: float) \-\> void:  
	match stat\_name:  
		"health":  
			health \+= amount  
		"energy":  
			energy \+= amount  
		"stress":  
			stress \+= amount

**4.4. UC05: Khám Phá Thế Giới**  
\# res://scripts/managers/WorldManager.gd  
extends Node

var current\_location\_id: String \= "HOME"  
var unlocked\_locations: Array\[String\] \= \["HOME", "STREET"\]

func travel\_to(location\_id: String, travel\_time\_hours: int, energy\_cost: float) \-\> bool:  
	if not location\_id in unlocked\_locations:  
		print("Khu vực chưa được mở khóa\!")  
		return false  
	if GameManager.energy \< energy\_cost:  
		print("Không đủ thể lực để di chuyển\!")  
		return false  
		  
	GameManager.energy \-= energy\_cost  
	TimeManager.advance\_time(travel\_time\_hours, 0\)  
	current\_location\_id \= location\_id  
	SignalBus.location\_changed.emit(current\_location\_id)  
	return true

func unlock\_location(location\_id: String) \-\> void:  
	if not location\_id in unlocked\_locations:  
		unlocked\_locations.append(location\_id)  
		SignalBus.location\_unlocked.emit(location\_id)

**4.5. UC06: Quan Hệ NPC**  
\# res://scripts/managers/NPCManager.gd  
extends Node

enum NPCStatus { STRANGER, FRIEND, LOVER, ENEMY }  
var npc\_data: Dictionary \= {} \# Key: npc\_id, Value: {"points": float, "status": NPCStatus}

func add\_friendship(npc\_id: String, points: float) \-\> void:  
	if not npc\_data.has(npc\_id):  
		npc\_data\[npc\_id\] \= {"points": 0.0, "status": NPCStatus.STRANGER}  
		  
	npc\_data\[npc\_id\]\["points"\] \= clamp(npc\_data\[npc\_id\]\["points"\] \+ points, 0.0, 100.0)  
	var current\_pts \= npc\_data\[npc\_id\]\["points"\]  
	SignalBus.npc\_friendship\_changed.emit(npc\_id, current\_pts)  
	  
	\# Kiểm tra ngưỡng thăng cấp quan hệ  
	var old\_status \= npc\_data\[npc\_id\]\["status"\]  
	if current\_pts \>= 80.0 and old\_status \!= NPCStatus.LOVER:  
		npc\_data\[npc\_id\]\["status"\] \= NPCStatus.LOVER  
		SignalBus.relationship\_tier\_up.emit(npc\_id, "LOVER")  
	elif current\_pts \>= 40.0 and old\_status \== NPCStatus.STRANGER:  
		npc\_data\[npc\_id\]\["status"\] \= NPCStatus.FRIEND  
		SignalBus.relationship\_tier\_up.emit(npc\_id, "FRIEND")

**4.6. UC07: Quest (Nhiệm vụ)**  
func accept\_quest(quest\_id: String, objectives: Dictionary) \-\> void:  
	active\_quests\[quest\_id\] \= {  
		"status": Q\# res://scripts/managers/QuestManager.gd  
extends Node

enum QuestSuestStatus.IN\_PROGRESS,  
		"objectives": objectives \# e.g. {"collect\_item\_A": {"current": 0, "target": 5}}  
	}  
	SignalBus.quest\_accepted.emit(quest\_id)

func update\_objective(quest\_id: String, objective\_id: String, progress\_amount: int) \-\> void:  
	if not active\_quests.has(quest\_id) or active\_quests\[quest\_id\]\["status"\] \!= QuestStatus.IN\_PROGRESS:  
		return  
		  
	var objs \= active\_quests\[quest\_id\]\["objectives"\]  
	if objs.has(objective\_id):  
		objs\[objective\_id\]\["current"\] \= min(objs\[objective\_id\]\["target"\], objs\[objective\_id\]\["current"\] \+ progress\_amount)  
		SignalBus.quest\_progress\_updated.emit(quest\_id, objective\_id, objs\[objective\_id\]\["current"\], objs\[objective\_id\]\["target"\])  
		\_check\_quest\_completion(quest\_id)

func \_check\_quest\_completion(quest\_id: String) \-\> void:  
	var objs \= active\_quests\[quest\_id\]\["objectives"\]  
	var all\_done \= true  
	for k in objs:  
		if objs\[k\]\["current"\] \< objs\[k\]\["target"\]:  
			all\_done \= false  
			break  
	if all\_done:  
		active\_quests\[quest\_id\]\["status"\] \= QuestStatus.COMPLETED  
		SignalBus.quest\_completed.emit(quest\_id)

**4.7. UC08: Kinh Doanh**  
\# res://scripts/managers/BusinessManager.gd  
extends Node

var business\_type\_id: String \= "CAFE"  
var operating\_cost: int \= 2000  
var base\_item\_sell\_price: int \= 50  
var items\_sold\_count: int \= 100  
var rent\_cost: int \= 1000  
var tax\_cost: int \= 500  
var market\_trend: float \= 1.2 \# Hệ số biến động thị trường

func process\_daily\_business() \-\> void:  
	var gross\_revenue \= base\_item\_sell\_price \* items\_sold\_count  
	var total\_operating\_cost \= operating\_cost \+ rent\_cost \+ tax\_cost  
	var net\_profit \= int((gross\_revenue \* market\_trend) \- total\_operating\_cost)  
	  
	if net\_profit \>= 0:  
		GameManager.add\_money(net\_profit, true, "Lợi nhuận kinh doanh: " \+ business\_type\_id)  
		SignalBus.revenue\_generated.emit(net\_profit)  
	else:  
		var deficit \= abs(net\_profit)  
		if not GameManager.deduct\_money(deficit, true, "Thua lỗ kinh doanh"):  
			print("CẢNH BÁO: Không đủ tiền trang trải chi phí kinh doanh\! Kích hoạt nợ tài chính.")  
			SignalBus.business\_status\_changed.emit(business\_type\_id, false)  
**4.8. UC09: Inventory & UC10: Shop**  
\# res://scripts/managers/InventoryShopManager.gd  
extends Node

var inventory\_slots: Array\[Dictionary\] \= \[\] \# {"item\_data": ItemData, "count": int}  
var max\_slots: int \= 20  
var limited\_shop\_stock: Dictionary \= {} \# item\_id \-\> count\_bought\_today

func \_ready() \-\> void:  
	SignalBus.day\_changed.connect(\_on\_day\_changed)

func \_on\_day\_changed(\_new\_day: int) \-\> void:  
	limited\_shop\_stock.clear() \# Reset số lượng đồ giới hạn mua trong ngày

func add\_item(item: ItemData, amount: int \= 1\) \-\> bool:  
	\# Xử lý Stacking  
	if item.is\_stackable:  
		for slot in inventory\_slots:  
			if slot\["item\_data"\].item\_id \== item.item\_id and slot\["count"\] \< item.max\_stack\_size:  
				slot\["count"\] \+= amount  
				SignalBus.inventory\_updated.emit()  
				return true  
	\# Thêm Slot mới  
	if inventory\_slots.size() \< max\_slots:  
		inventory\_slots.append({"item\_data": item, "count": amount})  
		SignalBus.inventory\_updated.emit()  
		return true  
	print("Túi đồ đã đầy\!")  
	return false

func use\_item(slot\_index: int) \-\> bool:  
	if slot\_index \< 0 or slot\_index \>= inventory\_slots.size():  
		return false  
	var slot \= inventory\_slots\[slot\_index\]  
	var item: ItemData \= slot\["item\_data"\]  
	  
	GameManager.energy \+= item.energy\_restore  
	GameManager.stress \-= item.stress\_reduce  
	  
	slot\["count"\] \-= 1  
	SignalBus.item\_used.emit(item.item\_id)  
	if slot\["count"\] \<= 0:  
		inventory\_slots.remove\_at(slot\_index)  
	SignalBus.inventory\_updated.emit()  
	return true

func buy\_item\_from\_shop(item: ItemData, amount: int \= 1, daily\_limit: int \= 999\) \-\> bool:  
	var current\_bought \= limited\_shop\_stock.get(item.item\_id, 0\)  
	if current\_bought \+ amount \> daily\_limit:  
		print("Đã đạt giới hạn mua trong ngày\!")  
		return false  
		  
	var total\_cost \= item.buy\_price \* amount  
	if GameManager.deduct\_money(total\_cost, false, "Mua item: " \+ item.item\_name):  
		if add\_item(item, amount):  
			limited\_shop\_stock\[item.item\_id\] \= current\_bought \+ amount  
			SignalBus.item\_purchased.emit(item.item\_id, total\_cost)  
			return true  
		else:  
			GameManager.add\_money(total\_cost, false, "Hoàn tiền do đầy giỏ đồ")  
	return false

func sell\_item\_to\_shop(slot\_index: int, amount: int \= 1\) \-\> bool:  
	if slot\_index \< 0 or slot\_index \>= inventory\_slots.size():  
		return false  
	var slot \= inventory\_slots\[slot\_index\]  
	var item: ItemData \= slot\["item\_data"\]  
	  
	var sell\_amount \= min(amount, slot\["count"\])  
	var total\_earned \= int(item.sell\_price \* sell\_amount)  
	  
	slot\["count"\] \-= sell\_amount  
	if slot\["count"\] \<= 0:  
		inventory\_slots.remove\_at(slot\_index)  
		  
	GameManager.add\_money(total\_earned, false, "Bán item: " \+ item.item\_name)  
	SignalBus.item\_sold.emit(item.item\_id, total\_earned)  
	SignalBus.inventory\_updated.emit()  
	return true

**4.9. UC11: Quản Lý Tiền**  
**Module này đảm bảo quy tắc chống số âm (max(0, value)) cho cả tiền mặt lẫn tài khoản ngân hàng, đồng thời ghi lại nhật ký giao dịch (transaction\_history) để phục vụ lưu trữ vào Save State.**  
extends Node  
class\_name WalletManager

signal money\_changed(new\_wallet: int, new\_bank: int)  
signal transaction\_logged(transaction\_type: String, amount: int, timestamp: String)

@export var wallet\_cash: int \= 10000:  
	set(value):  
		wallet\_cash \= max(0, value) \# Quy tắc chống số âm tuyệt đối  
		emit\_signal("money\_changed", wallet\_cash, bank\_balance)

@export var bank\_balance: int \= 50000:  
	set(value):  
		bank\_balance \= max(0, value) \# Quy tắc chống số âm tuyệt đối  
		emit\_signal("money\_changed", wallet\_cash, bank\_balance)

var transaction\_history: Array \= \[\]

func add\_transaction(type: String, amount: int) \-\> void:  
	var record \= {  
		"type": type,  
		"amount": amount,  
		"time": Time.get\_datetime\_string\_from\_system()  
	}  
	transaction\_history.append(record)  
	emit\_signal("transaction\_logged", type, amount, record\["time"\])

func spend\_money(amount: int, use\_bank: bool \= false) \-\> bool:  
	if use\_bank:  
		if bank\_balance \>= amount:  
			bank\_balance \-= amount  
			add\_transaction("SPEND\_BANK", amount)  
			return true  
	else:  
		if wallet\_cash \>= amount:  
			wallet\_cash \-= amount  
			add\_transaction("SPEND\_CASH", amount)  
			return true  
	return false

func earn\_money(amount: int, to\_bank: bool \= false) \-\> void:  
	if to\_bank:  
		bank\_balance \+= amount  
		add\_transaction("EARN\_BANK", amount)  
	else:  
		wallet\_cash \+= amount  
		add\_transaction("EARN\_CASH", amount)

**4.10. UC12: Công Ty & Nhân Sự**  
\# res://scripts/managers/CompanyManager.gd  
extends Node

var company\_name: String \= "Startup Co."  
var office\_level: int \= 1  
var office\_capacity: int \= 3  
var unpaid\_days: int \= 0  
var employee\_list: Array\[Dictionary\] \= \[\] \# {"id": String, "name": String, "salary": int, "loyalty": int}

func hire\_employee(emp\_id: String, emp\_name: String, salary: int) \-\> bool:  
	if employee\_list.size() \>= office\_capacity:  
		print("Văn phòng đã hết sức chứa\!")  
		return false  
	employee\_list.append({"id": emp\_id, "name": emp\_name, "salary": salary, "loyalty": 100})  
	SignalBus.employee\_hired.emit(emp\_id)  
	return true

func fire\_employee(emp\_id: String) \-\> bool:  
	for i in range(employee\_list.size()):  
		if employee\_list\[i\]\["id"\] \== emp\_id:  
			var severance\_pay \= int(employee\_list\[i\]\["salary"\] \* 1.5)  
			if GameManager.deduct\_money(severance\_pay, true, "Phí đền bù sa thải: " \+ emp\_name):  
				employee\_list.remove\_at(i)  
				SignalBus.employee\_fired.emit(emp\_id)  
				return true  
	return false

func process\_payroll() \-\> void:  
	var total\_payroll \= 0  
	for emp in employee\_list:  
		total\_payroll \+= emp\["salary"\]  
		  
	if GameManager.deduct\_money(total\_payroll, true, "Trả lương nhân viên"):  
		unpaid\_days \= 0  
		SignalBus.payroll\_processed.emit(total\_payroll)  
	else:  
		unpaid\_days \+= 1  
		for emp in employee\_list:  
			emp\["loyalty"\] \= max(0, emp\["loyalty"\] \- 20\)  
		if unpaid\_days \>= 3:  
			trigger\_strike\_event()

func trigger\_strike\_event() \-\> void:  
	print("ĐÌNH CÔNG\! Nhân viên nghỉ việc hàng loạt do nợ lương\!")  
	employee\_list.clear()

**4.11. UC13: Cây Kỹ Năng & Trang Bị**   
\# res://scripts/managers/SkillManager.gd  
extends Node

var skills\_database: Dictionary \= {} \# skill\_id \-\> SkillData  
var active\_slots: Array\[String\] \= \["", "", ""\] \# 3 Ô trang bị kỹ năng

func try\_upgrade\_skill(skill\_id: String) \-\> bool:  
	if not skills\_database.has(skill\_id):  
		return false  
	var skill: SkillData \= skills\_database\[skill\_id\]  
	  
	\# Kiểm tra hình phạt Burnout/Mệt mỏi  
	if GameManager.health \< 20.0 or GameManager.stress \> 80.0:  
		print("Nhân vật quá mệt mỏi\! Không thể học tập/nâng cấp.")  
		return false  
		  
	if skill.current\_level \< skill.max\_level:  
		if GameManager.skill\_points \>= skill.sp\_cost and GameManager.deduct\_money(skill.money\_cost, false, "Học kỹ năng"):  
			GameManager.skill\_points \-= skill.sp\_cost  
			skill.current\_level \+= 1  
			SignalBus.skill\_level\_up.emit(skill\_id, skill.current\_level)  
			if skill.current\_level \== 1:  
				SignalBus.skill\_unlocked.emit(skill\_id)  
			return true  
	return false

func equip\_skill(slot\_index: int, skill\_id: String) \-\> bool:  
	if slot\_index \< 0 or slot\_index \>= active\_slots.size():  
		return false  
	\# Quy tắc Unique Equip: Xóa kỹ năng khỏi ô cũ nếu đã trang bị  
	for i in range(active\_slots.size()):  
		if active\_slots\[i\] \== skill\_id:  
			active\_slots\[i\] \= ""  
			  
	active\_slots\[slot\_index\] \= skill\_id  
	SignalBus.skill\_equipped.emit(slot\_index, skill\_id)  
	return true

func get\_skill\_level(skill\_id: String) \-\> int:  
	if skills\_database.has(skill\_id):  
		return skills\_database\[skill\_id\].current\_level  
	return 0

**4.12. UC14: Mini Game**  
\# res://scripts/managers/MinigameManager.gd  
extends Node

func start\_minigame(minigame\_id: String) \-\> void:  
	get\_tree().paused \= true \# Pause Main Game  
	SignalBus.minigame\_started.emit(minigame\_id)  
	\# Load & Add Minigame Scene  
	var minigame\_scene \= load("res://scenes/minigames/" \+ minigame\_id \+ ".tscn").instantiate()  
	add\_child(minigame\_scene)

func finish\_minigame(minigame\_id: String, score: int, reward\_multiplier: float) \-\> void:  
	get\_tree().paused \= false  
	var reward\_money \= int(score \* reward\_multiplier)  
	GameManager.add\_money(reward\_money, false, "Thưởng Mini Game: " \+ minigame\_id)  
	GameManager.stress \= max(0.0, GameManager.stress \- 15.0) \# Chơi game giúp giảm stress  
	SignalBus.minigame\_finished.emit(minigame\_id, score)

**4.13. UC15: Thành Tựu & Bộ Sưu Tập Kết Cục (Gallery)**  
\# res://scripts/managers/AchievementManager.gd  
extends Node

var achievement\_db: Dictionary \= {} \# id \-\> AchievementData  
var unlocked\_achievements: Array\[String\] \= \[\]  
var claimed\_rewards: Array\[String\] \= \[\]  
var unlocked\_endings: Array\[String\] \= \[\]

func \_ready() \-\> void:  
	\# Tải profile vĩnh viễn khi khởi động  
	var profile \= SaveManager.load\_global\_profile()  
	unlocked\_achievements \= profile.get("achievements", \[\])  
	unlocked\_endings \= profile.get("endings", \[\])  
	  
	\# Đăng ký lắng nghe tín hiệu để tự động mở khóa thành tựu (UC15.2)  
	SignalBus.money\_changed.connect(\_check\_money\_achievements)

func \_check\_money\_achievements(wallet: int, bank: int) \-\> void:  
	if (wallet \+ bank) \>= 1000000 and not "RICH\_MIND" in unlocked\_achievements:  
		unlock\_achievement("RICH\_MIND")

func unlock\_achievement(achievement\_id: String) \-\> void:  
	if not achievement\_id in unlocked\_achievements:  
		unlocked\_achievements.append(achievement\_id)  
		SignalBus.achievement\_unlocked.emit(achievement\_id)  
		SaveManager.save\_global\_profile(unlocked\_achievements, unlocked\_endings)  
		claim\_reward(achievement\_id) \# Tự động nhận thưởng (UC15.3)

func claim\_reward(achievement\_id: String) \-\> void:  
	if achievement\_id in unlocked\_achievements and not achievement\_id in claimed\_rewards:  
		if achievement\_db.has(achievement\_id):  
			var data: AchievementData \= achievement\_db\[achievement\_id\]  
			GameManager.skill\_points \+= data.reward\_sp  
			GameManager.add\_money(data.reward\_money, false, "Thưởng thành tựu: " \+ data.title)  
			claimed\_rewards.append(achievement\_id)  
			SignalBus.reward\_claimed.emit(achievement\_id)

func unlock\_ending(ending\_id: String) \-\> void:  
	if not ending\_id in unlocked\_endings:  
		unlocked\_endings.append(ending\_id)  
		SignalBus.ending\_discovered.emit(ending\_id)  
		SaveManager.save\_global\_profile(unlocked\_achievements, unlocked\_endings)

**5\. VÍ DỤ MINH HỌA QUY TRÌNH KẾT NỐI UI VỚI CORE API**  
**Kịch bản: Màn hình Cây Kỹ Năng (SkillTreeUI.gd)**  
\# res://scenes/ui/SkillTreeUI.gd  
extends Control

@export var current\_skill: SkillData  
@onready var btn\_upgrade: Button \= \$MarginContainer/VBoxContainer/BtnUpgrade  
@onready var lbl\_sp: Label \= \$MarginContainer/VBoxContainer/LblSP

func \_ready() \-\> void:  
	\# Kết nối tín hiệu tự động cập nhật UI khi chỉ số SP thay đổi  
	SignalBus.sp\_changed.connect(\_on\_sp\_changed)  
	SignalBus.skill\_level\_up.connect(\_on\_skill\_level\_up)  
	\_update\_ui()

func \_on\_sp\_changed(\_new\_sp: int) \-\> void:  
	\_update\_ui()

func \_on\_skill\_level\_up(skill\_id: String, \_new\_level: int) \-\> void:  
	if skill\_id \== current\_skill.skill\_id:  
		\_update\_ui()

func \_update\_ui() \-\> void:  
	lbl\_sp.text \= "Điểm SP hiện có: " \+ str(GameManager.skill\_points)  
	btn\_upgrade.text \= "Nâng cấp (" \+ str(current\_skill.sp\_cost) \+ " SP)"  
	btn\_upgrade.disabled \= (GameManager.skill\_points \< current\_skill.sp\_cost)

func \_on\_btn\_upgrade\_pressed() \-\> void:  
	\# Gọi API trung tâm thay vì tự xử lý logic  
	var success \= SkillManager.try\_upgrade\_skill(current\_skill.skill\_id)  
	if not success:  
		print("Nâng cấp thất bại\! Kiểm tra lại điều kiện SP, Tiền hoặc Thể lực.")  
