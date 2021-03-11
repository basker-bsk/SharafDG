<template>
<div class="submenu-container">
     <div class="d-xs-flex flex-xs-column" >
        <div class="px-xs-20 py-xs-15 d-xs-flex  bg-cl-primary align-item-center" 
        @click="$emit('resetSelected')">
            <Icon  class="list__arrow white w-xs-12 h-xs-10 mr-xs-10" icon-id="LeftArrow" />
            <span class="cl-white font-bold">{{title}}</span>
        </div>
        <div class="level-1 bg-cl-white"> 
            <div class="px-xs-20 py-xs-20 d-xs-flex flex-xs-column "
            v-for="(menu,index) in data" :key="index">
                <div class="d-xs-flex w-100 justify-space-between align-item-center"
                @click="setSelectedSubCategory(index)"
                >
                    <router-link v-if="!menu.subcategories" :to="localizedRoute('/')" :title="$t(menu.name)" 
                    class="link-dark">{{menu.name}}</router-link>
                    <span v-if="menu.subcategories">{{menu.name}}</span>
                    <Icon v-if="menu.subcategories" class="list__arrow dark w-xs-12 h-xs-10" icon-id="RightArrow" />
                </div>
                <transition name="slide-left">
                    <div class="bg-cl-white z-xs-1 absolute h-100 w-100 top-0 left-0" 
                    v-if="(selectedSubCategory == index && openSubMenu)">
                        <SubCategories 
                        v-on:resetSubSelected="resetSubSelected"
                        :subcategories="menu.subcategories"
                        :title="menu.name"
                        />
                    </div>
                </transition>
            </div>            
        </div>
    </div>
</div>
</template>
<script>

import Icon from 'theme/components/custom/Global/Icon'
import SubCategories from './SubCategories'
export default {
    name:"ShopAllCategoriesMobile",
    components:{
        Icon,
        SubCategories
    },
    data(){
        return{
            openSubMenu:false,
            selectedSubCategory:Number,
        }
    },
    props: {
        data: {
            type: Array,
            required: true
        },
        title:{
            type: String,
            required: true,
        },
    },
    methods:{
        setSelectedSubCategory(index){
            this.selectedSubCategory = index;
            this.openSubMenu = true;
        },
         resetSubSelected(){
            this.selectedCategory = -1;
            this.openSubMenu = false;
        }
    },

}
</script>
