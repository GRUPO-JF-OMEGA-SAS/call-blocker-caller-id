# Hướng dẫn Submit ASO — Call Blocker: Caller ID (05i)

**Store**: a022 — GRUPO JF OMEGA SAS  
**Package**: `com.callerid.spamblock.shield`  
**Category**: Communication  

---

## 1. Store Listing (Main store listing → en-US)

| Trường | File | Ký tự |
|---|---|---|
| **App name** | [title.txt](title.txt) | 23/30 |
| **Short description** | [short_description.txt](short_description.txt) | 74/80 |
| **Full description** | [full_description.txt](full_description.txt) | 2937/4000 |

### Cách điền:
1. Play Console → **Grow → Store presence → Main store listing**
2. Copy-paste nội dung từ từng file vào ô tương ứng
3. **App name** = "Call Blocker: Caller ID"

---

## 2. Graphics

| Asset | File | Kích thước |
|---|---|---|
| **App icon** | [icon_512.png](icon_512.png) | 512×512 PNG |
| **Feature graphic** | [feature_graphic.png](feature_graphic.png) | 1024×500 PNG |
| **Phone screenshots** (5 ảnh) | [screenshots/](screenshots/) | 1080×1920 PNG |

### Cách điền:
1. Play Console → **Main store listing → Graphics**
2. Upload `icon_512.png` vào **App icon** (hoặc để từ lúc tạo app)
3. Upload `feature_graphic.png` vào **Feature graphic**
4. Upload 5 ảnh từ `screenshots/` vào **Phone screenshots** (theo thứ tự 01→05)

---

## 3. Release notes

| Trường | File |
|---|---|
| **Release notes** (en-US) | [release_notes.txt](release_notes.txt) |

### Cách điền:
1. Play Console → **Release → Production** (hoặc Internal testing)
2. Khi tạo release mới, paste nội dung `release_notes.txt` vào **Release notes**

---

## 4. Tags / Keywords

File tham khảo: [tags.txt](tags.txt)

> Tags không điền trực tiếp trên Play Console. Dùng để tham khảo khi chọn **Category** và khi optimize listing.

---

## 5. Data Safety

| File | Mô tả |
|---|---|
| [data_safety.csv](data_safety.csv) | Import trực tiếp vào Play Console |
| [data_safety.md](data_safety.md) | Giải thích chi tiết từng mục |

### Cách điền:
1. Play Console → **App content → Data safety**
2. Có thể điền tay theo `data_safety.md`, hoặc import CSV
3. Các mục chính:
   - **Data collected**: Device ID (Advertising ID — ads), Crash logs (Analytics/Crashlytics)
   - **Data shared**: Device ID (Advertising — shared with ad networks)
   - **Data NOT collected**: Location, contacts content, call content, messages content, photos, files, audio, health, financial, search history, browsing history, email, SMS text, app interactions beyond standard analytics
   - **Security**: Data encrypted in transit (HTTPS)
   - **Data deletion**: Uninstall removes all local data

---

## 6. App Content — Permission Declarations

File chi tiết: [permissions_declarations.md](permissions_declarations.md)

### 6a. Default Phone Handler (policy 16909972)

Play Console → **App content → App access → Permissions declarations**

| Quyền | Core functionality | Default handler | Video demo |
|---|---|---|---|
| **READ_CALL_LOG** | Yes | Yes (ROLE_DIALER) | [read_call_log.mp4](videos/read_call_log.mp4) |
| **SMS group** (READ/SEND/RECEIVE_SMS, RECEIVE_MMS) | Yes | Yes (ROLE_SMS) | [sms_group.mp4](videos/sms_group.mp4) |
| **READ_CONTACTS** | Yes | — | [read_contacts.mp4](videos/read_contacts.mp4) |
| **CALL_PHONE + ANSWER_PHONE_CALLS** | Yes | Yes (ROLE_DIALER) | [call_phone.mp4](videos/call_phone.mp4) |

### 6b. Video tổng hợp Default Handler

| Video | Nội dung | Thời lượng |
|---|---|---|
| [default_handler_demo.mp4](videos/default_handler_demo.mp4) | Set default dialer → set default SMS → cấp quyền → demo call log → contacts → messages → dialpad → cuộc gọi đến → SMS đến | ~45s |

### Cách điền:
1. Play Console → **App content → Permissions declarations**
2. Cho mỗi nhóm quyền, chọn **Yes** cho "Core functionality" và "Default handler" (nếu áp dụng)
3. Paste description từ `permissions_declarations.md`
4. Upload video tương ứng (hoặc dùng video tổng hợp `default_handler_demo.mp4` cho tất cả)

---

## 7. Privacy Policy & Terms

| Trang | URL (LIVE) |
|---|---|
| **Privacy Policy** | https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/privacy/ |
| **Terms of Service** | https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/terms/ |

### Cách điền:
1. Play Console → **App content → Privacy policy**
2. Paste URL Privacy Policy
3. Play Console → **Store presence → Main store listing** → có thể thêm Terms link vào phần liên hệ

---

## 8. Content Rating (IARC)

1. Play Console → **App content → Content rating**
2. Trả lời questionnaire:
   - Violence: No
   - Sexual content: No
   - Language: No
   - Controlled substances: No
   - **User-generated content**: No (app không có UGC)
   - **Ads**: Yes (Google AdMob)
   - **Data sharing for ads**: Yes

---

## 9. Target Audience

1. Play Console → **App content → Target audience**
2. Target: **18+** (có ads, phone/SMS handler)
3. KHÔNG chọn "Children" hoặc "Families"

---

## 10. Checklist trước khi Submit

- [ ] App name, short desc, full desc đã paste
- [ ] Icon 512, feature graphic, 5 screenshots đã upload
- [ ] Release notes đã paste trong release mới
- [ ] Data safety đã điền đầy đủ
- [ ] Permission declarations đã khai + upload video
- [ ] Privacy Policy URL đã điền
- [ ] Content rating đã hoàn thành
- [ ] Target audience = 18+
- [ ] Category = Communication
- [ ] Contact email = email của store a022

---

## Toàn bộ asset tải tại

**Landing page**: https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/

| Thư mục / File | Link |
|---|---|
| Videos xin quyền | [videos/](https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/videos/) |
| Screenshots | [screenshots/](https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/screenshots/) |
| Icon 512 | [icon_512.png](https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/icon_512.png) |
| Feature graphic | [feature_graphic.png](https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/feature_graphic.png) |
| Data safety CSV | [data_safety.csv](https://grupo-jf-omega-sas.github.io/call-blocker-caller-id/data_safety.csv) |
