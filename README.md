# 🚀 NyxRelay — راهنمای استقرار روی Hugging Face Spaces

> این راهنما به شما نشان می‌دهد چطور پنل **NyxRelay** را روی [Hugging Face Spaces](https://huggingface.co/spaces) آپلود کنید، وارد سایت شوید و آدرس (URL) پنل را پیدا کنید.

---

## 📋 پیش‌نیازها

قبل از شروع باید موارد زیر را داشته باشید:

- یک حساب کاربری رایگان روی [huggingface.co](https://huggingface.co)
- فایل `NyxRelay.html` که پنل شماست
- مرورگر مدرن (Chrome / Firefox / Edge)

---

## 1️⃣ ساخت حساب کاربری در Hugging Face

اگر حساب ندارید:

1. به آدرس [https://huggingface.co/join](https://huggingface.co/join) بروید
2. **Username**، **Email** و **Password** را وارد کنید
3. روی **Create Account** کلیک کنید
4. ایمیل تأیید را چک کنید و حساب را فعال کنید

---

## 2️⃣ ساخت یک Space جدید

یک **Space** در Hugging Face مثل یک سرور رایگان است که فایل‌های شما را هاست می‌کند.

### مرحله به مرحله:

1. وارد حساب خود شوید
2. از منوی بالا روی **+** کلیک کنید، سپس **New Space** را انتخاب کنید

   یا مستقیم به این آدرس بروید:
   ```
   https://huggingface.co/new-space
   ```

3. فرم ایجاد Space را پر کنید:

   | فیلد | مقدار پیشنهادی |
   |------|----------------|
   | **Space name** | `nyxrelay-panel` |
   | **License** | `mit` |
   | **SDK** | `Static` ← **این مهم است** |
   | **Visibility** | `Public` (رایگان) یا `Private` (پولی) |

4. روی **Create Space** کلیک کنید

> ✅ **چرا SDK = Static?** چون فایل ما یک HTML خالص است و نیاز به Python یا سرور ندارد.

---

## 3️⃣ آپلود فایل NyxRelay.html

### روش اول — آپلود مستقیم از مرورگر (ساده‌ترین روش):

1. بعد از ساخت Space، وارد صفحه آن شوید
2. روی تب **Files** کلیک کنید
3. دکمه **Add file** → **Upload files** را بزنید
4. فایل `NyxRelay.html` را انتخاب کنید
5. **نام فایل را حتماً به `index.html` تغییر دهید** (قبل یا بعد از آپلود)

   > ⚠️ اگر نام فایل `index.html` نباشد، سایت نمایش داده نمی‌شود!

6. در قسمت **Commit changes** یک پیام بنویسید مثل:
   ```
   Add NyxRelay panel
   ```
7. روی **Commit changes to main** کلیک کنید

---

### روش دوم — آپلود با Git (برای کاربران پیشرفته‌تر):

```bash
# ۱. نصب git-lfs
git lfs install

# ۲. کلون کردن Space
git clone https://huggingface.co/spaces/YOUR_USERNAME/nyxrelay-panel

# ۳. کپی فایل
cd nyxrelay-panel
cp /path/to/NyxRelay.html index.html

# ۴. آپلود
git add index.html
git commit -m "Add NyxRelay panel"
git push
```

> جای `YOUR_USERNAME` نام کاربری Hugging Face خود را بگذارید.

---

## 4️⃣ پیدا کردن آدرس (URL) پنل

بعد از آپلود، آدرس پنل شما به این فرمت است:

```
https://YOUR_USERNAME-nyxrelay-panel.hf.space
```

### مثال:
اگر نام کاربری شما `john123` باشد و Space را `nyxrelay-panel` نامیدید:
```
https://john123-nyxrelay-panel.hf.space
```

### چطور آدرس دقیق را پیدا کنید:

1. وارد صفحه Space خود شوید
2. روی تب **App** کلیک کنید
3. آدرس نوار مرورگر همان URL پنل شماست
4. یا روی آیکون **⋮** (سه نقطه) بالای Space کلیک کنید و **Embed this Space** را بزنید — URL مستقیم آنجاست

---

## 5️⃣ ورود به پنل NyxRelay

بعد از باز کردن آدرس:

1. صفحه Login نمایش داده می‌شود
2. اطلاعات پیش‌فرض ورود:

   | فیلد | مقدار پیش‌فرض |
   |------|----------------|
   | **Username** | `admin` |
   | **Password** | `admin` |

3. روی **Sign In** کلیک کنید

> ⚠️ **مهم:** بلافاصله بعد از اولین ورود، از بخش **Admin** در منوی کناری، رمز عبور را تغییر دهید!

---

## 🔒 تغییر رمز عبور (ضروری)

1. وارد پنل شوید
2. از سایدبار روی **Admin** کلیک کنید
3. نام کاربری و رمز جدید را وارد کنید
4. روی **Save Admin Account** کلیک کنید

اطلاعات جدید در مرورگر شما ذخیره می‌شود (`localStorage`).

---

## ⚙️ تنظیمات اختیاری Space

### Private کردن Space (پیشنهادی برای امنیت):

1. به تنظیمات Space بروید: **Settings** → **Change visibility**
2. گزینه **Private** را انتخاب کنید
3. این کار نیاز به حساب **Pro** دارد (ماهی ~۹ دلار)

### دامنه اختصاصی:

Hugging Face Spaces در حال حاضر دامنه اختصاصی (custom domain) ارائه نمی‌دهد.  
اما می‌توانید:

- آدرس `hf.space` را در یک **iframe** داخل سایت خودتان قرار دهید
- یا از **Cloudflare Workers** به عنوان Reverse Proxy استفاده کنید تا آدرس خودتان را روی آن بگذارید

---

## ❓ سوالات متداول

**Q: آیا داده‌ها بعد از بستن مرورگر از بین می‌روند؟**  
A: خیر. تمام اطلاعات (inbound ها، کلاینت‌ها) در `localStorage` مرورگر ذخیره می‌شود و ماندگار است.

**Q: آیا می‌توانم از گوشی هم وارد شوم؟**  
A: بله. پنل کاملاً Responsive است و روی موبایل هم کار می‌کند.

**Q: Space چقدر طول می‌کشد تا راه‌اندازی شود؟**  
A: معمولاً ۳۰ ثانیه تا ۲ دقیقه. اگر خطا دید، چند دقیقه صبر کنید و صفحه را Refresh کنید.

**Q: آیا استفاده رایگان است؟**  
A: بله. Static Spaces در Hugging Face کاملاً رایگان است.

---

## 📁 ساختار فایل‌ها

برای یک Space درست، Space شما باید این فایل را داشته باشد:

```
your-space/
└── index.html   ← فایل NyxRelay.html با نام تغییر یافته
```

---

## 🆘 رفع اشکال

| مشکل | راه‌حل |
|------|--------|
| صفحه سفید نمایش داده می‌شود | مطمئن شوید نام فایل `index.html` است |
| خطای 404 | چند دقیقه صبر کنید، Space هنوز در حال Build است |
| اطلاعات ذخیره نمی‌شود | مطمئن شوید مرورگر در حالت Private/Incognito نیست |
| رمز عبور را فراموش کردم | در Console مرورگر بنویسید: `localStorage.setItem('nyx-admin','{"user":"admin","pass":"admin"}')` سپس صفحه را Reload کنید |

---

<div align="center">

ساخته شده با ❤️ — **NyxRelay Panel**

</div>
