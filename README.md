# تحديثات PosUnt

مستودع توزيع تحديثات برنامج **PosUnt** عبر [AutoUpdater.NET](https://github.com/ravibpatel/AutoUpdater.NET).

- **بيان التحديث:** [`VersionInfo.xml`](VersionInfo.xml)
- **رابط البيان (يقرؤه البرنامج):**
  `https://raw.githubusercontent.com/mohammedhayde/posunt-updates/main/VersionInfo.xml`
- **حزم التثبيت:** مرفوعة كـ Assets في [Releases](https://github.com/mohammedhayde/posunt-updates/releases).

> هذا المستودع للتوزيع فقط — لا يحوي كود المصدر.

---

## خطوات إصدار تحديث جديد

1. **ارفع رقم الإصدار** في المشروع: `PosUnt/Properties/AssemblyInfo.cs`
   (`AssemblyVersion` و`AssemblyFileVersion` معاً، مثلاً `1.4.3.0` → `1.4.4.0`).

2. **ابنِ نسخة Release** وجهّز المثبّت `PosUnt_Setup_1.4.4.0.exe`.

3. **أنشئ Release وارفع المثبّت** (عبر GitHub CLI):
   ```bash
   gh release create v1.4.4.0 "PosUnt_Setup_1.4.4.0.exe" \
      --repo mohammedhayde/posunt-updates \
      --title "الإصدار 1.4.4.0" \
      --notes "إصلاحات ومزايا جديدة"
   ```

4. **احسب بصمة الملف** (اختياري لكن موصى للأمان):
   ```powershell
   Get-FileHash PosUnt_Setup_1.4.4.0.exe -Algorithm SHA256
   ```

5. **حدّث `VersionInfo.xml`** بالإصدار الجديد ورابط الـ Asset (وأضف `<checksum>` إن حسبته)، ثم:
   ```bash
   git commit -am "الإصدار 1.4.4.0" && git push
   ```

6. **انتهى** — يظهر التحديث لكل مستخدم عند تسجيل الدخول.

## صيغة `VersionInfo.xml`
```xml
<item>
  <version>1.4.4.0</version>
  <url>https://github.com/mohammedhayde/posunt-updates/releases/download/v1.4.4.0/PosUnt_Setup_1.4.4.0.exe</url>
  <checksum algorithm="SHA256">بصمة_الملف</checksum>
  <changelog>https://github.com/mohammedhayde/posunt-updates/releases/tag/v1.4.4.0</changelog>
  <mandatory>true</mandatory>
</item>
```
