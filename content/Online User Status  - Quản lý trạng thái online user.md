#tic_tac_toe_project 

## Các trạng thái của người dùng onine
`idle`, `waiting for invitation`, `invited`, `in game`, `invitation rejected`, `invited but no respond`, `invitaion timeout`, `opponent quitted`

## Kịch bản mời người chơi khác
**Chú thích:** trạng thái của người chơi được đặt trong `code inline block`
**Nhận xét**: Trạng thái người dùng sẽ trở về `idle` khi ở [[Online Home Page]], tạo thành một vòng lặp.
- Giả sử, người chơi 1 (`idle`) ở **Máy 1** mời người chơi 2 (`idle`) ở **Máy 2**. Cả hai người chơi đều đang ở **Online Home Page**. Hành động: Người chơi 1 nhấn vào người chơi 2.
- Người chơi 1 (`waiting for invitaion`) chờ người chơi 2 (`invited`) đồng ý để bắt đầu ván chơi. **Máy 1** hiện ra [[Challenge Dialog]]. **Máy 2** hiện ra [[Invited Dialog]]. [Challenge Dialog](Challenge%20Dialog.md) 
	- Người chơi 2 nhấn nút accept để bắt đầu ván cờ => Người chơi 1 và 2 (`in game`). **Máy 1** và **Máy 2** chuyển đến [[Online Game Page]] và ván cờ bắt đầu, bắt đầu từ người chơi 1. *P/S: Trường hợp 1 là thường là trường hợp thành công.*
	- Người chơi 2 từ chối lời mời => Người chơi 2 (`idle`), người chơi 1 (`invitation rejected` → `idle`). Người chơi 2 nhấn vào nút Reject, hộp thoại biến mất. **Máy 1** hiển thị [[Opponent Reject Dialog]].
	- Người chơi 2 vì đang bận làm việc gì khác, nên không phản hồi lời mời. Sau thời gian timout (khoảng 15s) người chơi 1 sẽ hủy lời mời => Người chơi 2 (`invited but no respond` → `idle`), người chơi 1 (`invitation timeout` → `idle`). 

## Kịch bản khi 2 người chơi đã vào ván chơi
- Người chơi 1 (`in game`) và người chơi 2 (`in game`) đã vào ván chơi. 
	- Hai người cùng nhau chơi hết ván
	- Giả sử người chơi 1 nhấn nút back để thoát game giữa chừng, hiển thị hộp thoại để xác nhận việc thoát game => Người chơi 1 (`idle`), người chơi 2 (`opponent quitted`). Người chơi 2 nhận được một hộp thoại thông báo, nhấn nút quit để thoát game => Người chơi 2 (`idle`)