<template>
    <button class="button" :style="style" :class="classes" type="button" @click="clickHandler">{{label}}</button>
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
        style: {
            type: Object
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
<style scoped lang="scss">
button, input[type="submit"] {
    background: none;
    color: inherit;
    border: none;
    padding: 0;
    cursor: pointer;
    outline: inherit;
}

.button {
    border-radius: 1px;
    font-family: "Open Sans";
    font-size: 12px;
    font-weight: 600;
    padding: 6px 12px 6px 10px;
    max-width: 190px;
}

.button--action {
    font-size: 12px;
    color: #333;
    background-color: #f3f3f3;
    padding: 6px 24px;
    border-radius: 3px;
}
</style>
