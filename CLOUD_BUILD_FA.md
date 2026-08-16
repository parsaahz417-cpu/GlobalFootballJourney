# Unity Cloud Build — تنظیمات آماده APK

این نسخه برای Unity Build Automation آماده شده است.

## تنظیمات Build Configuration

- Platform: Android
- Unity version: 6000.5.8f1
- Source: شاخه‌ای که پروژه در آن قرار دارد (معمولاً `main`)
- Project subfolder: خالی، اگر `Assets` و `ProjectSettings` در ریشه Repository هستند
- App Bundle / AAB: خاموش
- Architecture: ARM64
- Minimum Android API: 26
- Application Identifier: `com.indie.globalfootballjourney`

## مهم: Pre-Export Method

در Build Automation > Configuration > Advanced Settings > Script Hooks، مقدار **Pre-Export Method** را دقیقاً روی این مقدار قرار بده:

`GlobalFootball.EditorTools.CloudBuildSetup.PreExport`

این متد قبل از Build موارد زیر را انجام می‌دهد:

- ساخت خودکار `Assets/Scenes/Boot.unity` در checkout تمیز Cloud
- آماده‌سازی URP
- قرار دادن Boot scene در Build Settings
- تنظیم Input System
- تنظیم Android روی IL2CPP + ARM64
- خاموش کردن AAB و اجبار خروجی APK

## خروجی

بعد از اجرای Build و موفق شدن آن، از بخش Artifacts خروجی Android را دریافت کن.
