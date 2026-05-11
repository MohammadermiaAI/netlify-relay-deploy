
# 🚀 Netlify Relay Deploy App

این پروژه برای این ساخته شده که کاربر بتواند با اجرای یک فایل ساده‌ی ویندوزی، پروژه‌ی آماده‌ی Netlify Relay را Deploy کند.

شروع کار فقط با این فایل است:

```text
Run-Deploy-Netlify.bat
```

کاربر نیازی به Git، دستورهای دستی، نصب دستی CLI یا تنظیمات پیچیده ندارد. برنامه مرحله‌به‌مرحله اطلاعات لازم را می‌پرسد و در پایان لینک سایت Netlify را تحویل می‌دهد.

> [!IMPORTANT]
> این README مخصوص روش Deploy با فایل `.bat` و Netlify Token است. هدف این راهنما این است که کاربر مبتدی دقیقاً بداند بعد از باز کردن فایل BAT چه کاری باید انجام دهد.

---

## 📑 فهرست مطالب

- [دانلود](#-دانلود)
- [این پروژه چه کاری انجام می‌دهد؟](#-این-پروژه-چه-کاری-انجام-میدهد)
- [پیش‌نیازها](#-پیشنیازها)
- [ساخت Netlify Token](#-ساخت-netlify-token)
- [آموزش Deploy با فایل BAT](#-آموزش-deploy-با-فایل-bat)
- [Target Domain و Path را از کجا برداریم؟](#-target-domain-و-path-را-از-کجا-برداریم)
- [ساختار پروژه](#-ساختار-پروژه)
- [VLESS Config Creator](#-vless-config-creator)
- [Patch Notes](#-patch-notes)
- [خطاهای رایج](#-خطاهای-رایج)
- [نکات امنیتی](#-نکات-امنیتی)
- [تشکر و Credit](#-تشکر-و-credit)
- [حمایت و ارتباط](#-حمایت-و-ارتباط)

---

## 📦 دانلود

برای دانلود نسخه آماده، وارد بخش Releases شوید:

[![Download Latest Release](https://img.shields.io/badge/Download-Latest%20Release-00C7B7?style=for-the-badge&logo=github&logoColor=white)](https://github.com/amirshaker000/netlify-relay/releases/latest)

در بخش Release دو فایل جدا قرار می‌گیرد:

| فایل | توضیح |
|---|---|
| `netlify-installer-v2.0.0.zip` | پروژه اصلی برای Deploy روی Netlify با فایل `.bat` |
| `vless-config-creator-v2.0.0.zip` | برنامه جداگانه ساخت کانفیگ VLESS و تست Ping |

> [!NOTE]
> برنامه **VLESS Config Creator** به‌خاطر حجم بیشتر، جدا از پروژه اصلی منتشر می‌شود تا نصب و دانلود آن راحت‌تر باشد.

---

## ✨ این پروژه چه کاری انجام می‌دهد؟

این پروژه یک Deploy App آماده برای Netlify است. یعنی فایل‌های لازم از قبل داخل پروژه قرار گرفته‌اند و کاربر فقط باید فایل BAT را اجرا کند و چند مقدار ساده را وارد کند.

روند کلی:

```mermaid
flowchart LR
    A[اجرای Run-Deploy-Netlify.bat] --> B[وارد کردن Netlify Token]
    B --> C[انتخاب Template و Preset]
    C --> D[وارد کردن Target Domain و Path]
    D --> E[Deploy روی Netlify]
    E --> F[نمایش لینک نهایی سایت]

    style A fill:#0f172a,stroke:#00C7B7,color:#fff
    style B fill:#111827,stroke:#38bdf8,color:#fff
    style C fill:#111827,stroke:#a78bfa,color:#fff
    style D fill:#111827,stroke:#fbbf24,color:#fff
    style E fill:#052e2b,stroke:#00C7B7,color:#fff
    style F fill:#064e3b,stroke:#22c55e,color:#fff
```

خروجی نهایی چیزی شبیه این است:

```text
https://your-site-name.netlify.app
```

---

## ✅ پیش‌نیازها

قبل از اجرا فقط این موارد را آماده داشته باشید:

| مورد | توضیح |
|---|---|
| Windows | چون فایل اصلی اجرا `Run-Deploy-Netlify.bat` است |
| Netlify Account | برای ساخت سایت و گرفتن لینک نهایی |
| Netlify Token | برای اینکه برنامه بتواند Deploy را خودکار انجام دهد |
| اطلاعات Inbound سرور/VPS | شامل `Target Domain` و `Path` |
| فایل‌های کامل پروژه | فایل‌ها را از Release دانلود و Extract کنید |

---

## 🔑 ساخت Netlify Token

1. وارد حساب Netlify شوید.
2. از قسمت User Settings وارد بخش Applications شوید.
3. بخش Personal Access Tokens را باز کنید.
4. یک Token جدید بسازید.
5. Token را کپی کنید و فقط هنگام اجرای برنامه وارد کنید.

> [!WARNING]
> Token را داخل README، فایل پروژه، اسکرین‌شات یا GitHub قرار ندهید.

---

## 🚀 آموزش Deploy با فایل BAT

بعد از دانلود و Extract پروژه:

1. روی فایل زیر دوبار کلیک کنید:

```text
Run-Deploy-Netlify.bat
```

2. اگر Windows Defender یا SmartScreen هشدار داد، مطمئن شوید فایل را از Release همین پروژه گرفته‌اید و سپس اجازه اجرا بدهید.
3. برنامه از شما Netlify Token را می‌خواهد.
4. سپس نام پروژه، Template، Preset، Target Domain و Path را می‌پرسد.
5. برنامه فایل‌های Netlify را آماده می‌کند.
6. Deploy انجام می‌شود.
7. در پایان لینک سایت Netlify نمایش داده می‌شود.

نمونه ورودی‌ها:

```text
Netlify Token : **************
Site Name     : my-relay-site
Template      : default
Preset        : standard
Target Domain : https://example.com
Path          : /api
```

---

## 🎯 Target Domain و Path را از کجا برداریم؟

`Target Domain` و `Path` نباید حدسی وارد شوند. این دو مقدار باید از **پنل Inbound سرور/VPS** گرفته شوند؛ همان جایی که Inbound اصلی شما ساخته شده است.

### Target Domain چیست؟

`Target Domain` آدرس مقصدی است که Netlify Relay باید درخواست‌ها را به آن ارسال کند.

نمونه:

```text
https://your-domain.com
https://your-domain.com:443
```

### Path چیست؟

`Path` مسیر Inbound است و باید دقیقاً با مسیر داخل پنل Inbound یکی باشد.

نمونه:

```text
/api
/xhttp
/relay
```

> [!CAUTION]
> اگر `Path` داخل Netlify با Path داخل Inbound یکی نباشد، ممکن است Deploy موفق شود اما اتصال کار نکند.

نمونه از پنل Inbound:

```text
Protocol      : VLESS / XHTTP
Domain / Host : your-domain.com
Port          : 443
Path          : /api
```

مقدارهایی که در برنامه وارد می‌کنید:

```text
Target Domain : https://your-domain.com:443
Path          : /api
```

---

## 🧩 ساختار پروژه

ساختار اصلی پروژه به این صورت است:

```text
netlify-relay/
├─ netlify/
│  └─ edge-functions/        # فایل‌های Relay برای Netlify Edge Functions
├─ public/                   # فایل‌های عمومی سایت
├─ scripts/                  # اسکریپت‌های کمکی Deploy
├─ templates/                # قالب‌های آماده سایت برای Deploy
├─ Deploy-Netlify.ps1        # اسکریپت اصلی PowerShell
├─ Run-Deploy-Netlify.bat    # فایل شروع برای کاربر ویندوز
├─ netlify.toml              # تنظیمات Netlify
├─ package.json              # وابستگی‌های پروژه
├─ README.md                 # راهنمای فارسی
└─ README_EN.md              # English guide
```

توضیح کوتاه:

| بخش | کاربرد |
|---|---|
| `Run-Deploy-Netlify.bat` | فایل اصلی که کاربر اجرا می‌کند |
| `Deploy-Netlify.ps1` | منطق اصلی Deploy و آماده‌سازی پروژه |
| `netlify/edge-functions` | بخش Relay روی Netlify |
| `templates` | قالب‌های سایت که هنگام Deploy قابل انتخاب هستند |
| `scripts` | ابزارهای کمکی برای ساخت، تنظیم و بررسی Deploy |
| `public` | فایل‌های ظاهری و عمومی سایت |

---

## 🧪 VLESS Config Creator

این پروژه یک ابزار جداگانه هم دارد به نام **VLESS Config Creator**.

این برنامه برای ساخت کانفیگ‌های VLESS از ترکیب Address و SNI استفاده می‌شود و در نسخه دسکتاپ قابلیت تست Ping واقعی هم دارد.

ویژگی‌های اصلی:

- ساخت کانفیگ VLESS از ترکیب Address List و SNI List
- پشتیبانی از Domain و IP برای Address
- قبول کردن فقط Domain برای SNI
- حذف خودکار IP از لیست SNI
- کپی همه کانفیگ‌ها
- دانلود کانفیگ‌ها با فرمت `.txt`
- تست Ping واقعی داخل نسخه Electron
- انتخاب نتیجه‌های موفق و اعمال آن‌ها روی لیست‌ها
- بخش Credit و Donation داخل UI

> [!NOTE]
> این برنامه داخل Release به‌صورت فایل جدا منتشر می‌شود و لازم نیست داخل سورس اصلی Netlify Relay قرار بگیرد.

---

## 📝 Patch Notes

### v2.0.0

- اضافه شدن Templateهای سایت برای Deploy
- اضافه شدن Presetهای Deploy
- اضافه شدن Health Check بعد از Deploy
- اضافه شدن Deploy با فایل `.bat`
- اضافه شدن Deploy با Netlify Token
- ساده‌تر شدن مراحل برای کاربران مبتدی
- جدا شدن VLESS Config Creator از پروژه اصلی برای دانلود جداگانه
- بهبود ساختار پوشه‌ها و فایل‌های پروژه
- اضافه شدن README فارسی و انگلیسی
- اضافه شدن بخش Download و Release Assets
- اضافه شدن بخش Credit، Donation و لینک‌های ارتباطی

---

## 🐛 خطاهای رایج

<details>
<summary><b>فایل BAT اجرا نمی‌شود</b></summary>

- روی فایل راست‌کلیک کنید و Run as administrator را امتحان کنید.
- مطمئن شوید فایل را از Release رسمی همین پروژه دانلود کرده‌اید.
- اگر PowerShell محدودیت اجرا داشت، پنجره برنامه معمولاً راهنمای لازم را نمایش می‌دهد.

</details>

<details>
<summary><b>Deploy انجام می‌شود اما اتصال کار نمی‌کند</b></summary>

این موارد را بررسی کنید:

- `Target Domain` درست وارد شده باشد.
- `Path` دقیقاً با Path داخل پنل Inbound یکی باشد.
- Inbound روی سرور/VPS روشن باشد.
- پورت و TLS سمت سرور درست تنظیم شده باشد.

</details>

<details>
<summary><b>Token قبول نمی‌شود</b></summary>

- Token را دوباره از Netlify بسازید.
- فاصله اضافی قبل یا بعد Token وارد نکنید.
- Token را از حساب درست Netlify بسازید.

</details>

---

## 🔐 نکات امنیتی

قبل از Public کردن پروژه در GitHub:

- فایل `.env` واقعی را منتشر نکنید.
- Netlify Token را داخل هیچ فایل یا README قرار ندهید.
- اسکرین‌شات دارای Token منتشر نکنید.
- اگر Token لو رفت، سریع آن را حذف و Token جدید بسازید.
- فقط فایل `.env.example` را در GitHub نگه دارید.


