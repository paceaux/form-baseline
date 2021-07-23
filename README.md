#  form-baseline.css
> A good start to your form styles that covers most of the challenges

[![License][license-image]][license-url] [![Downloads][downloads-image]][downloads-url]

**NPM**
```
npm install --save form-baseline.css
```

**Download**
`https://raw.githubusercontent.com/paceaux/form-baseline/master/src/baseline.form.css`

## What does it do?
### It gives you a good start
Built on the typography-baseline foundations, it gives you a good, _small_ set of styles for forms to work with

### Gives you a "no-design" design
For those times where you need just a bit more than a [Normalize](http://necolas.github.io/normalize.css/), but way less than [Bootstrap](https://getbootstrap.com/), this gets your forms there. 

This is a fairly unopinionated approach to making sure that form controls don't look awful.

## Browser Support
* Firefox
* Chrome
* Edge
* Safari
* Opera


## Usage
While this is relatively unopinionated, there are a few "opinions" to consider:

* `em` for for `font-size`
* a unitless `line-height`
* `rem` for left/right spacing
* text-spacing based on the golden ratio (.618 / 1.618)

### Fitting it into a CSS architecture
This would come after a reset / normalize and and after your set baseline styles. If you're a fan of [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/), this is in the Elements layer.

### Modifying without Swearing or Heavy Drinking
One of the really annoying things about other CSS frameworks (cough cough <small>Bootstrap</small>) is that you mostly have to write new CSS to overwrite the existing styles. Often that means raising specificity, which is really stinking annoying. This is designed to avoid that by using [CSS Variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


The form baseline sets most of the CSS variables on the `form`. As CSS variables are subject to the cascade, you can override _any_ variable at any time by changing its value on the relevant selector. You can import this into your current CSS setup, and overwrite all the variables by setting new ones whereever makes sense.


All of the variables are prefixed with `form` so that they can't collide with any other css variables you may have. 

They also inherit values from the typography-baseline. But if you choose not to use it, that's totally fine! They all have default values. 


So if you want the `--controlBorderColor` to be different, you can write the following in your own stylesheet:

```
form.myClass {
    --controlBorderColor: #c0ffee;
}
```

No raising specificity. Just changing a variable. 


#### Colors
You have collections of color variables to work with:
```
    --controlColor:  var(--colorNeutralDark, rgb(165,165,165));
    --controlGroupColor: var(--colorNeutralDark, rgb(110,110,110));
    --controlBackgroundColor: rgb(255, 255, 255);
    --controlGroupBackgroundColor: transparent;
    --controlBorderColor: var(--controlColor);

```

**But what about `:hover`, and `:focus`, and `:active`, and...**

The Baseline breaks colors into four categories: 

1. Default
2. Interest (a combined `:hover` and `:focus`)
3. Active
4. Inform (attention or alert)

Additionally, it applies colors across two domains:

* "control": an `input`, `textarea`, `button` or `select`. 
* controlGroup: a collection of controls (a `fieldset`, usually)

##### Default Colors

```
    --controlColor:  var(--colorNeutralDark, rgb(165,165,165));
    --controlGroupColor: var(--colorNeutralDark, rgb(110,110,110));
    --controlBackgroundColor: rgb(255, 255, 255);
    --controlGroupBackgroundColor: transparent;
    --controlBorderColor: var(--controlColor);
```

##### Interest Colors
"interest" collectively refers to `:hover` and `:focus`. It means the user is _interested_ in the control, but not yet engaged with it. 
```
    --controlColorInterest: var(--colorNeutralDarker);
    --controlBackgroundColorInterest: var(--controlBackgroundColor);
    --controlBorderColorInterest: var(--controlColorInterest);
```

##### Active Colors
Active refers to engagement with the control. They are typing; clicking in the control. 

```
    --controlColorActive: var(--colorNeutralDarker);
    --controlBackgroundColorActive: var(--controlBackgroundColor);
    --controlBorderColorActive: var(--controlBorderColorActive);
    
```

##### Deactivated
This refers to `:disabled` either on a control or a fieldset

```
    --controlColorDeactivated: var(--controlColor);
    --controlBackgroundColorDeactivated: var(--colorNeutralLighter);
    --controlBorderColorDeactivated: var(--controlBackgroundColorDeactivated);

```

##### Informational
These are colors for the result of an action. Unlike the other colors, they aren't intended for a specific property. 

```
    --controlColorAlert: var(--colorWarmest, rgb(168, 62, 0));
    --controlColorAttention: var(--colorWarmer, rgb(168, 118, 0));
```


#### Line Heights
You have two line-heights to choose from:

```
    --formBaseLineHeight: var(--smallLineHeight, 1.2);
    --formSmallLineHeight: 1;
```


#### Text Sizes
You have a minimum of 6 text sizes in two categories: `--form<n>TextSize` and `--form<n>TitleSize`. You have a "base" and then superlatives or diminutives to describe the deviation from that base. e.g.:

You may notice that there is no "big" or "bigger" like with the typography or table baselines. This is because forms should use fewer font-sizes. But you are free to change these and add your own if you need to. 
```
	--formBiggestTextSize: var(--biggerTextSize, 1.2em);
	--formBaseTextSize: var(--baseTextSize, 1em);
	--formSmallestTextSize: var(--smallTextSize, .8em);
```

You may notice that title sizes overlap with base text sizes. This is intentional! You have the flexibility to have your smaller headings be the same as larger text, or to create new title sizes for your headings that won't overlap with the text. 


```
    --formBiggestTitleSize: var(--baseTitleSize, 1.5em);
    --formBaseTitleSize: var(--formBiggestTextSize);
    --formSmallestTitleSize: var(--formBaseTextSize);
```

You also have helpful abstractions to use:

```
	--formControlSize: var(--formBaseTextSize);
    --formLabelSize: var(--formBaseTextSize);
    --formTitleSize: var(--formBaseTitleSize);
```

#### Font families
You have two font families to choose from.

```
    --formBaseFontFamily: var(--baseFontFamily,  'Georgia','Times New Roman', 'serif');
    --formTitleFontFamily: var(--titleFontFamily, 'Helvetica', 'Arial', 'sans-serif');
```

## Conventions and Standards

### Style guide
The CSS follows the guidelines established [here](https://gist.github.com/paceaux/f31e278613ab29b74a412a7eb5046422).

### Naming Conventions
CSS Variable names follow a convention established [here](https://gist.github.com/paceaux/8638765e747f5bd6387b721cde99e066#sassscssstylus-naming).


[license-image]: http://img.shields.io/npm/l/form-baseline.css.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/form-baseline.css.svg
[downloads-url]: http://npm-stat.com/charts.html?package=form-baseline.css

