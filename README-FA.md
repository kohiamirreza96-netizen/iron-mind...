# ساخت APK از IRON MIND

## روش آسان (بدون نصب هیچ چیز): GitHub Actions
1. توی github.com یه حساب بساز و یه مخزن (Repository) جدید بساز.
2. کل محتوای این پوشه رو، همراه پوشه‌ی مخفی `.github`، آپلود کن (Add file ← Upload files).
3. برو به تب **Actions**، روی **Build APK** بزن و Run workflow رو بزن.
4. حدود ۵ تا ۸ دقیقه صبر کن. وقتی سبز شد، وارد اجرا شو و پایین صفحه، توی Artifacts فایل **IronMind-APK** رو دانلود کن. داخلش `app-debug.apk` هست.
5. فایل رو روی گوشی بریز و نصب کن (اجازه‌ی نصب از منبع ناشناس لازمه).

## روش محلی
نیاز: Node 20، Java 17، Android SDK
```
npm install
npx cap add android
npx capacitor-assets generate --android --iconBackgroundColor '#050b0a' --splashBackgroundColor '#050b0a'
npx cap sync android
cd android && ./gradlew assembleDebug
```
خروجی: `android/app/build/outputs/apk/debug/app-debug.apk`

## ویرایش سایت
فایل `www/index.html` رو عوض کن و دوباره Build رو اجرا کن.

## نکته‌ها
- فونت Vazirmatn داخل اپ هست و اینترنت نمی‌خواد (لایسنس SIL OFL).
- دکمه‌ی پشتیبان‌گیری و خروجی CSV توی اپ، منوی اشتراک‌گذاری گوشی رو باز می‌کنن.
- این APK دیباگ‌ه و برای نصب شخصی خوبه. برای انتشار توی مایکت یا بازار باید نسخه‌ی release امضاشده بسازی.
- داده‌ها داخل خود گوشی می‌مونن. با حذف اپ یا پاک کردن داده‌های اپ از بین می‌رن، پس گاهی پشتیبان بگیر.
