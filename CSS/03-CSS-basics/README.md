# درک عمیق Box Model در CSS
## آشنایی کامل با Content، Padding، Border و Margin

یکی از مهم‌ترین مفاهیم در CSS، مدل جعبه‌ای یا **CSS Box Model** است.

در CSS، هر عنصر HTML به‌صورت یک جعبه (Box) در نظر گرفته می‌شود. حتی اگر یک عنصر ظاهری ساده داشته باشد، مرورگر آن را به‌عنوان یک جعبه پردازش می‌کند.

این جعبه از چهار بخش اصلی تشکیل شده است:

1. `Content` — محتوای عنصر
2. `Padding` — فاصله داخلی
3. `Border` — حاشیه یا کادر دور عنصر
4. `Margin` — فاصله خارجی

درک درست این چهار مفهوم باعث می‌شود بتوانیم اندازه عناصر، فاصله‌ها، چیدمان صفحات و رفتار عناصر HTML را بهتر کنترل کنیم.

---

# ساختار کلی Box Model

ترتیب بخش‌های Box Model از داخل به خارج به شکل زیر است:

```text
+-------------------------------------------+
|                  MARGIN                   |
|   +-----------------------------------+   |
|   |              BORDER               |   |
|   |   +---------------------------+   |   |
|   |   |         PADDING           |   |   |
|   |   |   +-------------------+   |   |   |
|   |   |   |                   |   |   |   |
|   |   |   |      CONTENT      |   |   |   |
|   |   |   |                   |   |   |   |
|   |   |   +-------------------+   |   |   |
|   |   +---------------------------+   |   |
|   +-----------------------------------+   |
+-------------------------------------------+
```

هرکدام از این قسمت‌ها وظیفه متفاوتی دارند:

| بخش | کاربرد |
|---|---|
| Content | نمایش محتوای اصلی مانند متن، تصویر و سایر عناصر |
| Padding | ایجاد فاصله بین محتوا و Border |
| Border | ایجاد کادر دور عنصر |
| Margin | ایجاد فاصله بین عنصر و عناصر اطراف |

نکته مهم:

`Padding` داخل Border قرار دارد، اما `Margin` خارج از Border است.

---

# Content

`Content` هسته اصلی یک عنصر است.

محتوای عنصر می‌تواند شامل موارد زیر باشد:

- متن
- تصویر
- ویدئو
- عناصر HTML دیگر
- محتوای تولیدشده توسط CSS

برای مثال:

```html
<div class="box">
    Hello World!
</div>
```

```css
.box {
    width: 300px;
    height: 150px;
    background-color: lightblue;
}
```

در این مثال:

- عرض محتوای عنصر برابر 300 پیکسل است.
- ارتفاع محتوای عنصر برابر 150 پیکسل است.
- متن `Hello World!` داخل Content قرار می‌گیرد.

### ویژگی‌های مهم Content

دو ویژگی اصلی برای تعیین ابعاد محتوای یک عنصر عبارت‌اند از:

```css
width: 300px;
height: 150px;
```

ویژگی‌های دیگر:

```css
min-width: 200px;
max-width: 500px;

min-height: 100px;
max-height: 300px;
```

کاربرد:

- `width`: تعیین عرض
- `height`: تعیین ارتفاع
- `min-width`: حداقل عرض
- `max-width`: حداکثر عرض
- `min-height`: حداقل ارتفاع
- `max-height`: حداکثر ارتفاع

نکته:

در حالت پیش‌فرض `content-box`، مقدار `width` و `height` فقط ابعاد Content را مشخص می‌کنند، نه کل جعبه.

---

# Padding 

`Padding` فاصله داخلی یک عنصر است.

به زبان ساده، Padding فضای خالی بین محتوای عنصر و Border آن را مشخص می‌کند.

برای مثال:

```html
<div class="box">
    Hello World!
</div>
```

```css
.box {
    width: 300px;
    padding: 30px;
    border: 2px solid black;
}
```

