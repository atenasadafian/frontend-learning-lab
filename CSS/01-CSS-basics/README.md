# ترکیب سلکتورها و سلکتورهای پیشرفته در CSS
## CSS Selector Combinators & Advanced Selectors

در CSS برای انتخاب عناصر HTML و اعمال استایل روی آن‌ها از Selector استفاده می‌کنیم.

سلکتورها به ما اجازه می‌دهند مشخص کنیم کدام عناصر باید استایل مشخصی دریافت کنند.

در ابتدا ممکن است فقط با سلکتورهایی مانند موارد زیر کار کنیم:

```css
p {
    color: red;
}

.title {
    font-size: 24px;
}

#header {
    background-color: black;
}
```

اما در پروژه‌های واقعی، همیشه انتخاب عناصر به این سادگی نیست.

برای مثال ممکن است بخواهیم:

- فقط پاراگراف‌هایی را انتخاب کنیم که داخل یک `div` قرار دارند.
- فقط فرزند مستقیم یک عنصر را انتخاب کنیم.
- عناصری را انتخاب کنیم که ویژگی `target="_blank"` دارند.
- فقط اولین فرزند یک والد را استایل دهیم.
- به لینک‌هایی که قبلاً بازدید شده‌اند استایل متفاوت بدهیم.
- فیلدهای نامعتبر یک فرم را مشخص کنیم.
- عناصر خاصی را بر اساس موقعیتشان در ساختار HTML انتخاب کنیم.

برای انجام این کارها از موارد زیر استفاده می‌کنیم:

1. Selector Combinators
2. Attribute Selectors
3. Child Pseudo-classes
4. Structural Pseudo-classes
5. State Pseudo-classes
6. Logical Pseudo-classes

---

# انواع سلکتورهای پایه

قبل از بررسی سلکتورهای پیشرفته، بهتر است با سلکتورهای پایه آشنا باشیم.

## Universal Selector

با علامت `*` تمام عناصر HTML انتخاب می‌شوند.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

کاربرد رایج آن Reset کردن استایل‌های پیش‌فرض مرورگر است.

## Element Selector

برای انتخاب تمام عناصر با یک نام مشخص استفاده می‌شود.

```css
p {
    color: blue;
}

h1 {
    font-size: 32px;
}
```

## Class Selector

برای انتخاب عناصری که کلاس مشخصی دارند استفاده می‌شود.

```css
.card {
    background-color: white;
    padding: 20px;
}
```

HTML:

```html
<div class="card">
    Product Card
</div>
```

## ID Selector

برای انتخاب عنصری با شناسه مشخص استفاده می‌شود.

```css
#main-header {
    background-color: black;
    color: white;
}
```

HTML:

```html
<header id="main-header">
    Website Header
</header>
```

## Grouping Selector

برای اعمال استایل مشترک روی چند سلکتور از کاما استفاده می‌کنیم.

```css
h1, h2, h3 {
    font-family: Arial, sans-serif;
    color: #333;
}
```

در این مثال استایل روی تمام عناصر `h1`، `h2` و `h3` اعمال می‌شود.

---

# ترکیب سلکتورها (Combinators)

Combinatorها برای مشخص کردن رابطه بین عناصر HTML استفاده می‌شوند.

چهار Combinator اصلی داریم:

| علامت | نام | کاربرد |
|---|---|---|
| Space | Descendant | انتخاب تمام نوادگان |
| `>` | Child | انتخاب فرزندان مستقیم |
| `+` | Adjacent Sibling | انتخاب خواهر یا برادر بلافاصله بعدی |
| `~` | General Sibling | انتخاب تمام خواهر یا برادرهای بعدی |

## Descendant Selector

این سلکتور با استفاده از فاصله بین دو سلکتور نوشته می‌شود.

```css
.parent p {
    color: red;
}
```

به این معنی است:

تمام عناصر `p` که در داخل عنصر دارای کلاس `parent` قرار دارند انتخاب شوند.

نکته مهم:

فرقی ندارد عنصر `p` فرزند مستقیم باشد یا در چند سطح تو در تو قرار گرفته باشد.

### مثال

HTML:

```html
<div class="parent">
    <p>Paragraph 1</p>

    <div>
        <p>Paragraph 2</p>
    </div>

    <section>
        <div>
            <p>Paragraph 3</p>
        </div>
    </section>
</div>

<p>Paragraph 4</p>
```

