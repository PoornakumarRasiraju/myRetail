<template>
	<section>
        <p class="product-title">{{product.title}}</p>
        <img :src="primaryImage" alt="">
        <product-reviews></product-reviews>
	</section>
</template>

<script>
import ProductReviews from './ProductReviews';
import { mapState } from 'vuex';
import Vue from 'vue';

export default {
    name: 'Product',
    components: { 
        ProductReviews
    },
    
    props: {
    	
    },

     data() {
        return {
           
        }
    },

    computed: {
        ...mapState({
            product: state => state.CatalogEntryView[0],
            productImages: state => state.CatalogEntryView[0].Images[0]
        }),
        primaryImage() {
            return this.productImages.PrimaryImage[0].image;
        }
    },
    
    methods: {
    }
}
</script>

<style lang="scss" scoped>
section {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-title {
    font-size: 13px;
    color: #000;
    justify-content: center;
}

img {
    width: 400px;
}
</style>
