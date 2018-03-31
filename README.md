#Học Git tổng hợp bởi NVB

## Cơ bản về git :

  **1. Tổng quan**

  - **Git** khác gì so với **Github**
    1. Git : Git là tên gọi của một Hệ thống quản lý phiên bản phân tán
    2. Github : Github chính là một dịch vụ máy chủ repository công cộng, mỗi người có thể tạo tài khoản trên đó để tạo ra các kho chứa của riêng mình để có thể làm việc
  - Work tree là thư mục làm việc trong git
  - Mỗi project là 1 repository
  - Để tạo 1 repository vào thư mục máy local
    > $git init
  - thư mục git có file ẩn .git (mặc định là nhánh master)
  **Vòng đời của file trong git**
  - Một file khi thêm vào thư mục của git thì mặc định file đó là untracked(chưa đc git quản lý) 
  - Sau khi dùng git add tên file nó chuyển sang trang thái staged(khu vực trung gian gọi là Staging Area file nào nằm trong thư mục này có trạng thái là staged) chuẩn bị commit.
  - Edit file đó nó chuyển sang trạng thái là modified là trạng thái file được chỉnh sửa nhưng chưa được commit. Ta phải add lại file đó để chuyển lại sang staded để chuẩn bị commitlàm việc với git -> luôn luân chuyển nhau giữa các trạng thái. 
  - Để bỏ theo dõi 1 file trong git ta dùng **gitignoring** files.
## Một số lệnh của git
  - *Làm việc trên local*
    - Hủy commit trước đó và gộp với lần commit tiếp theo
      > $git commit -amend
    - Khi ta chuyển file thành staging k theo ý muốn ta có thể chuyển lại nó về trạng thái untracked bằng lệnh
      > $git reset HEAD name_file.
    - Hủy bỏ khi không thay đổi
      > $git checkout -- name_file. 
    - Để remove file trong git 
      > $git rm --cached  name_file
    - Xóa tất file .log trong thư mục log.
      > git rm bin/\*.txt delete tất cả file .txt trong thư mục bin.
    - Rename file trong git
      > $git mv name_1.txt name2.txt 
    - Hủy bỏ commit trước.
      > $git commit -amend
    - Xem chi tiết thay đổi.**
      > $git log --stat 
      > $git log --pretty=oneline.
  - *Làm việc với remote*    
    - Cách cách add remote repository.
      1. Clone repository từ github
        > git clone href_repository
      2. Đã có local ta chỉ cần liên kết với remote
        > git remote add name remote href_repository  
    - pull , fetch, remote.
      1. pull là kéo dữ liệu thằng về máy và tự động merge code.
      2. fetch là kéo dữ liệu về db của máy nhưng chưa đứa vào pepository local.
      3. push là đẩy dữ liệu lên github.
  - *Tag trong git*
    - có 2 loại tag trong git
    - tag ta tạo ra chỉ tồn tại ở local. Muốn người khác biết ta sẽ push lên git.
      > $git push name_remote name_tag    *push tag_name*
      
      > $git push name_remote --tag       *push all tag*
      1. tag.
      2. leightweight_tag.
    - list ra danh sách tag.
      > $git tag
    - list tag có đầu là v1.8.5
      > $git tag -l "v1.5.5\*" 
    - tạo annoted tag ở commit gần nhất.
      > $git tag -a name_tag -m "description tag" *- tag*
      
      > $git tag name_tag                         *- tag-lw*
      
      > $git tag -a name_tag code_bam             *- gắn tag có cho commit có mã băm trên*
    - show tag.
      > $git show name_tag
    - Tách nhánh bởi tag.
      > $git checkout -b name_branch name_tag.
    - Show all tag trong remote.
      > $git ls-remote --tags
    - Xóa tag trong local.
      > git tag -d tag_name
    - Xóa tag trong remote.
      > $git push --delete git tag_name

  - *Branch in git*
    - Tạo nhánh trong git.
     > $git branch name_branch
    - Đổi nhảnh trong git 
     > $git checkout name_branch
    - push nhánh lên github
     > $git push name_remote name_branch
    - merge code not conflig.
     > $git name_remote merge branch_mearch
    - merge code config.
     1. để có khu vực merge code cài diffmerge 
      - git config --global merge.tool diffmerege
       > $git mergetool
    - check nhánh merge 
     > $git branch --merged - *nhánh đã được merge*
     
     > $git branch --no-merged - *nhánh chưa được merge*
     
     > $git branch -d name_branch_delete - *xóa nhánh đã được merge*
     
     > $git branch -D name_branch_delete - *xoa tất cả các nhánh*
     
