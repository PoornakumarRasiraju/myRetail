<template>
  <div class="product-mobile-catalog">
    <product></product>
    <product-information></product-information>
    <product-reviews class="product-reviews"></product-reviews>
  </div>
</template>

<script>
import Product from 'components/Product/Product';
import ProductInformation from 'components/ProductInformation/ProductInformation';
import ProductReviews from 'components/Product/ProductReviews';

export default {
  name: 'MobileLayout',
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
.product-mobile-catalog {
  display: flex;
  flex-direction: column;
  margin: 40px 20px;
}

.product-reviews {
    margin-top: 50px;
}
</style>
