Bài 3: Xử lý xung đột phức tạp trong quá trình Rebase
Mục tiêu
• Hiểu được sự khác biệt giữa giải quyết xung đột khi Merge và khi Rebase.
• Áp dụng quy trình giải quyết xung đột từng bước (step-by-step conflict resolution) trong Rebase.
• Đưa lịch sử nhánh tính năng lên trên đầu nhánh chính một cách thẳng hàng.
Yêu cầu
• Bối cảnh: Nhánh main đã có thêm 2 commit mới từ các thành viên khác sửa đổi tệp tin cấu hình config.json. Nhánh feature-api của học viên cũng sửa đổi cùng các dòng trong tệp tin đó qua 2 commit khác nhau. Khi học viên rebase nhánh feature-api lên main, xung đột sẽ xảy ra ở từng commit trong tiến trình rebase.
• Ràng buộc: Học viên phải giải quyết xung đột thủ công ở từng chặng, không được dùng merge thông thường và không được phá hỏng code của nhánh chính.
Kiểm tra
• Lệnh kiểm tra:
• Kiểm tra trạng thái rebase:
git status
• Kiểm tra lịch sử sau khi hoàn thành:
git log --graph --oneline
• Kết quả mong đợi:
• Lịch sử Git thẳng tắp, không có merge commit phụ. Các commit của nhánh feature-api nằm nối tiếp ngay sau các commit mới nhất của main.
Hướng dẫn nộp bài
• Đường dẫn trên GitHub: homework/session_05/ex3/
• Cơ chế nộp: Học viên nộp tệp báo cáo README.md chi tiết các lần phát sinh conflict trong quá trình rebase và cách giải quyết cho từng chặng, kèm ảnh chụp git log --graph --oneline sau cùng.
Gợi ý/Bệ đỡ

1. Đứng ở main, tạo file config.json với nội dung ban đầu:
   {
   "port": 8080,
   "debug": false
   }
   Commit:
   git add config.json && git commit -m “init config”.
2. Tạo nhánh feature-api từ main: git checkout -b feature-api.
3. Ở nhánh feature-api, sửa "port": 9000 rồi commit feat: change port. Tiếp tục sửa tiếp "debug": true rồi commit feat: enable debug.
4. Quay lại main: git checkout main. Sửa "port": 8081 rồi commit update port on main. Sửa tiếp "env": "production" rồi commit add env config.
5. Quay lại feature-api: git checkout feature-api. Tiến hành rebase lên main:
   git rebase main
6. Khi gặp conflict lần 1 ở file config.json, mở file ra sửa thủ công phần port, lưu lại, chạy git add config.json rồi tiếp tục:
   git rebase --continue
7. Lặp lại việc sửa conflict lần 2 nếu có cho commit tiếp theo cho đến khi rebase hoàn tất.
