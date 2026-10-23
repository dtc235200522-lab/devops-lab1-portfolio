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

### 4.3 Trả lời câu hỏi củng cố

1. **DevOps workflow tự động hóa những bước nào mà cách thủ công phải làm bằng tay?**
   * **Trả lời:** Tự động hóa toàn bộ các bước **Build, Test (Validate) và Deploy**. Cụ thể: GitHub Actions tự động kiểm tra sự tồn tại của file `index.html`, kiểm tra dung lượng file, đóng gói mã nguồn và đẩy lên nhánh `gh-pages` để phát hành website công khai mà không cần con người can thiệp thủ công.

2. **Nếu bạn deploy sai (website bị lỗi), làm sao để quay lại phiên bản cũ?**
   * **Trả lời:** Thực hiện lệnh `git revert <commit_id_lỗi>` (hoặc `git reset --hard <commit_id_tốt>`) trên máy local để đưa mã nguồn về phiên bản hoạt động tốt trước đó, sau đó chạy `git push origin main`. Pipeline GitHub Actions sẽ ngay lập tức tự động chạy lại và deploy bản cũ lên website.

3. **GitHub Actions pipeline đã giúp bạn tiết kiệm bao nhiêu thời gian so với cách thủ công?**
   * **Trả lời:**
     * **Cách thủ công:** Tốn **15 – 30 phút** (phải mở phần mềm FTP/SFTP upload file lên server, cấu hình thư mục, kiểm tra đường dẫn).
     * **Cách DevOps (CI/CD):** Chỉ tốn **~10 giây** gõ lệnh `git push`, toàn bộ các bước còn lại hệ thống tự động hoàn thành 100%.
