[![vue-avatar-sdh](https://img.shields.io/twitter/url?color=green&label=vue-avatar-sdh&logo=vue-avatar-sdh&logoColor=yellow&style=for-the-badge&url=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fvue-avatar-sdh)](https://www.npmjs.com/package/vue-avatar-sdh)
[![Github](https://img.shields.io/twitter/url?color=green&label=Github&logo=github&logoColor=white&style=for-the-badge&url=https%3A%2F%2Fgithub.com%2Fsoumyadip001)](https://github.com/soumyadip001)
[![Email](https://img.shields.io/twitter/url?color=green&label=Email&logo=gmail&logoColor=red&style=for-the-badge&url=https%3A%2F%2Fgithub.com%2Fsoumyadip001)](mailto:soumyadiphazra@gmail.com)

# vue-avatar-sdh

- [vue-avatar-sdh](#vue-avatar-sdh)
	- [Inspired from vue-avatar](#inspired-from-vue-avatar)
	- [Installation](#installation)
	- [Version](#version)
	- [Usage](#usage)
		- [ES6](#es6)
		- [Basic Usage with username](#basic-usage-with-username)
		- [Basic Usage](#basic-usage)
		- [Name with abbreviations](#name-with-abbreviations)
		- [Background Color `backgroundColor`](#background-color-backgroundcolor)
		- [Foreground Color `color`](#foreground-color-color)
		- [Lighten Color `lighten`](#lighten-color-lighten)
		- [Border Radius `rounded`](#border-radius-rounded)
		- [Sizes `size`](#sizes-size)
		- [Custom Style `customStyle`](#custom-style-customstyle)
	- [Props](#props)
	- [Configs](#configs)
		- [Supported Abbreviations](#supported-abbreviations)
		- [Supported background colors](#supported-background-colors)

## Inspired from [vue-avatar](https://github.com/eliep/vue-avatar)

An avatar component for vue.js same as [vue-avatar](https://github.com/eliep/vue-avatar) only written on Vue3 and TypeScript.
It now supports many different styles. It can also be heavily customized as per design needs.

This component display an avatar image and if none is provided fallback to the
user initials.

Rules used to compute user initials:

- divide the username on space and hyphen
- use the first letter of each parts
- letters as initials can be controlled from outside
- if the username is divided in more than three parts, can be rendered differently
- can be customized heavily
- custom style can be passed

You can find a few examples and the documentation [here](https://github.com/soumyadip001/vue-avatar-sdh)

## Installation

`npm install vue-avatar-sdh`

## Version

| Vuejs version | vue-avatar-sdh version |
| ------------- | ---------------------- |
| ^3.0.5        | ^1.0.3                 |
| ^3.0.5        | ^1.0.1 		         |
| ^3.0.5        | ^1.0.0 		         |

## Usage

vue-avatar-sdh is a UMD module, which can be used as a module in both CommonJS and AMD modular environments.
When in non-modular environment, Avatar will be registered as a global variable.</p>

### ES6

```js

import Avatar from 'vue-avatar-sdh'

export default {
  ...
  components: {
    Avatar
  },
  ...
}
```

After that, you can use it in your templates:

```html
<avatar username="Soumyadip Hazra"></avatar>
```

### Basic Usage with username

By default it creates 2 letter initials. But you can customize it as per your need. `maxAllowedLength` allows you to pass any number. It also automatically checks for number of words available and it omit middle names if needed.

```html
<div class="row">
	<div class="items">
		<Avatar username="Rickdev" :inline="true" />
	</div>
	<div class="items">
		<Avatar username="Rickdev Hazra" :inline="true" />
	</div>
	<div class="items">
		<Avatar
			username="Rickdev Kumar Hazra"
			:inline="true"
			:maxAllowedLength="3"
		/>
	</div>
</div>
```

Also the initials are automatically removed from initials. It automatically detects the abbreviations and remove them from initials.

```html
<div class="items">
	<Avatar username="Dr. Soumyadip Hazra" :inline="true" />
</div>
```

### Basic Usage

How to pass name to generate initials? It very simple actually. Just pass the `username` attribute to the `<Avatar />` component and it's done. You can also control how many initials will the shown in the avatar.

```html
<Avatar username="Rickdev" :inline="true" />
<Avatar username="Rickdev Hazra" :inline="true" />
<Avatar username="Dr. Soumyadip Hazra" :inline="true" />
<Avatar username="Rickdev Kumar Hazra" :inline="true" :maxAllowedLength="3" />
```

![Basic Usage](https://raw.githubusercontent.com/soumyadip001/vue-avatar-sdh/master/screenshots/screen1.png)

---

### Name with abbreviations

What if the username can contain abbreviations? No worries we have got you covered. It'll automatically be parsed out and the name will be taken to generate the Avatar. Also notice the different between the two `Dr` and `Dr.`

```html
<Avatar username="Dr Soumyadip Hazra" :inline="true" />
<Avatar username="Dr. Soumyadip Hazra" :inline="true" />
```

![Name with abbreviations](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen2.png?raw=true)

---

### Background Color `backgroundColor`

```html
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#F44336" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#FF4081" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#9C27B0" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#673AB7" />
```

![Background Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen3.png?raw=true)

---

### Foreground Color `color`

```html
<Avatar
	username="Soumyadip Hazra"
	:inline="true"
	color="#F44336"
	backgroundColor="#eadede"
/>
<Avatar
	username="Soumyadip Hazra"
	:inline="true"
	color="#FF4081"
	backgroundColor="#eadede"
/>
<Avatar
	username="Soumyadip Hazra"
	:inline="true"
	color="#9C27B0"
	backgroundColor="#eadede"
/>
<Avatar
	username="Soumyadip Hazra"
	:inline="true"
	color="#673AB7"
	backgroundColor="#eadede"
/>
```

![Foreground Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen4.png?raw=true)

---

### Lighten Color `lighten`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="20" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="40" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="60" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="80" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="100" />
```

![Lighten Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen5.png?raw=true)

---

### Border Radius `rounded`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :rounded="true" />
<Avatar username="Soumyadip Hazra" :inline="true" :rounded="false" />
```

![Border Radius](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen6.png?raw=true)

---

### Sizes `size`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :size="40" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="60" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="70" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="80" />
```

![Sizes](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen7.png?raw=true)

---

### Custom Style `customStyle`

```html
<div class="items">
	<Avatar username="Soumyadip Hazra" :customStyle="customstyle1" />
</div>
```

```css
.customstyle1: {
	borderRadius: '10px',
	color: '#fff',
	backgroundColor: '#ff4081',
	border: '3px solid #d6054c',
}
```

![Custom Style](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen8.png?raw=true)

---

## Props

Looking for all the supported props and there use cases? We have got you covered here.

| Prop Name | Type | Description |
| --------- | ---- | ----------- |
| `backgroundColor` | String | Any valid hex string will work. ex: `backgroundColor="#F44336"` |
| `color` | String | Any valid hex string will work. ex: `color="#F44336"` |
| `customStyle` | Object | Any valid object with style definations ex: [`customStyle`](#custom-style-customstyle) |
| `maxAllowedLength` | Number | Number of characters in the avatar. default: 2. ex: [Basic Usage](#basic-usage) |
| `initials` | String | Initials with name which should be ignore while generating the avatar. |
| `inline` | Boolean | Show inline avatar |
| `lighten` | Number | Lighen the color automatically as per background color. default: 80 |
| `rounded` | Boolean | Rounded border(`borderRadius` of `50%`) or square(false). default: `true` |
| `size` | Number | `width` and `height` of the avatar in `pixels`. default: 50 |
| `src` | String | User provided thumbnail if any |
| `theme` | String | User provided theme. For now we only support `ROBO` |
| `username` | Boolean | (`required`) The name of the user |

-------------------
## Configs

### Supported Abbreviations

```javascript
'Dr', 'Esq', 'Hon', 'Er', 'Jr', 'Mr', 'Mrs', 'Ms', 'Messrs',
'Mmes', 'Msgr', 'Prof', 'Rev', 'Rt', 'Sr', 'St',
```

### Supported background colors

If you do not want to pass any `backgroundColor` or `color` as props then a random background color will be applied from the below list of colors. They also supports `lighten` props. It'll get adjusted automatically.

![#F44336](https://img.shields.io/badge/RED-%23F44336-%23F44336)
![#FF4081](https://img.shields.io/badge/French%20Rose-%23FF4081-%23FF4081)
![#9C27B0](https://img.shields.io/badge/Barney-%239C27B0-%239C27B0)
![#673AB7](https://img.shields.io/badge/Purple%20Heart-%23673AB7-%23673AB7)

![#3F51B5](https://img.shields.io/badge/Sapphire%20Blue-%233F51B5-%233F51B5)
![#2196F3](https://img.shields.io/badge/Azure-%232196F3-%232196F3)
![#03A9F4](https://img.shields.io/badge/Butterfly%20Blue-%2303A9F4-%2303A9F4)
![#00BCD4](https://img.shields.io/badge/Ball%20Blue-%2300BCD4-%2300BCD4)
![#009688](https://img.shields.io/badge/Teal-%23009688-%23009688)

![#4CAF50](https://img.shields.io/badge/Dark%20Pastel%20Green-%234CAF50-%234CAF50)
![#8BC34A](https://img.shields.io/badge/Green%20Peas-%238BC34A-%238BC34A)
![#CDDC39](https://img.shields.io/badge/Wattle-%23CDDC39-%23CDDC39)
![#FFC107](https://img.shields.io/badge/Golden-%23FFC107-%23FFC107)

![#FF9800](https://img.shields.io/badge/Dark%20Orange-%23FF9800-%23FF9800)
![#FF5722](https://img.shields.io/badge/Portland%20Orange-%23FF5722-%23FF5722)
![#795548](https://img.shields.io/badge/Roman%20Coffee-%23795548-%23795548)
![#9E9E9E](https://img.shields.io/badge/Star%20Dust-%239E9E9E-%239E9E9E)
![#607D8B](https://img.shields.io/badge/Light%20Slate%20Grey-%23607D8B-%23607D8B)

color names collected from: [artyclick.com](https://colors.artyclick.com/color-name-finder/)
