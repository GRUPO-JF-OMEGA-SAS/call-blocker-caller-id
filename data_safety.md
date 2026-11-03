# Data Safety — Call Blocker Caller ID (05i)

Khai báo dữ liệu thu thập / chia sẻ theo định nghĩa Google Play Data Safety.
File import: `data_safety.csv` (cùng thư mục).

## Tóm tắt

- **Thu thập dữ liệu cá nhân**: CÓ
- **Mã hoá truyền tải (TLS)**: CÓ (Firebase, AdMob, mediation đều HTTPS)
- **Tài khoản người dùng**: KHÔNG (không đăng nhập, không tạo tài khoản)
- **Xoá dữ liệu**: Không (không có tài khoản → không có dữ liệu để xoá)

## Data types khai báo

### 1. Crash logs — Collected
- **Bằng chứng**: `implementation(libs.firebase.crashlytics)` (build.gradle.kts:215)
- **SDK**: Firebase Crashlytics
- **Collected/Shared**: Collected only (gửi tới Firebase/Google cho developer)
- **Ephemeral**: Không (lưu 90 ngày trên Firebase Console)
- **User control**: Required (không có toggle opt-out)
- **Purpose**: App functionality, Analytics

### 2. Diagnostics — Collected
- **Bằng chứng**: `implementation(libs.firebase.analytics)` (build.gradle.kts:214), `implementation(libs.firebase.crashlytics)` (build.gradle.kts:215)
- **SDK**: Firebase Analytics + Crashlytics
- **Collected/Shared**: Collected only
- **Ephemeral**: Không
- **User control**: Required
- **Purpose**: App functionality, Analytics

### 3. App interactions — Collected
- **Bằng chứng**: `implementation(libs.firebase.analytics)` (build.gradle.kts:214)
- **SDK**: Firebase Analytics (tự log screen_view, user_engagement, session_start)
- **Collected/Shared**: Collected only
- **Ephemeral**: Không
- **User control**: Required
- **Purpose**: Analytics

### 4. Device or other IDs — Collected + Shared
- **Bằng chứng**:
  - `implementation(libs.module.ads)` (build.gradle.kts:206) — AdMob/GMA + mediation (AppLovin, Meta Audience Network)
  - `<uses-permission android:name="com.google.android.gms.permission.AD_ID" />` (AndroidManifest.xml:10)
  - `<uses-permission android:name="android.permission.ACCESS_ADSERVICES_AD_ID" />` (AndroidManifest.xml:11)
  - `implementation(libs.adjust.android)` (build.gradle.kts:208) — Adjust attribution
  - `implementation(libs.facebook.android.sdk)` (build.gradle.kts:209) — Facebook SDK
  - `implementation(libs.tiktok.business.android.sdk)` (build.gradle.kts:210) — TikTok Business SDK
  - `implementation(libs.firebase.analytics)` (build.gradle.kts:214)
- **SDK**: AdMob/GMA, AppLovin (mediation), Meta Audience Network (mediation), Adjust, Facebook SDK, TikTok SDK, Firebase Analytics
- **Collected/Shared**: Collected AND **Shared** (ad SDKs chia sẻ advertising ID với mạng quảng cáo bên thứ ba)
- **Ephemeral**: Không
- **User control**: Required (ads active mặc định; user có thể reset/tắt Advertising ID ở OS level nhưng app không có toggle riêng)
- **Collection purpose**: Analytics, Advertising or marketing
- **Sharing purpose**: Advertising or marketing

## Data types KHÔNG khai (lý do)

| Permission / tính năng | Lý do không khai |
|---|---|
| READ_CALL_LOG, READ_SMS, SEND_SMS, RECEIVE_SMS | Xử lý **on-device only** — dữ liệu cuộc gọi/tin nhắn KHÔNG rời khỏi thiết bị, không gửi lên server |
| READ_CONTACTS | Tra cứu caller ID **on-device** — danh bạ không upload |
| READ_PHONE_STATE, READ_PHONE_NUMBERS | Dùng cho InCallService/CallScreeningService — on-device |
| CALL_PHONE, ANSWER_PHONE_CALLS | System action, không thu thập dữ liệu |
| Location | KHÔNG có quyền location trong manifest |

## Đối chiếu Data Safety ↔ Privacy Policy

| Data type khai trong CSV | Nhắc trong Privacy Policy? |
|---|---|
| Crash logs | ✅ Mục "Firebase Crashlytics" — crash reports, stack traces |
| Diagnostics | ✅ Mục "Firebase Analytics" — event/session/device diagnostics |
| App interactions | ✅ Mục "Firebase Analytics" — screen views, engagement |
| Device IDs (Collected) | ✅ Mục "Advertising and Consent" — AD_ID, advertising identifier |
| Device IDs (Shared for Ads) | ✅ Mục "Advertising and Consent" — shared with ad networks for serving ads |

**Kết luận**: Nhất quán — mọi type khai trong CSV đều được Privacy Policy nhắc tới.
