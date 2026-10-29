# Templater — bản tùy chỉnh tiếng Việt

Việt hóa giao diện cài đặt, hộp thoại và các lệnh chính.

Đây là bản tùy chỉnh cá nhân, không phải bản phát hành chính thức. Đóng gói ngày 2026-10-29.

## Nguồn và giấy phép

- Plugin gốc: https://github.com/SilentVoid13/Templater
- Phiên bản nền: 2.26.0; tác giả: SilentVoid.
- Giữ giấy phép gốc trong LICENSE. source/upstream.zip chứa mã nguồn gốc đúng bản; source/*.patch ghi lại thay đổi của bản cài hiện tại so với bản sao lưu. patch-tools/ chứa công cụ sửa/Việt hóa ban đầu, tham chiếu cấu trúc vault gốc; không chạy trực tiếp trong repository này.
- main.js và styles.css là bản đang dùng, đã đóng gói để cài; thay đổi phiên bản manifest thành 2.26.0-vi.1. Các tùy chỉnh bổ sung có thể không nằm hết trong công cụ Việt hóa; bản diff là tài liệu đầy đủ của các thay đổi bundle.

## Cài qua BRAT

1. Cài và bật BRAT.
2. Chọn Add a beta plugin, nhập URL repository này.
3. Chọn release 2.26.0-vi.1 nếu BRAT yêu cầu.

ID vẫn là templater-obsidian để dùng được cấu hình hiện có. Trên vault đã cài plugin gốc, hãy sao lưu cấu hình trước khi chuyển sang bản này. Cập nhật từ danh mục Community plugins có thể ghi đè bản tùy chỉnh; dùng BRAT cho repository này. Không cài song song hai bản cùng ID.

## Phát hành

Tạo GitHub Release có tag khớp version trong manifest.json. Đính kèm main.js, manifest.json và styles.css (nếu có) trực tiếp vào release; không chỉ đính kèm ZIP. Khi cập nhật, tăng phiên bản và cập nhật versions.json.

Không chứa data.json, ghi chú, thông tin đăng nhập hoặc cấu hình cá nhân.

Mã nguồn và bản diff được đóng gói trong source-bundle.zip; giải nén để xem các thư mục source/ và patch-tools/.


## Công dụng

Templater tạo ghi chú theo mẫu động: điền ngày giờ, tên tệp, thông tin lặp lại và thực hiện các thao tác tự động bằng cú pháp `tp.*`. Khác với việc chép văn bản cố định, mẫu được xử lý khi chèn để tạo nội dung phù hợp tại thời điểm đó.

## Cách dùng nhanh

1. Tạo thư mục `Templates` trong vault.
2. Vào Settings → Templater → mục thư mục mẫu (**Template folder location**) và chọn `Templates`.
3. Tạo `Templates/Ghi chú học tập.md` với nội dung:

```markdown
# <% tp.file.title %>
Ngày học: <% tp.date.now("YYYY-MM-DD") %>

## Ý chính

## Ví dụ

## Câu hỏi cần ôn
```

4. Tạo hoặc mở ghi chú đích, đặt con trỏ nơi cần chèn.
5. Mở khay lệnh (`Ctrl+P`) → tìm **Templater: Open insert template modal** (hộp chọn/chèn mẫu trong bản Việt hóa), rồi chọn `Ghi chú học tập`.
6. Kiểm tra ngày và tên ghi chú đã được điền. Nếu chỉ dán mã mẫu vào tệp mà không thực thi, dùng lệnh **Templater: Replace templates in the active file** để xử lý các thẻ trong tệp đang mở.

Ví dụ: tạo một mẫu báo cáo thực hành STM32 gồm mục tiêu, sơ đồ đấu dây, mã chương trình và kết quả; mỗi buổi chèn cùng mẫu rồi bổ sung nội dung.

## Tự áp dụng mẫu khi tạo tệp

Trong Templater, có thể bật **Trigger Templater on new file creation**, sau đó cấu hình **Folder templates** để các ghi chú mới trong thư mục học tập nhận mẫu tương ứng. Thử trước với một thư mục mẫu riêng. Không dùng đồng thời nhiều cơ chế chèn mẫu cho cùng tệp nếu chúng làm nội dung bị lặp.

## Lưu ý khi dùng mẫu

- Giữ nguyên cú pháp `<% ... %>` và tên API `tp.*` dù giao diện được Việt hóa.
- Mẫu có JavaScript hoặc lệnh hệ thống có thể thực hiện thao tác ngoài việc chèn chữ; chỉ chạy mẫu bạn hiểu hoặc tin cậy.
- Nếu mẫu không được tìm thấy, kiểm tra thư mục mẫu và đuôi `.md`. Nếu báo lỗi thực thi, xem thông báo và kiểm tra cú pháp mẫu.

## Cài và cập nhật bản Việt hóa

Trong BRAT → **Add beta plugin**, nhập `donamgit151524/obsidian-templater-vi`. Bật plugin sau khi cài. ID giữ nguyên `templater-obsidian`; không cài song song với bản gốc cùng ID. Cấu hình cá nhân không nằm trong repository. Cập nhật bản Việt hóa bằng BRAT để tránh bị bản Community ghi đè.

Tham khảo [tài liệu Templater chính thức](https://silentvoid13.github.io/Templater/) để dùng thêm API và tính năng nâng cao.

