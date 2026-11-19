# چیدمان‌های سنتی در CSS (Traditional CSS Layouts)

معرفی روش‌های مدرن چیدمان در CSS مانند Flexbox و CSS Grid، توسعه‌دهندگان وب از روش‌های سنتی برای قرار دادن عناصر در کنار یکدیگر و ایجاد ساختار صفحات استفاده می‌کردند.

سه مورد از مهم‌ترین ابزارهای این روش‌ها عبارت‌اند از:

1. `display: block`
2. `display: inline`
3. `float`

این ویژگی‌ها همچنان بخش مهمی از CSS هستند و شناخت آن‌ها برای درک نحوه قرارگیری عناصر در صفحه وب ضروری است.

در این روش‌ها، چیدمان عناصر عمدتاً بر اساس جریان عادی سند (Normal Flow) انجام می‌شود.

---

## مفهوم Normal Flow

جریان عادی سند یا Normal Flow به نحوه پیش‌فرض قرارگیری عناصر HTML در صفحه گفته می‌شود.

مرورگر بر اساس نوع نمایش هر عنصر، موقعیت آن را تعیین می‌کند.

به‌طور کلی:

- عناصر Block به‌صورت عمودی و زیر یکدیگر قرار می‌گیرند.
- عناصر Inline در امتداد متن و کنار یکدیگر قرار می‌گیرند.
- عناصر Float از جریان عادی خارج می‌شوند و عناصر متنی می‌توانند در اطراف آن‌ها قرار بگیرند.

### مثال

```html
<div>Box One</div>
<div>Box Two</div>
<div>Box Three</div>
```

```css
div {
    background-color: lightblue;
    padding: 20px;
    margin: 10px;
}
```

در این مثال، هر سه عنصر `div` به دلیل Block بودن، زیر یکدیگر نمایش داده می‌شوند.

---

## ۲. چیدمان با display: block

### مفهوم Block

عناصری که مقدار `display` آن‌ها برابر با `block` است، به‌صورت بلوکی نمایش داده می‌شوند.

ویژگی‌های اصلی عناصر Block:

1. به‌صورت پیش‌فرض تمام عرض موجود در والد خود را اشغال می‌کنند.
2. هر عنصر از خط جدید شروع می‌شود.
3. عناصر بعدی به خط بعد منتقل می‌شوند.
4. می‌توان برای آن‌ها `width` و `height` تعیین کرد.
5. ویژگی‌های `margin` و `padding` در تمام جهت‌ها قابل استفاده هستند.

### عناصر Block رایج در HTML

- `div`
- `p`
- `h1` تا `h6`
- `section`
- `article`
- `header`
- `footer`
- `main`
- `ul`
- `ol`
- `li`

### مثال ساده

```html
<div class="box">Box 1</div>
<div class="box">Box 2</div>
<div class="box">Box 3</div>
```

```css
.box {
    display: block;
    width: 200px;
    height: 100px;
    background-color: lightblue;
    margin-bottom: 10px;
}
```

### نتیجه

سه عنصر به شکل عمودی و زیر یکدیگر نمایش داده می‌شوند.

```text
+------------------+
|      Box 1       |
+------------------+

+------------------+
|      Box 2       |
+------------------+

+------------------+
|      Box 3       |
+------------------+
```

### تغییر رفتار عناصر با display: block

حتی عناصری که به‌صورت پیش‌فرض Inline هستند، می‌توانند به Block تبدیل شوند.

```html
<span>Item 1</span>
<span>Item 2</span>
<span>Item 3</span>
```

```css
span {
    display: block;
    background-color: lightgreen;
    margin: 5px;
    padding: 10px;
}
```

در این حالت، هر `span` در یک خط مستقل قرار می‌گیرد.

### نکته مهم

تعیین `width` و `height` برای عناصر Block امکان‌پذیر است؛ اما عرض پیش‌فرض آن‌ها به‌صورت `auto` بوده و معمولاً فضای افقی موجود در والد را پر می‌کند.

---

## ۳. چیدمان با display: inline

### مفهوم Inline

