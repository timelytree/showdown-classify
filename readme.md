### classify

Although markdown is a fantastic markup language out-of-the-box, there are times when one needs to be able to target specific sections of markdown output via css classes, primarily for more fine-tuned styling. classify is an extension created for [ShowdownJS](https://github.com/showdownjs) - a fantastic open-source, javascript-based markdown parser - that gives you the ability to wrap markdown text in a `<div>` with a class while still being able to process markdown inside the `<div>`.

### How to use

Begin by including classify inside your website's `<head>` tag, after showdown.js

```html
<script type="text/javascript" src="js/showdown.js"></script>
<script type="text/javascript" src="js/showdown-classify.js"></script>
```

### Enabling the extension

Once the extension is included, you can enable it when a new showdown Converter is initialized:

```javascript
var converter = new showdown.Converter({
  extensions: ['classify'],
  // optionA: true,
  // optionB: false
});
```

### Example use case

This extension introduces a new piece of syntax to markdown itself. Using this will allow you to wrap markdown input inside a `<div>` with an identifying class of your choosing. The markdown inside the new tags _will be rendered as well_.

The syntax looks like this:

```
[tasty--]
## Header
1. Toast some bread
2. Scrape fresh garlic onto bread
3. Dip into olive oil
[--tasty]
```

Example input:

```javascript
var converter = new showdown.Converter({extensions: ['classify']}),
    markdownInput = `

      [tasty--]
      ## Garlic Toast
      1. Toast some bread
      2. Scrape fresh garlic onto bread
      3. Dip into olive oil
      [--tasty]

    `,
    html = converter.makeHtml(markdownInput);
```

This should output:

```html
<div class="tasty">
  <h2>Garlic Toast</h2>
  <ol>
    <li>Toast some bread</li>
    <li>Scrape fresh garlic onto bread</li>
    <li>Dip into olive oil</li>
  </ol>
</div>
```

## License
You are free to use, re-use, modify, integrate, incorporate, get angry at, ponder, or jump for joy at the thought of this code in any way you see fit :)
