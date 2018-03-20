<template>
    <div class="product-review">
        <p><strong>{{proReview.title}}</strong></p>
        <p>{{proReview.review}}</p>
    </div>
</template>

<script>
import { mapState } from 'vuex';
import Vue from 'vue';

export default {
    name: 'ProductReviews',
    components: {  },
    
    props: {
    	
    },

     data() {
        return {
           
        }
    },

    computed: {
      
    },
    
    methods: {
    }
}
</script>

<style lang="scss" scoped>

</style>