عناصری که مقدار `display` آن‌ها برابر با `inline` است، در امتداد محتوای متنی قرار می‌گیرند.

ویژگی‌های اصلی عناصر Inline:

1. در صورت وجود فضای کافی، کنار یکدیگر قرار می‌گیرند.
2. به‌صورت پیش‌فرض تمام عرض والد را اشغال نمی‌کنند.
3. به اندازه محتوای خود فضا می‌گیرند.
4. ویژگی‌های `width` و `height` معمولاً روی آن‌ها اعمال نمی‌شود.
5. `margin` و `padding` افقی روی آن‌ها اعمال می‌شود.
6. `margin` و `padding` عمودی ممکن است روی ظاهر اثر بگذارند، اما فضای خطوط اطراف را مانند عناصر Block تغییر نمی‌دهند.

### عناصر Inline رایج در HTML

- `span`
- `a`
- `strong`
- `em`
- `b`
- `i`
- `label`
- `small`
- `code`

### مثال ساده

```html
<span>Item 1</span>
<span>Item 2</span>
<span>Item 3</span>
```

```css
span {
    display: inline;
    background-color: lightcoral;
    padding: 10px;
    margin: 5px;
}
```

### نتیجه

عناصر در یک خط و کنار یکدیگر قرار می‌گیرند.

```text
+--------+ +--------+ +--------+
| Item 1 | | Item 2 | | Item 3 |
+--------+ +--------+ +--------+
```

### چرا width و height روی Inline تأثیر ندارند؟

در مدل Inline، اندازه عناصر عمدتاً با محتوای داخلی، فونت و تنظیمات خط تعیین می‌شود.

برای مثال:

```css
span {
    display: inline;
    width: 200px;
    height: 100px;
}
```

در این حالت، `width` و `height` به شکل معمول روی ابعاد عنصر Inline اعمال نمی‌شوند.

اگر نیاز داشته باشیم یک عنصر در کنار عناصر دیگر قرار بگیرد و در عین حال بتوانیم ابعاد آن را تنظیم کنیم، می‌توانیم از `inline-block` استفاده کنیم.

### آشنایی با inline-block

```css
span {
    display: inline-block;
    width: 150px;
    height: 100px;
    background-color: lightblue;
    margin: 10px;
    padding: 10px;
}
```

ویژگی‌های `inline-block`:

- عناصر کنار یکدیگر قرار می‌گیرند.
- امکان تعیین `width` و `height` وجود دارد.
- `margin` و `padding` در تمام جهت‌ها قابل استفاده هستند.
- مانند عناصر Inline، در جریان متنی قرار می‌گیرند.

> نکته: `inline-block` یکی از مقادیر مهم ویژگی display است، اما با Block و Inline معمولی تفاوت دارد.

---

## ۴. چیدمان با float

### مفهوم Float

ویژگی `float` در CSS برای قرار دادن یک عنصر در سمت چپ یا راست والد استفاده می‌شود.

این ویژگی در ابتدا برای قرار دادن تصاویر در کنار متن طراحی شده بود؛ اما در گذشته برای ساخت Layout کامل صفحات وب نیز استفاده می‌شد.

مقادیر اصلی Float:

| مقدار | توضیح |
|---|---|
| `left` | قرارگیری عنصر در سمت چپ |
| `right` | قرارگیری عنصر در سمت راست |
| `none` | غیرفعال کردن Float |
| `inline-start` | شناور شدن در ابتدای جهت نوشتار |
| `inline-end` | شناور شدن در انتهای جهت نوشتار |

### مثال Float Left

```html
<div class="container">
    <div class="box">Float Box</div>

    <p>
        Lorem ipsum dolor sit amet, consectetur
        adipiscing elit. This text flows around
        the floated element.
    </p>
</div>
```

```css
.box {
    float: left;
    width: 150px;
    height: 150px;
    background-color: lightblue;
    margin-right: 15px;
}
```

### نتیجه

عنصر موردنظر در سمت چپ قرار می‌گیرد و متن در فضای باقی‌مانده اطراف آن جریان پیدا می‌کند.

