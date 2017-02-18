# Modular Scale for CSS
Easily customizable modular scale css custom properties (variables) in pure CSS.

[![npm](https://img.shields.io/npm/v/modular-scale-css.svg?style=flat-square)](https://www.npmjs.com/package/modular-scale-css)
[![npm](https://img.shields.io/npm/dt/modular-scale-css.svg?style=flat-square)](https://www.npmjs.com/package/modular-scale-css) [![license](https://img.shields.io/github/license/nuclei/modular-scale.svg?style=flat-square)](https://github.com/nuclei/modular-scale/blob/master/LICENSE)

## Modular Scale
http://www.modularscale.com/

## Install
The easiest way is to grab it via `npm` or `yarn` and move/bundle the file in your build step.

```bash
npm i modular-scale-css --save
```

## Usage
The default ratio is the golden-ration `--golden` and the default bases are `1em` for the `--ms`/`--msa` values and `2.25em` for the `--msb` values.

To change which ratio to use, or update the base simply add the following in your css:

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
  font-size: var(--msa0);
  width: var(--msb10);
  margin: width: var(--msb-1);
}
```
