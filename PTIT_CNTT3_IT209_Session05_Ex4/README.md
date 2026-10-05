Bài 4: Mô phỏng quy trình Hotfix & Gitflow thực tế
Mục tiêu
•	Áp dụng mô hình phân nhánh Gitflow chuẩn trong quản lý vòng đời phần mềm.
•	Thực hành tạo, kiểm thử và tích hợp nhánh Hotfix trực tiếp vào hệ thống đang chạy.
•	Đồng bộ hóa bản vá nóng về nhánh phát triển (develop) để tránh trôi lỗi.
Yêu cầu
•	Bối cảnh: Hệ thống đang chạy trên nhánh main (phiên bản stable v1.0.0) gặp lỗi nghiêm trọng lộ dữ liệu người dùng. Nhánh develop đang phát triển dở dang các tính năng mới cho phiên bản tương lai và không thể deploy ngay được.
•	Ràng buộc:
•	Tạo nhánh sửa lỗi khẩn cấp hotfix/v1.0.1 tách ra trực tiếp từ main.
•	Sau khi sửa lỗi xong, gộp nhánh hotfix này vào main, tạo tag phiên bản v1.0.1 để chuẩn bị release.
•	Bắt buộc phải gộp ngược lại nhánh hotfix này vào nhánh develop để đảm bảo code phát triển tương lai cũng được sửa lỗi này.
Kiểm tra
•	Lệnh kiểm tra:
•	Kiểm tra các nhánh hiện có và danh sách tag:
git branch -a
git tag
•	Kiểm tra sơ đồ lịch sử gộp nhánh:
git log --graph --oneline --all
•	Kết quả mong đợi:
•	Có tag v1.0.1 chỉ vào commit mới trên nhánh main. Lịch sử nhánh develop chứa commit sửa lỗi từ hotfix.
Hướng dẫn nộp bài
•	Đường dẫn trên GitHub: homework/session_05/ex4/
•	Cơ chế nộp: Học viên nộp tệp báo cáo README.md giải thích sơ đồ phân nhánh Gitflow đã sử dụng và vẽ lại sơ đồ merge bằng ASCII hoặc ảnh chụp màn hình đồ thị commit của repository.
Gợi ý/Bệ đỡ
1.	Giả sử nhánh main giữ code production ổn định; nhánh develop giữ code đang phát triển. Khi cần sửa lỗi gấp, tách nhánh hotfix/ từ main.
2.	Sau khi fix xong trên hotfix/v1.0.1, chuyển về main: git checkout main -> git merge hotfix/v1.0.1 -> git tag -a v1.0.1 -m "Release Hotfix 1.0.1".
3.	Cuối cùng, chuyển về develop: git checkout develop -> git merge hotfix/v1.0.1. Xóa nhánh hotfix cục bộ sau khi hoàn tất để dọn dẹp.

