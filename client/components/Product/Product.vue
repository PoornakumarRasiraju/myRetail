<template>
	<section>
        <h1 class="product-title">{{product.title}}</h1>
        <product-image-slider :mainImage="primaryImage"
            :mainImageTitle="product.title"
            :secondaryImages="AlternateImages">
        </product-image-slider>
	</section>
</template>

<script>
import ProductImageSlider from '../Generic/ProductImageSlider';

export default {
    name: 'Product',
    components: { 
        ProductImageSlider
    },
    
    props: {
    },

    data() {
        return {
            primaryImage: this.$store.state.CatalogEntryView[0].Images[0].PrimaryImage[0].image,
            AlternateImages: this.$store.state.CatalogEntryView[0].Images[0].AlternateImages
        }
    },

    computed: {
        product() {
            return this.$store.state.CatalogEntryView[0];
        }
    },
    
    methods: {
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../styles/_colors';

section {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-title {
    font-size: 26px;
    font-weight: normal;
    color: $black-color;
    display: flex;
    justify-content: center;
    margin: 0;
}
</style>