در این مثال، متن از هر طرف 30 پیکسل با Border فاصله دارد.

### تصویر ذهنی Padding

```text
+--------------------------------+
|             BORDER             |
|                                |
|       30px PADDING             |
|                                |
|         Hello World!           |
|                                |
|                                |
+--------------------------------+
```

### روش‌های نوشتن Padding

#### حالت اول: مقدار یکسان برای چهار طرف

```css
.box {
    padding: 20px;
}
```

نتیجه:

- بالا: 20px
- راست: 20px
- پایین: 20px
- چپ: 20px

#### حالت دوم: دو مقدار

```css
.box {
    padding: 20px 40px;
}
```

نتیجه:

- بالا و پایین: 20px
- راست و چپ: 40px

#### حالت سوم: سه مقدار

```css
.box {
    padding: 10px 20px 30px;
}
```

نتیجه:

- بالا: 10px
- راست و چپ: 20px
- پایین: 30px

#### حالت چهارم: چهار مقدار

```css
.box {
    padding: 10px 20px 30px 40px;
}
```

ترتیب مقادیر:

```text
padding: TOP RIGHT BOTTOM LEFT;
```

یعنی:

- بالا: 10px
- راست: 20px
- پایین: 30px
- چپ: 40px

این ترتیب در CSS با عبارت ساعت‌گرد شناخته می‌شود.

### ویژگی‌های مستقل Padding

```css
.box {
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 30px;
    padding-left: 40px;
}
```

همچنین می‌توان از ویژگی‌های منطقی استفاده کرد:

```css
.box {
    padding-block: 20px;
    padding-inline: 30px;
}
```

این ویژگی‌ها به‌جای جهت‌های فیزیکی، با محورهای نوشتاری کار می‌کنند.

### نکات مهم Padding

1. Padding فضای داخلی عنصر را افزایش می‌دهد.
2. Padding پس‌زمینه عنصر را نیز پوشش می‌دهد.
3. Padding برخلاف Margin نمی‌تواند مقدار منفی داشته باشد.
4. Padding به‌صورت پیش‌فرض در محاسبه عرض و ارتفاع با Content جمع می‌شود.
5. Padding روی اندازه نهایی عنصر تأثیر می‌گذارد.

---

# Border

`Border` کادری است که دور Padding و Content قرار می‌گیرد.

با Border می‌توان برای عناصر HTML حاشیه بصری ایجاد کرد.

مثال:

```html
<div class="box">
    Hello World!
</div>
```

```css
.box {
    width: 300px;
    height: 150px;

    border: 3px solid black;
}
```

در این مثال یک کادر مشکی با ضخامت 3 پیکسل دور عنصر ایجاد می‌شود.

### ساختار Border

Border سه ویژگی اصلی دارد:

```css
border: 2px solid red;
```

این دستور شامل سه قسمت است:

| مقدار | کاربرد |
|---|---|
| 2px | ضخامت Border |
| solid | نوع خط |
| red | رنگ Border |

### انواع Border Style

```css
border-style: solid;
border-style: dashed;
border-style: dotted;
border-style: double;
border-style: groove;
border-style: ridge;
border-style: inset;
border-style: outset;
border-style: none;
```

توضیح:

- `solid`: خط پیوسته
- `dashed`: خط‌چین
- `dotted`: نقطه‌چین
- `double`: خط دوتایی
- `groove`: ظاهر فرورفته
- `ridge`: ظاهر برجسته
- `inset`: ظاهر داخلی و فرورفته
- `outset`: ظاهر خارجی و برجسته
- `none`: بدون Border

### تعیین Border برای هر طرف

```css
.box {
    border-top: 2px solid red;
    border-right: 3px dashed blue;
    border-bottom: 4px dotted green;
    border-left: 5px double black;
}
```

### تعیین ویژگی‌های مستقل

```css
.box {
    border-width: 2px;
    border-style: solid;
    border-color: red;
}
```

