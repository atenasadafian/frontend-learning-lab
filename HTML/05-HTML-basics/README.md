# آموزش دریافت اطلاعات از کاربر با انواع `input` در HTML

در HTML برای دریافت اطلاعات از کاربران از فرم‌ها (Forms) استفاده می‌کنیم. فرم‌ها در وب‌سایت‌ها کاربردهای زیادی دارند؛ از جمله:

- ثبت‌نام کاربران
- ورود به حساب کاربری
- جست‌وجو در سایت
- ثبت سفارش
- ارسال پیام و نظر
- انتخاب تاریخ رزرو
- بارگذاری تصاویر و فایل‌ها
- دریافت تنظیمات و ترجیحات کاربران

مهم‌ترین تگ‌های مورد استفاده برای ساخت فرم عبارت‌اند از:

| تگ | کاربرد |
|---|---|
| `<form>` | ایجاد فرم و تعیین روش ارسال اطلاعات |
| `<input>` | دریافت اطلاعات با انواع ورودی |
| `<label>` | مشخص کردن عنوان هر ورودی |
| `<textarea>` | دریافت متن چندخطی |
| `<select>` | ایجاد فهرست کشویی |
| `<option>` | تعریف گزینه‌های فهرست |
| `<button>` | ایجاد دکمه |
| `<fieldset>` | گروه‌بندی ورودی‌های مرتبط |
| `<legend>` | تعیین عنوان گروه ورودی‌ها |

نکته مهم: ویژگی `type` در تگ `input` تعیین می‌کند که ورودی چه نوع اطلاعاتی را دریافت کند.

```html
<input type="text">
<input type="email">
<input type="password">
<input type="number">
<input type="date">
```

هر یک از این ورودی‌ها رفتار متفاوتی در مرورگر دارند.

## ساختار کلی فرم در HTML

یک فرم ساده به شکل زیر نوشته می‌شود:

```html
<form action="/register" method="post">
    <label for="username">نام کاربری:</label>
    <input
        type="text"
        id="username"
        name="username"
        required
    >

    <button type="submit">ثبت اطلاعات</button>
</form>
```

### توضیح اجزای فرم

**تگ `form`:**

```html
<form action="/register" method="post">
```

- `action`: آدرس مقصدی که اطلاعات فرم به آن ارسال می‌شود.
- `method`: روش ارسال اطلاعات را مشخص می‌کند.
- `get`: اطلاعات را معمولاً در قالب پارامترهای URL ارسال می‌کند.
- `post`: اطلاعات را در بدنه درخواست HTTP ارسال می‌کند.

**تگ `label`:**

```html
<label for="username">نام کاربری:</label>
```

ویژگی `for` باید با مقدار `id` ورودی مرتبط برابر باشد. این ارتباط باعث می‌شود کلیک روی عنوان، ورودی مربوطه را فعال کند.

**تگ `input`:**

```html
<input type="text" id="username" name="username">
```

- `type`: نوع ورودی را تعیین می‌کند.
- `id`: شناسه ورودی در صفحه است.
- `name`: نام فیلدی است که هنگام ارسال فرم برای داده آن استفاده می‌شود.

**نکته مهم:** برای ارسال معمول اطلاعات فرم، وجود `name` ضروری است. داشتن `id` به‌تنهایی باعث ارسال مقدار ورودی نمی‌شود.

---

## ویژگی‌های مهم تگ input

| ویژگی | توضیح | مثال |
|---|---|---|
| `type` | نوع ورودی | `type="email"` |
| `id` | شناسه یکتا در صفحه | `id="email"` |
| `name` | نام فیلد ارسالی | `name="email"` |
| `value` | مقدار اولیه یا مقدار تنظیم‌شده | `value="Ali"` |
| `placeholder` | متن راهنما داخل ورودی | `placeholder="نام خود را وارد کنید"` |
| `required` | اجباری کردن ورودی | `required` |
| `disabled` | غیرفعال کردن ورودی | `disabled` |
| `readonly` | جلوگیری از ویرایش مستقیم مقدار | `readonly` |
| `min` | حداقل مقدار یا تاریخ | `min="1"` |
| `max` | حداکثر مقدار یا تاریخ | `max="100"` |
| `step` | فاصله مجاز بین مقادیر | `step="5"` |
| `minlength` | حداقل طول متن | `minlength="3"` |
| `maxlength` | حداکثر طول متن | `maxlength="50"` |
| `pattern` | الگوی مجاز برای مقدار | `pattern="[A-Za-z]+"` |
| `autocomplete` | راهنمای تکمیل خودکار | `autocomplete="email"` |
| `multiple` | اجازه انتخاب چند مقدار در انواع پشتیبانی‌شده | `multiple` |
| `accept` | محدود کردن انواع فایل پیشنهادی | `accept="image/*"` |
| `checked` | انتخاب اولیه Checkbox یا Radio | `checked` |
| `autofocus` | درخواست تمرکز اولیه روی ورودی | `autofocus` |

مثال:

```html
<input
    type="text"
    id="fullname"
    name="fullname"
    placeholder="نام و نام خانوادگی"
    minlength="3"
    maxlength="60"
    required
>
```

در این مثال، ورودی اجباری است و طول متن آن باید بین ۳ تا ۶۰ نویسه باشد.

---

## انواع input در HTML

### ورودی متن (text)

برای دریافت متن کوتاه مانند نام، نام خانوادگی و نام کاربری استفاده می‌شود.

```html
<label for="fullname">نام و نام خانوادگی:</label>

<input
    type="text"
    id="fullname"
    name="fullname"
    placeholder="مثلاً علی رضایی"
    required
>
```

