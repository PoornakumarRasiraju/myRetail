<template>
    <div class="product-review">
        <p class="product-review__title"><strong>{{review.title}}</strong></p>
        <p class="product-review__review">{{review.review}}</p>
        <p class="product-review__post">
            <span class="product-review__screen-name">{{review.screenName}}</span>
            <span class="product-review__date-posted">{{datePosted(review.datePosted)}}</span>
        </p>
        <div class="product-review__attributes" v-if="review.RatableAttributes.length">
            <div class="product-review__attribute" v-for="rating in review.RatableAttributes">
                <p class="product-review__name">{{rating.description}}</p>
                <product-rating :rating="rating.value" maxRating="5"></product-rating>
            </div>
        </div>
    </div>
</template>

<script>
import moment from 'moment';
import ProductRating from './ProductRating';

export default {
    name: 'ProductReview',
    components: { 
        ProductRating
    },
    
    props: {
    	review: {
            type: Object,
            default: {}
        }
    },

     data() {
        return {
           
        }
    },

    computed: {
      
    },
    
    methods: {
        datePosted(date) {
            return moment(date).format('LL');
        }
    }
}
</script>

<style lang="scss" scoped>
.product-review {
    margin-bottom: 20px;
}

.product-review__title {
    font-size: 16px;
    margin-bottom: 4px;
}

.product-review__review {
    margin-bottom: 8px;
}

.product-review__screen-name {
    color: #0066cc;
    cursor: pointer;
    margin-right: 4px;
}

.product-review__review,
.product-review__post {
    font-size: 12px;
    color: #333;
}

.product-review__attributes {
    display: flex;
    margin-top: 10px;
}

.product-review__attribute {
    margin-right: 20px;
}

.product-review__name {
    margin-bottom: 2px;
}
</style>