### Border Radius

برای گرد کردن گوشه‌های عنصر از `border-radius` استفاده می‌کنیم:

```css
.box {
    border: 2px solid black;
    border-radius: 15px;
}
```

مثال‌های دیگر:

```css
.box {
    border-radius: 50%;
}
```

```css
.box {
    border-radius: 10px 20px 30px 40px;
}
```

نکته:

`border-radius` فقط ظاهر گوشه‌های عنصر را تغییر می‌دهد و ضخامت Border را حذف نمی‌کند.

### نکات مهم Border

1. Border بین Padding و Margin قرار دارد.
2. ضخامت Border در حالت `content-box` به اندازه نهایی عنصر اضافه می‌شود.
3. Border می‌تواند برای هر چهار طرف مقدار متفاوتی داشته باشد.
4. Border می‌تواند از نظر ضخامت، رنگ و سبک متفاوت باشد.

---

# Margin 

`Margin` فاصله خارجی یک عنصر است.

به زبان ساده، Margin مشخص می‌کند که یک عنصر چه مقدار از عناصر اطراف خود فاصله داشته باشد.

مثال:

```html
<div class="box">
    Box One
</div>

<div class="box">
    Box Two
</div>
```

```css
.box {
    width: 200px;
    height: 100px;

    background-color: lightblue;

    margin: 20px;
}
```

در این مثال هر عنصر از اطراف خود 20 پیکسل فاصله خارجی دارد.

### تفاوت Padding و Margin

فرض کن یک کارت داریم که داخل آن متن قرار گرفته است.

- اگر بخواهیم متن از لبه داخلی کارت فاصله بگیرد، از Padding استفاده می‌کنیم.
- اگر بخواهیم کارت از عناصر اطراف فاصله بگیرد، از Margin استفاده می‌کنیم.

```css
.card {
    padding: 20px;
    margin: 30px;
}
```

### روش‌های نوشتن Margin

Margin نیز مانند Padding چهار روش اصلی دارد.

#### یک مقدار

```css
margin: 20px;
```

هر چهار طرف 20 پیکسل.

#### دو مقدار

```css
margin: 10px 20px;
```

- بالا و پایین: 10px
- راست و چپ: 20px

#### سه مقدار

```css
margin: 10px 20px 30px;
```

- بالا: 10px
- راست و چپ: 20px
- پایین: 30px

#### چهار مقدار

```css
margin: 10px 20px 30px 40px;
```

- بالا: 10px
- راست: 20px
- پایین: 30px
- چپ: 40px

### ویژگی‌های مستقل Margin

```css
.box {
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 30px;
    margin-left: 40px;
}
```

### استفاده از Auto در Margin

یکی از کاربردهای مهم Margin، وسط‌چین کردن یک عنصر بلوکی با عرض مشخص است.

```html
<div class="container">
    Hello World!
</div>
```

```css
.container {
    width: 400px;
    margin: 0 auto;
    background-color: lightblue;
}
```

در این مثال:

- `margin-top: 0`
- `margin-bottom: 0`
- `margin-left: auto`
- `margin-right: auto`

مرورگر فضای خالی افقی را بین دو طرف تقسیم می‌کند و عنصر در مرکز قرار می‌گیرد.

نکته مهم:

این روش زمانی کاربرد دارد که عنصر بتواند فضای افقی قابل تقسیم داشته باشد و عرض آن از فضای در دسترس کمتر باشد.

### Margin منفی

برخلاف Padding، مقدار Margin می‌تواند منفی باشد.

```css
.box {
    margin-top: -20px;
}
```

Margin منفی می‌تواند باعث نزدیک شدن عناصر به یکدیگر یا هم‌پوشانی آن‌ها شود.

### Margin Collapse

یکی از مفاهیم مهم و گاهی گیج‌کننده در CSS، پدیده Margin Collapse است.

این اتفاق معمولاً بین Margin عمودی دو عنصر Block در جریان عادی سند رخ می‌دهد.

