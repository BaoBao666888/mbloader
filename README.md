# MB Loader v2.4 – bản sửa lỗi

## Nội dung sửa
- Khởi tạo `Global.sharedPreferences` sớm trong `MyApplication.onCreate()` để tránh crash `lateinit property sharedPreferences`.
- Toggle VSync: kiểm tra/mkdirs thư mục `games/com.mojang/minecraftpe/` trước khi tạo `options.txt`, thiếu thư mục thì bỏ qua thay vì văng `IOException`.
- Backup/zip: kiểm tra file tồn tại trước khi mở `FileInputStream`, thiếu file (vd. mcpack trong cache) sẽ bỏ qua, tránh `FileNotFoundException`.
- Mở rộng bắt lỗi khi load thư viện trực tiếp (Condition #1 trong `InitLauncherUnifiedKt`) từ `Exception` sang `Throwable`, giúp tránh crash do `UnsatisfiedLinkError`/lỗi kiến trúc khi thiết bị có thư viện không khớp.