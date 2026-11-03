# Permission Declarations — Call Blocker Caller ID (05i)

App dùng các quyền nhạy cảm cần khai báo trên Play Console (App content).
Mỗi quyền có: (1) declaration answers, (2) mô tả, (3) kịch bản video demo.

---

## Sensitive permissions

### 1. READ_CALL_LOG + WRITE_CALL_LOG group
- **Permission**: `android.permission.READ_CALL_LOG` (AndroidManifest.xml:16)
- **Feature**: Hiển thị danh sách cuộc gọi gần đây (tab Recents), chặn số người dùng đã đánh dấu từ lịch sử cuộc gọi.
- **Declaration form**: Call Log permission declaration
  - **Core functionality**: Yes — app IS a default phone handler (ROLE_DIALER) and needs call log to display recent calls and identify repeat callers.
  - **Default handler**: Yes — app declares `android.intent.action.DIAL` + `android.intent.action.VIEW` + `tel:` scheme intent filters and uses `ROLE_DIALER`.
- **Describe**: "Call Blocker Caller ID is a default phone app (dialer). It reads call log to display your recent calls list, and let you block unwanted numbers directly from call history. This is core to the app's purpose as your phone handler."
- **Video**: `permission_videos/read_call_log.mp4`
  - **Kịch bản**: (1) Từ màn home điện thoại → tap icon app → (2) App mở → cấp quyền Call Log khi được hỏi → (3) Vào tab Recents → thấy danh sách cuộc gọi từ call log → (4) Tap một cuộc gọi → thấy chi tiết + nút Block
- **real-device-only**: NO (emulator có thể diễn được)

### 2. READ_SMS + SEND_SMS + RECEIVE_SMS + RECEIVE_MMS group
- **Permission**: `android.permission.READ_SMS` (AndroidManifest.xml:22), `android.permission.SEND_SMS` (AndroidManifest.xml:23), `android.permission.RECEIVE_SMS` (AndroidManifest.xml:24), `android.permission.RECEIVE_MMS` (AndroidManifest.xml:25)
- **Feature**: App đăng ký làm ứng dụng SMS mặc định (ROLE_SMS). Nhận/hiển thị/gửi tin nhắn SMS/MMS.
- **Declaration form**: SMS/MMS permission declaration
  - **Core functionality**: Yes — app IS a default SMS handler (ROLE_SMS) and must receive, display and send SMS/MMS.
  - **Default handler**: Yes — declares `SMS_DELIVER`, `WAP_PUSH_DELIVER` receivers + `RESPOND_VIA_MESSAGE` service + `SENDTO` with sms/smsto/mms/mmsto schemes.
- **Describe**: "Call Blocker Caller ID functions as the default SMS app. It receives and displays incoming SMS/MMS messages, lets users compose and send messages, The SMS permissions are required for its role as the device's default messaging handler."
- **Video**: `permission_videos/sms_group.mp4`
  - **Kịch bản**: (1) Từ màn home → tap icon app → (2) App mở → set default SMS handler khi được hỏi → (3) Vào tab Messages → thấy danh sách tin nhắn → (4) Tap Compose → soạn và gửi tin nhắn test → (5) Nhận tin nhắn đến (gửi từ thiết bị/emulator khác)
- **real-device-only**: PARTIAL (gửi/nhận SMS thật cần SIM, nhưng emulator có thể gửi SMS qua `adb emu sms send`)

### 3. READ_CONTACTS
- **Permission**: `android.permission.READ_CONTACTS` (AndroidManifest.xml:17)
- **Feature**: Tra cứu tên người gọi/nhắn tin từ danh bạ, hiển thị caller ID khi có cuộc gọi đến.
- **Declaration form**: Contacts permission (nếu Play yêu cầu khai)
- **Describe**: "The app reads contacts to identify incoming callers and message senders by name, displaying caller ID information during calls and in the message list. Contact data stays on-device and is not uploaded."
- **Video**: `permission_videos/read_contacts.mp4`
  - **Kịch bản**: (1) Từ home → tap icon → (2) Cấp quyền Contacts → (3) Vào tab Contacts → thấy danh bạ → (4) Có cuộc gọi đến → overlay caller ID hiện tên từ contacts
- **real-device-only**: NO

### 4. CALL_PHONE + ANSWER_PHONE_CALLS
- **Permission**: `android.permission.CALL_PHONE` (AndroidManifest.xml:20), `android.permission.ANSWER_PHONE_CALLS` (AndroidManifest.xml:21)
- **Feature**: Gọi điện từ ứng dụng (tap số trên dialpad/danh bạ), tự động trả lời cuộc gọi.
- **Declaration form**: Phone permission
- **Describe**: "As the default phone handler, the app needs CALL_PHONE to initiate outgoing calls from the dialer/contacts and ANSWER_PHONE_CALLS to handle the incoming call UI (answer/reject). These are core functions of a phone app."
- **Video**: `permission_videos/call_phone.mp4`
  - **Kịch bản**: (1) Home → tap icon → (2) Set default dialer → (3) Vào Dialpad → nhập số → tap Call → cuộc gọi bắt đầu → (4) Cuộc gọi đến → incoming call UI → tap Answer
- **real-device-only**: PARTIAL (emulator hỗ trợ gọi qua `adb emu gsm call`, nhưng InCallService UI tốt hơn trên máy thật)

---

## Video demo tổng hợp cho Default Phone + Default SMS handler

Google Play yêu cầu video demo cho app sử dụng **policy 16909972** (Default Phone Handler + Default SMS Handler). Video tổng hợp cần thể hiện:

### Video: `permission_videos/default_handler_demo.mp4`
**Kịch bản** (đây là video CHÍNH cho permission declarations):
1. **Từ màn home điện thoại** → tap icon Call Blocker Caller ID
2. **Set Default Dialer**: hệ thống hỏi "Set as default phone app?" → tap Yes/Allow
3. **Set Default SMS**: hệ thống hỏi "Set as default SMS app?" → tap Yes/Allow
4. **Cấp runtime permissions**: Call Log → Allow, Contacts → Allow, Phone → Allow, SMS → Allow
5. **Demo tính năng Phone**:
   - Mở tab Recents → thấy call log
   - Mở Dialpad → nhập số → gọi
   - Có cuộc gọi đến → incoming call overlay/UI → caller ID hiện tên → Answer/Reject
   - Block một số → confirm
6. **Demo tính năng SMS**:
   - Mở tab Messages → thấy threads
   - Tap thread → đọc tin nhắn
   - Compose → gửi tin test
   - Nhận tin nhắn mới

**Thời lượng**: ~45-60 giây
**Lưu ý quay**: Airplane mode ON (chặn test-ad), airplane OFF chỉ khi cần gọi/SMS thật.

---

## To REMOVE (thừa, không feature dùng)

Không có quyền thừa — tất cả quyền trong manifest đều có feature sử dụng.

---

## Checklist hoàn thành

- [x] Video `read_call_log.mp4` — AI quay trên emulator
- [x] Video `sms_group.mp4` — AI quay trên emulator (gửi SMS qua `adb emu sms send`)
- [x] Video `read_contacts.mp4` — AI quay
- [x] Video `call_phone.mp4` — AI quay
- [x] Video `default_handler_demo.mp4` — video tổng hợp CHÍNH (khuyến nghị quay trên máy thật cho chất lượng tốt nhất)
