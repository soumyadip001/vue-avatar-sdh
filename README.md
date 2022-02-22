# vue-avatar-sdh

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

You can find a few examples and the documentation [here](https://eliep.github.io/vue-avatar)

## Installation

`npm install vue-avatar-sdh`

## Version

| Vuejs version | vue-avatar-sdh version |
| ------------- | ---------------------- |
| ^3.0.5        | ^1.0.0                 |

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

![Basic Usage](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen1.png)

-----

### Name with abbreviations

What if the username can contain abbreviations? No worries we have got you covered. It'll automatically be parsed out and the name will be taken to generate the Avatar. Also notice the different between the two `Dr` and `Dr.`

```html
<Avatar username="Dr Soumyadip Hazra" :inline="true" />
<Avatar username="Dr. Soumyadip Hazra" :inline="true" />
```

![Name with abbreviations](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen2.png)

-----

### Background Color `backgroundColor`

```html
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#F44336" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#FF4081" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#9C27B0" />
<Avatar username="Soumyadip Hazra" :inline="true" backgroundColor="#673AB7" />
```

![Background Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen3.png)

-----

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

![Foreground Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen4.png)

-----

### Lighten Color `lighten`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="20" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="40" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="60" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="80" />
<Avatar username="Soumyadip Hazra" :inline="true" :lighten="100" />
```

![Lighten Color](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen5.png)

-----

### Border Radius `rounded`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :rounded="true" />
<Avatar username="Soumyadip Hazra" :inline="true" :rounded="false" />
```

![Border Radius](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen6.png)

-----

### Sizes `size`

```html
<Avatar username="Soumyadip Hazra" :inline="true" :size="40" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="60" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="70" />
<Avatar username="Soumyadip Hazra" :inline="true" :size="80" />
```

![Sizes](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen7.png)

-----

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

![Custom Style](https://github.com/soumyadip001/vue-avatar-sdh/blob/master/screenshots/screen8.png)

-----
