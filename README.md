---
title: NyxRelay
emoji: ⚡
colorFrom: blue
colorTo: purple
sdk: docker
pinned: false
license: mit
app_port: 7860
---

# ⚡ NyxRelay — راهنمای استقرار روی Hugging Face Spaces

> پروژه NyxRelay یک پنل مدیریت تونل مبتنی بر **FastAPI + WebSocket** است که با **Docker** اجرا می‌شود.  
> این راهنما گام‌به‌گام توضیح می‌دهد چطور آن را روی Hugging Face Spaces دیپلوی کنید، وارد شوید و آدرس دامنه را پیدا کنید.

---

## 📁 ساختار فایل‌های پروژه

```
hf-ren1/
├── app.py              ← سرور اصلی FastAPI (117 KB)
├── Dockerfile          ← تعریف محیط Docker
├── requirements.txt    ← کتابخانه‌های Python
└── README.md           ← همین فایل
```

---

## 1️⃣ ساخت حساب کاربری در Hugging Face

اگر حساب ندارید:

1. به آدرس **https://huggingface.co/join** بروید
2. **Username**، **Email** و **Password** را وارد کنید
3. روی **Create Account** کلیک کنید
4. ایمیل تأیید را چک کرده و حساب را فعال کنید

---

## 2️⃣ ساخت Space جدید با SDK = Docker

> ⚠️ **مهم:** چون پروژه از FastAPI و Python استفاده می‌کند، باید SDK را **Docker** انتخاب کنید — نه Static یا Gradio.

1. وارد حساب خود شوید
2. روی **+** در نوار بالا کلیک کنید → **New Space**  
   یا مستقیم به آدرس زیر بروید:
   ```
   https://huggingface.co/new-space
   ```

3. فرم را این‌گونه پر کنید:

   | فیلد | مقدار |
   |------|-------|
   | **Owner** | نام کاربری شما |
   | **Space name** | `nyxrelay` (یا هر نام دلخواه) |
   | **License** | `mit` |
   | **SDK** | **Docker** ← حتماً این را انتخاب کنید |
   | **Visibility** | `Public` (رایگان) |

4. روی **Create Space** کلیک کنید

---

## 3️⃣ آپلود فایل‌های پروژه

بعد از ساخت Space، باید ۴ فایل را آپلود کنید.

### روش اول — آپلود از طریق مرورگر (ساده‌ترین روش):

1. وارد صفحه Space خود شوید
2. روی تب **Files** کلیک کنید
3. دکمه **Add file** ← **Upload files** را بزنید
4. هر ۴ فایل را با هم انتخاب کنید:
   - `app.py`
   - `Dockerfile`
   - `requirements.txt`
   - `README.md`
5. در باکس **Commit changes** بنویسید:
   ```
   Initial deploy
   ```
6. روی **Commit changes to main** کلیک کنید

> ✅ Hugging Face بعد از هر commit به‌صورت خودکار Docker را Build می‌کند.

---

### روش دوم — آپلود با Git (برای کاربران پیشرفته):

```bash
# ۱. نصب git-lfs (اگر ندارید)
git lfs install

# ۲. کلون کردن Space خالی
git clone https://huggingface.co/spaces/YOUR_USERNAME/nyxrelay
cd nyxrelay

# ۳. کپی کردن فایل‌های پروژه به داخل پوشه
cp /path/to/hf-ren1/app.py .
cp /path/to/hf-ren1/Dockerfile .
cp /path/to/hf-ren1/requirements.txt .
cp /path/to/hf-ren1/README.md .

# ۴. آپلود
git add .
git commit -m "Initial deploy"
git push
```

> جای `YOUR_USERNAME` نام کاربری Hugging Face خود را بگذارید.

---

## 4️⃣ صبر کردن برای Build

بعد از آپلود، Hugging Face شروع به Build کردن Docker image می‌کند:

1. وارد صفحه Space شوید
2. روی تب **App** کلیک کنید
3. یک لوگوی چرخنده یا پیام **Building** می‌بینید
4. معمولاً **۱ تا ۳ دقیقه** طول می‌کشد
5. وقتی پیام **Running** سبز رنگ نمایش داده شد، پنل آماده است

> اگر بعد از ۵ دقیقه هنوز در حال Build بود، تب **Logs** را چک کنید تا خطا ببینید.

---

## 5️⃣ پیدا کردن آدرس (URL) پنل

آدرس Space شما به این فرمت است:

```
https://YOUR_USERNAME-nyxrelay.hf.space
```

### مثال:
اگر نام کاربری شما `john123` باشد و Space را `nyxrelay` نامیدید:
```
https://john123-nyxrelay.hf.space
```

### چطور آدرس دقیق را پیدا کنید:

- تب **App** را باز کنید — آدرس نوار مرورگر همان URL است
- یا روی آیکون **⋮** (سه نقطه) بالای Space کلیک کنید → **Embed this Space** — لینک مستقیم آنجاست
- یا در صفحه Space، روی دکمه **↗ Open in full page** کلیک کنید

