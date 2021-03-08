<template>
     <div class="subnav-container z-xs-5 bg-white w-100 brdr-cl-secondary brdr-top-1">
        <div class="subnav-wrapper">
            <div class="container px-md-0 h-100 bg-white">
                <div class="h-100 d-xs-flex">
                    <div class="col-md-2 brdr-right-1 brdr-cl-secondary py-md-5  dropdown-left">
                        <ul>
                        <li class="nav-list py-md-10" @mouseover="showsubmenu(menu.subcategories)" 
                        v-for="menu in categoryitems" :key="menu.id">
                        <a href="" >{{ menu.name }}</a>                            
                        </li>
                        </ul>       
                    </div>
                    <SubCategory  :category="subcategoryLists" /> 
                    
                    <div class="col-md-2 py-md-15 px-md-25  dropdown-right">
                        <strong>Featured Brands</strong>
                        </div>
                    </div>
            </div>
        </div>
    </div>
</template>
<script>
import SubCategory from './SubCategory'
export default {
    name:"ShopAllCategories",
      components: {
        SubCategory,
    },
    data () {
        return {
        isHovering:false,
        subcategoryLists:[],
        }
    },
    props: {
       categoryitems: {
        type: Array,
        required: true
        },
    },
    computerd:{          
        subCategoryList () {
            let subCategoryList = this.categoryitems || []
            return subCategoryList;
        },
    },
    methods: {
        showsubmenu (subcategories) {
        this.subcategoryLists = subcategories;
        return this.subcategoryLists;
        },

    }
}
</script>
<style  lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.nav-list{
    cursor: pointer;
     a::before{
        transform: scaleX(0);
        display: block;
        content: '';
    }
    &:hover{        
        a::before{
            content: '';
            width: 100%;
            position: absolute;
            bottom: -2px;
            border-bottom: 1px solid color(sdg-dark);
            transform: scaleX(1);
            transition: transform .25s ease-in-out;
            transform-origin: 0% 50%;
        }
    }   
}
.dropdown-left, .dropdown-center{
    a{
        color: color(sdg-dark);
    }
}
.dropdown-center{
  overflow-y: auto;
  overflow-x: auto;
  align-content: flex-start;
  flex-wrap: wrap;
  flex-direction: column;
  display:flex;
}
.dropdown-center .menulist{
  width: 25%;
}
</style>