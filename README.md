# Modular Scale for CSS
Easily customizable modular scale css custom properties (variables) in pure CSS.

[![npm](https://img.shields.io/npm/v/modular-scale-css.svg?style=flat-square)](https://www.npmjs.com/package/modular-scale-css)
[![npm](https://img.shields.io/npm/dt/modular-scale-css.svg?style=flat-square)](https://www.npmjs.com/package/modular-scale-css) [![license](https://img.shields.io/github/license/nuclei/modular-scale.svg?style=flat-square)](https://github.com/nuclei/modular-scale/blob/master/LICENSE)

## Installation
The easiest way is to grab it via `npm` or `yarn` and move/bundle the file in your build step.

```bash
npm i modular-scale-css --save
```

You need to either link the css file in your html or bundle it with your other css files.

## Usage
You can either use a simple modular scale by using the `--ms` properties or a double-stranded modular scale (= two modular scales with the same ratio but different base values) by using the `--ms_a` and `--ms_b` properties.

The default ratio is the golden-ration `--golden` and the default bases are `1em` for the `--ms-base`/`--ms-base-a` values and `2.25em` for the `--ms-base-b` values.

To change which ratio to use, or update the bases simply add the following in your css:

```css
--ms-ratio: var(--major-third);
--ms-base: 10px;
```

If you are using a double-stranded modular scale simple add an `a` and a `b` base.

```css
--ms-ratio: var(--major-third);
--ms-base-a: 10px;
--ms-base-b: 20px;
```

Now you can use your scale anywhere in your css:

```css
/* single scale */
p{
  font-size: var(--ms0);
  width: var(--ms10);
}
/* double stranded scale */
div{
  font-size: var(--ms_a0); /*use _ to separate the a and b scale*/
  width: var(--msb_10);
  margin: width: var(--ms_b-1); /*minus means a step down*/
}
```

### Moving up and down on the modular scale
The normal properties like `--ms3`, `--ms_a5` or `--ms_b2` are multiples of the ratio times the base value to the power of whatever number you used. By using the negative versions like `--ms-1`, `--ms_a-4` or `--ms_b-9` you move down the scale. Those are dividends of the base value by the ratio divided by itself multiple times.

### Custom ratios
If you want to use a custom ratio, you can simply add it as the `--ms-ratio` value.

```css
--ms-ratio: calc(3/5);
```

## Modular Scale
A modular scale is a measurement system that provides a set of numbers which you can use for your font-sizes, element sizes or negative space. Since it is based on an underlying ration, all numbers in your system are multiples of this ratio and your base, which makes them naturally fit together thus creating a more harmonies layout.

### What base should I choose?
A good start is your body text size. You could also use other font metrics like x-height or an important fixed-width like a sidebar or a major element.

### Which ratio is good?
This package includes many ratios from the visual arts, mathematics and music. If you have no reason to favor any of the provided, you can just try some ratios and see which values work best for your design.

To learn more about modular scales, visit [modularscale.com](http://www.modularscale.com).

### Included ratios
Below you find a list of the included ratios. The first column is the CSS custom property used to specify the ratio in your css. See [usage](#usage).

CSS custom property (variable) | Ratio | Value
--- | --- | ---
--minor-second | 15:16 | 1.067
--major-second | 8:9 | 1.125
--minor-third | 5:6 | 1.2
--major-third | 4:5 | 1.25
--fourth | 3:4 | 1.333
--augmented-fourth | 1:√2 | 1.414
--fifth | 2:3 | 1.5
--minor-sixth | 5:8 | 1.6
--phi | 1:1.618 | 1.618
--golden | 1:1.618 | 1.618
--major-sixth | 3:5 | 1.667
--minor-seventh | 9:16 | 1.778
--major-seventh | 8:15 | 1.875
--octave | 1:2 | 2
--major-tenth | 2:5 | 2.5
--major-eleventh | 3:8 | 2.667
--major-twelfth | 1:3 | 3
--double-octave | 1:4 | 4

### Why is there a SASS file, you said pure css right?
Correct, and the file you are using is pure a css file: `modular-scale.css`. However we can not use `calc` operations within `calc` operations, as this is not supported by the spec (even though chrome does still support it). Because of this we have to create the long variables with multiplying/dividing many times. SASS only allows me to create those calculations without writing them out. When you download the package you only need to care for the `.css` file and do NOT need SASS.
