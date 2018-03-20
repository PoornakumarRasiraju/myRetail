<template>
	<div class="product-counter">
        <p>quantity:</p>
        <i @click="decrementProduct" class="fas fa-minus-circle"></i>{{count}}
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
    display: flex;
}
</style>
