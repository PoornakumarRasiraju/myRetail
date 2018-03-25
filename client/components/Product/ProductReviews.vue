<template>
	<section class="product-reviews">
        <div class="product-review__overall-rating">
            <div class="product-review__overall-rating-wrapper">
                <product-rating :rating="productReviews.consolidatedOverallRating" maxRating="5"></product-rating>
                <span class="product-overall">{{resource.OVERALL_LABEL}}</span>
            </div>
            <p @click="viewAllReviews" class="product-view-all">{{resource.VIEW_LABEL}} {{resource.ALL_LABEL}} {{productReviews.Reviews.length}} {{resource.REVIEWS_LABEL}}</p>
        </div>
        <div class="product-review__details">
            <div v-if="!showAllReviews" class="product-review__details--wrapper">
                <div class="product-review__details-pro-con">
                    <p><span class="product-view-label">{{resource.PRO.LABEL}}</span><span class="product-view-text">{{resource.PRO.TEXT}}</span></p>
                    <p><span class="product-view-label">{{resource.CON.LABEL}}</span><span class="product-view-text">{{resource.CON.TEXT}}</span></p>
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
import Resource from '../../resource/Resource-en.js';

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
            resource: Resource
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
            this.view = this.showAllReviews ? this.resource.HIDE_LABEL : this.resource.VIEW_LABEL;
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../../styles/_colors';

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
    background-color: $white-smoke-color;
}

.product-review__details--wrapper {
    margin: 16px 12px 25px 20px;
}

.product-review__details-pro-con {
    border-bottom: 1px solid $grey-80-color;
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
    color: $grey-40-color;
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
    border-bottom: 1px solid $grey-84-color;
    margin-bottom: 30px;

    &:last-child {
        border-bottom: none;
    }
}
</style>