ویژگی‌های پرکاربرد:

- `placeholder`: نمایش متن راهنما.
- `minlength`: حداقل طول مجاز.
- `maxlength`: حداکثر طول مجاز.
- `required`: اجباری بودن ورودی.

مثال محدود کردن طول:

```html
<input
    type="text"
    name="username"
    minlength="4"
    maxlength="20"
    required
>
```

در این مثال طول مقدار باید بین ۴ تا ۲۰ نویسه باشد.

### ورودی ایمیل (email)

برای دریافت آدرس ایمیل استفاده می‌شود. مرورگر می‌تواند قالب معمول ایمیل را بررسی کند.

```html
<label for="email">آدرس ایمیل:</label>

<input
    type="email"
    id="email"
    name="email"
    placeholder="example@gmail.com"
    autocomplete="email"
    required
>
```

مثال‌های معمول:

- `user@example.com`: قالب معتبر.
- `user.example.com`: فاقد قالب معمول ایمیل.
- `user@`: فاقد بخش دامنه کامل.

اعتبارسنجی مرورگر تضمین نمی‌کند که آدرس واقعاً وجود داشته باشد یا به کاربر موردنظر تعلق داشته باشد. برای تأیید مالکیت ایمیل، معمولاً باید پیام تأیید ارسال شود.

### ورودی رمز عبور (password)

برای دریافت رمز عبور استفاده می‌شود. مرورگر معمولاً نویسه‌های واردشده را به‌صورت مخفی نمایش می‌دهد.

```html
<label for="password">رمز عبور:</label>

<input
    type="password"
    id="password"
    name="password"
    minlength="8"
    autocomplete="new-password"
    required
>
```

برای فرم ورود بهتر است از مقدار مناسب `autocomplete` استفاده شود:

```html
<input
    type="password"
    name="password"
    autocomplete="current-password"
    required
>
```

- `current-password`: برای رمز عبور فعلی در فرم ورود.
- `new-password`: برای ساخت رمز عبور جدید یا ثبت‌نام.

**نکته امنیتی:** مخفی شدن متن رمز عبور فقط نحوه نمایش آن را تغییر می‌دهد؛ این ویژگی به‌تنهایی رمز را رمزنگاری یا محافظت نمی‌کند.

همچنین بهتر است رمز عبور به‌صورت متن ساده در URL قرار نگیرد.

### 4.4. ورودی عدد (number)

برای دریافت مقادیر عددی مانند سن، تعداد کالا یا امتیاز استفاده می‌شود.

```html
<label for="age">سن:</label>

<input
    type="number"
    id="age"
    name="age"
    min="1"
    max="120"
    step="1"
    required
>
```

ویژگی‌های مهم:

- `min`: حداقل مقدار.
- `max`: حداکثر مقدار.
- `step`: گام تغییر مقدار.

مثال:

```html
<input type="number" name="quantity" min="1" max="50" step="1">
```

این ورودی برای تعداد صحیح کالا بین ۱ تا ۵۰ مناسب است.

برای دریافت پول یا مقادیر اعشاری می‌توان از `step` مناسب استفاده کرد:

```html
<input type="number" name="price" min="0" step="0.01">
```

**نکته:** `type="number"` برای مقادیر عددی واقعی مناسب است؛ برای شماره تلفن، کد ملی یا کد پستی معمولاً از `text` استفاده کنید، چون این مقادیر شناسه هستند و ممکن است با صفر شروع شوند.

### 4.5. ورودی تاریخ (date)

برای انتخاب تاریخ از رابط تقویم مرورگر استفاده می‌شود.

```html
<label for="birthdate">تاریخ تولد:</label>

<input
    type="date"
    id="birthdate"
    name="birthdate"
    min="1900-01-01"
    max="2026-12-31"
    required
>
```

قالب مقدار تاریخ در HTML استاندارد به صورت زیر است:

```text
YYYY-MM-DD
```

مثال:

```text
2000-05-20
```

ظاهر تقویم ممکن است با توجه به مرورگر، سیستم‌عامل و تنظیمات منطقه‌ای متفاوت باشد.

**توجه:** `type="date"` از تقویم میلادی استاندارد HTML استفاده می‌کند؛ برای انتخاب و نمایش تاریخ شمسی باید از راهکار جداگانه، مانند یک date picker سازگار با تقویم جلالی، استفاده کنید.

### 4.6. ورودی زمان (time)

برای انتخاب ساعت و دقیقه استفاده می‌شود.

```html
<label for="meeting-time">ساعت جلسه:</label>

<input
    type="time"
    id="meeting-time"
    name="meeting_time"
    min="09:00"
    max="17:00"
    required
>
```

قالب معمول مقدار:

```text
HH:MM
```

مثال:

```text
14:30
```

با توجه به نیاز می‌توان از `step` برای تعیین دقت انتخاب زمان استفاده کرد:

```html
<input type="time" name="time" step="900">
```

مقدار `900` بر حسب ثانیه است؛ در این مثال فاصله انتخاب‌ها ۱۵ دقیقه خواهد بود.

### 4.7. تاریخ و زمان

برای دریافت تاریخ و زمان با هم، معمولاً از دو ورودی مستقل استفاده می‌کنیم:

```html
<label for="date">تاریخ:</label>
<input type="date" id="date" name="date" required>

<label for="time">ساعت:</label>
<input type="time" id="time" name="time" required>
```

این روش برای فرم رزرو، تعیین زمان جلسه یا برنامه‌ریزی مناسب است.

توجه داشته باشید که `datetime-local` نیز وجود دارد:

```html
<input
    type="datetime-local"
    name="appointment"
    required
>
```

این ورودی تاریخ و زمان محلی را دریافت می‌کند، اما به‌تنهایی منطقه زمانی یا اختلاف ساعت UTC را مشخص نمی‌کند.

### 4.8. انتخاب یک گزینه با Radio

زمانی استفاده می‌شود که کاربر باید فقط یک گزینه از یک گروه را انتخاب کند.

```html
<fieldset>
    <legend>روش ارسال سفارش:</legend>

    <label>
        <input type="radio" name="shipping" value="standard" required>
        ارسال عادی
    </label>

    <label>
        <input type="radio" name="shipping" value="express">
        ارسال سریع
    </label>

    <label>
        <input type="radio" name="shipping" value="pickup">
        دریافت حضوری
    </label>
</fieldset>
```

**نکته مهم:** برای قرار گرفتن گزینه‌ها در یک گروه، باید `name` آن‌ها یکسان باشد.

مقدار `value` مشخص می‌کند که هنگام انتخاب هر گزینه چه داده‌ای ارسال شود.

### 4.9. انتخاب چند گزینه با Checkbox

برای زمانی که کاربر می‌تواند یک یا چند گزینه را انتخاب کند، از `checkbox` استفاده می‌شود.

```html
<fieldset>
    <legend>علاقه‌مندی‌ها:</legend>

    <label>
        <input type="checkbox" name="interests" value="programming">
        برنامه‌نویسی
    </label>

    <label>
        <input type="checkbox" name="interests" value="design">
        طراحی
    </label>

    <label>
        <input type="checkbox" name="interests" value="music">
        موسیقی
    </label>
</fieldset>
```

برای انتخاب اولیه یک گزینه:

```html
<input type="checkbox" name="newsletter" value="yes" checked>
```

تفاوت مهم:

- `radio`: معمولاً فقط یک گزینه از گروه انتخاب می‌شود.
- `checkbox`: هر گزینه مستقل است و چند گزینه می‌توانند انتخاب شوند.

در فرم‌های استاندارد، فقط Checkboxهای انتخاب‌شده ارسال می‌شوند.

### 4.10. انتخاب فایل (file)

برای انتخاب فایل از دستگاه کاربر استفاده می‌شود.

```html
<label for="avatar">تصویر پروفایل:</label>

<input
    type="file"
    id="avatar"
    name="avatar"
    accept="image/png, image/jpeg, image/webp"
>
```

برای انتخاب چند فایل:

```html
<input type="file" name="documents" multiple>
```

برای پیشنهاد انتخاب تصاویر:

```html
<input type="file" name="images" accept="image/*" multiple>
```

ویژگی `accept` به مرورگر کمک می‌کند فایل‌های مناسب را پیشنهاد دهد، اما **محدودیت امنیتی قطعی نیست**. سرور باید نوع، اندازه و محتوای واقعی فایل را بررسی کند.

برای ارسال فایل از طریق فرم HTML معمولاً به این تنظیمات نیاز داریم:

```html
<form action="/upload" method="post" enctype="multipart/form-data">
    <input type="file" name="document" required>
    <button type="submit">بارگذاری</button>
</form>
```

در پروژه‌های واقعی، ارسال فایل باید با بررسی امنیتی سمت سرور همراه باشد.

### 4.11. انتخاب رنگ (color)

برای انتخاب یک رنگ استفاده می‌شود.

```html
<label for="theme-color">رنگ قالب:</label>

<input
    type="color"
    id="theme-color"
    name="theme_color"
    value="#3366ff"
>
```

مقدار رنگ معمولاً در قالب Hex مانند `#3366ff` ارائه می‌شود.

این ورودی برای تنظیم رنگ پس‌زمینه، رنگ قالب یا رنگ موردعلاقه کاربر کاربرد دارد.

### 4.12. محدوده عددی (range)

برای انتخاب یک مقدار در یک بازه، معمولاً با اسلایدر، استفاده می‌شود.

```html
<label for="volume">شدت صدا:</label>

<input
    type="range"
    id="volume"
    name="volume"
    min="0"
    max="100"
    step="5"
    value="50"
>
```

مقدار اولیه در این مثال ۵۰ است و کاربر می‌تواند مقدار را در بازه ۰ تا ۱۰۰ تغییر دهد.

نمایش مقدار انتخاب‌شده با JavaScript:

```html
<label for="volume">شدت صدا:</label>
<input type="range" id="volume" min="0" max="100" value="50">

<output id="volume-value">50</output>

<script>
    const volume = document.querySelector("#volume");
    const output = document.querySelector("#volume-value");

    volume.addEventListener("input", () => {
        output.value = volume.value;
    });
</script>
```

### 4.13. ورودی تلفن (tel)

برای دریافت شماره تلفن استفاده می‌شود.

```html
<label for="phone">شماره تلفن:</label>

<input
    type="tel"
    id="phone"
    name="phone"
    placeholder="+989121234567"
    autocomplete="tel"
    required
>
```

نوع `tel` معمولاً صفحه‌کلید مناسب‌تری را در دستگاه‌های موبایل نمایش می‌دهد، اما به‌تنهایی شماره تلفن را اعتبارسنجی نمی‌کند.

برای شماره تلفن بین‌المللی بهتر است قالب مورد انتظار را مشخص کنید و اعتبارسنجی اصلی را متناسب با نیاز برنامه انجام دهید.

### 4.14. جست‌وجو (search)

برای دریافت عبارت جست‌وجو استفاده می‌شود.

