<template>
	<section>
        <p class="product-title">{{product.title}}</p>
        <div class="product-image">
            <img class="product-primary-image" :src="primaryImage" :alt="product.title">
        </div>
        <div class="product-view-large">
            <i class="fas fa-search-plus"></i><span>view larger</span>
        </div>
        <div class="product-images">
            <i @click="slideLeft" class="fas fa-angle-left"></i>
            <div>
                <ul class="product-image-slider">
                    <li v-for="(productImage, index) in AlternateImages" :key="productImage.id">
                        <button @click="viewImage($event, index)">
                            <img width="50" height="50" :src="productImage.image">
                        </button>
                    </li>
                </ul>
            </div>
            <i @click="slideRight" class="fas fa-angle-right"></i>
        </div>
	</section>
</template>

<script>
import $ from 'jQuery';

export default {
    name: 'Product',
    components: { 
    },
    
    props: {
    },

     data() {
        return {
            imageCounter: 0,
            isActive: true,
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
        viewImage($event, index) {
            let selectedImage = $event.currentTarget.querySelectorAll('img')[0].src;
            this.imageCounter = index+1;
            this.primaryImage = selectedImage;

            $('.product-image-slider li').removeClass('selected');
            $('.product-image-slider li:eq('+index+')').addClass('selected');
        },
        slideLeft($event) {
            $('.product-image-slider li').removeClass('selected');

            if(this.imageCounter > 1 &&  this.imageCounter <= this.AlternateImages.length) {
                console.log(this.imageCounter);
                this.imageCounter--;
                let imageSlide = this.imageCounter-1;
                $('.product-image-slider li:eq('+imageSlide+')').addClass('selected');
                this.primaryImage = this.$store.state.CatalogEntryView[0].Images[0].AlternateImages[this.imageCounter-1].image;
            } else {
                this.primaryImage = this.$store.state.CatalogEntryView[0].Images[0].AlternateImages[this.AlternateImages.length-1].image;
                this.imageCounter = this.AlternateImages.length - 1;
                $('.product-image-slider li:eq('+this.imageCounter+')').addClass('selected');
            }
        },
        slideRight($event) {
            $('.product-image-slider li').removeClass('selected');

            if(this.imageCounter < this.AlternateImages.length) {
                console.log(this.imageCounter);
                $('.product-image-slider li:eq('+this.imageCounter+')').addClass('selected');
                this.primaryImage = this.$store.state.CatalogEntryView[0].Images[0].AlternateImages[this.imageCounter].image;
                this.imageCounter++;
            } else {
                this.primaryImage = this.$store.state.CatalogEntryView[0].Images[0].AlternateImages[0].image;
                this.imageCounter = 1;
                $('.product-image-slider li:eq('+0+')').addClass('selected');
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../../styles/_colors';

section {
    display: flex;
    flex-direction: column;
    flex: 1;
}

.product-title {
    font-size: 26px;
    color: $black-color;
    justify-content: center;
}

.product-image {
    display: flex;
    justify-content: center;
    margin-top: 50px;
    margin-bottom: 72px;
}

.product-view-large {
    color: #666;
    display: flex;
    justify-content: center;

    .fa-search-plus {
        font-size: 20px;
    }

    span {
        font-size: 14px;
        margin-left: 6px;
    }
}

.product-primary-image {
    width: 400px;
}

.product-images {
    display: flex;
    justify-content: center;
}

.fas {
    cursor: pointer;
}

.fa-angle-left,
.fa-angle-right {
    display: flex;
    align-items: center;
    font-size: 28px;
}

.product-image-slider {
    display: flex;
    list-style: none;
    padding-left: 10px;
    padding-right: 10px;
    margin-top: 26px;
    margin-bottom: 25px;
    width: 220px;
    position: relative;
    overflow: hidden;

    li {
        border: 1px solid transparent;
        cursor: pointer;
        position: relative;
        margin-right: 10px;
    }

    .selected {
        border: 1px solid #D6D6D6;
        border-radius: 4px;
    }

    button {
        background-color: transparent;
        border: 1px solid transparent;
        cursor: pointer;
    }
}
</style>
