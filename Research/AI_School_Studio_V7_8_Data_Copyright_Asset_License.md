# AI School Studio V7.8
# Data, Copyright & Asset License Policy

## 1. Nguyên tắc

- Private by default.
- Người dùng giữ quyền đối với tài liệu họ tải lên.
- Không dùng dữ liệu riêng tư để train model nếu chưa có opt-in riêng, rõ ràng.
- Chỉ thu thập dữ liệu cần thiết để cung cấp dịch vụ.
- Không thu thập hoặc bán dữ liệu học sinh cho mục đích quảng cáo.
- Mọi asset tái sử dụng phải có nguồn và license rõ ràng.

Tài liệu này là policy thiết kế; cần luật sư Việt Nam rà soát trước khi trở thành điều khoản pháp lý.

---

## 2. Phân loại dữ liệu

### Account Data

- Tên, email, trường, môn và khối dạy.
- Dùng cho vận hành tài khoản, hỗ trợ và cá nhân hóa hợp lệ.

### User Content

- PDF, ảnh, Word/PPT trong tương lai.
- Prompt, chỉnh sửa, lesson package và export.
- Private mặc định; không đưa vào marketplace nếu chưa có hành động publish riêng.

### Student-related Data

- Tên, điểm, hình ảnh hoặc thông tin nhận dạng học sinh.
- Không cần cho MVP và nên chặn/khuyến cáo người dùng loại bỏ.
- Nếu phát hiện, hạn chế log, chia sẻ và retention.

### Telemetry

- Event sản phẩm, token, model, latency, cost, error.
- Không ghi toàn bộ nội dung tài liệu vào log quan sát hệ thống.

---

## 3. Quyền và cam kết của người dùng

Người dùng phải xác nhận:
- Có quyền tải lên và xử lý tài liệu.
- Không tải nội dung vi phạm bản quyền hoặc quyền riêng tư.
- Không tải dữ liệu học sinh nhạy cảm nếu chưa có cơ sở hợp lệ.
- Chịu trách nhiệm kiểm tra nội dung AI trước khi sử dụng trong lớp.

Platform không được diễn giải việc upload là chuyển quyền sở hữu.

---

## 4. SGK và học liệu có bản quyền

- Không xây kho lưu nguyên văn SGK để phân phối lại.
- Knowledge Graph chỉ lưu khái niệm, từ khóa, chuẩn đầu ra và metadata được phép.
- Không cho người dùng khác truy cập file nguồn private.
- Không tự động biến nội dung upload thành public asset.
- Output phải ưu tiên chuyển hóa, tóm tắt và hoạt động sư phạm; tránh sao chép dài nguyên văn.
- Thiết lập giới hạn trích dẫn và kiểm tra similarity trước marketplace.

---

## 5. Retention và deletion

### Project lifecycle mặc định

```text
Ngày 0-7: active_free
Ngày 7: expired hoặc renewed 30 ngày
Ngày 7-10: grace_period
Sau ngày 10: xóa media nặng nếu không gia hạn
```

Quy tắc:
- Upload, voice, ảnh, video và intermediate render được lưu miễn phí 7 ngày.
- Thông báo hết hạn vào ngày 5, 6 và 7.
- Gia hạn cloud theo project/30 ngày và cần opt-in rõ ràng.
- Không đủ credit: giữ grace period 3 ngày để tải xuống hoặc khôi phục.
- Sau grace period: xóa upload/media/intermediate nặng.
- Có thể giữ lesson JSON, quiz, worksheet, notes, metadata và cost ledger vì dung lượng nhỏ.
- Failed job artifacts: xóa sau 24-72 giờ.
- Audit/payment ledger: giữ theo yêu cầu pháp luật/kế toán.
- Deleted account: xóa hoặc ẩn danh dữ liệu không bắt buộc giữ trong 30 ngày.

Người dùng có thể chọn xóa hoàn toàn project ngay lập tức, tùy giới hạn backup và nghĩa vụ pháp lý.

