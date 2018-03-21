<template>
  <div class="product-catalog">
    <product></product>
    <product-information class="product-information"></product-information>
  </div>
</template>

<script>
import Product from 'components/Product';
import ProductInformation from 'components/ProductInformation';

export default {
  components: {
    Product,
    ProductInformation
  }
}
</script>

<style lang="scss">
.product-catalog {
  display: flex;
  margin: 40px 30px;
}

.product-information {
  margin-left: 33px;
}

p {
  margin: 0;
}
</style>
