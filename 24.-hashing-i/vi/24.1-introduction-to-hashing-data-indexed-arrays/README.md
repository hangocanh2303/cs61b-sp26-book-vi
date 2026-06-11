# 24.1 Giới thiệu về băm: Mảng đánh chỉ mục bằng dữ liệu

Cho tới giờ trong khóa học, ta đã xem xét nhiều cách để lưu trữ trong các cấu trúc dữ liệu, nhưng chúng không phải lúc nào cũng hiệu quả nhất về thời gian chạy. Giới thiệu một cấu trúc dữ liệu tuyệt vời có thể cung cấp thao tác chèn, xóa và kiểm tra tồn tại — bất kể có bao nhiêu phần tử bên trong (kể cả hàng triệu) — tất cả trong thời gian O(1) trong trường hợp tốt nhất! Nghe quá tốt để có thật?&#x20;

Ta sẽ khám phá sự kỳ diệu của băm (hashing) trong chương này để xem điều đó khả thi như thế nào.

### Ôn nhanh các cấu trúc dữ liệu đã học

Ta đã xem xét một số cấu trúc dữ liệu tìm kiếm hiệu quả sự tồn tại của phần tử bên trong nó. Ta đã học cây tìm kiếm nhị phân, rồi làm cho chúng cân bằng bằng cây 2-3.

Tuy nhiên, những cấu trúc này có một số hạn chế (đúng, kể cả cây 2-3!):

1. Chúng yêu cầu các phần tử phải so sánh được. Làm sao ta quyết định phần tử mới đặt ở đâu trong BST? Ta phải trả lời câu hỏi "bạn nhỏ hơn hay lớn hơn gốc?" Với một số đối tượng, câu hỏi này có thể vô nghĩa.
2. Chúng cho độ phức tạp $\Theta(\log N)$. Có tốt không? Tuyệt đối. Nhưng có lẽ ta có thể làm tốt hơn.

### Dùng dữ liệu làm chỉ mục

Mảng có thời gian chạy tuyệt vời cho các thao tác cơ bản. Có cách nào tốt để chuyển dữ liệu thành chỉ mục và lưu chúng trong mảng không? Trong vài tiểu mục tiếp theo, ta sẽ đi qua các bước cuối cùng dẫn tới phát minh cuối cùng — bảng băm. Xem các video được liên kết trong các tiểu mục sẽ giúp hiểu quá trình ta đi đến phát minh bảng băm. Bảng băm sẽ là trọng tâm chính cho phần còn lại của chương.&#x20;