```html
<form action="/search" method="get">
    <label for="query">جست‌وجو:</label>

    <input
        type="search"
        id="query"
        name="q"
        placeholder="عبارت موردنظر را وارد کنید"
        required
    >

    <button type="submit">جست‌وجو</button>
</form>
```

در برخی مرورگرها، این ورودی امکاناتی مانند دکمه پاک کردن متن دارد.

### 4.15. آدرس اینترنتی (url)

برای دریافت URL استفاده می‌شود.

```html
<label for="website">آدرس وب‌سایت:</label>

<input
    type="url"
    id="website"
    name="website"
    placeholder="https://example.com"
>
```

مرورگر قالب معمول URL را بررسی می‌کند؛ با این حال، برای محدود کردن دامنه‌های مجاز یا جلوگیری از آدرس‌های ناامن باید اعتبارسنجی سمت سرور هم انجام شود.

### 4.16. ورودی مخفی (hidden)

برای ارسال یک مقدار همراه فرم بدون نمایش مستقیم ورودی به کاربر استفاده می‌شود.

```html
<input type="hidden" name="source" value="website">
```

این مقدار در فرم ارسال می‌شود، اما کاربر می‌تواند از طریق ابزارهای مرورگر آن را مشاهده یا تغییر دهد.

**نکته امنیتی:** از `hidden` برای نگهداری رمز عبور، کلید محرمانه، اطلاعات حساس یا مقادیری که باید قابل اعتماد باشند استفاده نکنید.

### 4.17. ورودی ماه و هفته

**انتخاب ماه (`month`):**

```html
<label for="billing-month">ماه صورت‌حساب:</label>

<input
    type="month"
    id="billing-month"
    name="billing_month"
>
```

مقدار استاندارد معمولاً به صورت `YYYY-MM` است.

**انتخاب هفته (`week`):**

```html
<label for="week">هفته موردنظر:</label>

<input
    type="week"
    id="week"
    name="week"
>
```

مقدار استاندارد هفته معمولاً به شکل زیر است:

```text
2026-W12
```

پشتیبانی و ظاهر این ورودی‌ها ممکن است بین مرورگرها متفاوت باشد.

### 4.18. ورودی‌های عددی دیگر

ورودی `number` برای دریافت مقادیر عددی به کار می‌رود و با ویژگی‌های `min`، `max` و `step` قابل تنظیم است.

مثال دریافت امتیاز:

```html
<input
    type="number"
    name="rating"
    min="1"
    max="5"
    step="1"
>
```

برای انتخاب یک مقدار عددی پیوسته، معمولاً `range` مناسب‌تر است.

نکته: ویژگی `type="datetime"` در HTML مدرن یک نوع ورودی استاندارد و پشتیبانی‌شده عمومی نیست؛ برای دریافت تاریخ و زمان محلی از `datetime-local` استفاده کنید.

---

## 5. دکمه‌های فرم

تگ `button` و ورودی‌های دکمه‌ای انواع مختلفی دارند.

### دکمه ارسال فرم

```html
<button type="submit">ارسال اطلاعات</button>
```

این دکمه فرم را ارسال می‌کند.

### دکمه پاک‌کردن فرم

```html
<button type="reset">پاک کردن فرم</button>
```

این دکمه مقادیر ورودی‌ها را به حالت اولیه آن‌ها بازمی‌گرداند؛ لزوماً همه فیلدها را خالی نمی‌کند.

### دکمه معمولی

```html
<button type="button">اجرای عملیات</button>
```

این دکمه به‌تنهایی فرم را ارسال نمی‌کند و معمولاً همراه JavaScript استفاده می‌شود.

همچنین می‌توان از انواع قدیمی‌تر `input` برای دکمه استفاده کرد:

```html
<input type="submit" value="ارسال">
<input type="reset" value="بازنشانی">
<input type="button" value="عملیات">
```

در کدهای جدید، تگ `button` معمولاً انعطاف‌پذیری بیشتری دارد.

---

## 6. ارسال اطلاعات فرم

برای ارسال اطلاعات باید به ویژگی‌های `action`، `method` و `name` توجه کنیم.

### روش GET

```html
<form action="/search" method="get">
    <input type="search" name="q" required>
    <button type="submit">جست‌وجو</button>
</form>
```

اگر کاربر عبارت `html tutorial` را وارد کند، مرورگر می‌تواند درخواستی با URL مشابه زیر ایجاد کند:

```text
/search?q=html+tutorial
```

کاربردهای معمول GET:

- جست‌وجو
- فیلتر کردن نتایج
- صفحه‌بندی
- دریافت اطلاعات

از GET برای ارسال رمز عبور یا داده‌های حساس استفاده نکنید؛ اطلاعات ممکن است در URL، تاریخچه مرورگر و گزارش‌های سرور ثبت شوند.

### روش POST

```html
<form action="/register" method="post">
    <input type="text" name="username" required>
    <input type="email" name="email" required>
    <button type="submit">ثبت‌نام</button>
</form>
```

POST داده‌ها را معمولاً در بدنه درخواست HTTP ارسال می‌کند و برای عملیات ایجاد یا تغییر داده مناسب است.

البته POST به‌تنهایی اطلاعات را رمزنگاری نمی‌کند. برای انتقال امن داده‌ها باید از HTTPS استفاده شود.

### ارسال اطلاعات فایل

```html
<form
    action="/upload"
    method="post"
    enctype="multipart/form-data"
>
    <input type="file" name="file" required>
    <button type="submit">ارسال فایل</button>
</form>
```

در این حالت، `multipart/form-data` برای انتقال محتوای فایل لازم است.

