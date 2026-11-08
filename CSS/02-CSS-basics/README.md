# ویژگی‌های پایه‌ای CSS: رنگ، پس‌زمینه و فونت‌ها

سه مورد از مهم‌ترین قابلیت‌های CSS عبارت‌اند از:

1. **Color:** تعیین رنگ متن و سایر بخش‌های متنی.
2. **Background:** تعیین ظاهر پس‌زمینه عناصر HTML.
3. **Font:** تعیین نوع، اندازه، ضخامت و سبک نوشته‌ها.

این ویژگی‌ها نقش مهمی در خوانایی، زیبایی و تجربه کاربری صفحات وب دارند.

ساختار کلی تعریف ویژگی‌ها در CSS به شکل زیر است:

```css
selector {
    property: value;
}
```

مثال:

```css
p {
    color: blue;
    background-color: lightgray;
    font-size: 18px;
}
```

در این مثال:
- `p` انتخابگر پاراگراف است.
- `color` رنگ متن را تعیین می‌کند.
- `background-color` رنگ پس‌زمینه را مشخص می‌کند.
- `font-size` اندازه متن را تعیین می‌کند.

---

# 2. ویژگی رنگ (Color)

ویژگی `color` برای تعیین رنگ محتوای متنی یک عنصر استفاده می‌شود.

این ویژگی معمولاً رنگ موارد زیر را کنترل می‌کند:

- متن پاراگراف‌ها
- عنوان‌ها
- لینک‌ها
- نوشته‌های داخل دکمه‌ها
- محتوای متنی عناصر مختلف

## 2.1. روش‌های تعریف رنگ

در CSS روش‌های مختلفی برای مشخص کردن رنگ وجود دارد.

### روش اول: نام رنگ (Color Names)

در این روش از نام استاندارد رنگ‌ها استفاده می‌کنیم.

```css
h1 {
    color: red;
}

p {
    color: blue;
}

span {
    color: green;
}
```

نمونه‌ای از نام رنگ‌های CSS:

| نام رنگ | توضیح |
|---|---|
| `red` | قرمز |
| `blue` | آبی |
| `green` | سبز |
| `black` | مشکی |
| `white` | سفید |
| `yellow` | زرد |
| `orange` | نارنجی |
| `purple` | بنفش |
| `gray` | خاکستری |
| `pink` | صورتی |
| `transparent` | شفاف |

### روش دوم: کد HEX

یکی از رایج‌ترین روش‌های تعریف رنگ، استفاده از کدهای هگزادسیمال است.

ساختار کلی:

```css
color: #RRGGBB;
```

در این ساختار:

- `RR`: مقدار رنگ قرمز
- `GG`: مقدار رنگ سبز
- `BB`: مقدار رنگ آبی

هر بخش مقداری بین `00` تا `FF` دارد.

مثال:

```css
h1 {
    color: #FF0000;
}

p {
    color: #0000FF;
}

div {
    color: #008000;
}
```

چند نمونه:

| کد HEX | رنگ |
|---|---|
| `#FF0000` | قرمز |
| `#00FF00` | سبز |
| `#0000FF` | آبی |
| `#000000` | مشکی |
| `#FFFFFF` | سفید |
| `#FFFF00` | زرد |
| `#808080` | خاکستری |

**کدهای کوتاه HEX**

در صورتی که هر دو رقم هر بخش یکسان باشند، می‌توان از شکل سه‌رقمی استفاده کرد.

```css
color: #F00;
```

معادل است با:

```css
color: #FF0000;
```

**HEX همراه با شفافیت**

امکان تعریف میزان شفافیت نیز وجود دارد:

```css
color: #FF000080;
```

در این حالت دو رقم آخر میزان Alpha را مشخص می‌کنند.

### روش سوم: RGB

در روش RGB رنگ از ترکیب سه رنگ اصلی ساخته می‌شود:

- Red
- Green
- Blue

ساختار:

```css
color: rgb(red, green, blue);
```

هر مقدار می‌تواند بین 0 تا 255 باشد.

مثال:

```css
h1 {
    color: rgb(255, 0, 0);
}

p {
    color: rgb(0, 0, 255);
}

div {
    color: rgb(0, 128, 0);
}
```

### روش چهارم: RGBA

