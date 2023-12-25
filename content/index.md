---
title: Tic-tac-toe Project Document
---

## Related
- [Hiển thị danh sách những người chơi online khác](Hiển%20thị%20danh%20sách%20những%20người%20chơi%20online%20khác.md) 
- [Online User Status  - Quản lý trạng thái online user](Online%20User%20Status%20%20-%20Quản%20lý%20trạng%20thái%20online%20user.md) 
## Tìm kiếm
- [Ultimate tic-tac-toe - Wikipedia](https://en.wikipedia.org/wiki/Ultimate_tic-tac-toe) 
- [Trò chuyện với Google Bard](https://bard.google.com/chat/989f88e831db1649) 
- [Trò chuyện với ChatGPT](https://chat.openai.com/c/e28e4903-c369-4ad2-b56a-1caa72bfc2c4) 
- [Trò chuyện với Bing AI](https://www.bing.com/search?q=Bing+AI&showconv=1&FORM=undexpand) 
## Giới thiệu
Game Tic-tac-toe trên điện thoại Android cho phép 2 người chơi có thể chơi với nhau qua mạng LAN và mạng Internet theo luật chơi thông thường. 
[Demo](https://youtube.com/playlist?list=PLXVGUaJGNn95T5Lhll8nLXQkx8Q6Bgh-b&si=Wodqvb1-lppvJTww) 
### Luật chơi
Trò chơi gồm có hai người chơi. Một người chọn X và người còn lại chọn O . Hai người chơi luân phiên đánh X hoặc O lên bàn cờ, trong đó X được đánh trước. Nếu người chơi nào tạo được một đường thẳng hoặc một đường chéo 5 ô liền nhau trước thì sẽ giành chiến thắng.
Kết quả: Một người chơi giành chiến thắng, hoặc không có người chơi nào thắng do giới hạn của bàn cờ. Người chơi giành chiến thắng sẽ được cộng 1 điểm.
### Ngữ cảnh thông thường
1. Người chơi mở ứng dụng
2. **Home Screen** hiện ra
3. Người chơi nhấn vào **nút "+"** để tạo phòng mới
4. **New Room Dialog** hiện ra
5. Người chơi nhập thông tin phòng mới (tên người chơi 1, tên người chơi 2, số hàng và số cột của bàn cờ) và nhấn **nút Create room**
6. Chuyển đến **Game Screen**
7. Người chơi nhấn vào 1 ô -> ô đó được đánh X (người chơi 1) hoặc O (người chơi thứ 2). Theo mặc định, người chơi 1 đánh trước
8. Quét toàn bộ bàn cờ để kiểm tra người chiến thắng
	- Nếu phát hiện một người chơi giành chiến thắng, chuyển đến **bước 10**
		- Người chơi nhấn vào **nút Back**, chuyển đến **Home Screen (bước 2**)
9. Chuyển đến **bước 7**
10. Hiển thị **Winner Page** (lớp phủ), cập nhật điểm số, hiển thị **nút Next round**
11. Người chơi nhấn vào màn hình
12. Chuyển về **Game Page**
	- a. Người chơi nhấn vào **nút Next round**, chuyển đến **bước 6**
	- b. Người chơi nhấn vào **nút Back**, chuyển đến **Home Screen (bước 2**) 
13. Bàn cờ được reset (trở thành bàn cờ trắng), **nút Next round** biến mất
14. Chuyển đến **Game Screen (bước 6**) 

## UI
Design in [Figma](https://www.figma.com/file/qSo9fWz4WZj3gwyK8r35yk/Flutter-Tic-tac-toe-Game?type=design&node-id=0%3A1&mode=design&t=JNfjbzPTqdXng7bt-1) 
### Home Screen
Đây là màn hình đầu tiên xuất hiện khi người dùng lần đầu mở ứng dụng. **Home Screen** gồm có:
- **Room List:** Danh sách các phòng đã tạo, có thể nhấn vào một phòng để chơi tiếp ván cờ trong phòng đó.
- **Nút** + để tạo phòng mới
- **Nút Menu** để mở Drawer với các tùy chọn khác như cài đặt, chơi online, theme,…

![](https://i.imgur.com/GzwkyA9.png)
### Create Room Screen
Khi nhấn vào **nút +** thì chuyển sang **Create Room Screen** để nhập thông tin tạo phòng chơi mới. **Create Room Screen** gồm có:
- **Room Input Field:** tên phòng, là một chuỗi ký tự có độ dài từ 0 đến 30 ký tự. Nếu trường này để trống thì tên mặc định là "Untitled Room".
- **Player 1 Input Field:** tên người chơi 1 (X), là một chuỗi từ 0 đến 50 ký tự. Nếu trường này để trống, thì tên mặc định là "Player 1".
- **Player 2 Input Field:** tên người chơi 2 (O), là một chuỗi từ 0 đến 50 ký tự. Nếu trường này để trống, thì tên mặc định là "Player 2". 
- **Rows Input Field:** số hàng của bàn cờ. Một bảng có thể có từ 5 đến 18 hàng. Dùng bàn phím kiểu số để nhập. Giá tri mặc định là 10.
- **Columns Input Field:** số cột của bàn cờ. Một bảng có thể có từ 5 đến 12 hàng. Dùng bàn phím kiểu số để nhập. Giá trị mặc định là 10.
- **Nút Create Room:** validate Text Form Field, nếu input hợp lệ thì chuyển sang Game Page.
### Game Screen
Người chơi có thể chơi cờ bằng cách nhấn vào các ô trong Game Screen.
Có thể truy cập vào Game Screen qua 2 cách:
- Khi người dùng nhập thông tin trong **Create Room Screen** và nhấn vào nút **Create Room**, **Game Screen** hiện ra với một bàn cờ mới.
- Khi nhấn vào một phòng trong **Room List**, màn hình chuyển qua **Game Screen** để chơi tiếp ván cờ trong phòng đó.
![](https://i.imgur.com/3xV55IH.png)
**Game Screen** gồm có các thành phần sau:
- Nhấn **nút Back** trên App Bar hoặc thanh điều hướng để trở về **Home Screen**.
- Nhấn **nút History** trên App Bar để xem lại lịch sử các ván chơi trong phòng hiện tại, chuyển đến **Replay Screen**.
- Hai người chơi luân phiên nhấn vào từng ô để đánh X hoặc O. Người chơi 1 (X) đánh trước.
- Mỗi lần người chơi đánh vào một ô
	- 1. Cập nhật turn tiếp theo
	- 2. Quét toàn bộ bàn cờ để kiểm tra người chơi thắng cuộc.
		- Nếu phát hiện người thắng cuộc
			- 1. Cập nhật điểm số trên **Player Bottom Bar**.
			- 2. Hiển thị **Winner Screen** thông báo người chơi thắng cuộc, nhấn vào màn hình để quay lại **Game Screen**
			- 3. Hiển thị **nút Next Round** trên App Bar để reset bàn cờ và chuyển sang ván mới
- **Player Bottom Bar**
	- Ô màu nâu: lượt của người chơi hiện tại. Ví dụ: Đến lượt của của Player 1, ô Player 1 có nền màu nâu.
	- Ô màu xám: lượt của người chơi tiếp theo
### History Screen
![](https://i.imgur.com/6ibaUcB.jpg)


## Tính năng xem lại lịch sử ván chơi
Yêu cầu:
- Trong **History Details Screen**, khi một người chơi giành chiến thắng, thì **Player Bottom Bar** dừng lại ở người chơi thắng cuộc. Đến lượt phát hiện người chơi thắng cuộc, giữ nguyên số lượt và người chơi hiện tại.
- 
## Nháp
### Kiến trúc và công nghệ
- Flutter và Dart
- GetX: Route Manager, State Manager
## Tính năng mới

## Authentication và Cloud Storage
Đoạn chat với Claude AI: https://claude.ai/chat/0f3e28b1-708b-4590-9c87-ca05105d322c
### Firebase (unused)
- Project: Tic-tac-toe
- Tài khoản: thang258782001@gmail.com 
- SHA1: 41:5E:E9:07:24:21:1B:03:AD:FB:43:4B:EC:05:79:4A:8E:73:1C:3E 
### Google
Tutorial:
- [Flutter Tutorial - Google SignIn WITHOUT Firebase - Android, iOS, Flutter Web - YouTube](https://www.youtube.com/watch?v=E5WgU6ERZzA)
### Facebook
Tutorial:
- [Flutter : Facebook login using Firebase authentication | amplifyabhi - YouTube](https://www.youtube.com/watch?v=7EQZl2GyvVw) 
- [Flutter Facebook Login | Android & iOS - YouTube](https://www.youtube.com/watch?v=Hj0csDW6WUs) 
### Mongo DB
User:
thang5878
thang123
## Tham khảo 
- [Multi Player TicTacToe Game App using Flutter, Node, Express and Socket - Full Stack Development - YouTube](https://www.youtube.com/watch?v=Aut-wfXacXg) 
- https://www3.ntu.edu.sg/home/ehchua/programming/java/JavaGame_TicTacToe.html 
- [Lập trình game Caro với C# Winform - YouTube Playlist](https://www.youtube.com/playlist?list=PL33lvabfss1yCEzvLavt8jD4daqpejzwN) 
- [Drift (Moor) database for Flutter, an overview | by Mustafa Tahir | Medium](https://medium0.com/@mustafatahirhussein/drift-moor-database-for-flutter-an-overview-f17ff8548d85) 
## Vấn đề
Save game khi nào?
- Tạo room mới (done)
- Khi một người chơi giành chiến thắng
- Từ Game Screen quay trở về Home Screen (done)
- Nhấn nút reset (done)

History Details Screen xử lý như thế nào?
- Truyền room id và round number từ round card đên History Details Screen, hiển thị bàn cờ trắng.
- History Details Screen có thông tin của cả 1 room
- Lần lượt duyệt các phần tử trong list turns (Round). Mỗi lần duyệt đến một turn, hiển thị ô đó trên bàn cờ.

History Detail Screen cần thêm những thuộc tính gì?
- History Detail Screen cần có những thuộc tính tách biệt hẳn so với Game Screen. Các thuộc tính này ở trong lớp room.
- Thuộc tính cần thêm
	- historyCurrentRoundIndex
	- historyCurrentTurnIndex
	- 
## Chức năng đăng nhập và lưu thông tin người dùng trên Firebase
- Bước 1: Hiển thị các người chơi trong Firebase trên màn hình
- Bước 2: Hiển thị các người chơi **online** trong Firebase trên màn hình
## Chức năng 2 người chơi online
### Kịch bản thách đấu người chơi khác
*Chú thích: Trạng thái của người chơi được highlight màu vàng*
- Người chơi 1 đăng nhập vào app => chuyển đến **Welcome Page** ==idle==.
- Người chơi 1 nhấn **nút Back** => Xóa tất cả trang trước đó, chuyển đến **Online Home Page**.
- Trên **Online Home Page** hiển thị danh sách những người chơi online khác
- Người chơi 1 chọn một người chơi bất kỳ (người chơi 2 ==idle==) trong danh sách những người chơi online khác
	- Người chơi 1 hiển thị **Challenge Dialog**, nhấn vào **nút Challenge** để hiển thị **Waiting Dialog** ==waiting==, chờ người chơi 2 đồng ý vào ván cờ => `update opponent`
	- Người chơi 2 hiển thị **Accept Challenge Dialog** ==invited== => `update opponent`
- Nếu người chơi 2 không nhận lời thách đấu, nhấn **nút Cancel** và hộp thoại biến mất ==idle== => `remove opponent`. Người chơi 1 hiển thị **Opponent Refuse Dialog** ==refused==, thông báo người chơi 2 không chấp nhận thách đấu. => `remove opponent`
- Nếu người chơi 2 không có phản hồi, hết thời gian timeout 
	- Người chơi 1 hiển thị **Timeout Dialog**  ==invite timeout==. Nhấn **nút OK** để xóa bỏ hộp thoại ==idle==. => `remove opponent`
	- Người chơi 2 xóa bỏ hộp thoại ==idle==. => `remove opponent`
- Nếu người chơi 2 đồng ý thách đấu với người chơi 1, nhấn **nút Accept**, cả hai người chơi chuyển đến **Online Game Screen** và bắt đầu vào ván cờ ==in game==. 