مثال:

```html
<div class="box box-one">
    Box One
</div>

<div class="box box-two">
    Box Two
</div>
```

```css
.box-one {
    margin-bottom: 30px;
}

.box-two {
    margin-top: 20px;
}
```

ممکن است تصور کنیم فاصله دو عنصر برابر باشد با:

```text
30px + 20px = 50px
```

اما در حالت معمول Margin Collapse، مقدار بزرگ‌تر باقی می‌ماند:

```text
max(30px, 20px) = 30px
```

یعنی فاصله عمودی بین دو عنصر 30 پیکسل خواهد بود، نه 50 پیکسل.

نکات مهم Margin Collapse:

- عمدتاً برای Margin عمودی عناصر Block در جریان عادی رخ می‌دهد.
- Margin افقی به این شکل Collapse نمی‌شود.
- Margin عناصر Flex و Grid با یکدیگر Collapse نمی‌شود.
- ایجاد Border یا Padding بین دو Margin می‌تواند از Collapse شدن آن‌ها جلوگیری کند.
- ایجاد یک Block Formatting Context جدید نیز در شرایط مربوط، مانع Collapse شدن Marginهای بیرون و داخل آن می‌شود.

---

# تفاوت اصلی Padding و Margin

این دو ویژگی ممکن است در ابتدا شبیه به هم به نظر برسند، اما کاربرد متفاوتی دارند.

| ویژگی | Padding | Margin |
|---|---|---|
| نوع فاصله | داخلی | خارجی |
| محل قرارگیری | داخل Border | خارج Border |
| پس‌زمینه | شامل فضای Padding می‌شود | شامل فضای Margin نمی‌شود |
| مقدار منفی | مجاز نیست | مجاز است |
| Auto | برای وسط‌چین کردن عنصر کاربرد معمول ندارد | برای وسط‌چین کردن افقی کاربرد دارد |
| تأثیر بر ابعاد | در content-box ابعاد بیرونی را افزایش می‌دهد | فضای اشغال‌شده در چیدمان را افزایش می‌دهد |
| Collapse | ندارد | Margin عمودی ممکن است Collapse شود |

### مثال کاربردی

```html
<div class="card">
    <h2>Learning CSS</h2>
    <p>Understanding Box Model</p>
</div>
```

```css
.card {
    background-color: lightblue;

    padding: 30px;
    margin: 20px;

    border: 2px solid black;
}
```

در این مثال:

- `padding: 30px` محتوا را از Border دور می‌کند.
- `margin: 20px` کارت را از عناصر اطراف دور می‌کند.
- `border: 2px solid black` کادر دور کارت را ایجاد می‌کند.

---

# محاسبه اندازه واقعی عنصر در CSS

یکی از مهم‌ترین بخش‌های Box Model، محاسبه اندازه نهایی یک عنصر است.

برای این کار باید با ویژگی `box-sizing` آشنا شویم.

دو مقدار مهم آن عبارت‌اند از:

1. `content-box`
2. `border-box`

## Content-box

این مقدار، حالت پیش‌فرض CSS است.

```css
.box {
    width: 300px;
    height: 200px;

    padding: 20px;
    border: 5px solid black;

    box-sizing: content-box;
}
```

در این حالت:

`width` فقط عرض Content را مشخص می‌کند.

پس عرض واقعی عنصر برابر است با:

```text
Content Width = 300px

Padding Left  = 20px
Padding Right = 20px

Border Left  = 5px
Border Right = 5px

Total Width = 300 + 20 + 20 + 5 + 5

Total Width = 350px
```

برای ارتفاع:

```text
Content Height = 200px

Padding Top    = 20px
Padding Bottom = 20px

Border Top    = 5px
Border Bottom = 5px

Total Height = 200 + 20 + 20 + 5 + 5

Total Height = 250px
```

<details>
<summary>نمای تصویری محاسبه Content-box</summary>