```text
+-------------+  Lorem ipsum dolor
|             |  sit amet, consectetur
| Float Box   |  adipiscing elit.
|             |  This text flows around
+-------------+  the floated element.
```

### مثال Float Right

```css
.box {
    float: right;
    width: 150px;
    height: 150px;
    background-color: lightcoral;
    margin-left: 15px;
}
```

در این حالت، عنصر در سمت راست قرار می‌گیرد و متن در سمت چپ و اطراف آن نمایش داده می‌شود.

### ویژگی‌های مهم Float

1. عنصر Float از جریان عادی Block خارج می‌شود.
2. عناصر Block بعدی ممکن است فضای اشغال‌شده توسط Float را نادیده بگیرند.
3. محتوای Inline مانند متن می‌تواند در اطراف عنصر Float قرار بگیرد.
4. عناصر Float تا حد امکان در سمت تعیین‌شده قرار می‌گیرند.
5. عناصر Float نمی‌توانند خارج از محدوده والد خود قرار بگیرند، مگر اینکه شرایط دیگری مانند Overflow یا اندازه محتوا موجب سرریز شود.

### مثال چند عنصر Float

```html
<div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
</div>
```

```css
.box {
    float: left;
    width: 150px;
    height: 100px;
    background-color: lightblue;
    margin: 10px;
}
```

در این حالت، عناصر در صورت وجود فضای کافی کنار یکدیگر قرار می‌گیرند.

```text
+-------------+  +-------------+  +-------------+
|    Box 1    |  |    Box 2    |  |    Box 3    |
+-------------+  +-------------+  +-------------+
```

اگر فضای کافی وجود نداشته باشد، عناصر به خط بعد منتقل می‌شوند.

---

## ۵. ویژگی clear

### مفهوم Clear

وقتی عنصری دارای `float` باشد، عناصر بعدی ممکن است در اطراف آن قرار بگیرند.

گاهی لازم است یک عنصر از قرارگیری در کنار Float جلوگیری کند و حتماً از زیر آن شروع شود.

برای این کار از ویژگی `clear` استفاده می‌کنیم.

مقادیر Clear:

| مقدار | توضیح |
|---|---|
| `none` | رفتار پیش‌فرض |
| `left` | جلوگیری از قرارگیری در کنار Float چپ |
| `right` | جلوگیری از قرارگیری در کنار Float راست |
| `both` | جلوگیری از قرارگیری در کنار هر دو نوع Float |
| `inline-start` | پاک‌سازی Float در ابتدای جهت نوشتار |
| `inline-end` | پاک‌سازی Float در انتهای جهت نوشتار |

### مثال بدون Clear

```html
<div class="box">Float Box</div>

<div class="content">
    This is another content section.
</div>
```

```css
.box {
    float: left;
    width: 150px;
    height: 150px;
    background-color: lightblue;
}

.content {
    background-color: lightcoral;
    padding: 20px;
}
```

در این حالت، محتوای عنصر دوم ممکن است در کنار Float قرار بگیرد.

### مثال با Clear

```css
.content {
    clear: both;
    background-color: lightcoral;
    padding: 20px;
}
```

با استفاده از `clear: both`، عنصر دوم از زیر تمام عناصر Float عبور می‌کند.

### نمایش مفهومی

بدون Clear:

```text
+-------------+  +-------------------+
|             |  | Content           |
| Float Box   |  |                   |
|             |  +-------------------+
+-------------+
```

با Clear:

```text
+-------------+
|             |
| Float Box   |
|             |
+-------------+

+-----------------------------------+
| Content                           |
+-----------------------------------+
```

---

## ۶. تفاوت Block و Inline و Float

| ویژگی | Block | Inline | Float |
|---|---|---|---|
| شروع از خط جدید | بله | خیر | لزوماً خیر |
| اشغال کل عرض والد | معمولاً بله | خیر | خیر |
| قابلیت تعیین Width | بله | خیر | بله |
| قابلیت تعیین Height | بله | خیر | بله |
| قرارگیری کنار عناصر دیگر | معمولاً خیر | بله | بله |
| خروج از Normal Flow | خیر | خیر | بله |
| امکان جریان متن در اطراف | خیر | خیر | بله |