CSS:

```css
.parent p {
    color: red;
}
```

نتیجه:

- Paragraph 1 قرمز می‌شود.
- Paragraph 2 قرمز می‌شود.
- Paragraph 3 قرمز می‌شود.
- Paragraph 4 تغییری نمی‌کند.

زیرا سه پاراگراف اول از نوادگان `.parent` هستند.

## Child Selector

با استفاده از علامت `>` فقط فرزندان مستقیم یک عنصر انتخاب می‌شوند.

```css
.parent > p {
    color: blue;
}
```

### مثال

HTML:

```html
<div class="parent">
    <p>Paragraph 1</p>

    <div>
        <p>Paragraph 2</p>
    </div>

    <p>Paragraph 3</p>
</div>
```

CSS:

```css
.parent > p {
    color: blue;
}
```

نتیجه:

- Paragraph 1 آبی می‌شود.
- Paragraph 2 تغییر نمی‌کند.
- Paragraph 3 آبی می‌شود.

چرا؟

چون Paragraph 2 فرزند مستقیم `.parent` نیست و داخل یک `div` دیگر قرار دارد.

### تفاوت Descendant و Child

```css
.parent p {
    color: red;
}
```

تمام نوادگان `p` را انتخاب می‌کند.

```css
.parent > p {
    color: blue;
}
```

فقط فرزندان مستقیم `p` را انتخاب می‌کند.

## 3.3 Adjacent Sibling Selector

با علامت `+` نوشته می‌شود.

این سلکتور عنصر بلافاصله بعد از عنصر مشخص‌شده را انتخاب می‌کند، به شرط اینکه هر دو دارای والد یکسان باشند.

```css
h2 + p {
    color: green;
}
```

یعنی پاراگرافی را انتخاب کن که بلافاصله بعد از یک `h2` قرار گرفته است.

### مثال

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
</div>
```

CSS:

```css
h2 + p {
    color: green;
}
```

نتیجه:

- Paragraph 1 سبز می‌شود.
- Paragraph 2 تغییر نمی‌کند.

زیرا فقط اولین عنصر هم‌سطح و بلافاصله بعد از `h2` انتخاب می‌شود.

نکته:

اگر بین `h2` و `p` یک عنصر دیگر وجود داشته باشد، این سلکتور دیگر `p` را انتخاب نمی‌کند.

## 3.4 General Sibling Selector

با علامت `~` نوشته می‌شود.

تمام خواهر و برادرهای بعد از عنصر مشخص‌شده را انتخاب می‌کند.

```css
h2 ~ p {
    color: purple;
}
```

### مثال

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Paragraph 1</p>
    <span>Some text</span>
    <p>Paragraph 2</p>
    <p>Paragraph 3</p>
</div>
```

CSS:

```css
h2 ~ p {
    color: purple;
}
```

نتیجه:

هر سه پاراگراف انتخاب می‌شوند.

نکته:

وجود عناصر دیگر بین `h2` و `p` مشکلی ایجاد نمی‌کند؛ فقط باید هر دو هم‌والد باشند و `p` بعد از `h2` قرار گرفته باشد.

## 3.5 ترکیب چند سلکتور

می‌توان چند Combinator را با یکدیگر ترکیب کرد.

مثال:

```css
.container > .content p {
    color: red;
}
```

معنی:

1. عنصر دارای کلاس `container` را پیدا کن.
2. فرزند مستقیم آن با کلاس `content` را پیدا کن.
3. تمام پاراگراف‌های داخل آن را انتخاب کن.

مثال دیگر:

```css
.card > .card-body > p {
    font-size: 16px;
}
```

فقط پاراگراف‌هایی انتخاب می‌شوند که فرزند مستقیم `.card-body` باشند و `.card-body` نیز فرزند مستقیم `.card` باشد.

---

# 4. Attribute Selectors

Attribute Selectorها برای انتخاب عناصر بر اساس ویژگی‌های HTML استفاده می‌شوند.

ویژگی‌هایی مانند:

- `href`
- `src`
- `type`
- `target`
- `title`
- `disabled`
- `required`
- `data-*`

## 4.1 انتخاب عنصر دارای Attribute

ساختار:

```css
[attribute] {
    property: value;
}
```

مثال:

```css
input[required] {
    border: 2px solid red;
}
```

تمام inputهایی که ویژگی `required` دارند انتخاب می‌شوند.

HTML:

```html
<input type="text" required>

<input type="text">

<input type="email" required>
```

در این مثال input اول و سوم انتخاب می‌شوند.

## 4.2 انتخاب بر اساس مقدار دقیق Attribute

ساختار:

```css
[attribute="value"] {
    property: value;
}
```

مثال:

```css
input[type="text"] {
    border: 1px solid gray;
}
```

فقط inputهایی که مقدار `type` آن‌ها دقیقاً `text` است انتخاب می‌شوند.

HTML:

```html
<input type="text">

<input type="email">

<input type="password">
```

## 4.3 انتخاب Attribute با مقدار شروع‌شونده

از علامت `^=` استفاده می‌شود.

ساختار:

```css
[attribute^="value"] {
    property: value;
}
```

مثال:

```css
a[href^="https"] {
    color: green;
}
```

تمام لینک‌هایی که مقدار `href` آن‌ها با `https` شروع می‌شود انتخاب می‌شوند.

HTML:

```html
<a href="https://example.com">HTTPS Link</a>

<a href="http://example.com">HTTP Link</a>

<a href="/about">About</a>
```

فقط لینک اول انتخاب می‌شود.

## 4.4 انتخاب Attribute با مقدار پایان‌یابنده

از علامت `$=` استفاده می‌شود.

```css
[attribute$="value"] {
    property: value;
}
```

مثال:

```css
a[href$=".pdf"] {
    color: red;
}
```

تمام لینک‌هایی که آدرس آن‌ها به `.pdf` ختم می‌شود انتخاب می‌شوند.

HTML:

```html
<a href="file.pdf">PDF File</a>

<a href="image.png">Image</a>

<a href="document.pdf">Document</a>
```

لینک اول و سوم انتخاب می‌شوند.

## 4.5 انتخاب Attribute شامل یک عبارت

از علامت `*=` استفاده می‌شود.

```css
[attribute*="value"] {
    property: value;
}
```

مثال:

```css
a[href*="google"] {
    color: blue;
}
```

هر لینکی که مقدار `href` آن شامل عبارت `google` باشد انتخاب می‌شود.

HTML:

```html
<a href="https://google.com">Google</a>

<a href="https://google.com/search">Google Search</a>

<a href="https://example.com">Example</a>
```

دو لینک اول انتخاب می‌شوند.

## 4.6 انتخاب Attribute با مقدار شروع‌شونده از یک کلمه

از علامت `|=` استفاده می‌شود.

```css
[attribute|="value"] {
    property: value;
}
```

این عملگر زمانی کاربرد دارد که مقدار Attribute دقیقاً با عبارت مشخص‌شده برابر باشد یا با آن عبارت و یک خط تیره (`-`) شروع شود.

مثال:

```css
[lang|="en"] {
    color: blue;
}
```

HTML:

```html
<p lang="en">English</p>

<p lang="en-US">American English</p>

<p lang="en-GB">British English</p>

<p lang="fa">Persian</p>
```

سه پاراگراف اول انتخاب می‌شوند.

## 4.7 انتخاب Attribute شامل یک کلمه مشخص

از علامت `~=` استفاده می‌شود.

```css
[attribute~="value"] {
    property: value;
}
```

این عملگر زمانی استفاده می‌شود که مقدار Attribute شامل یک کلمه مستقل و جداشده با فاصله باشد.

مثال:

```css
[class~="active"] {
    background-color: green;
}
```

HTML:

```html
<div class="active">Item 1</div>

<div class="menu active">Item 2</div>

<div class="inactive">Item 3</div>
```

دو عنصر اول انتخاب می‌شوند.

نکته:

`~=` برای کلمات مستقل در مقادیر جداشده با فاصله کاربرد دارد، نه برای جست‌وجوی هر زیررشته.

## 4.8 Case Sensitivity در Attribute Selectors

در بعضی Attributeها، مقایسه مقدار می‌تواند به حروف بزرگ و کوچک حساس باشد.

برای تعیین مقایسه بدون حساسیت به حروف از `i` استفاده می‌کنیم.

```css
input[type="TEXT" i] {
    border: 2px solid red;
}
```

این سلکتور مقادیری مانند `text`، `TEXT` و `Text` را نیز تطبیق می‌دهد.

