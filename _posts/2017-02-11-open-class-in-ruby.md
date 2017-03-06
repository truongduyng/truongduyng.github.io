---
published: true
title: Open class in Ruby
layout: post
tags: ruby
---

Trong ruby, không có sự khác biệt thực sự giữa code định nghĩa lớp và code của bất cứ loại nào khác.

Nếu một lớp đã tồn lại, Ruby không định nghĩa nó lần nữa mà chỉ mở lớp này ra thêm các các methods mới vào. Có vẻ trong Ruby, chữ `class` giống một scope operator hơn là để khai báo lớp. Ví dụ:

{% highlight ruby %}
class OneClass
  def x
    "x"
  end
end

class OneClass
  def y
    "y"
  end
end

obj = OneClass.new
obj.x # => "x"
obj.y # => "y"
{% endhighlight %}

Ở đây chúng ta có thể dùng kỹ thuật này (Open Class) để mở các lớp có sẵn, thậm chí là các lớp của Ruby, để chỉnh sửa. Kỹ thuật này giúp chúng ta có thể thêm thắt, viết lại cái hàm của lớp đã được định nghĩa trong thư viện (monkey patching). Mặt trái của nó là khi chúng ta chỉnh sửa hành vi các phương thức của thư viện chuẩn sẽ làm phần mềm khó test và kiểm soát. Nhiều khi khiến phần mềm chạy lỗi hoàn toàn.

Có một số người khó tính thưòng hoàn toàn không khuyến khích các lập trình viên sử dụng kỹ thuật này. Nếu muốn làm việc gì đó, hãy tự viết hàm hay lớp cho nó.