### تفاوت اصلی

**Block:**

برای ساخت بخش‌های مستقل و بلوکی صفحه استفاده می‌شود.

**Inline:**

برای نمایش محتوا در امتداد متن استفاده می‌شود.

**Float:**

برای شناور کردن یک عنصر در سمت چپ یا راست و جریان یافتن محتوا در اطراف آن استفاده می‌شود.

---

## ۷. ترکیب Block و Inline و Float

در صفحات واقعی معمولاً از ترکیب این ویژگی‌ها استفاده می‌شود.

### مثال

```html
<div class="container">

    <h2>Article Title</h2>

    <img src="image.jpg" class="article-image" alt="Article">

    <p>
        This is the article content.
        The text will flow around the image.
    </p>

    <p>
        This is another paragraph.
        It continues around the floated image.
    </p>

</div>
```

```css
.container {
    display: block;
    width: 800px;
    margin: 0 auto;
}

.article-image {
    float: left;
    width: 200px;
    height: 150px;
    margin: 0 15px 15px 0;
}

p {
    display: block;
}

h2 {
    display: block;
}
```

در این مثال:

- `container` یک عنصر Block است.
- عنوان مقاله به‌صورت Block نمایش داده می‌شود.
- تصویر با استفاده از Float در سمت چپ قرار می‌گیرد.
- متن پاراگراف‌ها در اطراف تصویر جریان پیدا می‌کند.

---

## ۸. تکنیک Clearfix

### مشکل اصلی Float

یکی از مشکلات مهم Float زمانی رخ می‌دهد که تمام فرزندان یک والد دارای Float باشند.

در این حالت، ارتفاع والد ممکن است صفر یا کمتر از مقدار مورد انتظار شود؛ زیرا فرزندان Float از جریان عادی سند خارج شده‌اند.

### مثال مشکل‌دار

```html
<div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
</div>
```

```css
.container {
    background-color: lightgray;
}

.box {
    float: left;
    width: 150px;
    height: 100px;
    background-color: lightblue;
    margin: 10px;
}
```

در این مثال، ممکن است پس‌زمینه والد ارتفاع مورد انتظار را نداشته باشد.

### راه‌حل اول: استفاده از Clearfix

```css
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```

```html
<div class="container clearfix">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
</div>
```

با استفاده از Pseudo-element به نام `::after`، یک عنصر مجازی بعد از فرزندان ایجاد می‌شود که Float را پاک‌سازی می‌کند.

در نتیجه والد می‌تواند ارتفاع فرزندان شناور خود را در نظر بگیرد.

### راه‌حل دوم: استفاده از Flow Root

```css
.container {
    display: flow-root;
}
```

`display: flow-root` یک Block Formatting Context مستقل ایجاد می‌کند و باعث می‌شود والد ارتفاع فرزندان Float را در محاسبات خود لحاظ کند.

این روش معمولاً از Clearfix ساده‌تر است.

---

## ۹. مشکلات و محدودیت‌های روش‌های سنتی

استفاده از Block، Inline و Float برای ساخت Layoutهای پیچیده محدودیت‌هایی دارد.

### مشکلات Float

- مدیریت ارتفاع والد دشوارتر می‌شود.
- برای پاک‌سازی Float به `clear` یا Clearfix نیاز داریم.
- ساخت Layoutهای چندستونه پیچیده می‌شود.
- کنترل فاصله و تراز عناصر دشوارتر است.
- طراحی Responsive پیچیده‌تر می‌شود.

### مشکلات Inline

- امکان تعیین مستقیم Width و Height وجود ندارد.
- فاصله بین عناصر ممکن است تحت تأثیر فاصله‌های موجود در HTML قرار بگیرد.
- کنترل دقیق ابعاد عناصر دشوار است.
- تراز عمودی گاهی به تنظیمات اضافی نیاز دارد.

### مشکلات Block

- عناصر به‌صورت پیش‌فرض زیر یکدیگر قرار می‌گیرند.
- برای ساخت چیدمان‌های افقی به روش‌های دیگری نیاز داریم.
- کنترل موقعیت چند عنصر در یک ردیف دشوارتر است.