```text
          Total Width = 350px
    <---------------------------->

    +----------------------------+
    |           Border           | 5px
    |  +----------------------+  |
    |  |       Padding        | 20px
    |  |  +----------------+  |  |
    |  |  |                |  |  |
    |  |  |    CONTENT     |  |  |
    |  |  |    300px       |  |  |
    |  |  |                |  |  |
    |  |  +----------------+  |  |
    |  +----------------------+  |
    +----------------------------+
```

</details>

نکته:

Margin در محاسبه عرض و ارتفاع خود Box وارد نمی‌شود، اما فضای بیشتری در چیدمان اشغال می‌کند.

اگر Margin چپ و راست را هم در نظر بگیریم:

```css
.box {
    width: 300px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```

فضای افقی اشغال‌شده در چیدمان:

```text
350 + 10 + 10 = 370px
```

## Border-box

در این حالت، عرض و ارتفاع مشخص‌شده شامل Content، Padding و Border هستند.

```css
.box {
    width: 300px;
    height: 200px;

    padding: 20px;
    border: 5px solid black;

    box-sizing: border-box;
}
```

در این حالت:

```text
Total Width = 300px

Content Width = 300 - 40 - 10

Content Width = 250px
```

و برای ارتفاع:

```text
Total Height = 200px

Content Height = 200 - 40 - 10

Content Height = 150px
```

یعنی برخلاف `content-box`، اضافه شدن Padding و Border باعث بزرگ‌تر شدن اندازه تعیین‌شده نمی‌شود.

### مقایسه دو حالت

| ویژگی | Content-box | Border-box |
|---|---:|---:|
| Width تعیین‌شده | 300px | 300px |
| Padding چپ و راست | 40px | 40px |
| Border چپ و راست | 10px | 10px |
| عرض Content | 300px | 250px |
| عرض نهایی Box | 350px | 300px |

---

# چرا استفاده از Border-box مهم است؟

در پروژه‌های واقعی معمولاً ترجیح داده می‌شود از `border-box` استفاده کنیم.

دلیل آن ساده است:

فرض کن می‌خواهیم یک کارت دقیقاً 300 پیکسل عرض داشته باشد.

اگر از `content-box` استفاده کنیم و Padding و Border اضافه کنیم، اندازه نهایی بیشتر از 300 پیکسل خواهد شد.

اما با `border-box`، عرض کلی عنصر همان 300 پیکسل باقی می‌ماند.

به همین دلیل بسیاری از توسعه‌دهندگان از کد زیر در ابتدای فایل CSS استفاده می‌کنند:

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

این کد باعث می‌شود تمام عناصر و شبه‌عناصر با مدل `border-box` محاسبه شوند.

نکته:

این یک روش رایج در پروژه‌های مدرن است، نه یک قانون اجباری CSS.

---

# مثال جامع از Box Model

در این مثال تمام مفاهیم را کنار یکدیگر بررسی می‌کنیم.

### HTML

```html
<div class="container">
    <div class="card">
        <h2>CSS Box Model</h2>
        <p>
            Learning Content, Padding, Border and Margin.
        </p>
    </div>
</div>
```

### CSS

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}

.container {
    width: 600px;
    margin: 50px auto;
    background-color: #eeeeee;
}

.card {
    width: 400px;

    padding: 30px;

    border: 3px solid black;

    margin: 20px auto;

    background-color: lightblue;
}

.card h2 {
    margin-bottom: 15px;
}