---

## 7. ویژگی‌های اعتبارسنجی

HTML امکانات اولیه‌ای برای اعتبارسنجی ورودی‌ها دارد.

### 7.1. اجباری کردن ورودی

```html
<input type="text" name="fullname" required>
```

کاربر نمی‌تواند فرم را با این فیلد خالی از اعتبارسنجی معمول مرورگر عبور دهد.

### 7.2. تعیین حداقل و حداکثر طول

```html
<input
    type="text"
    name="username"
    minlength="4"
    maxlength="20"
    required
>
```

### 7.3. تعیین بازه عددی

```html
<input
    type="number"
    name="age"
    min="18"
    max="100"
    required
>
```

### 7.4. تعیین الگوی مجاز

ویژگی `pattern` یک الگوی منظم (Regular Expression) را برای اعتبارسنجی مقدار ورودی مشخص می‌کند.

```html
<label for="username">نام کاربری انگلیسی:</label>

<input
    type="text"
    id="username"
    name="username"
    pattern="[A-Za-z0-9_]{4,20}"
    title="از ۴ تا ۲۰ حرف انگلیسی، عدد یا زیرخط استفاده کنید."
    required
>
```

این الگو اجازه استفاده از حروف انگلیسی، اعداد و زیرخط را با طول ۴ تا ۲۰ نویسه می‌دهد.

نکته: `pattern` به‌طور معمول برای مقدار غیرخالی بررسی می‌شود؛ برای اجباری کردن ورودی همچنان از `required` استفاده کنید.

### 7.5. تفاوت disabled و readonly

```html
<input type="text" name="username" value="Ali" readonly>

<input type="text" name="reference" value="ABC123" disabled>
```

تفاوت اصلی:

- `readonly`: مقدار قابل ویرایش نیست، اما معمولاً هنگام ارسال فرم ارسال می‌شود.
- `disabled`: ورودی غیرفعال است و معمولاً در ارسال فرم شرکت نمی‌کند.

هیچ‌یک از این دو ویژگی، اعتبار داده را در سمت سرور تضمین نمی‌کند.

### 7.6. نکته مهم درباره اعتبارسنجی

اعتبارسنجی HTML برای تجربه کاربری مفید است، اما کافی نیست. کاربر می‌تواند درخواست HTTP را مستقیماً ارسال کند یا محدودیت‌های مرورگر را دور بزند.

بنابراین، اعتبارسنجی نهایی باید در سمت سرور انجام شود.

---

## 8. دریافت اطلاعات با JavaScript

HTML برای ساخت فرم و JavaScript برای خواندن و پردازش اطلاعات آن کاربرد دارد.

مثال دریافت نام کاربر:

```html
<label for="username">نام کاربری:</label>
<input type="text" id="username" name="username">

<button type="button" id="show-btn">نمایش مقدار</button>

<p id="result"></p>

<script>
    const usernameInput = document.querySelector("#username");
    const showButton = document.querySelector("#show-btn");
    const result = document.querySelector("#result");

    showButton.addEventListener("click", () => {
        const username = usernameInput.value.trim();

        result.textContent = username
            ? `نام کاربری: ${username}`
            : "لطفاً نام کاربری را وارد کنید.";
    });
</script>
```

### توضیح کد

**دسترسی به ورودی:**

```javascript
const usernameInput = document.querySelector("#username");
```

با استفاده از `querySelector`، عنصر دارای شناسه `username` انتخاب می‌شود.

**دریافت مقدار:**

```javascript
const username = usernameInput.value;
```

ویژگی `value` مقدار فعلی ورودی را برمی‌گرداند.

**حذف فاصله‌های ابتدا و انتها:**

```javascript
const username = usernameInput.value.trim();
```

متد `trim()` فاصله‌های ابتدا و انتهای رشته را حذف می‌کند.

**نمایش خروجی امن:**

```javascript
result.textContent = username;
```

برای نمایش متنی که کاربر وارد کرده، `textContent` انتخاب مناسبی است؛ برخلاف `innerHTML`، مقدار را به‌عنوان HTML تفسیر نمی‌کند.

### دریافت مقدار با رویداد input

اگر بخواهیم مقدار را هنگام تایپ کاربر دریافت کنیم:

```html
<input type="text" id="live-input" placeholder="شروع به تایپ کنید">
<p id="live-output"></p>

<script>
    const input = document.querySelector("#live-input");
    const output = document.querySelector("#live-output");

    input.addEventListener("input", () => {
        output.textContent = input.value;
    });
</script>
```

رویداد `input` با تغییر مقدار ورودی در اثر تایپ یا برخی عملیات دیگر اجرا می‌شود.

### دریافت اطلاعات هنگام ارسال فرم

```html
<form id="contact-form">
    <input type="text" name="fullname" placeholder="نام" required>
    <input type="email" name="email" placeholder="ایمیل" required>
    <button type="submit">ارسال</button>
</form>

<script>
    const form = document.querySelector("#contact-form");

    form.addEventListener("submit", (event) => {
        event.preventDefault();

        const fullname = form.elements.fullname.value.trim();
        const email = form.elements.email.value.trim();

        console.log({ fullname, email });
    });
</script>
```

در این مثال، `preventDefault()` از ارسال معمول فرم جلوگیری می‌کند تا اطلاعات ابتدا با JavaScript پردازش شوند.

این کد اطلاعات را فقط در کنسول مرورگر نمایش می‌دهد و آن‌ها را به سرور ارسال نمی‌کند.

---

## 9. دریافت اطلاعات با FormData

