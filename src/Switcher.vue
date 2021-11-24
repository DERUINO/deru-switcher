<template>
  <label :class="preparedStyles">
      <div class="switcher__button"></div>
      <input type="checkbox" @change="trigger" :checked="value" :disabled="disabled">
  </label>
</template>

<script>
export default {
    name: 'DeruSwitcher',
    props: {
        value: {
            type: Boolean,
            default: false,
        },
        color: {
            type: String,
            default: 'default',
        },
        theme: {
            type: String,
            default: 'default',
        },
        disabled: {
            type: Boolean,
            default: false,
        },
    },
    computed: {
       preparedStyles() {
           const { color, theme, value, disabled } = this;

           return {
               'switcher': true,
               ['switcher--checked']: value,
               ['switcher--disabled']: disabled,
               [`switcher-theme--${theme}`] : theme,
               [`switcher-color--${color}`] : color,
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
    $color-default-default: #aaa;
    $color-default-green: #53b96e;
    $color-default-blue: #539bb9;
    $color-default-red: #b95353;
    $color-default-orange: #b97953;
    $color-default-yellow: #bab353;

    $theme-default-colors: (
        default : $color-default-default,
        blue    : $color-default-blue,
        red     : $color-default-red,
        yellow  : $color-default-yellow,
        orange  : $color-default-orange,
        green   : $color-default-green
    );

    .switcher {
        width: 44px;
        height: 25px;
        border-radius: 15px;
        background: #e3e3e3;
        cursor: pointer;
        position: relative;
        display: block;
        border: 1px solid rgba(0,0,0,0.05);
        transition: 0.3s all;

        input {
            display: none;
        }

        &__button {
            top: 1px;
            left: 2px;
            background: rgba(0,0,0,0.3);
            position: absolute;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            transition: 0.3s all;
        }

        &--checked {
            background: $color-default-default;

            .switcher__button {
                background: white;
                left: inherit;
                transform: translateX(94%);
                
                &:hover {
                    background: white;
                }
            }
        }

        &--disabled {
            cursor: default;
            .switcher__button {
                background: rgba(0,0,0,0.1);
            }
        }

        &-theme--default {
            @each $colorName, $color in $theme-default-colors {
                &.switcher-color--#{$colorName} {
                    &.switcher--checked {
                        background: lighten($color, 20%);
                        .switcher__button {
                            background: $color;
                        }
                    }
                }
            }
        }
        
        &-theme--dark {
            background: rgba(0,0,0,0.4);

            .switcher__button {
                background: rgba(255,255,255,0.5);
            }

            @each $colorName, $color in $theme-default-colors {
                &.switcher-color--#{$colorName} {
                    &.switcher--checked {
                        background: lighten($color, 20%);
                        .switcher__button {
                            background: $color;
                        }
                    }
                }
            }
        }
    }
</style>