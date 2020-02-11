# CssToInlineStyles class
> CssToInlineStyles is a class that enables you to convert HTML-pages/files into
> HTML-pages/files with inline styles. This is very usefull when you're sending
> emails.

## About

PHP CssToInlineStyles is a class to convert HTML into HTML with inline styles.

## Installation

The recommended installation way is through [Composer](https://getcomposer.org).

```bash
$ composer require Mmaaikel/css-to-inline-styles
```

## Example

    use mmaaikel\CssToInlineStyles\CssToInlineStyles;

    // Convert HTML + CSS to HTML with inlined CSS
    $cssToInlineStyles= new CssToInlineStyles();
    $cssToInlineStyles->setHTML($html);
    $cssToInlineStyles->setCSS($css);
    $html = $cssToInlineStyles->convert();

    // Or use inline-styles blocks from the HTML as CSS
    $cssToInlineStyles = new CssToInlineStyles($html);
    $cssToInlineStyles->setUseInlineStylesBlock(true);
    $html = $cssToInlineStyles->convert();

    // Or use linked files from the HTML as CSS
    $cssToInlineStyles = new CssToInlineStyles($html);
    $cssToInlineStyles->setLoadCSSFromHTML(true);
    $html = $cssToInlineStyles->convert(false, 0, __DIR__ . '/../tests/');


## Documentation

The following properties exists and have set methods available:

Property | Default | Description
-------|---------|------------
cleanup|false|Should the generated HTML be cleaned?
useInlineStylesBlock |false|Use inline-styles block as CSS.
stripOriginalStyleTags |false|Strip original style tags.
excludeMediaQueries |true|Exclude media queries from extra "css" and keep media queries for inline-styles blocks.
excludeConditionalInlineStylesBlock |true|Exclude conditional inline-style blocks.

## Warning

Also if the default is ```cleanup === false```, you maybe need to use this feature, because Outlook has some special features where the inline-CSS will be ignored and it will fallback to use only the CSS-Class- or ID-properties.

```php
$cssToInlineStyles->setCleanup(true);
```

## Known issues

* no support for pseudo selectors