### جایگزین‌های مدرن

امروزه برای ساخت Layoutهای پیچیده معمولاً از دو ابزار مهم استفاده می‌شود:

1. Flexbox
2. CSS Grid

**Flexbox:**

برای چیدمان عناصر در یک بعد، یعنی یک ردیف یا یک ستون، بسیار مناسب است.

**CSS Grid:**

برای ساخت Layoutهای دوبعدی شامل ردیف‌ها و ستون‌ها کاربرد دارد.

البته این موضوع به معنی منسوخ شدن Block، Inline و Float نیست. این ویژگی‌ها همچنان در طراحی صفحات وب کاربرد دارند.

---

## ۱۰. مثال کاربردی

در این مثال یک ساختار ساده مقاله ایجاد می‌کنیم که تصویر آن در سمت چپ و متن آن در اطراف تصویر قرار می‌گیرد.

### HTML

```html
<div class="article">

    <h2>CSS Traditional Layout</h2>

    <img
        src="image.jpg"
        alt="CSS Layout"
        class="article-image"
    >

    <p>
        CSS provides different methods for arranging
        elements on a web page.
    </p>

    <p>
        Traditional layout techniques include
        block, inline and float.
    </p>

    <p>
        Float allows text to flow around an element.
    </p>

    <div class="clear"></div>

    <footer>
        Article Footer
    </footer>

</div>
```

### CSS

```css
* {
    box-sizing: border-box;
}

.article {
    width: 100%;
    max-width: 800px;
    margin: 30px auto;
    padding: 20px;
    background-color: #f5f5f5;
}

.article h2 {
    display: block;
}

.article-image {
    float: left;
    width: 200px;
    height: 150px;
    object-fit: cover;
    margin: 0 20px 10px 0;
}

.article p {
    display: block;
    line-height: 1.8;
}

.clear {
    clear: both;
}

.article footer {
    display: block;
    padding: 15px;
    background-color: #ddd;
}
```

### بررسی نتیجه

در این مثال:

1. کل مقاله با استفاده از Block ساخته شده است.
2. عنوان مقاله یک عنصر Block است.
3. تصویر با استفاده از `float: left` در سمت چپ قرار گرفته است.
4. پاراگراف‌ها در اطراف تصویر جریان دارند.
5. عنصر `clear` مانع قرارگیری Footer در کنار تصویر می‌شود.
6. Footer بعد از تصویر و محتوای شناور قرار می‌گیرد.

---

## ۱۱. جمع‌بندی

سه ویژگی اصلی این آموزش رفتارهای متفاوتی در چیدمان عناصر دارند:

| ویژگی | کاربرد اصلی |
|---|---|
| `display: block` | ساخت عناصر بلوکی و بخش‌های مستقل |
| `display: inline` | قرارگیری محتوا در امتداد متن |
| `float` | شناور کردن عناصر در سمت چپ یا راست |

### نکات مهم برای یادگیری

- عناصر Block معمولاً تمام عرض موجود را اشغال می‌کنند.
- عناصر Inline فقط به اندازه محتوای خود فضا می‌گیرند.
- عناصر Float از جریان عادی سند خارج می‌شوند.
- متن می‌تواند در اطراف عناصر Float جریان داشته باشد.
- ویژگی Clear برای جلوگیری از قرارگیری عناصر در کنار Float استفاده می‌شود.
- تکنیک Clearfix برای حل مشکل ارتفاع والد دارای فرزندان Float کاربرد دارد.
- `inline-block` ترکیبی از رفتار Inline و قابلیت تعیین ابعاد Block را ارائه می‌دهد.
- `display: flow-root` یکی از روش‌های مناسب برای مدیریت Floatهای داخلی یک والد است.
- برای Layoutهای پیچیده و مدرن، Flexbox و Grid معمولاً انتخاب مناسب‌تری هستند.

**نتیجه نهایی:** درک Block، Inline و Float پایه مهمی برای یادگیری CSS Layout است؛ زیرا رفتار این ویژگی‌ها در ساختار و جریان چیدمان عناصر HTML نقش اساسی دارد.
