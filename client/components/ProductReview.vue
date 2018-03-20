<template>
    <div class="product-review">
        <p><strong>{{review.title}}</strong></p>
        <p>{{review.review}}</p>
        <p><span>{{review.screenName}}</span><span>{{datePosted(review.datePosted)}}</span></p>
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

</style>
