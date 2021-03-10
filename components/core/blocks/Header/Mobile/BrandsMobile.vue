<template>
    <div class="submenu-container z-xs-1 bg-cl-white absolute h-100 w-100 top-0">
        <div class="d-xs-flex flex-xs-column ">
        <div class="d-xs-flex  px-xs-15 py-xs-20 brdr-bottom-1 brdr-cl-secondary" @click="$emit('resetSelected')">
        <router-link :to="localizedRoute('/')" class="font-bold d-xs-flex align-item-center">
            <Icon class="primary w-xs-12 h-xs-12 mr-xs-10" icon-id="LeftArrow" />
            <span>{{ $t(data.viewAll) }}</span>            
        </router-link>
        </div>
        <div class=" px-xs-10 pt-xs-15">
            <SearchBrands :data="data"/>
        </div>
        <div class="d-xs-flex flex-xs-column  px-xs-15 mb-xs-15">
            <p class="font-bold mt-xs-0 ">{{ $t(data.exclusiveBrandsTitle)}}</p>
            <VueSlickCarousel v-bind="settings" class="">
                <div class="pr-xs-15 d-xs-flex" v-for="(brand,index) in data.exclusiveBrandDetails" :key="index" >
                    <img :src="brand.brandLogo" :alt="brand.brandLogo" class="justify-center"  />
                </div>
            </VueSlickCarousel> 
        </div>
        </div>
    </div>
</template>
<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import Icon from 'theme/components/custom/Global/Icon'
import SearchBrands from '../Shared/Brands/SearchBrands'
export default {
    name:"BrandsMobile",
    components: {
        SearchBrands,
        VueSlickCarousel,
        Icon
    },
    data () {
        return {
            settings: {
                "dots": true,
                "arrows": false,
                "infinite": false,
                "slidesToShow": 2,
                "slidesToScroll": 1,               
            },
        }
    },
    props: {
        data: {
            type: Object,
            required: true
        },
    },
}
</script>
