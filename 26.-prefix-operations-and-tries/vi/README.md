---
description: 'Tác giả: Thomas Lee'
---

# 26. Thao Tác Tiền Tố và Trie

### Bài Toán Tìm Kiếm

Để dẫn dắt vào phần tiếp theo, hãy xét **bài toán tìm kiếm** (search problem). Trong bài toán này, ta nhận được một luồng dữ liệu, và mục tiêu là truy xuất thông tin mà ta quan tâm. Ví dụ, một trang web cho phép người dùng đăng nội dung lên trang cá nhân có thể muốn chỉ hiển thị nội dung đó cho bạn bè. Một ví dụ khác là nếu một đài tin tức nhận log từ hàng nghìn trạm thời tiết, và nó muốn hiển thị bản đồ thời tiết cho một ngày và giờ cụ thể.

Cả hai đều là ví dụ của bài toán tìm kiếm, chỉ khác nhau về dạng thức! Các cấu trúc dữ liệu mà ta đã xây dựng từ trước đến nay đều nhằm giải quyết bài toán tìm kiếm cho các miền quan tâm khác nhau.

Hãy ôn lại các cấu trúc dữ liệu mà ta đã gặp:

<table><thead><tr><th width="101">Tên</th><th width="222">Thao tác lưu trữ</th><th width="241">Thao tác truy xuất chính</th><th>Truy xuất theo</th></tr></thead><tbody><tr><td>List</td><td><code>add(key)</code>, <code>insert(key, index)</code></td><td><code>get(index)</code></td><td>chỉ số</td></tr><tr><td>Map</td><td><code>put(key, value)</code></td><td><code>get(key)</code></td><td>định danh khóa</td></tr><tr><td>Set</td><td><code>add(key)</code></td><td><code>containsKey(key)</code></td><td>định danh khóa</td></tr><tr><td>Priority Queue</td><td><code>add(key)</code></td><td><code>getSmallest()</code></td><td>thứ tự khóa (nhỏ đến lớn)</td></tr><tr><td>Disjoint Sets</td><td><code>connect(int_a, int_b)</code></td><td><code>isConnected(int_a, int_b)</code></td><td>hai giá trị nguyên</td></tr></tbody></table>

Tất cả các cấu trúc dữ liệu này đều được dùng để giải quyết các trường hợp khác nhau của bài toán tìm kiếm. Chúng đều có ứng dụng riêng tùy thuộc vào cách dữ liệu quan tâm cần được truy xuất.\
Một điều quan trọng cần lưu ý là đây đều là các **kiểu dữ liệu trừu tượng** (ADT — Abstract Data Type), nghĩa là ta định nghĩa hành vi của cấu trúc dữ liệu, chứ không phải cách cài đặt. Có nhiều cách cài đặt khả thi cho mỗi cấu trúc dữ liệu, và ta thậm chí có thể dùng một cấu trúc dữ liệu trong cách cài đặt của cấu trúc khác! Ta thường sử dụng các ADT này để tạo ra các cấu trúc dữ liệu phức tạp hơn.

### Trừu Tượng Hóa

Trừu tượng hóa (Abstraction) là ý tưởng chỉ quan tâm đến hành vi của một thứ gì đó mà không quan tâm đến cách cài đặt bên dưới. Khái niệm này không xa lạ như bạn nghĩ! Ta áp dụng nguyên lý trừu tượng hóa trong cuộc sống hàng ngày mà không hề nhận ra. Ví dụ, sử dụng bàn phím có thể coi là một sự trừu tượng hóa của việc viết văn bản lên máy tính. Có thể có nhiều cách cài đặt mạch điện bàn phím tùy thuộc vào công ty sản xuất, nhưng ta không lo lắng về những gì xảy ra bên trong, ta chỉ quan tâm rằng nó cho phép ta gõ văn bản lên máy tính.

Trừu tượng hóa thường được áp dụng theo nhiều _tầng_ khi tạo cấu trúc dữ liệu.

Khi cài đặt Priority Queue, ta có thể chọn sử dụng Heap Ordered Tree để lưu trữ các phần tử của priority queue. Ta không lo lắng về cách cài đặt của Heap Ordered Tree — ta chỉ quan tâm đến các phương thức mà Heap Ordered Tree cung cấp.

Tương tự, Heap Ordered Tree không quan tâm đến cách cài đặt của cấu trúc dữ liệu Tree mà nó sử dụng bên dưới.

Cuối cùng, bất kỳ ai sử dụng Priority Queue mà ta tạo ra cũng không quan tâm đến cách ta xây dựng nó. Họ chỉ quan tâm rằng Priority Queue của ta có thể hỗ trợ việc thêm phần tử và trả về phần tử nhỏ nhất một cách hiệu quả.

Tóm lại, ta thường có thể nghĩ về một ADT bằng cách sử dụng một ADT khác. Các ADT có nhiều tầng trừu tượng hóa, mỗi tầng định nghĩa hành vi cụ thể hơn so với ý tưởng trước đó.
