[![spectrum logo](./readme_assets/spectrum.svg)](https://github.com/Linkerin/spectrum#readme)

[![npm](https://img.shields.io/npm/dw/%40snipshot/spectrum?style=for-the-badge&logo=npm&label=NPM)](https://www.npmjs.com/package/@snipshot/spectrum)
[![TS Support](https://img.shields.io/badge/TS-supported-%233178C6?style=for-the-badge&logo=typescript)](#)
[![MIT License](https://img.shields.io/badge/License-MIT-%230B936A?style=for-the-badge)](https://github.com/Linkerin/spectrum/blob/main/LICENSE)

# Spectrum - сonverting colors with ease 🎨

Spectrum is a lightweight JavaScript / TypeScript library designed to simplify color manipulation and conversion tasks within the `RGB`, `HSL`, and `HEX` color spaces.

It may be not the most extensive library out there, but it's precisely what you need if you want to mix two colors, darken the color or adjust saturation of the color value you were provided in `hex`. We see it as a finely-tuned instrument focused on simplifying the most common color tasks.

## Installation

```bash
npm i @snipshot/spectrum
```

## Example

```javascript
import { Spectrum, adjustHsl } from '@snipshot/spectrum';

const spectrum = new Spectrum('hsl', [231, 0.66, 0.53, 0.8]);

const adjustedColor = adjustHsl(spectrum, { hue: -23, lightness: '-13%' });

console.log(adjustedColor.hsl); // { h: 208, s: 0.66, l: 0.4, a: 0.8 }
console.log(adjustedColor.hex); // #236aa9cc
```

## Main usage

Getting started with Spectrum is a breeze. Import the `Spectrum` class into your project and create an instance:

```javascript
import { Spectrum } from '@snipshot/spectrum';

const spectrum = new Spectrum('rgb', '255 255 0'); // yellow
```

That's it! `Spectrum` instance provides several methods to reveal information about your color. For color manipulations you can import the function you need. Let's see all of these in action.

### Color values

`Spectrum` instance has the properties `hex`, `hsl` and `rgb` to reveal the corresponting color values:

```javascript
spectrum.hex; // #ffff00
spectrum.hsl; // { h: 60, s: 1, l: 0.5, a: 1 }
spectrum.rgb; // {r: 255, g: 255, b: 0, a: 1}
```

> By default, alpha channel value is `1` if it was not provided during initialization

You may also find useful other properties which return each value separately:

```javascript
spectrum.alpha; // 1
spectrum.red; // 255
spectrum.green; // 255
spectrum.blue; // 0
spectrum.hue; // 60
spectrum.saturation; // 1
spectrum.lightness; // 0.5
```

### Mixing colors

```javascript
import { Spectrum, colorMix } from '@snipshot/spectrum';

const red = new Spectrum('hex', '#f00');
const blue = new Spectrum('rgb', '0, 0, 255, 1');

const purple = colorMix(red, blue, 0.5); // 0.5 is a weight of the first color (max value is 1)

console.log(purple.hex); // #800080
```

### Change value

Suppose that you need to set lightness equal to 50%. Here is how you can do it:

```javascript
import { Spectrum, setHsl } from '@snipshot/spectrum';

const darkgreen = new Spectrum('hex', '#006400');
const green = setHsl(darkgreen, { lightness: 0.5 });

console.log(green.hsl); // {h: 120, s: 0.98, l: 0.5, a: 1}
```

### Negative color

You can get a reversed or negative color from your color using the `invert()` function:

```javascript
import { Spectrum, invert } from '@snipshot/spectrum';

const yellow = new Spectrum('rgb', [255, 255, 0]);
const negativeColor = invert(yellow, 1); // 1 is a weight of the inverted color

console.log(negativeColor.rgb); // { r: 0, g: 0, b: 255, a: 1 } - blue
```

### Create a color palette

To generate a color palette from a given color of varios lightness it will be handy to use a `createPalette()` function. It returns an object with keys from 0 to 100 with step 1 and `Spectrum` instances as values with lightness set from 0 to 100.

```javascript
import { Spectrum, invert } from '@snipshot/spectrum';

const cyan = new Spectrum('hex', '#0ff');
const palette = createPalette(cyan);

console.log(palette[0].hsl); // { h: 180, s: 1, l: 0, a: 1 } - black
console.log(palette[44].hsl); // { h: 180, s: 1, l: 0.44, a: 1 }
console.log(palette[100].hsl); // { h: 180, s: 1, l: 1, a: 1 } - white
```

## API Documentation

Detailed API description and use cases will be available soon on [spectrum.snipshot.dev](https://spectrum.snipshot.dev). Stay tuned!

## Contributions

Contributions are always welcome! If you have ideas for improvements or new features, please [open an issue](https://github.com/Linkerin/spectrum/issues) or submit a [pull request](https://github.com/Linkerin/spectrum/pulls) on GitHub.

## Contacts

If you have any questions or need assistance, feel free to contact me at [gusev@snipshot.dev](mailto:gusev@snipshot.dev.).

## License

Spectrum is licensed under the MIT License. See the [LICENSE](https://github.com/Linkerin/spectrum/blob/main/LICENSE) file for details.

Happy coding! 😉
