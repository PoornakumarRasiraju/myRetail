<template>
    <div class="product-catalog">
        <div class="product-details">
            <product></product>
            <product-reviews></product-reviews>
        </div>
        <product-information class="product-information"></product-information>
    </div>
</template>

<script>
import Product from 'components/Product/Product';
import ProductInformation from 'components/ProductInformation/ProductInformation';
import ProductReviews from 'components/Product/ProductReviews';

export default {
    name: 'DesktopLayout',
    components: {
        Product,
        ProductInformation,
        ProductReviews
    },

    data() {
        return {
        }
    },

    methods: {
    },

    mounted() {
    }
}
</script>

<style lang="scss">
.product-catalog {
    display: flex;
    flex-direction: row;
    margin: 40px 30px;
}

.product-details {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-information {
    margin-left: 33px;
    display: flex;
    flex: 1;
}
</style>
