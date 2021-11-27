# Vue Switcher

A Vue.js component for easy switchers with custom themes.

![deru-switcher](https://a.radikal.ru/a24/2111/34/00efc8d91ca1.jpg)

[DEMO](https://deruwork.ru)
## Installation

```
npm i deru-switcher --save
```

## How Usage?

#### local component usage
```javascript
import DeruSwitcher from 'deru-switcher';  
  
new Vue({
 
    components: {
        Switches
    },
 
    data () {
        return {
            enabled: false
        }
    }
};
```

```javascript
<deru-switcher v-model="enabled"></deru-switcher>
```

#### global component usage (for example: in main.js)
```javascript
import DeruSwitcher from 'deru-switcher';

Vue.component('deru-switcher', DeruSwitcher);
```

```javascript
<deru-switcher v-model="enabled"></deru-switcher>
```

## Props

| Prop | type | Description |
| ---- | ------------| ---- |
| disabled | `Boolean` | Disabling switcher |
| theme | `String` | Name of theme (default, dark) |
| color | `String` | Name of color (default, blue, green, red, orange, yellow) |