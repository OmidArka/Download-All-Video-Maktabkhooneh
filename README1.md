# دانلودر مکتب‌خونه (Maktabkhooneh Downloader)

ابزار خط فرمان برای دانلود ویدیوهای قابل‌دسترسی دوره‌های سایت [مکتب‌خونه](https://maktabkhooneh.org/) با استفاده از کوکی کاربر به شکل همه‌ی ویدیوها با هم و یکجا. فقط محتوایی را می‌توانید دانلود کنید که قانوناً به آن دسترسی دارید.

![maktabkhooneh website screenshot](https://github.com/user-attachments/assets/b54f6fac-10f0-423c-9da2-236c4d8cc5d3)

## ویدیو
https://github.com/user-attachments/assets/38ecfd3e-4281-4e20-854d-18ad5dae5691

## امکانات
- احراز هویت با کوکی (از طریق متغیر محیطی یا فایل)
- استخراج منبع ویدیو از صفحه درس و انتخاب بهترین کیفیت موجود
- پوشه خروجی ثابت: `download/<نام دوره>`
- نمایش خلاصه پروفایل کاربر در ابتدای اجرا
- حالت نمونه‌گیری (Sample) با دانلود تنها N بایت اول هر ویدیو
- نوار پیشرفت با درصد/حجم/سرعت
- ادامه دانلود از همان‌جا (Resume) در صورت قطع شدن
- لاگ‌های رنگی و ایموجی برای خوانایی

## پیش‌نیازها
- ‏Node.js نسخه 18 یا بالاتر
- یک حساب کاربری در maktabkhooneh.org و کوکی معتبر

## تنظیم کوکی

بعد از اینکه به سایت maktabkhooneh.org لاگین شدید. روی صفحه راست کلیک کرده و inspect را بزنید. (یا CTRL+SHIFT+i بزنید) به تب Network بروید. صفحه را رفرش کنید. روی درخواست اول کلیک کنید. در سمت مقابل دنبال Cookie بگردید و آنجا چیزی که مهم است مقدار sessionid است و آن را کپی بگیرید.

![Get Cookies](https://github.com/user-attachments/assets/7943bed5-ffae-4075-a2ba-29f091d572b4)

دو روش برای تنظیم کوکی:
1) متغیر محیطی `MK_COOKIE`
2) یا قرار دادن مسیر فایل کوکی در `MK_COOKIE_FILE`

نکته: چون مقدار کوکی شامل کاراکترهایی مانند `;` و `=` است، حتماً مقدار را داخل کوتیشن قرار دهید.

### ویندوز – PowerShell
```powershell
# کوکی مستقیم
$env:MK_COOKIE = 'sessionid=...;'

# یا: مسیر فایل شامل کوکی
$env:MK_COOKIE_FILE = 'C:\\path\\to\\cookie.txt'
```

### ویندوز – CMD (Command Prompt)
```cmd
REM کوکی مستقیم
set "MK_COOKIE=sessionid=...;"

REM یا: مسیر فایل شامل کوکی
set "MK_COOKIE_FILE=C:\path\to\cookie.txt"
```

### لینوکس / مک – Bash/Zsh
```bash
# کوکی مستقیم
export MK_COOKIE='sessionid=...;'

# یا: مسیر فایل شامل کوکی
export MK_COOKIE_FILE="$HOME/cookie.txt"
```

نکته: اگر کوکی پیچیده یا چندخطی است، روش فایل (`MK_COOKIE_FILE`) توصیه می‌شود. البته در اینجا تک خطی است و همان تنظیم متغییر محیطی کفایت میکند.

## اجرا
نمایش راهنما:
```powershell
node .\download.mjs --help 
```

اجرای دانلود:
```powershell
node .\download.mjs "https://maktabkhooneh.org/course/<slug>/" 
```
نکته: آدرس صفحه دوره‌ی مورد نظر را در دستور فوق جایگزین کنید.

## تست عملکرد
حالت نمونه‌گیری (مثلاً 64KB اول هر ویدیو):
```powershell
node .\download.mjs "https://maktabkhooneh.org/course/<slug>/" --sample-bytes 65536 --verbose 
```

همچنین می‌توانید مقدار نمونه‌گیری را با متغیر محیطی ست کنید:
```powershell
$env:MK_SAMPLE_BYTES = "512000" 
node .\download.mjs "https://maktabkhooneh.org/course/<slug>/" 
```

## 👤 نویسنده

- نویسنده/نگهدارنده: [NabiKAZ](https://github.com/NabiKAZ)
- توییتر (X): [https://x.com/NabiKAZ](https://x.com/NabiKAZ)
- تلگرام: [https://t.me/BotSorati](https://t.me/BotSorati)

## ⭐ حمایت و دونیت

اگر این پروژه برایتان مفید بود، لطفاً در گیت‌هاب به آن یک ⭐ ستاره بدهید. \
برای حمایت از توسعه‌های بعدی می‌توانید به کیف پول TON زیر دونیت کنید: \
**TON Wallet:** `nabikaz.ton` \
حمایت شما باعث دلگرمی است.

## لایسنس
تحت مجوز GPL v3.0 – متن کامل در فایل [LICENSE](./LICENSE).

ساخته‌شده با ❤️ به کمک GPT-5