Deletion phải lan tới storage, cache và derived private assets, trừ dữ liệu bắt buộc giữ hoặc đã được publish theo license riêng.

### Thứ tự xóa để tối ưu chi phí

1. Intermediate render và temporary files.
2. Duplicate/cache artifacts không còn reference.
3. AI video và raw audio.
4. Generated images và source upload.
5. Final export nếu người dùng không chọn giữ.

Không xóa ledger/audit bằng cùng lifecycle job với media.

---

## 6. Security Baseline

- TLS khi truyền.
- Private bucket/object ACL mặc định.
- Signed URL có thời hạn ngắn.
- Tách workspace cá nhân và trường học.
- Tenant authorization trên mọi query/object access.
- Mã hóa secret và không log API key.
- Malware/file validation cho upload.
- Audit log cho publish, share, export và admin access.
- Backup có retention và deletion policy rõ ràng.

---

## 7. Asset Provenance

Mỗi asset phải có:
- asset_id
- source_type
- source_url/source_file_id
- source_owner_id
- created_by_user_id
- model/provider nếu generated
- prompt_hash
- content_hash
- license_type
- reuse_scope
- attribution_requirement
- marketplace_asset_id
- moderation_status
- created_at

Không cho Asset Library tái sử dụng asset thiếu provenance.

---

## 8. License cho Marketplace

### Personal Classroom License

- Một giáo viên sử dụng và chỉnh sửa cho lớp của mình.
- Không bán lại hoặc publish công khai.

### School License

- Giáo viên trong một school workspace được sử dụng.
- Không chuyển sang trường khác.

### Remix License

- Người mua được chỉnh sửa trong Studio.
- Creator vẫn sở hữu nội dung gốc.
- Bản remix không được bán lại trừ khi license cho phép rõ ràng.

### Platform Reuse License

- Chỉ áp dụng khi creator opt-in riêng.
- Nêu rõ platform được dùng asset ở đâu, thời hạn và revenue share.
- Không gộp mặc định vào điều khoản upload private.

---

## 9. Publish Flow

1. Creator chọn `Publish to Marketplace`.
2. Xác nhận quyền sở hữu và license.
3. Chạy similarity, PII và safety checks.
4. Human review đối với seller mới hoặc asset rủi ro.
5. Hiển thị preview có watermark.
6. Publish kèm license và attribution.
7. Cho phép report/takedown.

Không dùng một checkbox duy nhất để vừa đồng ý Terms vừa cấp quyền marketplace/platform reuse.

---

## 10. Copyright Takedown

- Có form báo cáo và email tiếp nhận.
- Ghi nhận người báo cáo, asset, bằng chứng và tuyên bố quyền.
- Tạm ẩn asset có khiếu nại đáng tin cậy.
- Thông báo creator và cho phép phản hồi.
- Hoàn tiền/credit khi asset bị gỡ theo policy.
- Áp dụng strike và khóa seller tái phạm.
- Lưu audit trail của quyết định.

SLA đề xuất:
- Xác nhận tiếp nhận trong 2 ngày làm việc.
- Triage trong 5 ngày làm việc.
- Trường hợp khẩn cấp về dữ liệu trẻ em xử lý ngay.

---

## 11. Advertising Data Boundary

Sponsor chỉ nhận dữ liệu tổng hợp:
- Impression.
- Completion.
- Click.
- Promotional credit redeemed.
- Nhóm môn/khối ở mức tổng hợp nếu đủ ngưỡng riêng tư.

Không cung cấp:
- Tài liệu upload.
- Prompt hoặc lesson package.
- Thông tin học sinh.
- Email/số điện thoại/danh tính giáo viên nếu chưa có consent riêng.

---

## 12. Pre-launch Gates

- Terms of Service và Privacy Policy được rà soát pháp lý.
- Có data inventory và retention map.
- Test tenant isolation.
- Test account/file deletion end-to-end.
- Có copyright report/takedown process.
- Marketplace publish dùng explicit opt-in.
- Không dùng private content để training mặc định.
- Có incident response owner và contact.