RGBA مشابه RGB است، اما یک مقدار اضافی برای شفافیت دارد.

ساختار:

```css
color: rgba(red, green, blue, alpha);
```

مقدار Alpha بین صفر و یک است:

- `0`: کاملاً شفاف
- `0.5`: نیمه‌شفاف
- `1`: کاملاً غیرشفاف

مثال:

```css
p {
    color: rgba(255, 0, 0, 0.5);
}
```

در این مثال متن قرمز با شفافیت 50 درصد نمایش داده می‌شود.

### روش پنجم: HSL

HSL مخفف سه مفهوم زیر است:

- Hue: نوع یا فام رنگ
- Saturation: میزان اشباع رنگ
- Lightness: میزان روشنایی

ساختار:

```css
color: hsl(hue, saturation, lightness);
```

مقادیر:

| پارامتر | محدوده |
|---|---|
| Hue | صفر تا 360 درجه |
| Saturation | صفر تا 100 درصد |
| Lightness | صفر تا 100 درصد |

مثال:

```css
h1 {
    color: hsl(0, 100%, 50%);
}

p {
    color: hsl(240, 100%, 50%);
}

div {
    color: hsl(120, 100%, 25%);
}
```

### روش ششم: HSLA

این روش مشابه HSL است و مقدار Alpha نیز به آن اضافه می‌شود.

```css
p {
    color: hsla(0, 100%, 50%, 0.5);
}
```

### روش هفتم: استفاده از currentColor

کلمه کلیدی `currentColor` به رنگ فعلی ویژگی `color` عنصر اشاره می‌کند.

این قابلیت برای هماهنگ کردن رنگ متن، حاشیه و سایر ویژگی‌ها کاربرد دارد.

```css
.box {
    color: blue;
    border: 2px solid currentColor;
}
```

در این مثال رنگ حاشیه نیز آبی خواهد بود.

---

## 2.2. ویژگی Opacity

ویژگی `opacity` میزان شفافیت کل یک عنصر را تعیین می‌کند.

مقادیر آن بین صفر و یک هستند.

```css
.box {
    opacity: 0.5;
}
```

مقادیر مهم:

| مقدار | توضیح |
|---|---|
| `0` | کاملاً شفاف |
| `0.25` | شفافیت زیاد |
| `0.5` | نیمه‌شفاف |
| `0.75` | شفافیت کم |
| `1` | کاملاً غیرشفاف |

**تفاوت Opacity با RGBA**

```css
.box1 {
    background-color: rgba(255, 0, 0, 0.5);
}

.box2 {
    opacity: 0.5;
}
```

تفاوت:

- در روش RGBA فقط رنگ پس‌زمینه شفاف می‌شود.
- در روش Opacity تمام محتوای عنصر، شامل متن، تصویر و پس‌زمینه، شفاف می‌شود.

---

## 2.3. ویژگی Color و وراثت

ویژگی `color` از ویژگی‌های قابل وراثت (Inherited) در CSS است.

یعنی اگر رنگی برای یک عنصر والد تعیین شود، فرزندان آن معمولاً همان رنگ را دریافت می‌کنند؛ مگر اینکه برای فرزند رنگ دیگری تعریف شده باشد.

```html
<div class="parent">
    <p>متن اول</p>
    <p>متن دوم</p>
</div>
```

```css
.parent {
    color: blue;
}
```

هر دو پاراگراف به‌صورت پیش‌فرض آبی خواهند بود.

---

# 3. ویژگی پس‌زمینه (Background)

ویژگی‌های Background برای تعیین ظاهر پس‌زمینه عناصر HTML استفاده می‌شوند.

با استفاده از این ویژگی‌ها می‌توان:

- رنگ پس‌زمینه تعیین کرد.
- تصویر پس‌زمینه قرار داد.
- نحوه تکرار تصویر را کنترل کرد.
- موقعیت تصویر را تغییر داد.
- اندازه تصویر را تنظیم کرد.
- تصویر را ثابت یا متحرک نگه داشت.

## 3.1. Background Color

ویژگی `background-color` برای تعیین رنگ پس‌زمینه عنصر استفاده می‌شود.

```css
body {
    background-color: lightblue;
}

div {
    background-color: yellow;
}

p {
    background-color: #eeeeee;
}
```

