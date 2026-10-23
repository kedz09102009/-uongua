# Đường Đua

Web app chạy đua với chính mình: đặt mục tiêu và hạn chót, ghi lại biến cố, gia hạn bằng lập luận khi chưa kịp. Dùng được trên điện thoại và máy tính, cài được lên màn hình chính, mở được khi mất mạng, và đồng bộ dữ liệu giữa các thiết bị.

Đây là một website tĩnh, không cần máy chủ. Đưa lên GitHub Pages là chạy, miễn phí.

## Có gì trong thư mục này

| Tệp | Việc của nó |
|---|---|
| `index.html` | Toàn bộ app (giao diện và logic) |
| `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png`, `favicon.svg` | Để cài lên màn hình điện thoại với biểu tượng riêng |
| `sw.js` | Giúp app mở được khi mất mạng |
| `.nojekyll` | Báo GitHub Pages phục vụ nguyên các tệp, không xử lý gì thêm. Tệp này ẩn trên nhiều máy, thiếu nó vẫn chạy bình thường |

## Phần 1. Đưa lên GitHub Pages

1. Giải nén tệp zip.
2. Đăng nhập [github.com](https://github.com). Bấm dấu **+** ở góc trên bên phải, chọn **New repository**.
3. Đặt **Repository name** là `duong-dua`. Chọn **Public**. Bấm **Create repository**.
   - GitHub Pages miễn phí yêu cầu repository công khai. Repository chỉ chứa mã của app. Dữ liệu cá nhân của bạn không nằm trong đó (xem phần Bảo mật).
4. Ở trang repository vừa tạo, bấm liên kết **uploading an existing file**.
5. Mở thư mục `duong-dua` đã giải nén, chọn **tất cả tệp bên trong** rồi kéo thả vào trang GitHub. Đừng kéo cả thư mục bọc ngoài, vì `index.html` phải nằm ngay ở gốc repository.
6. Cuộn xuống, bấm **Commit changes**.
7. Vào **Settings**, chọn **Pages** ở thanh bên trái. Ở mục **Build and deployment**, chọn **Source: Deploy from a branch**. Chọn **Branch: main**, thư mục **/ (root)**, rồi bấm **Save**.
8. Chờ khoảng 1 đến 2 phút, tải lại trang Pages. GitHub sẽ hiện địa chỉ web của bạn, dạng:

   `https://TÊN-GITHUB-CỦA-BẠN.github.io/duong-dua/`

   Tên được viết thường hết.

## Phần 2. Cài lên điện thoại và máy tính

- **iPhone (Safari):** mở địa chỉ web, bấm nút **Chia sẻ**, chọn **Thêm vào MH chính**.
- **Android (Chrome):** mở địa chỉ web, bấm menu **⋮**, chọn **Cài đặt ứng dụng** hoặc **Thêm vào màn hình chính**.
- **Máy tính (Chrome, Edge):** bấm biểu tượng cài đặt ở cuối thanh địa chỉ. Bước này tùy chọn, dùng thẳng trên trình duyệt vẫn được.

## Phần 3. Đồng bộ giữa các thiết bị

Mặc định, dữ liệu nằm trong trình duyệt của từng thiết bị. Để điện thoại và máy tính dùng chung một dữ liệu, app lưu một bản vào **Gist bí mật** trong tài khoản GitHub của bạn. Bạn cần một **token** để app được phép ghi vào Gist đó.

**Tạo token (làm một lần cho mỗi thiết bị):**

1. Trong app, bấm nút **Chưa đồng bộ** ở góc trên bên phải.
2. Bấm liên kết **trang tạo token**. Nếu trang không tự điền sẵn, vào GitHub, chọn ảnh đại diện, **Settings**, **Developer settings**, **Personal access tokens**, **Tokens (classic)**, **Generate new token (classic)**.
3. Ở ô **Note**, gõ `Duong Dua`. Ở **Expiration**, chọn thời hạn bạn muốn. Khi token hết hạn, app báo lỗi và bạn chỉ cần tạo token mới.
4. Ở danh sách quyền, **chỉ tích ô `gist`**.
5. Kéo xuống cuối, bấm **Generate token**, sao chép chuỗi bắt đầu bằng `ghp_`. GitHub chỉ hiện chuỗi này một lần.
6. Dán vào ô **Token GitHub** trong app, bấm **Kết nối**.

**Thiết bị thứ hai:** mở web, làm lại các bước trên bằng **cùng tài khoản GitHub**. App tự tìm Gist cũ và **gộp** dữ liệu hai bên, không mất mục nào. Mỗi thiết bị có thể dùng token riêng.

Nút ở góc trên cho biết tình trạng: **Đã đồng bộ**, **Đang đồng bộ…**, **Ngoại tuyến** (mất mạng, dữ liệu vẫn lưu trên máy và tự gửi đi khi có mạng), **Lỗi đồng bộ** (bấm vào để đọc lý do).

**Khi nào app đồng bộ:** khoảng 1,5 giây sau mỗi thay đổi, khi bạn mở lại app hoặc quay về tab, và mỗi phút khi đang mở.

**Cách gộp dữ liệu:**

- Mục tiêu thêm hoặc sửa trên hai thiết bị khác nhau đều được giữ.
- Mục tiêu xóa ở một thiết bị cũng biến mất ở thiết bị kia.
- Giới hạn cần biết: nếu bạn sửa **cùng một mục tiêu** trên hai thiết bị khi **cả hai đều mất mạng**, app giữ bản sửa **sau cùng** và bỏ bản kia. Dùng bình thường thì hầu như không gặp.

## Bảo mật

- **Repository công khai chỉ chứa mã app.** Mục tiêu và lập luận của bạn không nằm ở đó.
- **Gist "bí mật" không phải riêng tư tuyệt đối.** Không ai tìm thấy nó trong danh sách công khai, nhưng ai có đường link đều xem được. Đừng chia sẻ link Gist của bạn.
- **Token chỉ có quyền `gist`.** Nó được lưu trong trình duyệt của thiết bị đó và chỉ gửi tới `api.github.com`. Không đăng token ở đâu cả. Mất máy hoặc nghi ngờ lộ token thì vào GitHub, **Settings**, **Developer settings**, **Personal access tokens** và xóa token đó.
- Dùng máy chung: vào hộp thoại đồng bộ và bấm **Ngắt kết nối thiết bị này**.

## Sao lưu bằng tệp

Trong hộp thoại đồng bộ có **Xuất tệp** (tải về một tệp `.json`) và **Nhập từ tệp** (gộp vào dữ liệu hiện có). Nên xuất tệp thỉnh thoảng, nhất là trước khi xóa dữ liệu trình duyệt. Nếu chưa bật đồng bộ mà xóa dữ liệu trình duyệt, mục tiêu sẽ mất.

## Cập nhật app

Tải tệp mới lên repository: **Add file**, **Upload files**, kéo thả để ghi đè, rồi **Commit changes**. Chờ một đến hai phút. Với app đã cài lên điện thoại, đóng hẳn app rồi mở lại một hai lần để nhận bản mới. Dữ liệu của bạn không bị ảnh hưởng.

## Gặp sự cố

| Hiện tượng | Cách xử lý |
|---|---|
| Mở địa chỉ báo 404 | Chờ vài phút sau khi bật Pages. Kiểm tra `index.html` nằm ở gốc repository, và Pages đang trỏ vào branch `main`, thư mục `/ (root)` |
| "Token không hợp lệ" | Tạo lại token loại **Classic** và tích đúng ô `gist` |
| "Không truy cập được Gist" | Token thiếu quyền `gist`. Tạo token mới, hoặc bấm **Ngắt kết nối** rồi kết nối lại |
| Hai thiết bị không thấy dữ liệu của nhau | Kiểm tra cả hai dùng cùng một tài khoản GitHub, rồi bấm **Đồng bộ ngay** |
| "GitHub tạm giới hạn số lần gọi" | Chờ vài phút, app tự thử lại |
| Chữ hiện bằng phông hệ thống | App tải phông từ Google Fonts. Khi mất mạng lần đầu mở, nó dùng phông có sẵn của máy, không ảnh hưởng chức năng |
