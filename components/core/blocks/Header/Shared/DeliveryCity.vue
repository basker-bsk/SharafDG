<template>
<div>
<div :class="['delivery_container relative d-xs-flex pointer py-xs-12 justify-center', 
{ 'delivery_active': isDeliveryCityVisible }]"
 @click="isDeliveryCityVisible = true" 
@mouseover="isDeliveryCityVisible = true" @mouseout="isDeliveryCityVisible = false" >
    <div class="d-xs-flex justify-center justify-md-xs-flex-end align-item-center" >
        <Icon class="dark w-xs-24 h-xs-24 mr5" icon-id="pin" />
        <span>Delivery to Dubai Festival City</span>
        <Icon class="list__arrow w-xs-12 h-xs-10 ml10" :class="{ 'active': isDeliveryCityVisible }" icon-id="downArrow" />
    </div>
    <div class="delivery_wrapper bg-cl-white p-xs-30 w-100 absolute" >
        <ButtonFull color="primary" class="w-100">Sign in to see your address</ButtonFull>
        <div class="sep"><span>OR</span></div>
        <vue-dropdown :config="city"></vue-dropdown>
        <div class="sep"><span>OR</span></div>
        <vue-dropdown :config="OutsideofUAE"></vue-dropdown>
    </div>
</div>
<div v-if="isDeliveryCityVisible" @click="isDeliveryCityVisible = false" class="overlay" />
</div>
</template>

<script>
import ButtonFull from 'theme/components/theme/ButtonFull'
import Icon from 'theme/components/custom/Global/Icon'
import vueDropdown from "theme/components/custom/Global/Vue-DropDown";
export default {
    name: 'Delivery-City',
    components: {
        ButtonFull,
        Icon,
        vueDropdown
    },
    data () {
    return {
      isDeliveryCityVisible:false,
      city: {
        options: [
          {
            value: "Dubai"
          },
          {
            value: "Kathar"
          },
          {
            value: "Bahrain"
          }
        ],
        placeholder: "Select Your City",
        width: 100
      },
      OutsideofUAE: {
        options: [
          {
            value: "India"
          },
          {
            value: "Pakistan"
          },
          {
            value: "China"
          }
        ],
        placeholder: "Ship Outside of UAE",
        width: 100
      }
    }
    },
    watch: {
    $route () {
      this.isHelpMenuVisible = false;
    },
    methods: {
        setNewSelectedOption(selectedOption) {
        this.config.placeholder = selectedOption.value;
        }
    },
  },
}
</script>
<style scoped  lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
@include media(md-down){
    .delivery_container + .overlay{
        top: 102px;
    }
}
@include media(md-up){
    .delivery_container + .overlay{
        top: 118px;
    }

}

.delivery_wrapper{
    top:41px;
    z-index: 3;
    display: none;    
}
.delivery_active {
    .delivery_wrapper{ 
        display: block;
    }      
}
@include media(sm-down){
    .delivery_wrapper{
        transform: translate(-50%, 0);
        left:50%;
    }
}
@include media(sm-up){
    .delivery_wrapper{
        width: 420px;
        border-radius: 5px;
         box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19); 
        -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
        -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    }
}
@include media(md-up){
    .delivery_wrapper{
        right:0;        
        box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19); 
        -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
        -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
    }
}
.delivery_wrapper .sep{    
    position: relative;  
}
.delivery_wrapper .sep span{    
    padding: 15px;
    color: color(sdg-gray6);
    font-size: 11px;
    display: inline-block;
    position: relative;
    z-index: 1;
    background: color(white);
}
.delivery_wrapper .sep::after{
    content: '';
    border-bottom: 1px solid color(sdg-clrgray);
    position: absolute;
    left: 0;
    top: 20px;
    height: 1px;
    width: 100%;
}
</style>