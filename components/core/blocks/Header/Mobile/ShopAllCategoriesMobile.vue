<template>
<div class="submenu-container">
     <div class="d-xs-flex flex-xs-column" >
        <div class="px-xs-20 py-xs-15 d-xs-flex  bg-cl-primary align-item-center" 
        @click="$emit('resetSelected')">
            <Icon  class="list__arrow white w-xs-12 h-xs-10 mr-xs-10" icon-id="LeftArrow" />
            <span class="cl-white font-bold">{{title}}</span>
        </div>
        <ul class="level-1 bg-cl-white"> 
            <li class="px-xs-20 py-xs-20 relative d-xs-flex flex-xs-column "
            v-for="(menu,index) in data" :key="index">
                <div class="d-xs-flex w-100 justify-space-between align-item-center"
                @click="showMenu(menu,index)"
                >
                    <router-link v-if="!menu.subcategories" :to="localizedRoute('/')" :title="$t(menu.name)" 
                    class="link-dark">{{menu.name}}</router-link>
                    <span v-if="menu.subcategories">{{menu.name}}</span>
                    <Icon v-if="menu.subcategories" class="list__arrow dark w-xs-12 h-xs-10" icon-id="RightArrow" />
                </div>
                <div class="" v-if="openMenu">
                    <!-- bg-cl-white z-xs-1 absolute h-100 w-100 top-0 left-0 -->
                    <ul>
                        <li v-for="(submenu,index) in menu.subcategories" :key="index">
                            {{submenu.name}}
                        </li>
                    </ul>
                </div>
            </li>            
        </ul>
    </div>
</div>
</template>
<script>

import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"ShopAllCategoriesMobile",
    components:{
        Icon
    },
    data(){
        return{
            openMenu:false,
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
        showMenu(menu,index){
            
            if(menu.id === menu.subcategories[index].parent_id){
                this.openMenu = !this.openMenu;
            }
            
            // let categoryList = menu.subcategories || []
            // return categoryList.filter((subcategory) => {
            //     return subcategory.parent_id === this.data.id
            // })
        }
    },

}
</script>
