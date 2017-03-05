---
layout: post
title: 3 common security issues in Rails
tag: rails
---

* ### SQL injection

  Đây là kiểu tấn công gây ảnh hưởng lên câu truy vấn dữ liệu thông qua các tham số của ứng dụng web. Thường thì chúng được dùng để vượt qua bước chứng thực hay để đánh cắp dữ liệu. Ví dụ bạn muốn tìm những project có tên được lấy từ tham số name:

  `Project.where("name = '#{params[:name]}'")`

  Tham số này có thể là `'OR 1 --`. Kết quả câu truy vấn là:

  `SELECT * FROM projects WHERE name = '' OR 1 --'`(trả về là tất cả projects).

  Hay nếu tham số là

  `') UNION SELECT id,login AS name,password AS description,1,1,1 FROM users --`

  thì câu truy vấn dữ liệu là:

  `SELECT * FROM projects WHERE (name = '') UNION SELECT id,login AS name,password AS description,1,1,1 FROM users --'` (lấy name và password của tất cả users).

  ##### Cách phòng chống:

  Ruby on Rails đã xây dựng 1 filter để lọc các ký tự đặc biệt trong SQL: `'`, `"`, `null` và xuống dòng. Filter này được dùng tự động cho câu lệnh `find` hay `find_by_something`. Với các câu lệnh có dùng sql, thì thay vì đưa vào 1 string, ta đưa vào 1 dãy hay hash tham số đã được xử lý. Ví dụ như sau:

  `Model.where("login = ? AND password = ?", entered_user_name, entered_password)` hoặc `Model.where(login: entered_user_name, password: entered_password)`

  Dãy hay hash tham số chỉ có thể dùng cho đối tượng thuộc lớp model. Dùng `sanitize_sql()` ở chỗ khác.

* ### Cross-site scripting (XSS)

  Kẻ tấn công nhập vài đoạn code giả mạo. Ứng dụng web lưu nó lại và hiện thị cho nạn nhân. Đó là cách XSS hoạt động. XSS có thể đánh cắp cookie, session, hiện thị nội dung quảng cáo có lợi cho kẻ tấn công, chuyển nạn nhận về trang web giả mạo hay lấy thông tin bí mật hay cài đặt phần mềm giả mạo thông qua lỗ hỗng của ứng dụng web.

  Đoạn mã giả đi từ user input. Chúng có thể là Html/Javascript Injection.

  ##### Cách chống:
  1. Dùng hàm `sanitize()` để filter user input.
  2. Dùng hàm `escapeHTML()` hay tên rút gọn h() để thay thế các ký tự nhập vào `&, ", <, > bằng dạng hiện thị của chúng (&amp;, &quot;, &lt;, and &gt;). Dùng gem `SafeErb` để nhắc nhở.

    {% highlight ruby %}
      tags = %w(a acronym b strong i em li ul ol h1 h2 h3 h4 h5 h6 \
      blockquote br cite sub sup ins p)
      s = sanitize(user_input, tags: tags, attributes: %w(href title))
    {% endhighlight %}


* ### Cross-Site Request Forgery (CSRF)
  Đây là kiểu tấn công bằng cách chèn một đoạn code giả mạo có thể truy cập vào một ứng dụng web mà người dùng đã chứng thực trước đó. Nếu người dùng chưa đăng xuất hay session chưa hết hạn thì kẻ tấn công có thể thực thi những lệnh chưa được chứng thực.

  Ví dụ bạn đăng nhập vào web A (weba.com). Session thông tin chứng thực của bạn ở web A được lưu lại và chưa hết hạn. Xong rồi bạn truy cập web B. Thí dụ trong web B có 1 link hay hình ảnh có url là: `http://weba.com/user/1/destroy`, thì mặc định bạn đang thực hiện 1 yêu cầu có phương thức là GET tới web A kèm thèm session chứng thực trước đó đã có. Lúc này vô tình bạn đã xóa user có id=1 ở web A trong lúc truy cập web B mà bạn không hề hay biết.

  ##### Cách chống:
  1. Dùng theo CRUD. Tức là không bao giờ dùng phương thức GET cho các lệnh kiểu sửa đổi thông tin hay xóa đối tượng. GET chỉ được dùng để lấy thông tin.
  2. Bật chức năng `protect_from_forgery with: :exception` và chèn `<%= csrf_meta_tags %>` vào application view trong Rails lên. Khi bật lên, Rails sẽ tự động thêm 1 token cho tất cả các form hay lệnh ajax. Token lấy từ header mình đã chèn và nó được dùng để xác thực là lệnh này được thực hiện từ chính ứng dụng của mình. Nếu sai thì quăng exception.
