# vue-avatar-sdh
## Inspired from [vue-avatar](https://github.com/eliep/vue-avatar)

An avatar component for vue.js.

This component display an avatar image and if none is provided fallback to the
user initials.  This component is highly inspired from
[react-user-avatar](https://github.com/wbinnssmith/react-user-avatar).

Rules used to compute user initials:
- divide the username on space and hyphen
- use the first letter of each parts
- never use more than three letters as initials
- if the username is divided in more than three parts and has part
  starting with an uppercase, skip parts starting with a lowercase.

You can find a few examples and the documentation [here](https://eliep.github.io/vue-avatar)

## Installation
# Inspired from [https://github.com/eliep/vue-avatar](vue-avatar)

`npm install vue-avatar`

## Version

| Vuejs version | vue-avatar version |
| ------------- | -----------------  |
| ^1.0.18       | ^1.3.0             |
| ^2.0.0        | ^2.0.0             |


## Usage
vue-avatar is a UMD module, which can be used as a module in both CommonJS and AMD modular environments.
When in non-modular environment, Avatar will be registered as a global variable.</p>

### ES6
```js

import Avatar from 'vue-avatar'

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
<avatar username="Jane Doe"></avatar>
```
