<template>
	<section class="product-reviews">
        <div class="product-review__overall-rating">
            <div class="product-review__overall-rating-wrapper">
                <product-rating :rating="productReviews.consolidatedOverallRating" maxRating="5"></product-rating>
                <span class="product-overall">overall</span>
            </div>
            <p @click="viewAllReviews" class="product-view-all">{{view}} all 14 reviews</p>
        </div>
        <div class="product-review__details">
            <div v-if="!showAllReviews" class="product-review__details--wrapper">
                <div class="product-review__details-pro-con">
                    <p><span class="product-view-label">PRO</span><span class="product-view-text">most helpful 4-5 star review</span></p>
                    <p><span class="product-view-label">CON</span><span class="product-view-text">most helpful 1-2 star review</span></p>
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

            <div v-else class="product-review__details--wrapper">
                <div class="product-review__review" v-for="review in productReviews.Reviews">
                    <product-rating :rating="review.overallRating" maxRating="5"></product-rating>
                    <product-review :viewMore=true :review="review"></product-review>
                </div>
            </div>
        </div>
	</section>
</template>

<script>
import moment from 'moment';
import ProductRating from '../Generic/ProductRating';
import ProductReview from '../Generic/ProductReview';

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
            showAllReviews: false,
            view: 'view'
        }
    },

    computed: {
        productReviews() {
            return this.$store.state.CatalogEntryView[0].CustomerReview[0];
        }
    },
    
    methods: {
        viewAllReviews() {
            this.showAllReviews = !this.showAllReviews;
            this.view = this.showAllReviews ? 'hide' : 'view';
        }
    }
}
</script>

<style lang="scss" scoped>
.product-reviews {
    display: flex;
    flex-direction: column;
    font-size: 14px;
}

.product-review__overall-rating {
    display: flex;
}

.product-review__overall-rating-wrapper {
    display: flex;
    flex: 1;
    margin-bottom: 10px;
}

.product-view-all {
    cursor: pointer;
    font-weight: bold;
}

.product-overall {
    font-weight: bold;
}

.product-review__details {
    background-color: #f6f5f5;
}

.product-review__details--wrapper {
    margin: 16px 12px 25px 20px;
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

.product-view-label {
    font-size: 18px;
}

.product-view-text {
    font-size: 12px;
    color: #666;
}

.product-review__details-wrapper {
    display: flex;
    flex: 1;
    margin-top: 20px
}

.product-review__details-pro {
    margin-right: 22px;
}

.product-review__details-pro,
.product-review__details-con {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-review__review {
    border-bottom: 1px solid #D6D6D6;
    margin-bottom: 30px;

    &:last-child {
        border-bottom: none;
    }
}
</style>
