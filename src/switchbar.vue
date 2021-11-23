<template>
  <label for="switch" :class="preparedStyles">
      <div class="switch-bar__button"></div>
      <input type="checkbox" id="switch" @change="trigger" :checked="value">
  </label>
</template>

<script>
export default {
    name: 'deruSwitcher',
    props: {
        value: {
            default: false,
        },
        color: {
            default: 'default',
        },
        theme: {
            default: 'default',
        },
    },
    computed: {
       preparedStyles() {
           const {color, theme} = this;

           return {
               'switch-bar': true,
               ['switch-bar--checked']: this.value,
               [`switch-bar-theme--${theme}`] : color,
               [`switch-bar-color--${color}`] : color,
           }
       }, 
    },
    mounted() {
        this.$emit('input', this.value);
    },
    methods: {
        trigger(e) {
            this.$emit('input', e.target.checked);
        }
    }
}
</script>

<style lang="scss" scoped>
    $bgColor: rgb(157, 255, 0);

    .switch-bar {
        width: 44px;
        height: 25px;
        border-radius: 15px;
        background: #e3e3e3;
        cursor: pointer;
        position: relative;

        input {
            display: none;
        }

        &__button {
            top: 1px;
            left: 2px;
            background: gray;
            position: absolute;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            transition: 0.3s all;
        }

        &--checked {
            background: $bgColor;

            .switch-bar__button {
                background: white;
                left: inherit;
                transform: translateX(94%);
                box-shadow: 0 0 5px $bgColor, 0 0 15px $bgColor;
                
                &:hover {
                    background: white;
                }
            }
        }

        &-theme--default {
        }
        
        &-theme--dark {
            background: gray;

            .switch-bar__button {
                background: #e3e3e3;
            }
        }
    }
</style>