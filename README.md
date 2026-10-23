# devops-lab1-portfolio
Lab 1 — DevOps Course: My First CI/CD Pipeline
Họ và tên: Trương Thị Hà My
MSSV: DTC235200522
## 4. So sánh DevOps vs Truyền thống

### 4.1 Bảng so sánh
| Tiêu chí | Cách THỦ CÔNG (Traditional) | Cách DEVOPS (CI/CD Pipeline) |
| :--- | :--- | :--- |
| **Làm sao để deploy?** | Upload file bằng tay qua FTP/SFTP (FileZilla, WinSCP) hoặc SSH chép file vào server | Push code lên GitHub → pipeline tự chạy |
| **Mất bao lâu?** | 15 – 30 phút | ~10 giây |
| **Ai làm deploy?** | Con người (Developer / SysAdmin thao tác bằng tay) | GitHub Actions (máy tự làm) |
| **Có bị sai sót không?** | CÓ — dễ sai sót do thao tác tay (chép nhầm/thiếu file, sai quyền) | Không — pipeline nhất quán 100% |
| **Rollback nếu lỗi?** | Phức tạp (tìm bản backup cũ rồi upload đè thủ công) | `git revert` + `push` → tự động rollback |
| **Làm sao biết deploy thành công?** | Mở trình duyệt F5 kiểm tra hoặc soi log server thủ công | GitHub Actions gửi notification ✅/❌ |

### 4.2 Sơ đồ DevOps Workflow
`Developer` --(git push)--> `GitHub Repo` --> `GitHub Actions Runner` --> `GitHub Pages (Live)`

### 4.3 Trả lời câu hỏi
1. **Tự động hóa các bước:** Kiểm tra file (Validate HTML), build, chép file sang branch `gh-pages` và phát hành website.
2. **Quay lại phiên bản cũ:** Dùng lệnh `git revert <commit_id>` rồi `git push`, pipeline sẽ tự deploy lại bản cũ.
3. **Tiết kiệm thời gian:** Tiết kiệm khoảng 95% thời gian (rút ngắn từ 15-30 phút xuống còn ~10 giây).