برای مقایسه حساس به حروف می‌توان از `s` استفاده کرد:

```css
[data-status="Active" s] {
    color: green;
}
```

نکته: پشتیبانی و رفتار مقایسه به نوع Attribute و استاندارد مربوط به آن وابسته است.

### جدول خلاصه Attribute Selectors

| علامت | کاربرد | مثال |
|---|---|---|
| `[attr]` | وجود Attribute | `[required]` |
| `[attr="x"]` | مقدار دقیق | `[type="text"]` |
| `[attr^="x"]` | شروع با مقدار | `[href^="https"]` |
| `[attr$="x"]` | پایان با مقدار | `[href$=".pdf"]` |
| `[attr*="x"]` | شامل مقدار | `[href*="google"]` |
| `[attr~="x"]` | شامل کلمه مستقل | `[class~="active"]` |
| `[attr\|="x"]` | مقدار دقیق یا شروع با مقدار و خط تیره | `[lang\|="en"]` |

---

# 5. Child Pseudo-classes

Child Pseudo-classها برای انتخاب عناصر بر اساس موقعیت آن‌ها در بین فرزندان یک والد استفاده می‌شوند.

این دسته از مهم‌ترین سلکتورهای پیشرفته CSS هستند.

## 5.1 :first-child

اولین فرزند یک والد را انتخاب می‌کند.

```css
li:first-child {
    color: red;
}
```

HTML:

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

فقط Item 1 انتخاب می‌شود.

## 5.2 :last-child

آخرین فرزند یک والد را انتخاب می‌کند.

```css
li:last-child {
    color: blue;
}
```

در مثال قبل، Item 3 انتخاب می‌شود.

## 5.3 :only-child

عنصری را انتخاب می‌کند که تنها فرزند عنصر والد خود باشد.

```css
p:only-child {
    color: green;
}
```

HTML:

```html
<div>
    <p>Only Paragraph</p>
</div>

<div>
    <p>First Paragraph</p>
    <p>Second Paragraph</p>
</div>
```

فقط پاراگراف داخل `div` اول انتخاب می‌شود.

## 5.4 :nth-child()

برای انتخاب فرزند بر اساس شماره موقعیت آن استفاده می‌شود.

```css
li:nth-child(2) {
    color: red;
}
```

فقط دومین فرزند انتخاب می‌شود.

HTML:

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
</ul>
```

Item 2 انتخاب می‌شود.

### انتخاب فرزندان زوج

```css
li:nth-child(even) {
    background-color: lightgray;
}
```

فرزندان دوم، چهارم، ششم و ... انتخاب می‌شوند.

### انتخاب فرزندان فرد

```css
li:nth-child(odd) {
    background-color: lightblue;
}
```

فرزندان اول، سوم، پنجم و ... انتخاب می‌شوند.

### انتخاب هر سه فرزند یک‌بار

```css
li:nth-child(3n) {
    color: red;
}
```

فرزندان سوم، ششم، نهم و ... انتخاب می‌شوند.

### انتخاب از فرزند دوم به بعد

```css
li:nth-child(n+2) {
    color: blue;
}
```

تمام فرزندان از موقعیت دوم به بعد انتخاب می‌شوند.

### انتخاب سه فرزند اول

```css
li:nth-child(-n+3) {
    color: green;
}
```

فرزندان اول، دوم و سوم انتخاب می‌شوند.

### فرمول nth-child

ساختار کلی:

```css
:nth-child(An + B)
```

در این فرمول:

- `A`: فاصله بین موقعیت‌های انتخاب‌شده را مشخص می‌کند.
- `n`: یک عدد صحیح از صفر به بعد است.
- `B`: موقعیت اولیه را مشخص می‌کند.

مثال:

```css
li:nth-child(2n+1) {
    color: red;
}
```

موقعیت‌های انتخاب‌شده:

```text
1, 3, 5, 7, 9, ...
```

مثال:

```css
li:nth-child(3n+2) {
    color: blue;
}
```

موقعیت‌های انتخاب‌شده:

```text
2, 5, 8, 11, ...
```

## 5.5 :nth-last-child()

مشابه `nth-child()` است، با این تفاوت که شمارش را از انتهای فرزندان شروع می‌کند.

```css
li:nth-last-child(2) {
    color: red;
}
```

دومین فرزند از انتها انتخاب می‌شود.

مثال:

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
    <li>Item 5</li>
</ul>
```