---

## 6️⃣ ورود به پنل NyxRelay

1. آدرس Space را در مرورگر باز کنید
2. به صورت خودکار به `/login` هدایت می‌شوید
3. اطلاعات پیش‌فرض ورود:

   | فیلد | مقدار پیش‌فرض |
   |------|----------------|
   | **Username** | `admin` |
   | **Password** | `admin` |

4. روی **Sign In** کلیک کنید و وارد داشبورد می‌شوید

> ⚠️ **مهم:** بلافاصله بعد از اولین ورود رمز عبور را تغییر دهید!

---

## 7️⃣ تغییر رمز عبور (ضروری)

1. از داشبورد، بخش **Settings** را باز کنید
2. فیلدهای **Current Password**، **New Password** و **Confirm** را پر کنید
3. روی **Change Password** کلیک کنید

رمز جدید فوری اعمال می‌شود و session های قدیمی باطل می‌گردند.

---

## 8️⃣ تنظیم متغیرهای محیطی (اختیاری اما پیشنهادی)

برای امنیت بیشتر، می‌توانید مقادیر پیش‌فرض را از طریق **Environment Variables** تغییر دهید:

1. در صفحه Space روی **Settings** کلیک کنید
2. بخش **Repository secrets** یا **Variables** را پیدا کنید
3. متغیرهای زیر را اضافه کنید:

   | متغیر | توضیح | مثال |
   |-------|-------|------|
   | `ADMIN_USERNAME` | نام کاربری ادمین | `myadmin` |
   | `ADMIN_PASSWORD` | رمز عبور اولیه | `MyStr0ngPass!` |
   | `SECRET_KEY` | کلید رمزنگاری session | یک رشته تصادفی طولانی |
   | `PANEL_VERSION` | نسخه نمایشی پنل | `v1.0.0` |

> ⚠️ **توجه:** بعد از تغییر متغیرها، Space را Restart کنید تا اعمال شوند.

---

## 9️⃣ پیدا کردن دامنه برای استفاده در VLESS

پنل NyxRelay لینک‌های VLESS می‌سازد که به دامنه شما نیاز دارند.

### دامنه پیش‌فرض (رایگان):

آدرس `hf.space` شما خودکار شناسایی می‌شود:
```
YOUR_USERNAME-nyxrelay.hf.space
```

### تنظیم دامنه سفارشی در پنل:

1. وارد پنل شوید
2. به بخش **Addresses / Domain** بروید
3. دامنه اختصاصی خود را وارد کنید (اگر دارید)
4. روی **Save** کلیک کنید

لینک VLESS به‌صورت خودکار با دامنه جدید به‌روز می‌شود.

### اگر دامنه اختصاصی دارید:

برای استفاده از دامنه خودتان (مثلاً `relay.example.com`) به‌جای `hf.space`:

1. در DNS پنل دامنه‌تان یک رکورد **CNAME** بسازید:
   ```
   relay.example.com  →  YOUR_USERNAME-nyxrelay.hf.space
   ```
2. دامنه را در بخش **Settings → Custom Domain** پنل وارد کنید

> ⚠️ Hugging Face در حال حاضر Custom Domain رسمی برای Spaces ارائه نمی‌دهد. CNAME یک روش غیررسمی است و ممکن است TLS آن کار نکند. برای کار درست از Cloudflare Proxy استفاده کنید.

---

## 🆘 رفع اشکال

| مشکل | راه‌حل |
|------|--------|
| پنل Build نمی‌شود | تب **Logs** را بررسی کنید؛ معمولاً خطای pip install است |
| صفحه خالی یا خطای 502 | چند دقیقه صبر کنید، سپس Space را از Settings → Restart کنید |
| خطای `Module not found` | مطمئن شوید `requirements.txt` آپلود شده |
| رمز عبور فراموش شد | در Settings متغیر `ADMIN_PASSWORD` را تغییر دهید و Restart کنید |
| لینک VLESS اشتباه است | در پنل → Domain، آدرس `hf.space` خود را به‌صورت دستی وارد کنید |
| Space بعد از مدتی خاموش می‌شود | HF Spaces رایگان بعد از عدم استفاده Sleep می‌کنند؛ پنل Keep-Alive داخلی دارد اما ممکن است کافی نباشد |

---

## 📋 چک‌لیست نهایی

قبل از استفاده، همه موارد زیر را تیک بزنید:

- [ ] Space با SDK = **Docker** ساخته شده
- [ ] هر ۴ فایل آپلود شده‌اند (`app.py`, `Dockerfile`, `requirements.txt`, `README.md`)
- [ ] Status در تب App برابر **Running** (سبز) است
- [ ] با `admin` / `admin` وارد شده‌اید
- [ ] رمز عبور تغییر داده شده
- [ ] دامنه `hf.space` در بخش Domain پنل تأیید شده

---

<div align="center">

**⚡ NyxRelay** — Advanced Proxy Management Panel  
FastAPI · WebSocket · Docker · Hugging Face Spaces

</div>
