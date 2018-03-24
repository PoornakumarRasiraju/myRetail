<template>
	<section>
        <p class="product-price">
            <span class="product-price__value">{{productPrice.formattedPriceValue}}</span>
            <span class="product-price__qualifier">{{productPrice.priceQualifier}}</span>
        </p>
        <div class="product-promotions">
            <p  class="product-promotion" v-for="promotion in productPromotions">
                <i class="fas fa-tag"></i>
                <span v-html="promotion.Description[0].shortDescription"></span>
            </p>
        </div>
        <product-counter></product-counter>
          <div class="product-add-to-cart">
            <v-button  v-if="isInStore" :buttonStyle="pickUpStyle" label="PICK UP IN STORE"></v-button>
            <v-button v-if="isProductAvailable" :buttonStyle="cartStyle" label="ADD TO CART"></v-button>
        </div>
        <div class="product-returns">
            <div class="product-returns__copy" v-html="productReturns"></div>
        </div>
        <div class="product-actions">
            <div class="product-add-registry">
                <v-button label="ADD TO REGISTRY"></v-button>
            </div>
            <div class="product-add-list">
                <v-button :buttonStyle="listStyle" label="ADD TO LIST"></v-button>
            </div>
            <div class="product-add-cart">
                <v-button :buttonStyle="shareStyle" label="SHARE"></v-button>
            </div>
        </div>
        <div class="product-features">
            <p class="product-highlight-text">product highlights</p>
            <ul class="product-highlight">
                <li v-for="feature in productFeatures" v-html="feature"></li>
            </ul>
        </div>
	</section>
</template>

<script>
import ProductCounter from './ProductCounter';
import VButton from '../Generic/VButton';

export default {
    name: 'ProductInformation',
    components: {
        ProductCounter,
        VButton
    },
    
    props: {
    	
    },

    data() {
        return {
            listStyle: `paddingLeft: 48px;
                        paddingRight: 54px`,
            shareStyle: `paddingLeft: 51px;
                        paddingRight: 57px`,
            pickUpStyle: `backgroundColor: #000;
                        color:#fff;
                        paddingLeft: 34px;
                        paddingRight: 34px;
                        marginRight: 30px`,
            cartStyle: `paddingLeft: 48px;
                        paddingRight: 54px;
                        backgroundColor: #cc0000;
                        color: #fff`
        }
    },

    computed: {
        productPrice() {
            return this.$store.state.CatalogEntryView[0].Offers[0].OfferPrice[0];
        },
        productFeatures() {
            return this.$store.state.CatalogEntryView[0].ItemDescription[0].features;
        },
        productPromotions() {
            return this.$store.state.CatalogEntryView[0].Promotions;
        },
        productReturns() {
            return this.$store.state.CatalogEntryView[0].ReturnPolicy[0].legalCopy;
        },
        isInStore() {
            let purchaseCode = parseInt(this.$store.state.CatalogEntryView[0].purchasingChannelCode);

            if(purchaseCode === 0 || purchaseCode === 1) {
                return true;
            }

            return false;
        },
        isProductAvailable() {
            let purchaseCode = parseInt(this.$store.state.CatalogEntryView[0].purchasingChannelCode);

            if(purchaseCode === 0 || purchaseCode === 2) {
                return true;
            }

            return false;
        }
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

.product-price {
    margin-bottom: 42px;
}

.product-price__value {
    font-size: 30px;
    font-weight: bold;
}

.product-price__qualifier {
    color: #666;
    font-size: 12px;
}

.product-add-to-cart {
    margin-bottom: 20px;
}

.product-promotions {
    color: #cc0000;
    font-size: 18px;
    padding-top: 9px;
    padding-bottom: 11px;
    border-top: 1px solid #ccc;
    border-bottom: 1px solid #ccc;
}

.product-promotion {
    .fa-tag {
        margin-right: 5px;
    }

    &:first-child {
        margin-bottom: 5px;
    }
}

.product-features {
    display: flex;
    flex-direction: column;
}

.product-highlight-text {
    font-size: 36px;
}

.product-highlight {
    color: #666;
    font-size: 14px;
    padding-left: 18px;

    li {
        margin-bottom: 6px;
    }
}

.product-actions {
    display: flex;
    margin-top: 24px;
    margin-bottom: 30px;
}

.product-add-list {
    margin-left: 6px;
    margin-right: 6px;
}

.product-returns,
.product-returns__copy {
    display: flex;
}

.product-returns__copy {
    font-size: 20px;
    align-items: center;
    color: #666;
}
</style>

<style lang="scss">
.product-returns__copy {
    p {
        font-size: 10px !important;
        padding-left: 15px;
        border-left: 1px solid #ccc;
        margin-left: 20px;
    }
}
</style>
