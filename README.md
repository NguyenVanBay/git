#Học Git tổng hợp bởi NVB

## Cơ bản về git :
  **1. Tổng quan**
  - Mỗi project là 1 repository.
  - Để tạo 1 repository vào thư mục máy local:
    > $git init
  - thư mục git có file ẩn .git (mặc định là nhánh master)
  **Vòng đời của file trong git**
  - Một file khi thêm vào thư mục của git thì mặc định file đó là untracked(chưa đc git quản lý) 
  - Sau khi dùng git add tên file nó chuyển sang trang thái staged(khu vực trung gian gọi là Staging Area file nào nằm trong thư mục này có trạng thái là staged) chuẩn bị commit.
  - Edit file đó nó chuyển sang trạng thái là modified là trạng thái file được chỉnh sửa nhưng chưa được commit. Ta phải add lại file đó để chuyển lại sang staded để chuẩn bị commitlàm việc với git -> luôn luân chuyển nhau giữa các trạng thái. 
  - Để bỏ theo dõi 1 file trong git ta dùng **gitignoring** files.
  - Để remove file trong git 
    > $git rm --cached  name_file
  - Xóa tất file .log trong thư mục log.
    > git rm bin/\*.txt delete tất cả file .txt trong thư mục bin.
  - Rename file trong git
    > $git mv name_1.txt name2.txt 
    
## xem lịch sử COMMIT
  **Xem chi tiết thay đổi.**
    > $git log --stat 
    > $git log --pretty=oneline.

--------------------- Bài 8 : hủy sự thay đổi UNDO THING -------------------------

git commit -amend cho phép remove commit trước.

UNDOTHING

git commit --amend -> gọp commit sửa commit.

UNSTAGE

git reset HEAD tên_file để unstage.

CHECKOUT : thay đổi giờ k muốn thay đổi nữa.
git checkout -- tên_file. 


---------------------- BÀI 9 : làm việc với remore repository--------------------

remore repository là phiên bản code ở trên 1 server nào đó.
để tham gia dự án ta phải trao đổi vs thành viên khác.

github là server chứa free các repository cho các dự án.
để làm việc với git ta phải clone dự án về. 

để clone về ta dùng

git clone url -> sẽ clone được repository về.

có 2 đường link 1 đường link fetch để đẩy dữ liệu và 1 đường link push để kéo dữ liệu.

đầu tiên ta sẽ commit nó. 

........ để chia sẽ 1 code ra sẽ 

git fetch về. là thao tác cập nhật dữ liệu mới nhất về. chỉ để nhìn qua xem có gì ms k.

git fetch ten_remote_repository.

còn pull ms là fetch để download dữ liệu là cập nhật dữ liêu. 

git pull tên_local_repo master

git push tên_local_repo master (master = tên nhánh)

để xem thông tin remote.
git remote show tên repo_local. 

-------- remove remote.

// các dụng là remove bỏ remote để làm mới.
git remote rm tên_remote.

git remote rename ten_cu ten_moi