رنگ پس‌زمینه می‌تواند با روش‌های مختلف رنگی CSS تعریف شود.

مثال:

```css
.box {
    background-color: rgba(0, 0, 255, 0.3);
}
```

---

## 3.2. Background Image

ویژگی `background-image` برای قرار دادن تصویر در پس‌زمینه عنصر استفاده می‌شود.

ساختار:

```css
selector {
    background-image: url("image.jpg");
}
```

مثال:

```css
body {
    background-image: url("images/background.jpg");
}
```

برای قرار دادن تصویر پس‌زمینه معمولاً از فایل‌های زیر استفاده می‌شود:

- JPG
- JPEG
- PNG
- WebP
- SVG
- GIF

**نکته:** تصویر پس‌زمینه با تگ HTML یعنی `img` تفاوت دارد. تصویر پس‌زمینه معمولاً بخشی تزئینی از طراحی عنصر محسوب می‌شود و مانند تگ `img` محتوای مستقل ندارد.

---

## 3.3. Background Repeat

ویژگی `background-repeat` مشخص می‌کند تصویر پس‌زمینه چگونه تکرار شود.

مقادیر اصلی:

| مقدار | عملکرد |
|---|---|
| `repeat` | تکرار تصویر در هر دو جهت |
| `repeat-x` | تکرار افقی |
| `repeat-y` | تکرار عمودی |
| `no-repeat` | عدم تکرار تصویر |
| `space` | تکرار با فاصله بین تصاویر |
| `round` | تغییر اندازه تصویر برای جاگیری کامل |

مثال:

```css
body {
    background-image: url("pattern.png");
    background-repeat: repeat;
}
```

عدم تکرار:

```css
.hero {
    background-image: url("banner.jpg");
    background-repeat: no-repeat;
}
```

تکرار افقی:

```css
.box {
    background-repeat: repeat-x;
}
```

تکرار عمودی:

```css
.box {
    background-repeat: repeat-y;
}
```

---

## 3.4. Background Position

ویژگی `background-position` موقعیت قرارگیری تصویر پس‌زمینه را مشخص می‌کند.

مقادیر متداول:

```css
background-position: center;
background-position: top;
background-position: bottom;
background-position: left;
background-position: right;
```

مثال:

```css
.hero {
    background-image: url("banner.jpg");
    background-repeat: no-repeat;
    background-position: center;
}
```

امکان استفاده از مقادیر عددی نیز وجود دارد:

```css
.box {
    background-position: 20px 50px;
}
```

در این مثال:

- مقدار اول موقعیت افقی است.
- مقدار دوم موقعیت عمودی است.

همچنین می‌توان از درصد استفاده کرد:

```css
.box {
    background-position: 50% 50%;
}
```

این مقدار تصویر را در مرکز عنصر قرار می‌دهد.

---

## 3.5. Background Size

ویژگی `background-size` اندازه تصویر پس‌زمینه را مشخص می‌کند.

مقادیر مهم:

### مقدار Cover

```css
.hero {
    background-size: cover;
}
```

تصویر به‌اندازه‌ای بزرگ یا کوچک می‌شود که تمام فضای عنصر را بپوشاند.

ممکن است بخشی از تصویر بریده شود.

### مقدار Contain

```css
.hero {
    background-size: contain;
}
```

تصویر به شکلی تغییر اندازه می‌دهد که تمام آن داخل عنصر دیده شود.

ممکن است بخشی از پس‌زمینه بدون تصویر باقی بماند.

### مقدار Auto

```css
.hero {
    background-size: auto;
}
```

تصویر با اندازه اصلی خود یا اندازه محاسبه‌شده خود نمایش داده می‌شود.

### اندازه مشخص

```css
.hero {
    background-size: 300px 200px;
}
```

در این مثال:

- عرض تصویر 300 پیکسل است.
- ارتفاع تصویر 200 پیکسل است.

همچنین می‌توان از درصد استفاده کرد:

```css
.hero {
    background-size: 100% 100%;
}
```

---

## 3.6. Background Attachment

ویژگی `background-attachment` مشخص می‌کند تصویر پس‌زمینه هنگام پیمایش صفحه چگونه رفتار کند.

مقادیر اصلی:

### Scroll

```css
body {
    background-attachment: scroll;
}
```