برای جمع‌آوری اطلاعات فرم، می‌توان از API استاندارد `FormData` استفاده کرد.

```html
<form id="register-form">
    <input type="text" name="fullname" required>
    <input type="email" name="email" required>
    <input type="password" name="password" required>

    <button type="submit">ثبت‌نام</button>
</form>

<script>
    const form = document.querySelector("#register-form");

    form.addEventListener("submit", (event) => {
        event.preventDefault();

        const formData = new FormData(form);

        const fullname = formData.get("fullname");
        const email = formData.get("email");
        const password = formData.get("password");

        console.log(fullname, email);

        // در برنامه واقعی، رمز عبور را در کنسول چاپ نکنید.
    });
</script>
```

### متدهای مهم FormData

| متد | کاربرد |
|---|---|
| `get(name)` | دریافت اولین مقدار با نام مشخص |
| `getAll(name)` | دریافت همه مقادیر دارای یک نام |
| `has(name)` | بررسی وجود نام |
| `append(name, value)` | افزودن مقدار جدید |
| `set(name, value)` | تنظیم یا جایگزینی مقدار |
| `delete(name)` | حذف مقدار |

مثال دریافت چند گزینه Checkbox:

```html
<form id="interest-form">
    <label>
        <input type="checkbox" name="interests" value="coding">
        برنامه‌نویسی
    </label>

    <label>
        <input type="checkbox" name="interests" value="design">
        طراحی
    </label>

    <button type="submit">ثبت</button>
</form>

<script>
    const form = document.querySelector("#interest-form");

    form.addEventListener("submit", (event) => {
        event.preventDefault();

        const formData = new FormData(form);
        const interests = formData.getAll("interests");

        console.log(interests);
    });
</script>
```

اگر هر دو گزینه انتخاب شوند، خروجی می‌تواند چنین باشد:

```javascript
["coding", "design"]
```

### ارسال اطلاعات با Fetch

در صورت وجود یک API سمت سرور:

```javascript
const form = document.querySelector("#register-form");

form.addEventListener("submit", async (event) => {
    event.preventDefault();

    if (!form.reportValidity()) {
        return;
    }

    const formData = new FormData(form);

    try {
        const response = await fetch("/api/register", {
            method: "POST",
            body: formData
        });

        if (!response.ok) {
            throw new Error("ارسال اطلاعات ناموفق بود.");
        }

        console.log("اطلاعات با موفقیت ارسال شد.");
    } catch (error) {
        console.error(error.message);
    }
});
```

این مثال فرض می‌کند که مسیر `/api/register` در سرور وجود دارد. در صورت ارسال `FormData`، معمولاً نباید `Content-Type` را دستی تعیین کنید؛ مرورگر آن را همراه مرزهای لازم برای داده‌های چندبخشی تنظیم می‌کند.

نکته: `reportValidity()` برای نمایش خطاهای اعتبارسنجی مرورگر است و جایگزین اعتبارسنجی سمت سرور نیست.

---

## 10. استایل‌دهی فرم با CSS

برای خوانایی بیشتر می‌توان از CSS استفاده کرد.

```html
<style>
    * {
        box-sizing: border-box;
    }

    body {
        font-family: Arial, sans-serif;
        line-height: 1.8;
        padding: 24px;
    }

    .form-container {
        max-width: 500px;
        margin: 0 auto;
    }

    .form-group {
        margin-bottom: 16px;
    }

    label {
        display: block;
        margin-bottom: 6px;
    }

    input,
    select,
    textarea {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 6px;
        font: inherit;
    }

    input:focus,
    select:focus,
    textarea:focus {
        outline: 2px solid #3366ff;
        outline-offset: 1px;
    }

    button {
        padding: 10px 18px;
        border: none;
        border-radius: 6px;
        cursor: pointer;
    }
</style>
```

نکته: برای `checkbox`، `radio` و برخی ورودی‌های دیگر معمولاً بهتر است عرض ۱۰۰ درصد اعمال نشود. می‌توان آن‌ها را جداگانه استایل‌دهی کرد.

---

## 11. پروژه عملی ثبت‌نام کاربر

در این مثال یک فرم ثبت‌نام شامل نام، ایمیل، رمز عبور، تاریخ تولد، شماره تلفن، شهر، جنسیت و پذیرش قوانین ایجاد می‌کنیم.

کد زیر را در فایل `index.html` ذخیره کنید.