در این مثال Item 4 انتخاب می‌شود.

## 5.6 :first-of-type

اولین عنصر از یک نوع مشخص را در بین خواهر و برادرهای خود انتخاب می‌کند.

```css
p:first-of-type {
    color: red;
}
```

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Paragraph 1</p>
    <p>Paragraph 2</p>
    <p>Paragraph 3</p>
</div>
```

فقط اولین `p` انتخاب می‌شود.

## 5.7 :last-of-type

آخرین عنصر از نوع مشخص را انتخاب می‌کند.

```css
p:last-of-type {
    color: blue;
}
```

در مثال قبل، Paragraph 3 انتخاب می‌شود.

## 5.8 :only-of-type

عنصری را انتخاب می‌کند که تنها عنصر از نوع خودش در بین خواهر و برادرهایش باشد.

```css
p:only-of-type {
    color: green;
}
```

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Only Paragraph</p>
    <span>Text</span>
</div>
```

پاراگراف انتخاب می‌شود؛ زیرا تنها عنصر `p` در بین فرزندان این والد است.

## 5.9 :nth-of-type()

برای انتخاب عنصر از یک نوع مشخص بر اساس موقعیت استفاده می‌شود.

```css
p:nth-of-type(2) {
    color: red;
}
```

دومین پاراگراف در بین خواهر و برادرهای هم‌نوع خودش انتخاب می‌شود.

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Paragraph 1</p>
    <span>Text</span>
    <p>Paragraph 2</p>
    <p>Paragraph 3</p>
</div>
```

Paragraph 2 انتخاب می‌شود.

## 5.10 :nth-last-of-type()

مشابه `nth-of-type()` است، اما شمارش از انتهای عناصر هم‌نوع انجام می‌شود.

```css
p:nth-last-of-type(2) {
    color: purple;
}
```

دومین پاراگراف از انتها انتخاب می‌شود.

### تفاوت nth-child و nth-of-type

این تفاوت بسیار مهم است.

HTML:

```html
<div>
    <h2>Title</h2>
    <p>Paragraph 1</p>
    <span>Text</span>
    <p>Paragraph 2</p>
</div>
```

CSS:

```css
p:nth-child(2) {
    color: red;
}
```

در اینجا Paragraph 1 انتخاب می‌شود؛ زیرا دومین فرزند والد است.

اما:

```css
p:nth-of-type(2) {
    color: blue;
}
```

Paragraph 2 انتخاب می‌شود؛ زیرا دومین عنصر `p` است.

**نکته مهم:**

- `nth-child()` تمام فرزندان را برای شمارش در نظر می‌گیرد.
- `nth-of-type()` فقط عناصر هم‌نوع را برای شمارش در نظر می‌گیرد.

---

# 6. Structural Pseudo-classes

این Pseudo-classها برای انتخاب عناصر بر اساس ساختار و وضعیت خاص DOM استفاده می‌شوند.

## 6.1 :empty

عناصری را انتخاب می‌کند که هیچ فرزند عنصری یا گره متنی ندارند.

```css
div:empty {
    display: none;
}
```

HTML:

```html
<div></div>

<div>
    Hello
</div>

<div>
    <p>Text</p>
</div>
```

فقط `div` کاملاً خالی انتخاب می‌شود.

نکته:

وجود حتی یک فضای خالی یا خط جدید متنی ممکن است باعث شود عنصر دیگر با `:empty` مطابقت نداشته باشد.

## 6.2 :root

عنصر ریشه سند را انتخاب می‌کند.

در سند HTML معمولاً عنصر `html` است.

```css
:root {
    --primary-color: #3498db;
    --text-color: #333;
}
```

یکی از کاربردهای مهم آن تعریف CSS Variables است.

مثال استفاده:

```css
button {
    background-color: var(--primary-color);
    color: white;
}
```

---

# 7. State Pseudo-classes

State Pseudo-classها برای انتخاب عناصر بر اساس وضعیت فعلی آن‌ها استفاده می‌شوند.

## 7.1 :checked

برای انتخاب checkbox یا radio انتخاب‌شده استفاده می‌شود.

```css
input:checked {
    accent-color: green;
}
```

HTML:

```html
<input type="checkbox" checked>

