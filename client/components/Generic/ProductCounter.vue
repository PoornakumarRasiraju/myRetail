<template>
	<div class="product-counter">
        <p class="product-counter-text">{{label}}</p>
        <i @click="decrementProduct" class="fas fa-minus-circle"></i><span class="product-quantity">{{counter}}</span>
        <i @click="incrementProduct" class="fas fa-plus-circle"></i>
    </div>
</template>

<script>
import Resource from '../../resource/Resource-en.js';

export default {
    name: 'ProductCounter',
    components: {
    },
    
    props: {
    	label: {
            type: String
        },
        count: {
            type: [String, Number],
            default: 1
        }
    },

    data() {
        return {
           counter: this.count
        }
    },

    computed: {
    },
    
    methods: {
        incrementProduct() {
            this.counter++;
        },
        decrementProduct() {
            if(this.counter > 1) {
                this.counter--;
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

.product-counter {
    border: 1px solid $grey-light-color;
    border-radius: 3px;
    display: flex;
    margin-top: 22px;
    margin-bottom: 30px;
    padding: 5px 15px 5px 11px;
    max-width: 225px;

    .fas {
        color: $grey-80-color;
        font-size: 30px;
        cursor: pointer;

        &:hover {
            color: $grey-20-color;
        }
    }

    .fa-minus-circle {
        margin-right: 15px;
    }

    .fa-plus-circle {
        margin-left: 15px;
    }
}

.product-quantity {
    font-size: 18px;
    display: flex;
    justify-content: center;
    min-width: 20px;
    align-items: center;
}

.product-counter-text {
    display: flex;
    align-items: center;
    font-size: 14px;
    margin-right: 70px;
}
</style>
