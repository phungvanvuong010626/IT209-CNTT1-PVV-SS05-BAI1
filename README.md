Bài 1: Khôi phục commit đã mất bằng Git Reflog

1. Mục tiêu

Thực hành sử dụng Git Reflog để tìm và khôi phục một commit đã bị mất sau khi sử dụng git reset --hard.

2. Tạo repository

Khởi tạo repository bằng lệnh:

git init

Tạo file feature.txt với nội dung:

Day la tinh nang quan trong

Sau đó commit:

git add feature.txt
git commit -m "Them tinh nang quan trong"

3. Giả lập mất commit

Thực hiện:

git reset --hard HEAD~1

Sau khi reset, commit Them tinh nang quan trong không còn xuất hiện trong:

git log --oneline

4. Tìm commit bằng Reflog

Sử dụng:

git reflog

Tìm dòng commit:

HEAD@{1}: commit: Them tinh nang quan trong

Lấy mã hash của commit này.

Ví dụ:

e3a5b2c

5. Khôi phục commit

Thực hiện:

git reset --hard e3a5b2c

Trong đó e3a5b2c là mã hash thực tế lấy được từ git reflog.

6. Kiểm tra kết quả

Kiểm tra lịch sử:

git log --oneline

Commit:

Them tinh nang quan trong

đã xuất hiện trở lại.

Kiểm tra nội dung file:

cat feature.txt

Kết quả:

Day la tinh nang quan trong

7. Kết luận

Đã sử dụng thành công git reflog để tìm mã hash của commit bị mất và khôi phục commit bằng git reset --hard.
