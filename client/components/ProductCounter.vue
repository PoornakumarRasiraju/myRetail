<template>
	<div class="product-counter">
        <p class="product-counter-text">quantity:</p>
        <i @click="decrementProduct" class="fas fa-minus-circle"></i><span class="product-quantity">{{count}}</span>
        <i @click="incrementProduct" class="fas fa-plus-circle"></i>
    </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
    name: 'ProductCounter',
    components: {
        
    },
    
    props: {
    	
    },

    data() {
        return {
           count: 1
        }
    },

    computed: {
        ...mapState({
            productPrice: state => state.CatalogEntryView[0].Offers[0].OfferPrice[0]
        })
    },
    
    methods: {
        incrementProduct() {
            this.count++;
        },
        decrementProduct() {
            if(this.count > 1) {
                this.count--;
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.product-counter {
    border: 1px solid #d3d2d2;
    border-radius: 3px;
    display: flex;
    margin-top: 30px;
    margin-bottom: 30px;
    padding: 5px 15px 5px 11px;
    max-width: 225px;

    .fas {
        color: #ccc;
        font-size: 30px;
        cursor: pointer;
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
