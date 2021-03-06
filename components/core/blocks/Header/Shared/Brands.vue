<template>
    <div class="subnav-container  bg-white w-100 brdr-cl-secondary brdr-top-1">
        <div class="sharaf-brands">
            <div class="px-md-0 h-100 bg-white">
                <div class="h-100 d-xs-flex flex-xs-column ">
                    <div class="container">
                        <div class="d-xs-flex row">
                            <div class="col-xs-12 col-md-9 py-xs-35">
                                <p class="font-bold mt-xs-0">{{ $t(categoryitems.exclusiveBrandsTitle)}}</p>
                                <div class="d-xs-flex flex-md-wrap">
                                    <div v-for="(brand,index) in categoryitems.exclusiveBrandDetails" 
                                    :key="index"
                                    class="col-md-2 d-xs-flex align-item-center w170">
                                        <img :src="brand.brandLogo" :alt="brand.brandLogo" >
                                    </div>
                                </div>
                            </div>
                            <div class="col-xs-12 col-md-3 p-md-35 brdr-cl-secondary brdr-left-1">
                                <p class="font-bold mt-xs-0">{{ $t(categoryitems.atoz)}}</p>
                                <div class="d-xs-flex brdr-cl-secondary brdr-1 brdr-round-5 px-xs-10 align-item-center justify-lg-space-between">                                    
                                    <input
                                        ref="autocompletesearch"
                                        name="search"
                                        class="input__field search-form__input brdr-none py-xs-10 brdr-round-5 "
                                        :placeholder="$t(categoryitems.searchPlaceholder)"
                                        type="text"
                                        autocomplete="off"
                                        >
                                    <Icon class="search_icon w-xs-16 h-xs-16" icon-id="search" /> 
                                </div>
                                <div class="d-xs-flex my-xs-15 flex-xs-column brandlist_container custom-scroll">
                                    <div class="d-xs-flex flex-xs-column" v-for="(lists,index) in categoryitems.brandList" :key="index">
                                        <p class="font-bold mt-xs-0">{{lists.code}}</p>
                                        <ul class="d-xs-flex flex-xs-column mb-xs-15">
                                            <li v-for="(list,index) in lists.brands" :key="index" class="pb-xs-5">
                                                <router-link :to="localizedRoute('/')" class="link">{{list.name}}</router-link>
                                            </li>
                                        </ul> 
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="d-xs-flex brdr-cl-secondary brdr-top-1  py-xs-20">
                        <div class="container">
                            <router-link :to="localizedRoute('/')" class="font-bold d-xs-flex align-item-center">
                                <span>{{ $t(categoryitems.viewAll) }}</span>
                                <Icon class="icon_arrow w-xs-12 h-xs-12 ml-xs-10" icon-id="RightArrow" />
                            </router-link>                            
                        </div>
                    </div>                  
                </div>

            </div>
        </div>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"Brands",
    components:{
        Icon
    },
    data () {
        return {
            brandList:[],
        }
    },
    props: {
        categoryitems: {
            type: Object,
            required: true
        },
    },
    computed: {
        brandsDisplay () {
            this.categoryitems.brandList.map((brandGroup, index) => {
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
    .brandlist_container{
        overflow-y: auto;
        height: 40vh;            
    }  
}
</style>