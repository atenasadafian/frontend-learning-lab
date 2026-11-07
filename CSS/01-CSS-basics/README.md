# ترکیب سلکتورها و سلکتورهای پیشرفته در CSS
## CSS Selector Combinators & Advanced Selectors

## فهرست مطالب

- [1. مقدمه](#1-مقدمه)
- [2. انواع سلکتورهای پایه](#2-انواع-سلکتورهای-پایه)
- [3. ترکیب سلکتورها (Combinators)](#3-ترکیب-سلکتورها-combinators)
  - [3.1 Descendant Selector](#31-descendant-selector)
  - [3.2 Child Selector](#32-child-selector)
  - [3.3 Adjacent Sibling Selector](#33-adjacent-sibling-selector)
  - [3.4 General Sibling Selector](#34-general-sibling-selector)
  - [3.5 ترکیب چند سلکتور](#35-ترکیب-چند-سلکتور)
- [4. Attribute Selectors](#4-attribute-selectors)
- [5. Child Pseudo-classes](#5-child-pseudo-classes)
- [6. Structural Pseudo-classes](#6-structural-pseudo-classes)
- [7. State Pseudo-classes](#7-state-pseudo-classes)
- [8. User Action Pseudo-classes](#8-user-action-pseudo-classes)
- [9. Form Pseudo-classes](#9-form-pseudo-classes)
- [10. Logical Pseudo-classes](#10-logical-pseudo-classes)
- [11. Pseudo-elements](#11-pseudo-elements)
- [12. ترکیب سلکتورهای پیشرفته](#12-ترکیب-سلکتورهای-پیشرفته)
- [13. Specificity یا اولویت سلکتورها](#13-specificity-یا-اولویت-سلکتورها)
- [14. مثال کاربردی جامع](#14-مثال-کاربردی-جامع)
- [15. نکات مهم و اشتباهات رایج](#15-نکات-مهم-و-اشتباهات-رایج)
- [16. جمع‌بندی](#16-جمع‌بندی)

---

# 1. مقدمه

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

# 2. انواع سلکتورهای پایه

قبل از بررسی سلکتورهای پیشرفته، بهتر است با سلکتورهای پایه آشنا باشیم.

## 2.1 Universal Selector

با علامت `*` تمام عناصر HTML انتخاب می‌شوند.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

کاربرد رایج آن Reset کردن استایل‌های پیش‌فرض مرورگر است.

## 2.2 Element Selector

برای انتخاب تمام عناصر با یک نام مشخص استفاده می‌شود.

```css
p {
    color: blue;
}

h1 {
    font-size: 32px;
}
```

## 2.3 Class Selector

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

## 2.4 ID Selector

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

## 2.5 Grouping Selector

برای اعمال استایل مشترک روی چند سلکتور از کاما استفاده می‌کنیم.

```css
h1, h2, h3 {
    font-family: Arial, sans-serif;
    color: #333;
}
```

در این مثال استایل روی تمام عناصر `h1`، `h2` و `h3` اعمال می‌شود.

---

# 3. ترکیب سلکتورها (Combinators)

Combinatorها برای مشخص کردن رابطه بین عناصر HTML استفاده می‌شوند.

چهار Combinator اصلی داریم:

| علامت | نام | کاربرد |
|---|---|---|
| Space | Descendant | انتخاب تمام نوادگان |
| `>` | Child | انتخاب فرزندان مستقیم |
| `+` | Adjacent Sibling | انتخاب خواهر یا برادر بلافاصله بعدی |
| `~` | General Sibling | انتخاب تمام خواهر یا برادرهای بعدی |

## 3.1 Descendant Selector

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

## 3.2 Child Selector

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

نکته امنیتی:

مرورگرها برای جلوگیری از افشای تاریخچه بازدید کاربران، محدودیت‌هایی روی استایل‌دهی `:visited` اعمال می‌کنند. برای مثال، امکان تغییر آزادانه تمام ویژگی‌های CSS وجود ندارد.

## 8.7 :link

لینک‌هایی را انتخاب می‌کند که هنوز در تاریخچه مرورگر بازدیدشده محسوب نمی‌شوند.

```css
a:link {
    color: blue;
}
```

---

# 9. Form Pseudo-classes

این سلکتورها به‌خصوص هنگام طراحی فرم‌ها بسیار کاربرد دارند.

## 9.1 :placeholder-shown

زمانی فعال می‌شود که Placeholder یک فیلد در حال نمایش باشد.

```css
input:placeholder-shown {
    background-color: #f5f5f5;
}
```

HTML:

```html
<input type="text" placeholder="Enter your name">
```

## 9.2 :default

عنصر فرم پیش‌فرض را انتخاب می‌کند.

```css
input:default {
    accent-color: green;
}
```

برای مثال، یک radio یا checkbox که به‌صورت پیش‌فرض انتخاب شده است.

## 9.3 :indeterminate

عناصری را انتخاب می‌کند که وضعیت آن‌ها نامشخص یا میانی است.

```css
input:indeterminate {
    outline: 2px solid orange;
}
```

این حالت در checkboxهایی که وضعیت انتخاب آن‌ها توسط ویژگی‌های مرورگر یا کنترل فرم به حالت میانی تنظیم شده، کاربرد دارد.

## 9.4 :user-valid

زمانی عنصر را انتخاب می‌کند که کاربر با آن تعامل داشته و مقدار آن معتبر باشد.

```css
input:user-valid {
    border-color: green;
}
```

## 9.5 :user-invalid

زمانی عنصر را انتخاب می‌کند که کاربر با آن تعامل داشته و مقدار آن نامعتبر باشد.

```css
input:user-invalid {
    border-color: red;
}
```

تفاوت مهم:

`:invalid` ممکن است قبل از تعامل کاربر نیز فعال باشد؛ اما `:user-invalid` برای نمایش وضعیت نامعتبر پس از تعامل کاربر مناسب‌تر است.

---

# 10. Logical Pseudo-classes

این دسته امکان نوشتن سلکتورهای پیشرفته‌تر و انعطاف‌پذیرتر را فراهم می‌کند.

مهم‌ترین موارد:

- `:not()`
- `:is()`
- `:where()`
- `:has()`

## 10.1 :not()

برای انتخاب عناصری استفاده می‌شود که با سلکتور مشخص‌شده مطابقت ندارند.

مثال:

```css
button:not(.primary) {
    background-color: gray;
}
```

تمام دکمه‌هایی که کلاس `primary` ندارند انتخاب می‌شوند.

مثال دیگر:

```css
input:not([type="submit"]) {
    border: 1px solid gray;
}
```

تمام inputها به‌جز inputهایی که نوع آن‌ها submit است انتخاب می‌شوند.

### ترکیب چند شرط

```css
p:not(.active):not(.hidden) {
    color: blue;
}
```

پاراگراف‌هایی انتخاب می‌شوند که نه کلاس `active` دارند و نه کلاس `hidden`.

## 10.2 :is()

برای گروه‌بندی چند سلکتور و کوتاه کردن کد CSS استفاده می‌شود.

بدون `:is()`:

```css
header a,
main a,
footer a {
    color: blue;
}
```

با `:is()`:

```css
:is(header, main, footer) a {
    color: blue;
}
```

تمام لینک‌های داخل `header`، `main` و `footer` انتخاب می‌شوند.

### مثال پیشرفته

```css
.card :is(h1, h2, h3, p) {
    margin-bottom: 10px;
}
```

تمام عناصر عنوان و پاراگراف داخل `.card` انتخاب می‌شوند.

نکته:

Specificity سلکتور `:is()` برابر با بیشترین Specificity بین آرگومان‌های آن است.

## 10.3 :where()

از نظر انتخاب عناصر مشابه `:is()` عمل می‌کند؛ اما تفاوت مهمی دارد.

Specificity مربوط به `:where()` و تمام آرگومان‌های آن صفر است.

مثال:

```css
:where(header, main, footer) a {
    color: blue;
}
```

لینک‌های داخل این سه بخش انتخاب می‌شوند، اما خود `:where()` در محاسبه Specificity هیچ امتیازی اضافه نمی‌کند.

### تفاوت :is و :where

```css
:is(.card, #main) p {
    color: red;
}
```

در این مثال Specificity به دلیل وجود `#main` مقدار بالایی دارد.

اما:

```css
:where(.card, #main) p {
    color: blue;
}
```

Specificity فقط از `p` محاسبه می‌شود؛ زیرا `:where()` و محتوای داخل آن امتیاز صفر دارند.

کاربرد مهم `:where()`:

نوشتن استایل‌های پایه و عمومی که به‌راحتی توسط استایل‌های اختصاصی‌تر بازنویسی شوند.

## 10.4 :has()

یکی از قدرتمندترین Pseudo-classهای CSS است.

از آن برای انتخاب یک عنصر بر اساس وجود عناصر دیگر در داخل آن یا رابطه آن با عناصر دیگر استفاده می‌شود.

به همین دلیل گاهی به آن Parent Selector نیز گفته می‌شود.

مثال:

```css
.card:has(img) {
    border: 2px solid green;
}
```

تمام کارت‌هایی انتخاب می‌شوند که حداقل یک `img` داخل آن‌ها وجود دارد.

HTML:

```html
<div class="card">
    <img src="product.jpg" alt="Product">
    <h2>Product 1</h2>
</div>

<div class="card">
    <h2>Product 2</h2>
</div>
```

فقط کارت اول انتخاب می‌شود.

### انتخاب والد دارای فرزند مشخص

```css
div:has(> p) {
    background-color: lightgray;
}
```

تمام divهایی انتخاب می‌شوند که حداقل یک پاراگراف به‌عنوان فرزند مستقیم دارند.

### انتخاب کارت دارای دکمه

```css
.card:has(button) {
    padding: 20px;
}
```

### انتخاب فرم دارای فیلد نامعتبر

```css
form:has(input:invalid) {
    border: 2px solid red;
}
```

### انتخاب عنصر قبل از یک عنصر مشخص

```css
h2:has(+ p) {
    color: red;
}
```

عنوان‌هایی انتخاب می‌شوند که بلافاصله بعد از آن‌ها یک پاراگراف قرار گرفته است.

نکته:

`:has()` قابلیت بسیار قدرتمندی است، اما در انتخاب‌های پیچیده و پرتکرار بهتر است به عملکرد و خوانایی کد نیز توجه شود.

---

# 11. Pseudo-elements

Pseudo-elementها با Pseudo-classها متفاوت هستند.

Pseudo-class برای انتخاب یک عنصر بر اساس وضعیت یا موقعیت آن استفاده می‌شود.

اما Pseudo-element بخشی از یک عنصر را انتخاب می‌کند یا یک بخش مجازی در ساختار نمایشی ایجاد می‌کند.

معمولاً با دو دونقطه (`::`) نوشته می‌شوند.

## 11.1 ::before

برای ایجاد محتوای مجازی قبل از محتوای عنصر استفاده می‌شود.

```css
.title::before {
    content: "★ ";
    color: orange;
}
```

HTML:

```html
<h2 class="title">Welcome</h2>
```

نتیجه نمایشی:

```text
★ Welcome
```

## 11.2 ::after

برای ایجاد محتوای مجازی بعد از محتوای عنصر استفاده می‌شود.

```css
.title::after {
    content: " ✓";
    color: green;
}
```

## 11.3 ::first-letter

اولین حرف یک بخش متنی را انتخاب می‌کند.

```css
p::first-letter {
    font-size: 30px;
    color: red;
    font-weight: bold;
}
```

## 11.4 ::first-line

اولین خط متنی را انتخاب می‌کند.

```css
p::first-line {
    color: blue;
    font-weight: bold;
}
```

## 11.5 ::selection

بخشی از متن را که کاربر انتخاب کرده است استایل می‌دهد.

```css
::selection {
    background-color: yellow;
    color: black;
}
```

## 11.6 ::placeholder

متن Placeholder داخل فرم را انتخاب می‌کند.

```css
input::placeholder {
    color: gray;
    font-size: 14px;
}
```

## 11.7 ::marker

نشانگر لیست را انتخاب می‌کند.

```css
li::marker {
    color: red;
    font-size: 20px;
}
```

## 11.8 ::file-selector-button

دکمه انتخاب فایل در input از نوع file را انتخاب می‌کند.

```css
input::file-selector-button {
    background-color: blue;
    color: white;
    border: none;
    padding: 10px;
}
```

---

# 12. ترکیب سلکتورهای پیشرفته

یکی از مهم‌ترین مهارت‌ها در CSS توانایی ترکیب چند نوع Selector است.

در ادامه چند نمونه کاربردی را بررسی می‌کنیم.

## مثال 1: انتخاب لینک‌های خارجی

```css
a[href^="https"] {
    color: green;
}
```

تمام لینک‌هایی که آدرس آن‌ها با https شروع می‌شود انتخاب می‌شوند.

## مثال 2: انتخاب فرزندان مستقیم یک کارت

```css
.card > .card-body > p {
    color: #333;
}
```

## مثال 3: انتخاب آخرین پاراگراف داخل کارت

```css
.card p:last-of-type {
    margin-bottom: 0;
}
```

## مثال 4: انتخاب دکمه‌هایی که Disabled نیستند

```css
button:not(:disabled) {
    cursor: pointer;
}
```

## مثال 5: انتخاب کارت‌هایی که تصویر دارند

```css
.card:has(img) {
    border: 1px solid green;
}
```

## مثال 6: انتخاب فیلدهای اجباری داخل فرم

```css
form input[required] {
    border-left: 3px solid red;
}
```

## مثال 7: انتخاب دومین آیتم فعال در لیست

```css
li.active:nth-child(2) {
    color: red;
}
```

این سلکتور عنصری را انتخاب می‌کند که هم کلاس `active` دارد و هم فرزند دوم والد خود است.

## مثال 8: انتخاب پاراگراف‌هایی که بعد از Heading قرار دارند

```css
h2 + p {
    font-size: 18px;
}
```

## مثال 9: انتخاب تمام پاراگراف‌های بعد از Heading

```css
h2 ~ p {
    color: gray;
}
```

## مثال 10: انتخاب فرم دارای فیلد نامعتبر و استایل‌دهی به آن

```css
form:has(input:invalid) {
    border: 2px solid red;
    padding: 20px;
}
```

## مثال 11: انتخاب لینک داخل کارت‌هایی که تصویر دارند

```css
.card:has(img) a {
    color: blue;
}
```

## مثال 12: ترکیب Attribute و Pseudo-class

```css
input[type="email"]:focus {
    border-color: blue;
}
```

## مثال 13: ترکیب چند شرط برای انتخاب یک عنصر

```css
ul.menu > li:not(.disabled):nth-child(odd) {
    background-color: #eee;
}
```

این سلکتور عناصر `li` را انتخاب می‌کند که:

1. فرزند مستقیم `ul.menu` باشند.
2. کلاس `disabled` نداشته باشند.
3. موقعیت فرد داشته باشند.

---

# 13. Specificity یا اولویت سلکتورها

یکی از مهم‌ترین موضوعات در CSS، Specificity است.

زمانی که چند قانون CSS روی یک عنصر اعمال می‌شوند، مرورگر باید تصمیم بگیرد کدام قانون اولویت دارد.

برای این کار از مفهوم Specificity استفاده می‌کند.

## 13.1 ساختار Specificity

به‌صورت ساده، Specificity را می‌توان با چهار بخش در نظر گرفت:

```text
A - B - C - D
```

| بخش | نوع |
|---|---|
| A | Inline Styles |
| B | ID Selectors |
| C | Class، Attribute و Pseudo-class |
| D | Element و Pseudo-element |

برای درک بهتر:

| Selector | Specificity |
|---|---|
| `*` | 0-0-0-0 |
| `p` | 0-0-0-1 |
| `.title` | 0-0-1-0 |
| `#header` | 0-1-0-0 |
| `p.title` | 0-0-1-1 |
| `div#main p` | 0-1-0-2 |
| `[type="text"]` | 0-0-1-0 |
| `p:hover` | 0-0-1-1 |
| `p::before` | 0-0-0-2 |

## 13.2 تأثیر Combinatorها

Combinatorها به‌تنهایی Specificity ندارند.

مثال:

```css
div p {
    color: red;
}
```

Specificity:

```text
0-0-0-2
```

مثال:

```css
.card > p {
    color: blue;
}
```

Specificity:

```text
0-0-1-1
```

## 13.3 تأثیر :is()

Specificity تابع `:is()` برابر با بیشترین Specificity بین آرگومان‌های آن است.

```css
:is(p, .title, #main) {
    color: red;
}
```

Specificity:

```text
0-1-0-0
```

## 13.4 تأثیر :where()

Specificity این Pseudo-class همیشه صفر است.

```css
:where(#main, .card, p) {
    color: red;
}
```

Specificity:

```text
0-0-0-0
```

## 13.5 تأثیر :not() و :has()

خود این Pseudo-classها امتیاز جداگانه‌ای به Specificity اضافه نمی‌کنند؛ Specificity آن‌ها بر اساس بیشترین Specificity آرگومانشان محاسبه می‌شود.

مثال:

```css
div:not(.active) {
    color: red;
}
```

Specificity:

```text
0-0-1-1
```

مثال:

```css
.card:has(#title) {
    color: blue;
}
```

Specificity:

```text
0-1-1-0
```

## 13.6 قانون مهم

اگر Specificity دو سلکتور برابر باشد، در شرایط یکسان قانون CSS که دیرتر نوشته شده است اولویت می‌گیرد.

مثال:

```css
.title {
    color: red;
}

.title {
    color: blue;
}
```

رنگ نهایی آبی خواهد بود.

نکته:

Specificity تنها عامل تعیین‌کننده در Cascade نیست. مواردی مانند Origin، Importance، Cascade Layers و ترتیب قوانین نیز نقش دارند. همچنین `!important` و استایل‌های inline باید در چارچوب کامل CSS Cascade بررسی شوند.

---

# 14. مثال کاربردی جامع

در این بخش یک ساختار HTML واقعی را در نظر می‌گیریم و با استفاده از سلکتورهای مختلف روی آن استایل اعمال می‌کنیم.

## HTML

```html
<!DOCTYPE html>
<html lang="fa">
<head>
    <meta charset="UTF-8">
    <title>CSS Advanced Selectors</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header class="header">
        <h1>My Website</h1>

        <nav>
            <ul class="menu">
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
                <li class="active"><a href="/products">Products</a></li>
                <li class="disabled"><a href="/contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main class="container">

        <section class="products">

            <article class="card">
                <img src="product-1.jpg" alt="Product 1">

                <div class="card-body">
                    <h2>Product 1</h2>
                    <p>Product description 1</p>
                    <a href="https://example.com">View Product</a>
                    <button>Buy Now</button>
                </div>
            </article>

            <article class="card">
                <div class="card-body">
                    <h2>Product 2</h2>
                    <p>Product description 2</p>
                    <button disabled>Unavailable</button>
                </div>
            </article>

        </section>

        <form class="contact-form">

            <div class="form-group">
                <label>Name</label>
                <input type="text" required placeholder="Your Name">
            </div>

            <div class="form-group">
                <label>Email</label>
                <input type="email" required placeholder="Your Email">
            </div>

            <button type="submit">Submit</button>

        </form>

    </main>

</body>
</html>
```

## CSS

```css
/* Reset */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Root Variables */

:root {
    --primary-color: #3498db;
    --danger-color: #e74c3c;
    --success-color: #2ecc71;
}

/* Header */

.header {
    background-color: #222;
    color: white;
    padding: 20px;
}

/* Descendant Selector */

.header a {
    color: white;
    text-decoration: none;
}

/* Child Selector */

.menu > li {
    display: inline-block;
    padding: 10px;
}

/* Attribute Selector */

a[href^="https"] {
    color: green;
}

/* Active Menu */

.menu li.active {
    background-color: var(--primary-color);
}

/* Disabled Menu */

.menu li.disabled {
    opacity: 0.5;
}

/* First Child */

.menu li:first-child {
    border-left: 2px solid white;
}

/* Last Child */

.menu li:last-child {
    border-right: 2px solid white;
}

/* Odd Items */

.menu li:nth-child(odd) {
    background-color: #444;
}

/* Card */

.card {
    padding: 20px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
}

/* Card with Image */

.card:has(img) {
    border: 2px solid var(--success-color);
}

/* Direct Child */

.card > .card-body {
    padding: 15px;
}

/* First Heading */

.card h2:first-of-type {
    color: var(--primary-color);
}

/* Last Paragraph */

.card p:last-of-type {
    margin-bottom: 15px;
}

/* Adjacent Sibling */

.card h2 + p {
    font-size: 14px;
}

/* Disabled Button */

button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}

/* Enabled Button */

button:enabled {
    background-color: var(--primary-color);
    color: white;
    cursor: pointer;
}

/* Button Hover */

button:enabled:hover {
    background-color: #217dbb;
}

/* Form Focus */

.form-group:focus-within {
    border-left: 3px solid var(--primary-color);
    padding-left: 10px;
}

/* Required Inputs */

input[required] {
    border: 1px solid #ccc;
}

/* Invalid Inputs */

input:invalid {
    border-color: var(--danger-color);
}

/* Valid Inputs */

input:valid {
    border-color: var(--success-color);
}

/* Placeholder */

input::placeholder {
    color: #999;
}

/* Form with Invalid Input */

form:has(input:invalid) {
    background-color: #fff5f5;
}

/* Not Disabled */

button:not(:disabled) {
    transition: 0.3s;
}
```

در این مثال از موارد زیر استفاده کردیم:

- Universal Selector
- Class Selector
- Descendant Selector
- Child Selector
- Attribute Selector
- `:first-child`
- `:last-child`
- `:nth-child()`
- `:first-of-type`
- `:last-of-type`
- `:has()`
- `:focus-within`
- `:hover`
- `:enabled`
- `:disabled`
- `:valid`
- `:invalid`
- `:not()`
- `::placeholder`

---

# 15. نکات مهم و اشتباهات رایج

## 15.1 اشتباه گرفتن Descendant و Child

اشتباه:

```css
.parent > p
```

درحالی‌که هدف انتخاب تمام پاراگراف‌های داخل والد است.

در این حالت باید بنویسیم:

```css
.parent p
```

## 15.2 اشتباه گرفتن + و ~

```css
h2 + p
```

فقط پاراگراف بلافاصله بعد از `h2` را انتخاب می‌کند.

اما:

```css
h2 ~ p
```

تمام پاراگراف‌های بعد از `h2` را که هم‌والد آن هستند انتخاب می‌کند.

## 15.3 اشتباه گرفتن nth-child و nth-of-type

```css
p:nth-child(2)
```

دومین فرزند والد را بررسی می‌کند و سپس بررسی می‌کند که آیا آن عنصر `p` است یا خیر.

اما:

```css
p:nth-of-type(2)
```

دومین عنصر `p` را در بین خواهر و برادرهای هم‌نوع انتخاب می‌کند.

## 15.4 فراموش کردن تفاوت Pseudo-class و Pseudo-element

Pseudo-class:

```css
p:hover {
    color: red;
}
```

Pseudo-element:

```css
p::first-letter {
    font-size: 30px;
}
```

Pseudo-class معمولاً با یک دونقطه و Pseudo-element با دو دونقطه نوشته می‌شود.

## 15.5 استفاده بیش از حد از ID

استفاده زیاد از ID باعث افزایش Specificity و سخت‌تر شدن مدیریت استایل‌ها می‌شود.

بهتر است در طراحی سیستم‌های استایل‌دهی از کلاس‌ها استفاده کنیم.

## 15.6 استفاده نادرست از :empty

```css
div:empty {
    display: none;
}
```

اگر داخل عنصر حتی یک گره متنی شامل فاصله وجود داشته باشد، ممکن است دیگر با `:empty` مطابقت نداشته باشد.

## 15.7 فراموش کردن فرزند مستقیم

```css
.container p
```

تمام پاراگراف‌های داخل Container را انتخاب می‌کند.

```css
.container > p
```

فقط پاراگراف‌های فرزند مستقیم را انتخاب می‌کند.

## 15.8 استفاده بیش از حد از سلکتورهای پیچیده

مثال:

```css
body main .container section .card div p:first-child {
    color: red;
}
```

این نوع سلکتورها معمولاً خوانایی و نگهداری کد را دشوار می‌کنند.

بهتر است در صورت امکان از کلاس‌های مشخص و ساختار ساده‌تر استفاده کنیم.

## 15.9 استفاده از :hover برای قابلیت‌های ضروری

در طراحی رابط کاربری نباید قابلیت‌های ضروری فقط به Hover وابسته باشند؛ زیرا دستگاه‌های لمسی ممکن است Hover را به شکل سنتی پشتیبانی نکنند.

برای دسترس‌پذیری بهتر، حالت Focus را نیز در نظر بگیرید.

```css
button:hover,
button:focus-visible {
    background-color: blue;
}
```

---

# 16. جمع‌بندی

سلکتورهای پیشرفته CSS به ما کمک می‌کنند بدون نیاز به اضافه کردن کلاس‌های متعدد به HTML، عناصر موردنظر خود را با دقت انتخاب کنیم.

## خلاصه Combinators

| Selector | توضیح |
|---|---|
| `A B` | انتخاب B در هر سطحی از A |
| `A > B` | انتخاب B به‌عنوان فرزند مستقیم A |
| `A + B` | انتخاب B بلافاصله بعد از A |
| `A ~ B` | انتخاب تمام Bهای هم‌والد بعد از A |

## خلاصه Attribute Selectors

| Selector | توضیح |
|---|---|
| `[attr]` | دارای Attribute |
| `[attr="x"]` | مقدار دقیق |
| `[attr^="x"]` | شروع با مقدار مشخص |
| `[attr$="x"]` | پایان با مقدار مشخص |
| `[attr*="x"]` | شامل عبارت مشخص |
| `[attr~="x"]` | شامل کلمه مستقل |
| `[attr\|="x"]` | مقدار دقیق یا شروع با مقدار و خط تیره |

## خلاصه Child Pseudo-classes

| Pseudo-class | توضیح |
|---|---|
| `:first-child` | اولین فرزند |
| `:last-child` | آخرین فرزند |
| `:only-child` | تنها فرزند |
| `:nth-child()` | فرزند با موقعیت مشخص |
| `:nth-last-child()` | فرزند با موقعیت از انتها |
| `:first-of-type` | اولین عنصر از نوع مشخص |
| `:last-of-type` | آخرین عنصر از نوع مشخص |
| `:only-of-type` | تنها عنصر از نوع مشخص |
| `:nth-of-type()` | عنصر هم‌نوع با موقعیت مشخص |
| `:nth-last-of-type()` | عنصر هم‌نوع با موقعیت مشخص از انتها |

## خلاصه Logical Pseudo-classes

| Pseudo-class | توضیح |
|---|---|
| `:not()` | انتخاب عناصر غیرمطابق |
| `:is()` | گروه‌بندی سلکتورها |
| `:where()` | گروه‌بندی با Specificity صفر |
| `:has()` | انتخاب بر اساس وجود عناصر مرتبط |

## خلاصه State و Interaction Pseudo-classes

| Pseudo-class | توضیح |
|---|---|
| `:hover` | قرار گرفتن نشانگر روی عنصر |
| `:active` | فعال بودن عنصر |
| `:focus` | دریافت Focus |
| `:focus-visible` | Focus قابل مشاهده |
| `:focus-within` | دریافت Focus توسط خود عنصر یا فرزندان |
| `:visited` | لینک بازدیدشده |
| `:link` | لینک بازدیدنشده |
| `:checked` | انتخاب‌شده |
| `:disabled` | غیرفعال |
| `:enabled` | فعال |
| `:required` | اجباری |
| `:optional` | اختیاری |
| `:valid` | مقدار معتبر |
| `:invalid` | مقدار نامعتبر |
| `:read-only` | فقط خواندنی |
| `:read-write` | قابل ویرایش |

## بهترین روش یادگیری

برای تسلط بر این مبحث، ترتیب زیر پیشنهاد می‌شود:

1. ابتدا تفاوت چهار Combinator اصلی را کاملاً یاد بگیرید.
2. سپس Attribute Selectorها را با مثال‌های واقعی تمرین کنید.
3. تفاوت `nth-child` و `nth-of-type` را به‌خوبی درک کنید.
4. Pseudo-classهای مربوط به فرم و تعامل کاربر را یاد بگیرید.
5. در مرحله آخر با `:not()`، `:is()`، `:where()` و `:has()` سلکتورهای پیچیده بسازید.
6. در تمام مراحل به Specificity توجه کنید.

**نکته نهایی:** تسلط بر Selectorها باعث می‌شود CSS تمیزتر، قابل نگهداری‌تر و حرفه‌ای‌تری بنویسید و برای بسیاری از استایل‌دهی‌ها نیازی به اضافه کردن کلاس‌های اضافی به HTML نداشته باشید.