.card p {
    margin: 0;
}
```

### بررسی کد

**Container:**

- عرض آن 600 پیکسل است.
- از بالا و پایین 50 پیکسل Margin دارد.
- با `margin: auto` در مرکز افقی قرار می‌گیرد.

**Card:**

- عرض کلی آن 400 پیکسل است.
- از هر طرف 30 پیکسل Padding دارد.
- Border آن 3 پیکسل است.
- با Margin در مرکز Container قرار می‌گیرد.

**Heading:**

- از پایین 15 پیکسل Margin دارد.

**Paragraph:**

- تمام Marginهای پیش‌فرض آن صفر شده‌اند.

---

# تفاوت Box Model در Block و Inline

رفتار Box Model در عناصر مختلف HTML یکسان نیست.

برای مثال:

### Block Elements

عناصر Block معمولاً فضای افقی در دسترس را اشغال می‌کنند.

نمونه‌ها:

```html
<div></div>
<p></p>
<section></section>
<header></header>
```

ویژگی‌های Width و Height برای آن‌ها قابل اعمال است.

Padding، Border و Margin نیز در چهار جهت قابل استفاده هستند.

### Inline Elements

عناصر Inline معمولاً در جریان متن قرار می‌گیرند.

نمونه‌ها:

```html
<span></span>
<a></a>
<strong></strong>
```

در عناصر Inline غیرجایگزین‌شونده:

- Width و Height معمولاً اعمال نمی‌شوند.
- Padding افقی و Border افقی در چیدمان قابل مشاهده هستند.
- Padding و Border عمودی ممکن است روی محتوای اطراف هم‌پوشانی بصری داشته باشند، اما ارتفاع خط را به همان شکل افزایش نمی‌دهند.
- Margin افقی قابل اعمال است.
- Margin عمودی در جریان عادی روی فاصله خطوط اثر معمول ندارد.

برای کنترل بهتر ابعاد می‌توان از `inline-block` استفاده کرد:

```css
span {
    display: inline-block;

    width: 150px;
    height: 50px;

    padding: 10px;
    margin: 10px;

    border: 2px solid black;
}
```

در این حالت عنصر همچنان در جریان Inline قرار می‌گیرد، اما می‌توان Width و Height برای آن تعیین کرد.

نکته:

رفتار عناصر جایگزین‌شونده مانند `img` با عناصر Inline غیرجایگزین‌شونده یکسان نیست.

---

### یک قانون ساده برای همیشه

```text
Content
   ↓
Padding
   ↓
Border
   ↓
Margin
```

از داخل به بیرون:

1. Content: محتوای اصلی
2. Padding: فاصله داخلی
3. Border: کادر عنصر
4. Margin: فاصله خارجی

### فرمول محاسبه عرض در Content-box

```text
Total Width =
Content Width +
Padding Left +
Padding Right +
Border Left +
Border Right
```

### فرمول محاسبه ارتفاع در Content-box

```text
Total Height =
Content Height +
Padding Top +
Padding Bottom +
Border Top +
Border Bottom
```

### فرمول فضای افقی اشغال‌شده در چیدمان

```text
Occupied Width =
Margin Left +
Border Left +
Padding Left +
Content Width +
Padding Right +
Border Right +
Margin Right
```

CSS Box Model یکی از پایه‌ای‌ترین و در عین حال مهم‌ترین مفاهیم طراحی رابط کاربری است.

اگر این مفهوم را به‌خوبی درک کنی:

- اندازه واقعی عناصر را درست محاسبه می‌کنی.
- فاصله‌گذاری بین عناصر را بهتر مدیریت می‌کنی.
- مشکلات مربوط به Overflow را راحت‌تر تشخیص می‌دهی.
- کارت‌ها و کامپوننت‌های دقیق‌تری طراحی می‌کنی.
- رفتار عناصر Block و Inline را بهتر می‌فهمی.
- در طراحی Layoutهای پیچیده کمتر دچار مشکل می‌شوی.

**مهم‌ترین نکته:**

هیچ‌وقت Padding و Margin را با هم اشتباه نگیر.

Padding فضای داخل عنصر را کنترل می‌کند، اما Margin فاصله بیرونی عنصر را مشخص می‌کند.

وقتی این تفاوت را به‌درستی درک کنی و مفهوم `box-sizing` را یاد بگیری، بخش مهمی از منطق اندازه‌گیری و فاصله‌گذاری در CSS را فهمیده‌ای.

