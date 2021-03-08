<template>
     <div class="z-xs-10 top-0 absolute h-100 w-100"   v-if="isMenuOpen"
        :class="{'left-0 transition-300-ease-in-out':isMenuOpen}">
        <div class="px-xs-20 py-xs-20 d-xs-flex  bg-cl-primary align-item-center">
            <Icon  class="list__arrow white w-xs-12 h-xs-10 mr-xs-10" icon-id="LeftArrow" />
            <span class="cl-white">Shop All Products</span>
        </div>
        <ul class="level-1 bg-cl-white"> 
            <li class="px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between "
            v-for="(menu,index) in data" :key="index"
            >
                <a class="link-dark" href="">{{menu.name}}</a>
                <Icon  class="list__arrow dark w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>            
        </ul>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"ShopAllCategoriesMobile",
       data(){
        return{
           
        }
    },
    components:{
Icon
    },
    props: {
        data: {
            type: Array,
            required: true
        },
        categorySelected:{
            type:Boolean,
            required: true
        },
     
        isMenuOpen:{
            type:Boolean,
            required: true
        }
    },
    methods: {
        openMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
        },
        closeSidebarMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
        }, 
    },
}
</script>