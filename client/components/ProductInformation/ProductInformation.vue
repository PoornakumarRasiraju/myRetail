<template>
	<div class="product-information__wrapper">
        <p class="product-price">
            <span class="product-price__value">{{productPrice.formattedPriceValue}}</span>
            <span class="product-price__qualifier">{{productPrice.priceQualifier}}</span>
        </p>
        <div class="product-promotions">
            <p  class="product-promotion" v-for="promotion in productPromotions" :key="promotion.id">
                <i class="fas fa-tag"></i>
                <span v-html="promotion.Description[0].shortDescription"></span>
            </p>
        </div>
        <product-counter :label="resource.QUANTITY_LABEL" count="1"></product-counter>
        <div class="product-add-to-cart">
            <v-button v-if="isInStore" :classes="pickUpStyle" :label="resource.BUTTON_LABEL.PICK_UP"></v-button>
            <v-button v-if="isProductAvailable" :classes="cartStyle" :label="resource.BUTTON_LABEL.ADD_CART"></v-button>
        </div>
        <div class="product-returns">
            <div class="product-returns__copy" v-html="productReturns"></div>
        </div>
        <div class="product-actions">
            <div class="product-add-registry">
                <v-button :label="resource.BUTTON_LABEL.ADD_REGISTRY"></v-button>
            </div>
            <div class="product-add-list">
                <v-button :buttonStyle="listStyle" :label="resource.BUTTON_LABEL.ADD_LIST"></v-button>
            </div>
            <div class="product-add-cart">
                <v-button :buttonStyle="shareStyle" :label="resource.BUTTON_LABEL.SHARE"></v-button>
            </div>
        </div>
        <section class="product-features">
            <h2 class="product-highlight-text">{{resource.PRODUCT_HIGHLIGHTS}}</h2>
            <ul class="product-highlight">
                <li v-for="feature in productFeatures" v-html="feature" :key="feature.id"></li>
            </ul>
        </section>
	</div>
</template>

<script>
import ProductCounter from '../Generic/ProductCounter';
import VButton from '../Generic/VButton';
import Resource from '../../resource/Resource-en.js';

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
            resource: Resource,
            listStyle: `paddingLeft: 48px;
                        paddingRight: 54px`,
            shareStyle: `paddingLeft: 51px;
                        paddingRight: 57px`,
            pickUpStyle: `button--pick-up`,
            cartStyle: `button--cart`
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

.product-information__wrapper {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-price {
    margin-bottom: 40px;
}

.product-price__value {
    font-size: 30px;
    font-weight: bold;
}

.product-price__qualifier {
    color: $grey-40-color;
    font-size: 12px;
}

.product-add-to-cart {
    margin-bottom: 44px;
}

.product-promotions {
    color: $primary-brand-color;
    font-size: 18px;
    padding-top: 18px;
    padding-bottom: 22px;
    border-top: 1px solid $grey-80-color;
    border-bottom: 1px solid $grey-80-color;
}

.product-promotion {
    .fa-tag {
        margin-right: 5px;
    }

    &:first-child {
        margin-bottom: 8px;
    }
}

.product-features {
    display: flex;
    flex-direction: column;
}

.product-highlight-text {
    font-size: 36px;
    font-weight: normal;
    margin: 0;
}

.product-highlight {
    color: $grey-40-color;
    padding-left: 18px;

    li {
        margin-bottom: 8px;
    }
}

.product-actions {
    display: flex;
    margin-top: 26px;
    margin-bottom: 28px;
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
    font-size: 14px;
    align-items: center;
    color: $grey-40-color;
}
</style>

<style lang="scss">
@import '../../styles/_colors';

.product-returns__copy {
    p {
        font-size: 10px !important;
        padding-left: 15px;
        border-left: 1px solid $grey-80-color;
        margin-left: 20px;
    }
}

.product-highlight {
    li {
        font-size: 14px;
    }

    strong {
        font-weight: normal;
    }
}

@media only screen and (max-device-width : 768px) {
    .product-promotions {
        padding-top: 20px;
        padding-bottom: 30px;
    }
}
</style>