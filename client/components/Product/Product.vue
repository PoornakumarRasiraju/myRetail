<template>
	<section>
        <p class="product-title">{{product.title}}</p>
        <div class="product-image">
            <img class="product-primary-image" :src="primaryImage" :alt="product.title">
        </div>
       
        <ul class="product-image-slider">
            <li v-for="productImage in product.Images[0].AlternateImages">
                <button @click="viewImage">
                    <img width="50" height="50" :src="productImage.image">
                </button>
            </li>
        </ul>
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
           primaryImage: this.$store.state.CatalogEntryView[0].Images[0].PrimaryImage[0].image
        }
    },

    computed: {
        product() {
            return this.$store.state.CatalogEntryView[0];
        },
        // primaryImage() {
        //     return this.$store.state.CatalogEntryView[0].Images[0].PrimaryImage[0].image;
        // }
    },
    
    methods: {
        viewImage($event, image) {
            let selectedImage = $event.currentTarget.querySelectorAll('img')[0].src;

            this.primaryImage = selectedImage;
        }
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

.product-image {
    display: flex;
    justify-content: center;
    margin-top: 50px;
    margin-bottom: 68px;
}

.product-primary-image {
    width: 400px;
}

.product-image-slider {
    display: flex;
    list-style: none;
    margin-bottom: 25px;

    li {
        cursor: pointer;
        margin-right: 10px;
    }

    button {
        background-color: transparent;
        border: 1px solid #D6D6D6;
        cursor: pointer;
    }
}
</style>
