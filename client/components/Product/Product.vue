<template>
	<section>
        <p class="product-title">{{product.title}}</p>
        <div class="product-primary-image">
            <img :src="primaryImage" alt="">
        </div>
        <product-reviews></product-reviews>
	</section>
</template>

<script>
import ProductReviews from './ProductReviews';

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
        product() {
            return this.$store.state.CatalogEntryView[0];
        },
        primaryImage() {
            return this.$store.state.CatalogEntryView[0].Images[0].PrimaryImage[0].image;
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
    font-size: 26px;
    color: #000;
    justify-content: center;
}

.product-primary-image {
    display: flex;
    justify-content: center;
    margin-top: 50px;
    margin-bottom: 68px;
}

img {
    width: 400px;
}
</style>
