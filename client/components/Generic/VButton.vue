<template>
    <button class="button" :style="buttonStyle" :class="classes" type="button" @click="clickHandler">{{label}}</button>
</template>

<script>
export default {
    name: 'VButton',
    props: {
        label: {
            type: String
        },
        classes: {
            type: String,
            default: 'button--action'
        },
        buttonStyle: {
            type: String
        }
    },
    methods: {
        clickHandler() {
            this.$emit('buttonClick');
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

button, input[type="submit"] {
    background: none;
    color: inherit;
    border: none;
    padding: 0;
    cursor: pointer;
    outline: inherit;
}

.button {
    border-radius: 4px;
    font-size: 12px;
    font-weight: 600;
    padding: 6px 12px 6px 10px;
    max-width: 190px;
}

.button--action {
    font-size: 12px;
    color: $grey-20-color;
    background-color: $white-variant-color;
    padding: 6px 24px;
    border-radius: 3px;
}

.button--cart {
    padding-left: 48px;
    padding-right: 54px;
    background-color: $primary-brand-color;
    color: $white-color;

    &:hover {
        background-color: $primary-brand-hover-color;
    }
}

.button--pick-up {
    background-color: $black-color;
    color: $white-color;
    padding-left: 34px;
    padding-right: 34px;
    margin-right: 30px;

    &:hover {
        background-color: $grey-20-color;
    }
}
</style>
