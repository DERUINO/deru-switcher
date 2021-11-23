# Vue Switcher

A Vue.js component for easy switchers with custom themes.

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
| theme | `String` | Name of theme |
| color | `String` | Name of color |