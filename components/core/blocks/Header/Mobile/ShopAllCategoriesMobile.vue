<template>
<div class="submenu-container  z-xs-10 bg-cl-white absolute h-100 w-100 top-0">
     <div class="d-xs-flex flex-xs-column" >
        <div class="px-xs-20 py-xs-20 d-xs-flex  bg-cl-primary align-item-center" 
        @click="$emit('resetSelected')">
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
       
       
    },
    methods: {

    },
}
</script>
