<template>
<div class="relative">
  <div :class="['language_container', { 'language_active': isLangVisible }]"
    @click="isLangVisible = true" @mouseover="isLangVisible = true" @mouseout="isLangVisible = false" >
    <div class="align-item-center py-md-25 d-xs-flex flag"  
      @mouseover="showMenu = true"  @mouseout="showMenu = false">
       <img :src="setSelectedFlag?setSelectedFlag:city.options[0].flag" class="w-xs-20 h-xs-20 mr-xs-10" alt=""/> 
        <span class="">{{setSelectedLang?setSelectedLang:city.options[0].lang}}</span>
        <Icon class="list__arrow w-xs-12 h-xs-10 ml5"  :class="{'active':showMenu}" icon-id="downArrow" />
    </div>
    <div class="language_wrapper bg-cl-white p-xs-20 absolute" >
        <vue-dropdown :config="city" @clicked="selectedFlag"></vue-dropdown>
        <div class="d-xs-flex flex-xs-column pt-xs-10">
          <label class="d-xs-flex align-item-center py-xs-10 pointer">
            <input type="radio" name="lang" class="w-xs-20 h-xs-20 mr-xs-10"><span>English - EN</span>
          </label>
          <label class="d-xs-flex align-item-center py-xs-10 pointer">
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
        setSelectedFlag:'',
        setSelectedLang:'',
        city: {
          options: [
            {
              value: "United States",
              flag: "https://cdn.countryflags.com/thumbs/united-states-of-america/flag-square-250.png",
              lang: "EN"
            },
            {
              value: "United Arab Emirates",
              flag: "https://cdn.countryflags.com/thumbs/united-arab-emirates/flag-square-250.png",
              lang: "AR"
            },
          ],
          placeholder: "Select Country",
          width: 100
        },
      }
    },
    components: {
      Icon,
      vueDropdown
    },
    methods:{     
      selectedFlag(value){
       this.setSelectedFlag = value.flag
       this.setSelectedLang = value.lang
      },
      
    }
    
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
@include media(xs-down){
    .language_container + .overlay{
        display: none;
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
.flag{
    img{
      border-radius: 50%;
    }
  }
.language_wrapper{
    z-index: 3;
    width: 300px;
    display: none;
    color: color(black);    
    left: 50%;
    transform: translateX(-50%);
    box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19); 
    -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    border-radius: 5px;
    @include media(sm-up){
      top: 65px;
    }
    @include media(xs-down){
      bottom: 42px;
    }
}
.language_active {
    .language_wrapper{ 
        display: block;
    }      
}


</style>
