<template>
     <div class="menulinks_wrapper" @click="closeSidebarMenu">
        <ul class="level-1" :class="{'active':openLevelTwo}"> 
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " @click="openLevelOne = true"
            >
                <span class="cl-white" href=""></span>
                <Icon  class="list__arrow cl-white w-xs-12 h-xs-10" icon-id="RightArrow" />
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
            openLevelTwo:false,
            openSidebarMenu:false,
        }
    },
    components:{
Icon
    },
    props: {
       shopallcategories: {
        type: Array,
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