تصویر همراه با محتوای عنصر حرکت می‌کند. این مقدار پیش‌فرض است.

### Fixed

```css
body {
    background-attachment: fixed;
}
```

تصویر پس‌زمینه نسبت به صفحه ثابت می‌ماند.

### Local

```css
.box {
    background-attachment: local;
}
```

تصویر پس‌زمینه همراه با محتوای قابل پیمایش خود عنصر حرکت می‌کند.

---

## 3.7. Background Origin و Clip

### Background Origin

ویژگی `background-origin` مشخص می‌کند موقعیت و محدوده محاسبه تصویر پس‌زمینه از کدام بخش جعبه عنصر آغاز شود.

مقادیر:

- `padding-box`
- `border-box`
- `content-box`

مثال:

```css
.box {
    background-image: url("image.jpg");
    background-origin: content-box;
}
```

### Background Clip

ویژگی `background-clip` مشخص می‌کند پس‌زمینه تا کدام قسمت جعبه عنصر نمایش داده شود.

مقادیر:

- `border-box`
- `padding-box`
- `content-box`
- `text`

مثال:

```css
.box {
    background-color: red;
    background-clip: padding-box;
}
```

مثال استفاده از متن:

```css
.title {
    background: linear-gradient(to right, red, blue);
    color: transparent;
    background-clip: text;
}
```

در این مثال گرادیان به‌عنوان رنگ متن نمایش داده می‌شود.

---

## 3.8. ویژگی ترکیبی Background

به‌جای نوشتن تمام ویژگی‌های پس‌زمینه به‌صورت جداگانه، می‌توان از ویژگی ترکیبی `background` استفاده کرد.

مثال:

```css
.hero {
    background:
        url("banner.jpg")
        no-repeat
        center / cover
        fixed;
}
```

این ویژگی می‌تواند شامل موارد زیر باشد:

- background-color
- background-image
- background-position
- background-size
- background-repeat
- background-origin
- background-clip
- background-attachment

مثال کامل‌تر:

```css
.box {
    background:
        #eeeeee
        url("image.jpg")
        no-repeat
        center / cover
        scroll;
}
```

**نکته:** در مقدار ترکیبی، ترتیب مقادیر اهمیت دارد. برای مشخص کردن `background-size` باید آن را پس از `background-position` و با علامت `/` جدا کرد.

---

## 3.9. چند پس‌زمینه‌ای (Multiple Backgrounds)

CSS امکان استفاده از چند تصویر پس‌زمینه برای یک عنصر را فراهم می‌کند.

برای این کار مقادیر را با کاما از هم جدا می‌کنیم.

```css
.hero {
    background-image:
        url("logo.png"),
        url("background.jpg");

    background-repeat:
        no-repeat,
        no-repeat;

    background-position:
        center,
        center;

    background-size:
        100px,
        cover;
}
```

نکته مهم:

تصویری که در ابتدای لیست نوشته می‌شود در لایه بالاتری قرار می‌گیرد.

---

# 4. فونت‌ها (Fonts)

فونت‌ها نقش بسیار مهمی در طراحی صفحات وب دارند.

با استفاده از ویژگی‌های فونت می‌توان موارد زیر را کنترل کرد:

- نوع قلم
- اندازه نوشته
- ضخامت نوشته
- حالت نوشته
- فاصله خطوط
- فاصله حروف
- فاصله کلمات

## 4.1. Font Family

ویژگی `font-family` نوع فونت مورد استفاده را تعیین می‌کند.

مثال:

```css
body {
    font-family: Arial, sans-serif;
}
```

در این مثال:

- ابتدا مرورگر فونت Arial را جست‌وجو می‌کند.
- اگر Arial در دسترس نباشد، از یک فونت بدون سریف استفاده می‌کند.

### دسته‌بندی اصلی فونت‌ها

| دسته | توضیح |
|---|---|
| `serif` | فونت‌های دارای زوائد انتهایی |
| `sans-serif` | فونت‌های بدون زوائد انتهایی |
| `monospace` | فونت‌هایی با عرض یکسان برای کاراکترها |
| `cursive` | فونت‌های دست‌نویس |
| `fantasy` | فونت‌های تزئینی |

مثال:

```css
.serif {
    font-family: Georgia, serif;
}

.sans {
    font-family: Arial, sans-serif;
}

.mono {
    font-family: "Courier New", monospace;
}
```

