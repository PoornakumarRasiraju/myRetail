<template>
	<section class="product-reviews">
        <p>
            <span>Create Star Component</span>
            <span>view all 14 reviews</span>
        </p>
        <div class="product-review__details">
            <div class="product-review__details-pro-con">
                <p><span>PRO</span><span>most helpful 4-5 star review</span></p>
                <p><span>CON</span><span>most helpful 1-2 star review</span></p>
            </div>
            <div class="product-review__details-wrapper">
                <div class="product-review__details-pro" v-for="proReview in productReviews.Pro">
                    <p><strong>{{proReview.title}}</strong></p>
                    <p>{{proReview.review}}</p>
                    <p><span>{{proReview.screenName}}</span><span>{{proReview.datePosted}}</span></p>
                </div>
                <div class="product-review__details-con" v-for="conReview in productReviews.Con">
                    <p><strong>{{conReview.title}}</strong></p>
                    <p>{{conReview.review}}</p>
                    <p><span>{{conReview.screenName}}</span> <span>{{conReview.datePosted}}</span></p>
                </div>
            </div>
        </div>
	</section>
</template>

<script>
// import ProductReview from './ProductReview.vue';
import { mapState } from 'vuex';
import Vue from 'vue';

export default {
    name: 'ProductReviews',
    components: {
        // ProductReview
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
            productImages: state => state.CatalogEntryView[0].Images[0],
            productReviews: state => state.CatalogEntryView[0].CustomerReview[0],
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
.product-reviews {
    display: flex;
    flex-direction: column;
    font-size: 14px;
}

.product-review__details {
    background-color: #ccc;
}

.product-review__details-pro-con {
    display: flex;

    p {
        display: flex;
        flex-direction: column;
        flex: 1;
    }
}
</style>