```html
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>فرم ثبت‌نام</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            font-family: Tahoma, Arial, sans-serif;
            background: #f5f5f5;
            margin: 0;
            padding: 24px;
            line-height: 1.8;
        }

        .container {
            max-width: 520px;
            margin: 0 auto;
            background: white;
            padding: 24px;
            border-radius: 12px;
        }

        h1 {
            font-size: 24px;
            text-align: center;
        }

        .form-group {
            margin-bottom: 16px;
        }

        label {
            display: block;
            margin-bottom: 6px;
        }

        input:not([type="radio"]):not([type="checkbox"]),
        select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font: inherit;
        }

        input[type="radio"],
        input[type="checkbox"] {
            margin-left: 6px;
        }

        .option-label {
            display: inline-block;
            margin-left: 12px;
        }

        button {
            width: 100%;
            padding: 12px;
            border: 0;
            border-radius: 6px;
            cursor: pointer;
            font: inherit;
            background: #2457d6;
            color: white;
        }

        #result {
            overflow-wrap: anywhere;
            margin-top: 16px;
        }
    </style>
</head>

<body>
    <main class="container">
        <h1>فرم ثبت‌نام</h1>

        <form id="register-form">
            <div class="form-group">
                <label for="fullname">نام و نام خانوادگی:</label>
                <input
                    type="text"
                    id="fullname"
                    name="fullname"
                    minlength="3"
                    maxlength="80"
                    autocomplete="name"
                    required
                >
            </div>

            <div class="form-group">
                <label for="email">ایمیل:</label>
                <input
                    type="email"
                    id="email"
                    name="email"
                    autocomplete="email"
                    required
                >
            </div>

            <div class="form-group">
                <label for="password">رمز عبور:</label>
                <input
                    type="password"
                    id="password"
                    name="password"
                    minlength="8"
                    autocomplete="new-password"
                    required
                >
            </div>

            <div class="form-group">
                <label for="birthdate">تاریخ تولد:</label>
                <input
                    type="date"
                    id="birthdate"
                    name="birthdate"
                    required
                >
            </div>

            <div class="form-group">
                <label for="phone">شماره تلفن:</label>
                <input
                    type="tel"
                    id="phone"
                    name="phone"
                    autocomplete="tel"
                    placeholder="+989121234567"
                    required
                >
            </div>

            <div class="form-group">
                <label for="city">شهر:</label>
                <select id="city" name="city" required>
                    <option value="">انتخاب شهر</option>
                    <option value="tehran">تهران</option>
                    <option value="shiraz">شیراز</option>
                    <option value="isfahan">اصفهان</option>
                    <option value="tabriz">تبریز</option>
                </select>
            </div>

            <fieldset class="form-group">
                <legend>جنسیت:</legend>

                <label class="option-label">
                    <input type="radio" name="gender" value="male" required>
                    مرد
                </label>

                <label class="option-label">
                    <input type="radio" name="gender" value="female">
                    زن
                </label>

                <label class="option-label">
                    <input type="radio" name="gender" value="other">
                    ترجیح می‌دهم مشخص نکنم
                </label>
            </fieldset>

            <div class="form-group">
                <label>
                    <input type="checkbox" name="terms" value="accepted" required>
                    قوانین را می‌پذیرم.
                </label>
            </div>

            <button type="submit">ثبت‌نام</button>
        </form>

        <p id="result" role="status" aria-live="polite"></p>
    </main>

    <script>
        const form = document.querySelector("#register-form");
        const result = document.querySelector("#result");

        form.addEventListener("submit", (event) => {
            event.preventDefault();

            if (!form.reportValidity()) {
                return;
            }

            const formData = new FormData(form);

            const fullname = formData.get("fullname").trim();
            const email = formData.get("email").trim();
            const birthdate = formData.get("birthdate");
            const phone = formData.get("phone").trim();
            const city = formData.get("city");
            const gender = formData.get("gender");

            // رمز عبور را در خروجی نمایش نمی‌دهیم.
            result.textContent =
                `اطلاعات فرم آماده است: ${fullname}، ${email}، ` +
                `${birthdate}، ${phone}، ${city}، ${gender}`;

            // این مثال فقط داده‌ها را در صفحه نمایش می‌دهد.
            // برای ثبت واقعی، اطلاعات باید به سرور ارسال شوند.
        });
    </script>
</body>
</html>
```

### ویژگی‌های پروژه

- استفاده از انواع مختلف `input`.
- تعیین فیلدهای اجباری با `required`.
- بررسی اولیه قالب ایمیل.
- تعیین حداقل طول رمز عبور.
- استفاده از `select` برای انتخاب شهر.
- استفاده از `radio` برای انتخاب یک گزینه.
- استفاده از `checkbox` برای پذیرش قوانین.
- دریافت اطلاعات با `FormData`.
- نمایش خروجی با `textContent`.
- سازگاری اولیه با نمایش راست‌به‌چپ زبان فارسی.

**توجه:** این پروژه یک نمونه آموزشی سمت مرورگر است. اطلاعات در پایگاه داده ذخیره نمی‌شوند و احراز هویت واقعی انجام نمی‌شود.

---

## 12. نکات امنیتی

در طراحی فرم‌های واقعی، رعایت نکات زیر ضروری است.

### 12.1. اعتبارسنجی سمت سرور

تمام داده‌های ورودی باید در سمت سرور نیز بررسی شوند. به داده‌های مرورگر به‌عنوان داده‌های قابل اعتماد نگاه نکنید.

### 12.2. استفاده از HTTPS

برای ارسال اطلاعات حساس، از ارتباط امن HTTPS استفاده کنید.

### 12.3. محافظت از رمز عبور

- رمز عبور را در URL قرار ندهید.
- آن را در کنسول مرورگر یا گزارش‌های برنامه چاپ نکنید.
- رمز عبور را به‌صورت متن ساده در پایگاه داده ذخیره نکنید.
- در سمت سرور از روش‌های مناسب هش رمز عبور، مانند Argon2id یا الگوریتم‌های استاندارد مناسب دیگر، استفاده کنید.
- از سیاست‌های مناسب برای محدود کردن تلاش‌های ورود و محافظت از حساب‌ها بهره ببرید.

### 12.4. جلوگیری از تزریق کد

هنگام نمایش اطلاعات کاربر، از روش‌هایی مانند `textContent` استفاده کنید و از قرار دادن ورودی‌های کنترل‌نشده در `innerHTML` خودداری کنید.

### 12.5. محافظت در برابر درخواست‌های جعلی

در برنامه‌هایی که با نشست کاربر و کوکی احراز هویت کار می‌کنند، متناسب با معماری برنامه از راهکارهای مقابله با CSRF استفاده کنید.

### 12.6. بررسی فایل‌های آپلودشده

برای فایل‌های ارسالی موارد زیر را در سمت سرور بررسی کنید:

- اندازه فایل
- نوع واقعی فایل
- محتوای فایل
- نام و مسیر ذخیره‌سازی
- مجوزهای دسترسی
- محدودیت تعداد و نرخ بارگذاری

ویژگی `accept` به‌تنهایی برای ایمن‌سازی آپلود کافی نیست.

### 12.7. اطلاعات حساس در فیلدهای مخفی

اطلاعات موجود در `input type="hidden"` محرمانه نیستند. کاربر می‌تواند آن‌ها را مشاهده و تغییر دهد؛ بنابراین تصمیم‌های امنیتی نباید صرفاً بر اساس این مقادیر گرفته شوند.

---

## 13. اشتباهات رایج

### اشتباه اول: فراموش کردن name

```html
<!-- نادرست برای ارسال مقدار با نام مشخص -->
<input type="text" id="username">

<!-- درست -->
<input type="text" id="username" name="username">
```

### اشتباه دوم: استفاده از number برای شماره تلفن

```html
<!-- نامناسب -->
<input type="number" name="phone">

<!-- مناسب‌تر -->
<input type="tel" name="phone">
```

شماره تلفن ممکن است با صفر شروع شود یا شامل علامت `+` باشد.

### اشتباه سوم: استفاده از placeholder به‌جای label

```html
<!-- بهتر است عنوان قابل مشاهده نیز وجود داشته باشد -->
<label for="email">ایمیل:</label>
<input type="email" id="email" name="email" placeholder="example@mail.com">
```

`placeholder` جایگزین مناسبی برای عنوان دائمی و قابل دسترس ورودی نیست.

### اشتباه چهارم: اعتماد به اعتبارسنجی HTML

وجود `required` یا `pattern` تضمین نمی‌کند که داده دریافتی در سمت سرور معتبر است.

### اشتباه پنجم: استفاده نادرست از value در Checkbox

```html
<input type="checkbox" name="newsletter" value="yes">
```

ویژگی `value` مشخص می‌کند چه مقداری هنگام انتخاب شدن ارسال شود؛ این ویژگی به‌تنهایی به معنی انتخاب اولیه نیست. برای انتخاب اولیه از `checked` استفاده کنید.

### اشتباه ششم: استفاده از button بدون type

داخل فرم بهتر است نوع دکمه را صریح مشخص کنید:

```html
<button type="button">اجرای عملیات</button>
<button type="submit">ارسال فرم</button>
```

دکمه‌ای که داخل فرم قرار دارد و نوع مشخصی ندارد، معمولاً رفتار ارسال فرم را خواهد داشت.

### اشتباه هفتم: تصور رمزنگاری شدن password

```html
<input type="password" name="password">
```

این ورودی فقط نمایش متن را مخفی می‌کند. امنیت انتقال و ذخیره‌سازی رمز عبور به راهکارهای دیگری نیاز دارد.

---

## 14. جمع‌بندی

در HTML، تگ `input` یکی از اصلی‌ترین ابزارهای دریافت اطلاعات از کاربر است. با تغییر ویژگی `type` می‌توان انواع مختلفی از ورودی‌ها را ایجاد کرد.

| نوع ورودی | کاربرد |
|---|---|
| `text` | دریافت متن کوتاه |
| `email` | دریافت ایمیل |
| `password` | دریافت رمز عبور |
| `number` | دریافت مقدار عددی |
| `date` | انتخاب تاریخ |
| `time` | انتخاب ساعت |
| `datetime-local` | انتخاب تاریخ و زمان محلی |
| `radio` | انتخاب یک گزینه |
| `checkbox` | انتخاب چند گزینه |
| `file` | انتخاب فایل |
| `color` | انتخاب رنگ |
| `range` | انتخاب مقدار با اسلایدر |
| `tel` | دریافت شماره تلفن |
| `search` | دریافت عبارت جست‌وجو |
| `url` | دریافت آدرس اینترنتی |
| `hidden` | ارسال مقدار بدون نمایش مستقیم ورودی |
| `month` | انتخاب ماه |
| `week` | انتخاب هفته |

برای ساخت فرم‌های حرفه‌ای، به این نکات توجه کنید:

1. از `label` برای عنوان‌گذاری صحیح ورودی‌ها استفاده کنید.
2. برای فیلدهایی که باید ارسال شوند، `name` مناسب تعیین کنید.
3. برای اعتبارسنجی اولیه از ویژگی‌هایی مانند `required`، `min`، `max` و `pattern` بهره ببرید.
4. برای خواندن اطلاعات فرم در JavaScript از `value` یا `FormData` استفاده کنید.
5. برای انتقال اطلاعات حساس از HTTPS بهره ببرید.
6. داده‌ها را در سمت سرور مجدداً اعتبارسنجی کنید.
7. رمز عبور و اطلاعات حساس را در خروجی‌های قابل مشاهده یا گزارش‌ها قرار ندهید.

با یادگیری این مفاهیم، می‌توانید فرم‌های ثبت‌نام، ورود، جست‌وجو، رزرو، سفارش و بسیاری از فرم‌های دیگر را در وب‌سایت خود پیاده‌سازی کنید.

---

## منابع پیشنهادی

- [MDN — HTML input element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
- [MDN — HTML forms](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms)
- [MDN — FormData API](https://developer.mozilla.org/en-US/docs/Web/API/FormData)
- [MDN — Constraint validation](https://developer.mozilla.org/en-US/docs/Web/HTML/Constraint_validation)
- [WHATWG — HTML Living Standard](https://html.spec.whatwg.org/multipage/input.html)