### تعریف چند فونت جایگزین

بهتر است همیشه چند فونت تعریف کنیم تا در صورت در دسترس نبودن فونت اول، مرورگر از گزینه بعدی استفاده کند.

```css
body {
    font-family: Tahoma, Arial, sans-serif;
}
```

### فونت‌هایی با نام چندبخشی

اگر نام فونت دارای فاصله باشد، باید آن را داخل کوتیشن قرار دهیم.

```css
p {
    font-family: "Times New Roman", serif;
}
```

### فونت‌های فارسی

برای نمایش مناسب زبان فارسی می‌توان از فونت‌های فارسی استفاده کرد.

نمونه‌ها:

- Vazirmatn
- Shabnam
- Sahel
- Samim
- IRANSans

مثال:

```css
body {
    font-family: Tahoma, Arial, sans-serif;
}
```

---

## 4.2. Font Size

ویژگی `font-size` اندازه نوشته را مشخص می‌کند.

مثال:

```css
h1 {
    font-size: 32px;
}

p {
    font-size: 16px;
}
```

### واحدهای اندازه فونت

**px**

واحد پیکسل است.

```css
p {
    font-size: 18px;
}
```

**em**

اندازه‌ای نسبی نسبت به اندازه فونت عنصر والد (در اغلب موارد) است.

```css
.parent {
    font-size: 20px;
}

.child {
    font-size: 1.5em;
}
```

اندازه متن فرزند برابر 30 پیکسل خواهد بود.

**rem**

واحدی نسبی نسبت به اندازه فونت عنصر ریشه، یعنی معمولاً `html`، است.

```css
html {
    font-size: 16px;
}

h1 {
    font-size: 2rem;
}
```

اندازه عنوان برابر 32 پیکسل خواهد بود.

**%**

برای تعیین اندازه نسبی استفاده می‌شود.

```css
p {
    font-size: 120%;
}
```

**vw**

اندازه‌ای وابسته به عرض صفحه نمایش است.

```css
h1 {
    font-size: 5vw;
}
```

**نکته:** برای طراحی واکنش‌گرا (Responsive) معمولاً استفاده از `rem` و ترکیب آن با `clamp()` گزینه مناسبی است.

مثال:

```css
h1 {
    font-size: clamp(24px, 4vw, 48px);
}
```

---

## 4.3. Font Weight

ویژگی `font-weight` ضخامت یا وزن نوشته را مشخص می‌کند.

مقادیر متداول:

| مقدار | توضیح |
|---|---|
| `100` | بسیار نازک |
| `200` | نازک |
| `300` | نسبتاً نازک |
| `400` | معمولی |
| `500` | متوسط |
| `600` | نیمه‌ضخیم |
| `700` | ضخیم |
| `800` | بسیار ضخیم |
| `900` | فوق‌العاده ضخیم |

مثال:

```css
p {
    font-weight: 400;
}

h1 {
    font-weight: 700;
}
```

همچنین می‌توان از کلمات زیر استفاده کرد:

```css
p {
    font-weight: normal;
}

strong {
    font-weight: bold;
}
```

مقادیر نسبی:

- `lighter`
- `bolder`

**نکته:** همه فونت‌ها تمام وزن‌های بالا را پشتیبانی نمی‌کنند. در صورت نبود وزن موردنظر، مرورگر ممکن است وزن نزدیک‌تری را انتخاب کند.

---

## 4.4. Font Style

ویژگی `font-style` حالت ظاهری فونت را تعیین می‌کند.

مقادیر اصلی:

### Normal

حالت عادی نوشته:

```css
p {
    font-style: normal;
}
```

### Italic

حالت مورب نوشته:

```css
p {
    font-style: italic;
}
```

### Oblique

حالت مایل نوشته:

```css
p {
    font-style: oblique;
}
```

تفاوت:

- `italic` معمولاً از شکل ایتالیک طراحی‌شده فونت استفاده می‌کند.
- `oblique` معمولاً نسخه مایل‌شده فونت است.

---

## 4.5. Font Variant

ویژگی `font-variant` شکل نمایش بعضی حروف را تغییر می‌دهد.

یکی از کاربردهای آن استفاده از حروف کوچک به شکل Small Caps است.

