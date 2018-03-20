<template>
	<section class="product-reviews">
        <div class="product-review__overall-rating">
            <div>
                <product-rating :rating="productReviews.consolidatedOverallRating" maxRating="5"></product-rating>
                <span>overall</span>
            </div>
            <p>view all 14 reviews</p>
        </div>
        <div class="product-review__details">
            <div class="product-review__details-pro-con">
                <p><span>PRO</span><span>most helpful 4-5 star review</span></p>
                <p><span>CON</span><span>most helpful 1-2 star review</span></p>
            </div>
            <div class="product-review__details-wrapper">
                <div class="product-review__details-pro" v-for="proReview in productReviews.Pro">
                    <product-rating :rating="proReview.overallRating" maxRating="5"></product-rating>
                    <product-review :review="proReview"></product-review>
                </div>
                <div class="product-review__details-con" v-for="conReview in productReviews.Con">
                    <product-rating :rating="conReview.overallRating" maxRating="5"></product-rating>
                    <product-review :review="conReview"></product-review>
                </div>
            </div>
        </div>
	</section>
</template>

<script>
import moment from 'moment';
import { mapState } from 'vuex';
import ProductRating from './ProductRating';
import ProductReview from './ProductReview';

export default {
    name: 'ProductReviews',
    components: {
        ProductRating,
        ProductReview
    },
    
    props: {
    	
    },

     data() {
        return {
        }
    },

    computed: {
        ...mapState({
            productReviews: state => state.CatalogEntryView[0].CustomerReview[0]
        }),
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
