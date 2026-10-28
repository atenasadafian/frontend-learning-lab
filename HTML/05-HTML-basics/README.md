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

### ورودی عدد (number)

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

### ورودی تاریخ (date)

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

### ورودی زمان (time)

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

### تاریخ و زمان

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

### انتخاب یک گزینه با Radio

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

### انتخاب چند گزینه با Checkbox

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

### انتخاب فایل (file)

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

### انتخاب رنگ (color)

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

### محدوده عددی (range)

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

### ورودی تلفن (tel)

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

### جست‌وجو (search)

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

### آدرس اینترنتی (url)

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

### ورودی مخفی (hidden)

برای ارسال یک مقدار همراه فرم بدون نمایش مستقیم ورودی به کاربر استفاده می‌شود.

```html
<input type="hidden" name="source" value="website">
```

این مقدار در فرم ارسال می‌شود، اما کاربر می‌تواند از طریق ابزارهای مرورگر آن را مشاهده یا تغییر دهد.

**نکته امنیتی:** از `hidden` برای نگهداری رمز عبور، کلید محرمانه، اطلاعات حساس یا مقادیری که باید قابل اعتماد باشند استفاده نکنید.

### ورودی ماه و هفته

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

### ورودی‌های عددی دیگر

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

## دکمه‌های فرم

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

## ارسال اطلاعات فرم

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

## ویژگی‌های اعتبارسنجی

HTML امکانات اولیه‌ای برای اعتبارسنجی ورودی‌ها دارد.

### اجباری کردن ورودی

```html
<input type="text" name="fullname" required>
```

کاربر نمی‌تواند فرم را با این فیلد خالی از اعتبارسنجی معمول مرورگر عبور دهد.

### تعیین حداقل و حداکثر طول

```html
<input
    type="text"
    name="username"
    minlength="4"
    maxlength="20"
    required
>
```

### تعیین بازه عددی

```html
<input
    type="number"
    name="age"
    min="18"
    max="100"
    required
>
```

### تعیین الگوی مجاز

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

### تفاوت disabled و readonly

```html
<input type="text" name="username" value="Ali" readonly>

<input type="text" name="reference" value="ABC123" disabled>
```

تفاوت اصلی:

- `readonly`: مقدار قابل ویرایش نیست، اما معمولاً هنگام ارسال فرم ارسال می‌شود.
- `disabled`: ورودی غیرفعال است و معمولاً در ارسال فرم شرکت نمی‌کند.

هیچ‌یک از این دو ویژگی، اعتبار داده را در سمت سرور تضمین نمی‌کند.

### نکته مهم درباره اعتبارسنجی

اعتبارسنجی HTML برای تجربه کاربری مفید است، اما کافی نیست. کاربر می‌تواند درخواست HTTP را مستقیماً ارسال کند یا محدودیت‌های مرورگر را دور بزند.

بنابراین، اعتبارسنجی نهایی باید در سمت سرور انجام شود.
