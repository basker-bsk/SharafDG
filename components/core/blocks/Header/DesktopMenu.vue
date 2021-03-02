<template>
    <nav >
      <div class="nav-container w-100 bg-white brdr-cl-secondary brdr-bottom-1" v-bind:class = "isHovering?'nav-active':''">
        <div class="container px-xs-0 px-md-10"  >
          <div class="row">
              <div class="col-md-2 justify-space-between brdr-right-1 brdr-cl-secondary d-xs-none d-md-flex pointer align-item-center" @mouseover="isHovering = true" @mouseout="isHovering = false">
                  <a href="#" class="no-underline">Shop All Products</a>
                   <Icon class="list__arrow cl-white w-xs-12 h-xs-10 ml10" icon-id="downArrow" />
              </div>
              <div class="col-md-6 col-lg-7 d-md-flex d-xs-none" >
                <ul>
                  <li></li>
                </ul>
              </div>
              <div class="col-md-4 col-xs-12 col-lg-3 center-xs ">
                  <DeliveryCity ></DeliveryCity>
              </div>
          </div>
        </div>
        
          <div class="subnav-container bg-white w-100 brdr-cl-secondary brdr-top-1" @mouseover="isHovering = true" @mouseout="isHovering = false">
              <div class="subnav-wrapper">
                <div class="container px-md-0 h-100 bg-white">
                  <div class="h-100 d-xs-flex">
                        <div class="col-md-2 brdr-right-1 brdr-cl-secondary py-md-5  dropdown-left">
                          <ul>
                          <li class="nav-list py-md-10" @mouseover="showsubmenu(menu.subcategories)" 
                          v-for="menu in categoryitems" :key="menu.id">
                            <a  href="" >{{ menu.name }}</a>                            
                          </li>
                          </ul>       
                        </div>                 
                        <SubCategory  v-if="subcategoryLists.length" :category="subcategoryLists" /> 
                          
                        <div class="col-md-2 py-md-15  dropdown-right">
                          <strong>Featured Brands</strong>
                          </div>
                      </div>
                </div>
                </div>
        </div>
       
      </div>
    </nav>
</template>
<script>
import DeliveryCity from 'theme/components/core/blocks/Header/DeliveryCity'
import SubCategory from 'theme/components/core/blocks/Header/SubCategory'
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name: 'Desktop-Menu',
    components: {
        DeliveryCity,
        SubCategory,
        Icon
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
        }  
    },
    watch: {
      $route () {
        this.isHelpMenuVisible = false;
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
.nav-container{
  font-size: 13px;
  position: relative;
  a{
    padding: 12px 0;
    color: black;
  }
  a:after, a:hover:after{
    display: none;
  } 
  ul{
    list-style: none;
  }
}
.subnav-container{
  position: absolute;
  overflow: hidden;
  left: 0;
  display: none;
  z-index: 10;
  background: #fff;
  .subnav-wrapper{  
    overflow: hidden;
    height: 76.66667vh;
  }  
  a:hover{
    text-decoration: underline;
  }
}
.nav-active .subnav-container{
  display: block;
}
</style>