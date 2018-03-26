<template>
    <div class="product-review">
        <p class="product-review__title"><strong>{{review.title}}</strong></p>
        <p class="product-review__review">{{review.review}}</p>
        <p class="product-review__post">
            <span class="product-review__screen-name">{{review.screenName}}</span>
            <span class="product-review__date-posted">{{datePosted(review.datePosted)}}</span>
            <a href="javascript:void(0);" v-if="viewMore" @click="viewDetailedReview" class="product-review__view-more">{{viewMoreLabel}}</a>
        </p>
        <div v-if="showRatableAttributes" class="product-review__attributes">
            <div class="product-review__attribute" v-for="rating in review.RatableAttributes" :key="rating.id">
                <p class="product-review__name">{{rating.description}}</p>
                <product-rating :rating="rating.value" maxRating="5"></product-rating>
            </div>
        </div>
    </div>
</template>

<script>
import moment from 'moment';
import ProductRating from './ProductRating';
import Resource from '../../resource/Resource-en.js';

export default {
    name: 'ProductReview',
    components: { 
        ProductRating
    },
    
    props: {
    	review: {
            type: Object,
            default: {}
        },
        viewMore: {
            type: Boolean,
            default: false
        }
    },

     data() {
        return {
           viewMoreLabel: Resource.VIEW_MORE_LABEL,
           showRatableAttributes: false
        }
    },

    computed: {
      
    },
    
    methods: {
        datePosted(date) {
            return moment(date).format('LL');
        },
        viewDetailedReview() {
            this.showRatableAttributes = !this.showRatableAttributes;
            this.viewMoreLabel = this.showRatableAttributes ? Resource.VIEW_LESS_LABEL : Resource.VIEW_MORE_LABEL;
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

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
    color: $blue-color;
    cursor: pointer;
    margin-right: 4px;
}

.product-review__review,
.product-review__post {
    font-size: 12px;
    color: $grey-20-color;
}

.product-review__attributes {
    display: flex;
    margin-top: 10px;
}

.product-review__view-more {
    color: $grey-20-color;
    cursor: pointer;
    margin-left: 6px;
}

.product-review__attribute {
    margin-right: 20px;
}

.product-review__name {
    margin-bottom: 2px;
}
</style>
