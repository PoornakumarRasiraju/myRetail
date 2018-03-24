<template>
    <div class="product-review">
        <p class="product-review__title"><strong>{{review.title}}</strong></p>
        <p class="product-review__review">{{review.review}}</p>
        <p class="product-review__post">
            <span class="product-review__screen-name">{{review.screenName}}</span>
            <span class="product-review__date-posted">{{datePosted(review.datePosted)}}</span>
        </p>
    </div>
</template>

<script>
import moment from 'moment';

export default {
    name: 'ProductReview',
    components: {  },
    
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
    margin-bottom: 4px;
}

.product-review__review {
    margin-bottom: 6px;
}
</style>
