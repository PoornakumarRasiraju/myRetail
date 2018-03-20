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
                    <product-rating :rating="proReview.overallRating" maxRating="5"></product-rating>
                    <p><strong>{{proReview.title}}</strong></p>
                    <p>{{proReview.review}}</p>
                    <p><span>{{proReview.screenName}}</span><span>{{proReview.datePosted}}</span></p>
                </div>
                <div class="product-review__details-con" v-for="conReview in productReviews.Con">
                    <product-rating :rating="conReview.overallRating" maxRating="5"></product-rating>
                    <p><strong>{{conReview.title}}</strong></p>
                    <p>{{conReview.review}}</p>
                    <p><span>{{conReview.screenName}}</span> <span>{{conReview.datePosted}}</span></p>
                </div>
            </div>
        </div>
	</section>
</template>

<script>
import ProductRating from './ProductRating.vue';
import { mapState } from 'vuex';

export default {
    name: 'ProductReviews',
    components: {
        ProductRating
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
    background-color: #f6f5f5;
}

.product-review__details-pro-con {
    border-bottom: 1px solid #ccc;
    display: flex;
    padding-bottom: 10px;
    padding-top: 10px;

    p {
        display: flex;
        flex-direction: column;
        flex: 1;
    }
}

.product-review__details-wrapper {
    display: flex;
    flex: 1;
}

.product-review__details-pro,
.product-review__details-con {
    display: flex;
    flex-direction: column;
    flex: 1;
}
</style>
