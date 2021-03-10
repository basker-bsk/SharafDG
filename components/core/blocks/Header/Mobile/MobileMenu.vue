<template>
     <div class="menulinks_wrapper">
        <ul class="level-1"> 
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " 
            @click="setSelectedCategory(shopallcategories.link.title)"
            >
                <span class="cl-white" href="">{{shopallcategories.link.title}}</span>
                <Icon v-if="shopallcategories.categoryItems.length > 0" 
                class="list__arrow white w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>  
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " 
            @click="setSelectedCategory(brands.link.title)"
            >
                <span class="cl-white" href="">{{brands.link.title}}</span>
                <Icon v-if="brands.brandList.length > 0" 
                class="list__arrow white w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>            
        </ul>
        <div :class="{'active':openMenu && selectedCategory === categoriesTitle}" >
            <ShopAllCategoriesMobile 
                v-if="(selectedCategory === categoriesTitle)"
                v-on:resetSelected="resetSelected"
                :data="shopallcategories.categoryItems"
            />
        </div>
        <div :class="{'active':openMenu && selectedCategory === brandsTitle}" >
            <BrandsMobile  
                v-if="(selectedCategory===brandsTitle)"
                v-on:resetSelected="resetSelected"
                :data="brands"
            />
        </div>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import ShopAllCategoriesMobile from './ShopAllCategoriesMobile'
import BrandsMobile from './BrandsMobile'
export default {
    name:"MobileMenu",
    components: {
        Icon,
        ShopAllCategoriesMobile,
        BrandsMobile,
    },
     data(){
        return{
            openMenu:false,
            selectedCategory:String,
            categoriesTitle:this.shopallcategories.link.title,
            brandsTitle:this.brands.link.title,
        }
    },
    props: {
       shopallcategories: {
            type: Object,
            required: true
        },
        brands:{
            type:Object,
            required: true
        },
        openSidebarMenu:Boolean,
        
    },
     methods: {
        setSelectedCategory (value){
            this.selectedCategory = value;
            this.openMenu= true;
        },
        resetSelected(){
            this.selectedCategory ='';
            this.openMenu = false;
        }
        

    },
}
</script>
<style scoped lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.menulinks_wrapper{
 
    a{
        color: color(white);
    }
    .level-1{
        > li{
            border-bottom: 1px solid rgba(255, 255, 255, .3);                
        }                       
    }
    .level-1.active{
        .level-2{
            left: 0;
            transition-duration: .25s;  
        }
    } 
}

</style>