```css
p {
    font-variant: small-caps;
}
```

در این حالت حروف کوچک به شکل حروف بزرگ کوچک‌تر نمایش داده می‌شوند.

مقادیر رایج:

- `normal`
- `small-caps`

---

## 4.6. Font Stretch

ویژگی `font-stretch` میزان فشردگی یا کشیدگی حروف را تعیین می‌کند.

مثال:

```css
p {
    font-stretch: condensed;
}
```

مقادیر متداول:

- `ultra-condensed`
- `extra-condensed`
- `condensed`
- `semi-condensed`
- `normal`
- `semi-expanded`
- `expanded`
- `extra-expanded`
- `ultra-expanded`

**نکته:** تأثیر این ویژگی به پشتیبانی فونت از عرض‌های مختلف بستگی دارد.

---

## 4.7. Line Height

ویژگی `line-height` فاصله عمودی خطوط متن را کنترل می‌کند.

مثال:

```css
p {
    font-size: 16px;
    line-height: 1.8;
}
```

در این مثال ارتفاع خط برابر 1.8 برابر اندازه فونت است.

روش‌های مختلف تعریف:

```css
p {
    line-height: normal;
}
```

```css
p {
    line-height: 24px;
}
```

```css
p {
    line-height: 150%;
}
```

```css
p {
    line-height: 1.5;
}
```

**پیشنهاد:** برای متن‌های طولانی معمولاً مقدار 1.5 تا 1.8 انتخاب مناسبی است، اما مقدار دقیق به نوع فونت و طراحی بستگی دارد.

---

## 4.8. Letter Spacing و Word Spacing

### Letter Spacing

ویژگی `letter-spacing` فاصله بین حروف را کنترل می‌کند.

```css
h1 {
    letter-spacing: 2px;
}
```

برای کاهش فاصله:

```css
h1 {
    letter-spacing: -1px;
}
```

### Word Spacing

ویژگی `word-spacing` فاصله بین کلمات را کنترل می‌کند.

```css
p {
    word-spacing: 5px;
}
```

مثال ترکیبی:

```css
p {
    letter-spacing: 1px;
    word-spacing: 4px;
}
```

**نکته برای زبان فارسی:** تنظیم زیاد فاصله حروف می‌تواند پیوستگی بصری حروف فارسی را به هم بزند. بنابراین معمولاً باید با احتیاط استفاده شود.

---

## 4.9. Font Shorthand

ویژگی `font` یک ویژگی ترکیبی است که امکان تعریف چند ویژگی فونت را در یک دستور فراهم می‌کند.

مثال:

```css
p {
    font: italic bold 18px/1.5 Arial, sans-serif;
}
```

در این مثال:

- `italic`: حالت نوشته
- `bold`: ضخامت نوشته
- `18px`: اندازه فونت
- `1.5`: ارتفاع خط
- `Arial, sans-serif`: نوع فونت

ساختار کلی:

```css
font: font-style font-variant font-weight font-stretch font-size/line-height font-family;
```

تمام مقادیر اختیاری هستند، اما اندازه فونت و خانواده فونت باید مشخص شوند.

مثال ساده:

```css
body {
    font: 16px Arial, sans-serif;
}
```

---

## 4.10. بارگذاری فونت سفارشی

در CSS می‌توان فونت دلخواه را با استفاده از `@font-face` به پروژه اضافه کرد.

ساختار:

```css
@font-face {
    font-family: "MyFont";
    src: url("fonts/myfont.woff2") format("woff2");
    font-weight: 400;
    font-style: normal;
}
```

سپس از آن استفاده می‌کنیم:

```css
body {
    font-family: "MyFont", sans-serif;
}
```

### فرمت‌های متداول فونت

| فرمت | توضیح |
|---|---|
| WOFF | فرمت فشرده فونت وب |
| WOFF2 | نسخه بهینه‌تر و فشرده‌تر WOFF |
| TTF | TrueType Font |
| OTF | OpenType Font |

### تعریف وزن‌های مختلف

اگر چند فایل برای وزن‌های مختلف فونت داشته باشیم، می‌توانیم آن‌ها را جداگانه تعریف کنیم.

