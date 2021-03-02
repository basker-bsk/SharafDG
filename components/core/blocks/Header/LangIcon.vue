<template>
<div class="relative">
  <div :class="['language_container', { 'language_active': isLangVisible }]"
    @click="isLangVisible = true" @mouseover="isLangVisible = true" @mouseout="isLangVisible = false" >
    <div class="align-item-center py-md-20 d-xs-flex"  
      @mouseover="showMenu = true"  @mouseout="showMenu = false">
        <Icon class="w-xs-24 h-xs-24 mr10" icon-id="login" />
        <span class="">EN</span>
        <Icon class="list__arrow w-xs-12 h-xs-10 ml5"  :class="{'active':showMenu}" icon-id="downArrow" />
    </div>
    <div class="language_wrapper bg-cl-white p-xs-20 absolute" >
        <vue-dropdown :config="city" ></vue-dropdown>
        <div class="d-xs-flex flex-column pt-xs-10">
          <label class="d-xs-flex align-item-center py-xs-10">
            <input type="radio" name="lang" class="w-xs-20 h-xs-20 mr-xs-10"><span>English - EN</span>
          </label>
          <label class="d-xs-flex align-item-center py-xs-10">
            <input type="radio" name="lang" class="w-xs-20 h-xs-20 mr-xs-10"><span>Arabia - AR</span>
          </label>
        </div>
    </div>    
    </div>
  <div v-if="isLangVisible" @click="isLangVisible = false" class="overlay" />
</div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import vueDropdown from "theme/components/custom/Global/Vue-DropDown";
export default {
    name:"LanguageIcon",
    data () {
      return {
        showMenu:false,
        isLangVisible:false,
        city: {
          options: [
            {
              value: "India",
              flag: "https://cdn.countryflags.com/thumbs/india/flag-square-250.png"
            },
            {
              value: "Australia",
              flag: "https://cdn.countryflags.com/thumbs/new-zealand/flag-square-250.png"
            },
            {
              value: "Pakistan",
              flag:"https://cdn.countryflags.com/thumbs/pakistan/flag-square-250.png"
            }
          ],
          placeholder: "",
          width: 100
        },
      }
    },
    components: {
    Icon,
    vueDropdown
  },
}
</script>
<style scoped  lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
@include media(md-down){
    .language_container + .overlay{
        top: 102px;
    }
}
@include media(md-up){
    .language_container + .overlay{
        top: 118px;
    }
    .header.fixed{
      .language_container + .overlay{
        top: 69px;
      }
    }
}

.language_wrapper{
    top:41px;
    z-index: 3;
    width: 300px;
    display: none;
    color: color(black);
    top: 65px;
     left: 50%;
      transform: translateX(-50%);
    box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19); 
    -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    border-radius: 5px;
}
.language_active {
    .language_wrapper{ 
        display: block;
    }      
}


</style>
