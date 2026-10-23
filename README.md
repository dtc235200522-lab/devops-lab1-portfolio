| Tiêu chí | Cách THỦ CÔNG (Traditional) | Cách DEVOPS (CI/CD Pipeline) |
| :--- | :--- | :--- |
| **Làm sao để deploy?** | Upload file bằng tay qua FTP/SFTP (FileZilla, WinSCP) hoặc SSH chép file vào server | Push code lên GitHub → pipeline tự chạy |
| **Mất bao lâu?** | 15 – 30 phút | ~10 giây |
| **Ai làm deploy?** | Con người (Developer / SysAdmin thao tác bằng tay) | GitHub Actions (máy tự làm) |
| **Có bị sai sót không?** | CÓ — dễ sai sót do thao tác tay (chép nhầm/thiếu file, sai quyền) | Không — pipeline nhất quán 100% |
| **Rollback nếu lỗi?** | Phức tạp (tìm bản backup cũ rồi upload đè thủ công) | `git revert` + `push` → tự động rollback |
| **Làm sao biết deploy thành công?** | Mở trình duyệt F5 kiểm tra hoặc soi log server thủ công| GitHub Actions gửi notification ✅/❌ |
