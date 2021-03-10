<template>
    <div class="searchbrands col-xs-12 col-md-3 p-md-35 ">
        <p class="font-bold mt-xs-0">{{ $t(data.atoz)}}</p>
        <div class="d-xs-flex brdr-cl-secondary brdr-1 brdr-round-5 px-xs-10 align-item-center justify-lg-space-between">                                    
            <input
                ref="autocompletesearch"
                name="search"
                v-model="searchQuery"
                class="input__field search-form__input brdr-none py-xs-10 brdr-round-5 "
                :placeholder="$t(data.searchPlaceholder)"
                type="text"
                autocomplete="off"
                >
            <Icon class="search_icon w-xs-16 h-xs-16" icon-id="search" /> 
        </div>
        <div class="d-xs-flex my-xs-15 flex-xs-column brandlist_container custom-scroll">
            <div class="d-xs-flex flex-xs-column" v-for="(lists,index) in data.brandList" :key="index">
                <p class="font-bold mt-xs-0">{{lists.code}}</p>
                <ul class="d-xs-flex flex-xs-column mb-xs-15">
                    <li v-for="(list,index) in lists.brands" :key="index" class="pb-xs-5">
                        <router-link :to="localizedRoute(list.url)" class="link-dark" :target="list.openNewTab?'_blank':''">
                            {{list.name}}
                        </router-link>
                    </li>
                </ul> 
            </div>
        </div>
</div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
  name: 'SearchBrands',
  components: {
        Icon
    },
   data () {
        return {
            searchQuery: null,
            brandList:[],
        }
    },
    props: {        
        data:{
            type:Object,
            required:true
        }
    },
}
</script>
<style lang="scss" scoped>
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.searchbrands{
    @include media(md-up){
        border-left:1px solid color(gainsboro);
    }
     .brandlist_container{
        overflow-y: auto;
        height: 40vh;                  
    }
}
</style>