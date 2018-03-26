<template>
  <div class="product-catalog">
    <div class="product-details">
      <product></product>
      <product-information class="product-information"></product-information>
    </div>
    <product-reviews class="product-reviews"></product-reviews>
  </div>
</template>

<script>
import Product from 'components/Product/Product';
import ProductInformation from 'components/ProductInformation/ProductInformation';
import ProductReviews from 'components/Product/ProductReviews';

export default {
  components: {
    Product,
    ProductInformation,
    ProductReviews
  }
}
</script>

<style lang="scss">
.product-catalog {
  display: flex;
  flex-direction: column;
  font-family: Arial, Helvetica, sans-serif;
  margin: 40px 30px;
}

.product-details {
  display: flex;
}

.product-information {
  margin-left: 33px;
}

.product-reviews {
  display: flex;
  width: 50%;
}

p {
  margin: 0;
}

@media only screen and (max-device-width : 768px) {
  .product-details {
    flex-direction: column;
  }

  .product-reviews {
    margin-top: 58px;
    width: 100%;
  }
}
</style>
