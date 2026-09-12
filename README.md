# استخراج Design System از هر وب‌سایت با Codex

این مخزن برای تست Skill ناتان آن جهت استخراج Design System یک وب‌سایت با **Codex** ساخته شده است.

منبع اصلی:

- https://www.nathanonn.com/extract-design-system-from-website/
- https://github.com/nathanonn/agent-skills

## ۱. نصب اولیه

این مراحل را فقط یک‌بار انجام بده:

```bash
npm install -g @playwright/cli@latest
playwright-cli install --skills

npx skills add nathanonn/agent-skills \
  --skill extract-design-system \
  --agent codex
```

برای اطمینان از نصب Playwright:

```bash
which playwright-cli
```

## ۲. استفاده برای هر دامنه

برای هر سایت یک پوشه جدا بساز و آن را با Codex باز کن:

```bash
mkdir my-design-test
cd my-design-test
```

سپس داخل Codex این دستور را اجرا کن:

```text
$extract-design-system https://DOMAIN.COM --pages 5
```

مثال برای Laracasts:

```text
$extract-design-system https://laracasts.com --pages 5
```

Codex ابتدا چند صفحه مهم از سایت را پیشنهاد می‌دهد. آن‌ها را بررسی و تأیید کن تا استخراج ادامه پیدا کند.

## تعداد صفحات پیشنهادی

برای اکثر سایت‌ها همین مقدار مناسب است:

```text
--pages 5
```

برای سایت کوچک:

```text
--pages 3
```

برای سایت بزرگ و متنوع:

```text
--pages 8
```

## خروجی

خروجی معمولاً داخل این پوشه ساخته می‌شود:

```text
.design_systems/
```

ساختار خروجی می‌تواند شامل مواردی مثل این باشد:

```text
.design_systems/
└── example-com-YYYYMMDD/
    ├── DESIGN.md
    ├── AGENTS.md
    ├── components/
    ├── tokens/
    ├── eval/
    ├── screenshots/
    └── raw/
```

Skill فقط رنگ و فونت را استخراج نمی‌کند و می‌تواند مواردی مثل این‌ها را هم بررسی کند:

- رنگ‌ها و تایپوگرافی
- فاصله‌گذاری‌ها و اندازه‌ها
- دکمه‌ها، کارت‌ها، فرم‌ها و سایر کامپوننت‌ها
- حالت‌های مختلف کامپوننت‌ها
- Hover و Focus
- الگوهای چیدمان بخش‌های صفحه
- نمونه‌های مرجع
- شواهد و فایل‌های لازم برای ارزیابی خروجی

## خلاصه

بعد از نصب اولیه، برای هر دامنه تقریباً فقط همین دستور لازم است:

```text
$extract-design-system https://DOMAIN.COM --pages 5
```

سپس صفحات پیشنهادی را تأیید کن و اجازه بده Codex فرایند استخراج را کامل کند.

> نکته: استخراج Design System از سایت‌های دیگر را برای مطالعه، آزمایش و الهام انجام بده. قبل از استفاده تجاری یا انتشار طراحی نزدیک به یک سایت، مجوز و حقوق استفاده از آن را بررسی کن.