<input type="checkbox">
```

فقط checkbox اول انتخاب می‌شود.

## 7.2 :disabled

عناصر غیرفعال را انتخاب می‌کند.

```css
input:disabled {
    background-color: #ddd;
    cursor: not-allowed;
}
```

HTML:

```html
<input type="text">

<input type="text" disabled>
```

## 7.3 :enabled

عناصر فعال را انتخاب می‌کند.

```css
input:enabled {
    border: 1px solid green;
}
```

## 7.4 :required

فیلدهایی را انتخاب می‌کند که ویژگی `required` دارند.

```css
input:required {
    border-left: 3px solid red;
}
```

## 7.5 :optional

فیلدهایی را انتخاب می‌کند که اجباری نیستند.

```css
input:optional {
    border-left: 3px solid gray;
}
```

## 7.6 :valid

عناصری را انتخاب می‌کند که مقدار آن‌ها مطابق محدودیت‌های اعتبارسنجی HTML است.

```css
input:valid {
    border: 2px solid green;
}
```

مثال:

```html
<input type="email" value="test@example.com">
```

## 7.7 :invalid

عناصری را انتخاب می‌کند که مقدار آن‌ها با محدودیت‌های اعتبارسنجی مطابقت ندارد.

```css
input:invalid {
    border: 2px solid red;
}
```

مثال:

```html
<form>
    <input type="email" required>
    <button type="submit">Submit</button>
</form>
```

## 7.8 :in-range

فیلدهایی را انتخاب می‌کند که مقدار آن‌ها در محدوده min و max قرار دارد.

```css
input:in-range {
    border: 2px solid green;
}
```

HTML:

```html
<input type="number" min="1" max="100" value="50">
```

## 7.9 :out-of-range

فیلدهایی را انتخاب می‌کند که مقدار آن‌ها خارج از محدوده مجاز است.

```css
input:out-of-range {
    border: 2px solid red;
}
```

## 7.10 :read-only

عناصری را انتخاب می‌کند که وضعیت فقط‌خواندنی دارند.

```css
input:read-only {
    background-color: #eee;
}
```

HTML:

```html
<input type="text" value="Fixed Value" readonly>
```

## 7.11 :read-write

عناصری را انتخاب می‌کند که کاربر می‌تواند مقدار آن‌ها را تغییر دهد.

```css
input:read-write {
    background-color: white;
}
```

---

# 8. User Action Pseudo-classes

این دسته برای استایل‌دهی بر اساس تعامل کاربر با عناصر استفاده می‌شوند.

## 8.1 :hover

زمانی فعال می‌شود که نشانگر ماوس روی عنصر قرار بگیرد.

```css
button:hover {
    background-color: blue;
    color: white;
}
```

## 8.2 :active

در زمانی که عنصر در حال فعال شدن توسط کاربر است، مثلاً هنگام فشردن دکمه ماوس، اعمال می‌شود.

```css
button:active {
    transform: scale(0.95);
}
```

## 8.3 :focus

زمانی فعال می‌شود که عنصر Focus دریافت کند.

```css
input:focus {
    outline: 2px solid blue;
}
```

مثلاً زمانی که کاربر داخل یک input کلیک می‌کند یا با کیبورد به آن می‌رسد.

## 8.4 :focus-visible

زمانی اعمال می‌شود که مرورگر تشخیص دهد نمایش نشانه Focus برای کاربر ضروری است؛ معمولاً هنگام استفاده از کیبورد.

```css
button:focus-visible {
    outline: 3px solid orange;
    outline-offset: 3px;
}
```

این Pseudo-class برای دسترس‌پذیری بسیار مفید است.

## 8.5 :focus-within

زمانی روی یک والد فعال می‌شود که خود عنصر یا یکی از عناصر داخلی آن Focus داشته باشد.

```css
.form-group:focus-within {
    border: 2px solid blue;
}
```

HTML:

```html
<div class="form-group">
    <label>Email</label>
    <input type="email">
</div>
```

وقتی input داخل `.form-group` فوکوس دریافت کند، خود `.form-group` نیز استایل می‌گیرد.

## 8.6 :visited

لینک‌هایی را انتخاب می‌کند که کاربر قبلاً از آن‌ها بازدید کرده است.

```css
a:visited {
    color: purple;
}
```

نکته امن
