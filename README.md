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
