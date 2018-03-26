<template>
	<div class="product-rating">
        <span v-for="star in maxStarRatings" :key="star.id">
            <i v-if="star <= starRating" class="fas fa-star red"></i>
            <i v-else class="fa fa-star grey"></i>
        </span>
    </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
    name: 'ProductRating',
    components: {},
    
    props: {
    	rating: {
            type: [Number,String],
            default: 0
        },
        maxRating: {
            type: [Number, String],
            default: 5
        }
    },

     data() {
        return {
           starRating: Math.round(this.rating),
           maxStarRatings: Math.round(this.maxRating)
        }
    },

    computed: {
    },
    
    methods: {
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

.red {
    color: $primary-brand-color;
}

.grey {
    color: $grey-color;
}

.product-rating {
    margin-bottom: 6px;
    margin-right: 8px;
}
</style>