```css
@font-face {
    font-family: "MyFont";
    src: url("fonts/myfont-regular.woff2") format("woff2");
    font-weight: 400;
}

@font-face {
    font-family: "MyFont";
    src: url("fonts/myfont-bold.woff2") format("woff2");
    font-weight: 700;
}
```

استفاده:

```css
body {
    font-family: "MyFont", sans-serif;
}

h1 {
    font-weight: 700;
}

p {
    font-weight: 400;
}
```

---

# 5. واحدهای اندازه‌گیری

در ویژگی‌های رنگ، پس‌زمینه و فونت از واحدهای مختلفی استفاده می‌شود.

## واحدهای مطلق

| واحد | توضیح |
|---|---|
| `px` | پیکسل CSS |
| `cm` | سانتی‌متر |
| `mm` | میلی‌متر |
| `in` | اینچ |
| `pt` | پوینت |
| `pc` | پیکا |

## واحدهای نسبی

| واحد | توضیح |
|---|---|
| `%` | درصد نسبت به مرجع مربوطه |
| `em` | نسبت به اندازه فونت عنصر والد یا مرجع محاسباتی مربوطه |
| `rem` | نسبت به اندازه فونت عنصر ریشه |
| `vw` | یک درصد عرض viewport |
| `vh` | یک درصد ارتفاع viewport |
| `vmin` | یک درصد از کوچک‌ترین بُعد viewport |
| `vmax` | یک درصد از بزرگ‌ترین بُعد viewport |

مثال:

```css
.container {
    width: 80%;
}

h1 {
    font-size: 2rem;
}

p {
    font-size: 1em;
}
```

---

# 6. مثال عملی

در این بخش یک نمونه ساده از ترکیب رنگ، پس‌زمینه و فونت را بررسی می‌کنیم.

## ساختار HTML

```html
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>آموزش CSS</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="card">
        <h1>آموزش CSS</h1>

        <p>
            CSS برای طراحی و زیباسازی صفحات وب استفاده می‌شود.
        </p>

        <a href="#">مشاهده بیشتر</a>
    </div>

</body>
</html>
```

## کد CSS

```css
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Tahoma, Arial, sans-serif;
    background-color: #f1f5f9;
    color: #1e293b;
}

.card {
    width: 80%;
    max-width: 500px;
    margin: 100px auto;
    padding: 30px;

    background-color: white;

    background-image:
        linear-gradient(
            rgba(255, 255, 255, 0.95),
            rgba(255, 255, 255, 0.95)
        );

    border-radius: 12px;
}

h1 {
    color: #2563eb;
    font-size: 30px;
    font-weight: 700;
    line-height: 1.5;
}

p {
    color: #475569;
    font-size: 16px;
    line-height: 1.8;
}

a {
    color: #ffffff;
    background-color: #2563eb;
    font-size: 16px;
    font-weight: bold;
    text-decoration: none;
    padding: 10px 20px;
    display: inline-block;
    border-radius: 6px;
}
```

در این مثال موارد زیر را به کار بردیم:

- تعیین رنگ متن با `color`
- تعیین رنگ پس‌زمینه با `background-color`
- استفاده از تصویر گرادیانی با `background-image`
- تعیین نوع فونت با `font-family`
- تعیین اندازه فونت با `font-size`
- تعیین ضخامت فونت با `font-weight`
- تعیین ارتفاع خط با `line-height`
- استفاده از رنگ HEX
- استفاده از فونت‌های جایگزین

---

# 7. نکات مهم و بهترین روش‌ها

## 7.1. انتخاب رنگ مناسب

بهتر است رنگ متن و پس‌زمینه تضاد کافی داشته باشند تا خوانایی متن حفظ شود.

مثال مناسب:

```css
body {
    color: #222222;
    background-color: #ffffff;
}
```

## 7.2. استفاده از متغیرهای CSS برای رنگ‌ها

برای مدیریت بهتر رنگ‌های پروژه می‌توان از CSS Custom Properties استفاده کرد.

```css
:root {
    --primary-color: #2563eb;
    --text-color: #222222;
    --background-color: #f8fafc;
}

body {
    color: var(--text-color);
    background-color: var(--background-color);
}

button {
    background-color: var(--primary-color);
}
```

مزیت این روش:

- مدیریت آسان رنگ‌ها
- جلوگیری از تکرار کد
- تغییر سریع تم سایت
- یکپارچگی طراحی

