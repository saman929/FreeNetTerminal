# ترمینال ریموت با GitHub Actions

این پروژه یک **شبه ترمینال ریموت** با استفاده از **GitHub Actions** ایجاد می‌کند.

با اجرای workflow، یک ماشین لینوکس موقت در GitHub اجرا می‌شود که به‌صورت دوره‌ای فایل دستورات را بررسی می‌کند و در صورت تغییر، آن‌ها را اجرا می‌کند.

خروجی دستورات در فایل `output.txt` ذخیره شده و به‌صورت خودکار در ریپازیتوری ثبت (commit) می‌شود.

---

# ساختار پروژه

```
.github/workflows/live-terminal.yml   اسکریپت اجرای GitHub Actions
command.sh                            فایل دستورات
output.txt                            خروجی دستورات
downloads/                            پوشه فایل‌های دانلودی
README.md                             توضیحات پروژه
```

---

# نحوه اجرا

1. پروژه را Fork کنید.
2. وارد بخش **Actions** شوید.
3. workflow با نام **Live Command Terminal** را اجرا کنید.
4. ماشین مجازی GitHub اجرا شده و شروع به بررسی دستورات می‌کند.

---

# ارسال دستور

برای اجرای دستور کافی است فایل زیر را ویرایش کنید:

```
command.sh
```

مثال:

```bash
whoami
uname -a
ls -la
```

حدود **۱۵ ثانیه بعد** runner دستور را اجرا می‌کند.

---

# مشاهده خروجی

خروجی تمام دستورات در فایل زیر ذخیره می‌شود:

```
output.txt
```

این فایل بعد از هر اجرا به‌روزرسانی می‌شود.

---

# دانلود فایل از اینترنت

برای دانلود فایل از لینک‌های عمومی می‌توانید از ابزارهایی مثل `wget` یا `curl` استفاده کنید.

مثال:

```bash
wget https://example.com/file.zip -P downloads
```

یا:

```bash
curl -L https://example.com/file.zip -o downloads/file.zip
```

---

# دانلود ویدیو از یوتیوب (نمونه)

ابتدا ابزار `yt-dlp` را نصب کنید:

```bash
pip install yt-dlp
```

دانلود یک ویدیو:

```bash
yt-dlp https://www.youtube.com/watch?v=VIDEO_ID -o downloads/%(title)s.%(ext)s
```

دانلود فقط صدا:

```bash
yt-dlp -x --audio-format mp3 https://www.youtube.com/watch?v=VIDEO_ID -o downloads/%(title)s.%(ext)s
```

---

# انتشار فایل‌ها در ریپازیتوری

برای ذخیره فایل دانلود شده در ریپازیتوری:

```bash
git add downloads/*
git commit -m "add downloaded files"
git push
```

توجه داشته باشید که GitHub محدودیت حجم برای فایل‌ها دارد.

---

# محدودیت‌ها

- ماشین‌های GitHub Actions **موقتی** هستند.
- هر session معمولاً حدود **۶ ساعت** فعال می‌ماند.
- بعد از آن workflow باید دوباره اجرا شود.

---

# نکات امنیتی

- اطلاعات حساس مثل **رمزها یا توکن‌ها** را در دستورات قرار ندهید.
تمام خروجی‌ها در تاریخچه گیت ذخیره می‌شوند.

**پاینده باد ایران**
---
