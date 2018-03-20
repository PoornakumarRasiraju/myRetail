<template>
	<section>
        <p>{{productPrice.formattedPriceValue}} {{productPrice.priceQualifier}}</p>
        <div class="product-promotions">
            <p  class="product-promotions" v-for="promotion in productPromotions">
                <i class="fas fa-tag"></i>
                <span v-html="promotion.Description[0].shortDescription"></span>
            </p>
        </div>
        <div class="product-features">
            <p>product highlights</p>
            <ul>
                <li v-for="feature in productFeatures" v-html="feature"></li>
            </ul>
        </div>
        <div class="product-returns">
            <div class="product-returns__copy" v-html="productReturns"></div>
        </div>
	</section>
</template>

<script>
import { mapState } from 'vuex';
import Vue from 'vue';

export default {
    name: 'ProductInformation',
    components: {  },
    
    props: {
    	
    },

    data() {
        return {
           
        }
    },

    computed: {
        ...mapState({
            productPrice: state => state.CatalogEntryView[0].Offers[0].OfferPrice[0],
            productFeatures: state => state.CatalogEntryView[0].ItemDescription[0].features,
            productPromotions: state => state.CatalogEntryView[0].Promotions,
            productReturns: state => state.CatalogEntryView[0].ReturnPolicy[0].legalCopy
        })
    },
    
    methods: {
    }
}
</script>

<style lang="scss" scoped>
section {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-promotions {
    color: #cc0000;
    font-size: 12px;
}

.product-features {
    display: flex;
    flex-direction: column;
}

.product-returns,
.product-returns__copy {
    display: flex;
}
</style>