## 7.3. استفاده از فونت جایگزین

همیشه بهتر است برای فونت اصلی یک یا چند فونت جایگزین تعریف شود.

```css
body {
    font-family: Tahoma, Arial, sans-serif;
}
```

## 7.4. استفاده از واحدهای مناسب

برای طراحی واکنش‌گرا:

- برای اندازه فونت از `rem` استفاده کنید.
- برای اندازه‌های وابسته به والد از `%` استفاده کنید.
- برای اندازه‌های وابسته به viewport از `vw` و `vh` استفاده کنید.
- برای اندازه‌های ثابت و دقیق از `px` استفاده کنید.

## 7.5. بهینه‌سازی تصاویر پس‌زمینه

برای تصاویر پس‌زمینه بهتر است:

- حجم تصاویر بهینه باشد.
- از فرمت WebP استفاده شود.
- اندازه تصویر با فضای مورد استفاده هماهنگ باشد.
- از تصاویر بسیار بزرگ و غیرضروری استفاده نشود.

## 7.6. رعایت خوانایی فونت فارسی

در طراحی صفحات فارسی:

- فونت مناسب فارسی انتخاب کنید.
- ارتفاع خط را به‌اندازه کافی تنظیم کنید.
- از فاصله حروف بیش از حد استفاده نکنید.
- اندازه فونت متن اصلی را بیش از حد کوچک نکنید.
- جهت متن را با توجه به زبان محتوا تنظیم کنید.

---

# 8. جمع‌بندی

در این آموزش سه گروه مهم از ویژگی‌های CSS را بررسی کردیم.

## ویژگی‌های Color

| ویژگی | کاربرد |
|---|---|
| `color` | تعیین رنگ متن |
| `opacity` | تعیین شفافیت کل عنصر |

روش‌های تعریف رنگ:

- Color Names
- HEX
- RGB
- RGBA
- HSL
- HSLA
- currentColor

## ویژگی‌های Background

| ویژگی | کاربرد |
|---|---|
| `background-color` | تعیین رنگ پس‌زمینه |
| `background-image` | تعیین تصویر پس‌زمینه |
| `background-repeat` | کنترل تکرار تصویر |
| `background-position` | تعیین موقعیت تصویر |
| `background-size` | تعیین اندازه تصویر |
| `background-attachment` | تعیین رفتار تصویر هنگام پیمایش |
| `background-origin` | تعیین محدوده مرجع موقعیت پس‌زمینه |
| `background-clip` | تعیین محدوده نمایش پس‌زمینه |
| `background` | ویژگی ترکیبی پس‌زمینه |

## ویژگی‌های Font

| ویژگی | کاربرد |
|---|---|
| `font-family` | تعیین نوع فونت |
| `font-size` | تعیین اندازه فونت |
| `font-weight` | تعیین ضخامت فونت |
| `font-style` | تعیین حالت فونت |
| `font-variant` | تعیین حالت‌هایی مانند Small Caps |
| `font-stretch` | تعیین میزان کشیدگی یا فشردگی فونت |
| `line-height` | تعیین ارتفاع خط |
| `letter-spacing` | تعیین فاصله حروف |
| `word-spacing` | تعیین فاصله کلمات |
| `font` | ویژگی ترکیبی فونت |
| `@font-face` | بارگذاری فونت سفارشی |

**نتیجه‌گیری:**

ویژگی‌های Color، Background و Font از پایه‌ای‌ترین ابزارهای طراحی با CSS هستند. تسلط بر این سه گروه به شما کمک می‌کند ظاهر صفحات وب را کنترل کنید، خوانایی محتوا را افزایش دهید و رابط کاربری زیباتر و حرفه‌ای‌تری بسازید.

---

## منابع برای مطالعه بیشتر

- MDN – CSS Colors: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_colors
- MDN – Background: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_backgrounds_and_borders
- MDN – CSS Fonts: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_fonts
- MDN – Color: https://developer.mozilla.org/en-US/docs/Web/CSS/color
- MDN – Font Family: https://developer.mozilla.org/en-US/docs/Web/CSS/font-family
- MDN – Background Image: https://developer.mozilla.org/en-US/docs/Web/CSS/background-image

[بازگشت به فهرست مطالب](#top)
