---
layout: post
title: Sessions là gì? Và Rails làm nó như thế nào?
tag: [rails, ruby]
---

### Sessions là gì? Tại sao ứng dụng web cần nó?

Nhiều ứng dụng web muốn lưu trữ thông tin trạng thái của người dùng theo thời gian. Ví dụ như thông tin giỏ hàng, hay thông tin chứng thực. Vì HTTP không làm đưọc điều đó nên chúng ta cần sessions. Nếu không có sessions, người dùng có thể cần phải chứng thực ở mọi request. Điều này thật sự khó chịu và không tiện nghi. Vậy sessions chỉ là 1 nơi lưu trữ thông tin của người dùng để có thể dùng chúng ở những request tiếp theo trong tương lai.

### Sessions được xây dựng thế nào?

Mỗi khi có 1 user mới truy cập thì server sẽ cấp cho nó 1 session id. Id này đưọc gửi xuống client trong response trả về và lưu trong cookies của browser. Khi gửi yêu cầu tới server, browser của client sẽ gửi cookies có kém session_id trong đó nên server sẽ biết đc đây là request của user nào. Nếu không có session Id thì đó là 1 request của 1 user mới.

Session Id tùy theo mỗi framework hay ứng dụng sẽ được build khác nhau. Ví dụ Rails thì nó là MD5 hash long value của 1 string. String này là thời gian hiện tại (lúc khởi tạo), số random từ 0 tới 1, process id của trình thông dịch ruby (thực chất cũng là 1 số ngẫu nhiên) and một chuỗi cố định.

### Sessions Store ở Rails

Mặc định Rails dùng cookies để lưu trữ thông tin sessions (CookieSstore). CookieStrore lưu trữ sessions hash trực tiếp ở trong cookie của client. Server lấy thông tin sessions từ cookie của request gửi lên. Cách làm này làm tăng tốc độ của ứng dụng nhưng cũng có 2 điểm cần lưu ý:

* Giới hạn lưu trữ 4kb của cookies.

* Client có thể thấy cookies nên không nên lưu trữ những thông tin nhạy cảm trong sesions hoặc phải mã hóa thông tin. Hiện nay, Rails dùng secret key base để mã hóa sessions trước khi gửi xuống lưu trữ trong cookies. Điều này ngăn user truy cập hay giả mạo sessions của người khác. Điều này có nghĩa mức độ an toàn của CookieStore phụ thuộc vào secret key base và thuật toán mã hóa (mặc định là SHA1).

Ngoài ra Rails còn hỗ trợ Database Store, Memcache Store hoặc tự xây store của riêng bạn.
