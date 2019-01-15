# Localization

**Nuxt** uses **nuxt-i18n** which itself uses [vue-i18n](https://kazupon.github.io/vue-i18n/guide).

## Best practices

### Always Use UTF-8

It is the best choice 99% of the time as it fixes this issue by standardizing the encodings across browser and server. So ideally every layer in our stack should use UTF-8.

```html
<meta http-equiv="content-type" content="text/html; charset=utf-8">
```

```http
Content-Type: text/html; charset=utf-8
```

```sql
CREATE DATABASE dbname CHARACTER SET utf8 COLLATE utf8_general_ci;
```

## Locales

Folders are named after a locale registered as a string with a [BCP 47 language tag](https://www.w3.org/International/articles/language-tags/).

Default AND fallback localization is set in `/i18n/index.js`.

Locales are located in `/i18n/language-region`

## Messages

* [Formating](https://kazupon.github.io/vue-i18n/guide)
* [Pluralization](https://kazupon.github.io/vue-i18n/guide/pluralization.html)
* [Syntax](https://kazupon.github.io/vue-i18n/guide/messages.html)
* [Component based](https://kazupon.github.io/vue-i18n/guide/component.html)
* [Interpolation](https://kazupon.github.io/vue-i18n/guide/interpolation.html)

## Use messages

In a `vue` template:

```js
{{ $t('home.title') }}
// Home
```

## Date Time format

[vue-i18n documentation](https://kazupon.github.io/vue-i18n/guide/datetime.html) about date and time format.

You can define the datetime format with named (e.g. short, long, etc), and you need to use [the options with ECMA-402 Intl.DateTimeFormat](http://www.ecma-international.org/ecma-402/2.0/#sec-intl-datetimeformat-constructor)

[The 5 laws about API dates and times](http://apiux.com/2013/03/20/5-laws-api-dates-and-times/)

### Use date time formats

In a `vue` template:

```js
{{ $d(new Date(), 'short') }}
// Apr 19, 2017
```

## Number format

[vue-i18n documentation](https://kazupon.github.io/vue-i18n/guide/number.html) about number format.

You can define the number format with named (e.g. currency, etc), and you need to use [the options with ECMA-402 Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NumberFormat).

Currencies follow the [ISO 4217 currency code](https://www.iso.org/iso-4217-currency-codes.html).

Style

### Use number formats

In a `vue` template:

```js
{{ $n(100, 'currency') }}
// $100.00
```

## Images

Sometimes images that contain text can pose a serious pain for translators and can slow down and otherwise hinder the translation process.

Try to never use text in graphics. Ask for help on CSS if needed.

## Directions

Arabic, Hebrew and some other languages go from right to left and East-Asian languages using Chinese – or traditional Mongolian if you’re feeling adventurous – characters have a long history of vertical writing.

There is a `direction` property in CSS.

```css
p { direction: rtl; }
p { direction: ltr; }
```

## Translation key namespaces

In order to avoid translation collisions, each translation key should be namespaced according to the following rules:

### Translations in components

All translation keys in a component should be namespaced to the component path.

```json
{
    "component": {
        "forms/group": {
            "title": {
                "add": "Add a group",
                "edit": "Edit a group"
            }
        }
    }
}
```

### Translations in pages

All translation keys in a page should be namespaced to the page path.

```json
{
    "page": {
        "groups": {
            "title": "Groups"
        },
        "group/_id": {
            "title": "Group: {groupname}"
        }
    }
}
```

### Global translations

Any translation that should be kept throughout the site should be namespaced to `app`.

```json
{
    "app": {
        "name": "Weinto Ltd",
        "authors" : {
            "txt" : "authors",
            "url" : "https://weinto.com/en-AU/team"
        }
    }
}
```

## Automate

It is often hard to afford to send translation requests through e-mails or cut and paste strings from a spreadsheet to a source file. All translation hand-offs should be automated and managed through a centralized system.

[OneSky app](https://www.oneskyapp.com/) is a service that works with Github and remunerate translators per word.
