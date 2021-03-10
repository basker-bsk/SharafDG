<template>
    <div class="subnav-container z-xs-5 bg-white w-100 brdr-cl-secondary brdr-top-1">
        <div class="sharaf-brands">
            <div class="px-md-0 h-100 bg-white">
                <div class="h-100 d-xs-flex flex-xs-column ">
                    <div class="container order-xs-1 order-md-0 py-xs-20 py-md-0">
                        <div class="d-xs-flex row">
                            <FeaturedBrands :data="data" class="order-xs-1 order-md-0" />
                            <SearchBrands :data="data" class="order-xs-0 order-md-1" />                           
                        </div>
                    </div>
                    <div class="viewall d-xs-flex py-xs-20 order-xs-0 order-md-1">                        
                        <div class="container">
                            <div class="d-xs-flex">
                                <router-link :to="localizedRoute('/')" class="font-bold d-xs-flex align-item-center">
                                    <span>{{ $t(data.viewAll) }}</span>
                                    <Icon class="icon_arrow w-xs-12 h-xs-12 ml-xs-10 d-xs-none d-md-block" icon-id="RightArrow" />
                                </router-link>
                            </div>      
                        </div>
                    </div>                  
                </div>

            </div>
        </div>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import FeaturedBrands from './FeaturedBrands'
import SearchBrands from './SearchBrands'
export default {
    name:"Brands",
    components:{
        Icon,
        FeaturedBrands,
        SearchBrands,
    },
    data () {
        return {
            searchQuery: null,
            brandList:[],
        }
    },
    props: {
        data: {
            type: Object,
            required: true
        },
    },
    computed: {
        brandsDisplay () {
            this.data.brandList.map((brandGroup, index) => {
              return this.brandList = brandGroup.brands.filter(brand =>
                    brand.name.toLowerCase(),
                )
            })
        },
    },
}
</script>
<style lang="scss" scoped>
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.sharaf-brands{
    .viewall{
        @include media(xs-down){
            border-bottom:1px solid color(gainsboro);
            .container{
                width: 100%;
                text-align: left;
            }      
        }        
        @include media(md-up){
            border-top:1px solid color(gainsboro);        
        }
    }  
}
</style>