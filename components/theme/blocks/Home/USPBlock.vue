<template>
    <div class="usp-content">
        <div class="container">
            <div class="row">
                <div class="col-xs-4">
                    <div class="usp-block flex flex-column flex-md-row justify-center align-content-center text-center py-xs-20 px-xs-10 px-md-0">                       
                        <Icon icon-id="authentic-product" class="usp-icon mr-md-20 mb-xs-10 mb-md-0"></Icon>
                        <div><a href="">Authentic Products</a></div>                       
                    </div>
                </div>
                <div class="col-xs-4">
                    <div class="usp-block flex flex-column flex-md-row justify-center align-content-center text-center py-xs-20 px-xs-10 px-md-0">                        
                        <Icon icon-id="pin" class="usp-icon mr-md-20 mb-xs-10 mb-md-0"></Icon>
                        <div><a href="">Store Pick Up and Returns</a></div>                        
                    </div>
                </div>
                <div class="col-xs-4">
                    <div class="usp-block flex flex-column flex-md-row justify-center align-content-center text-center py-xs-20 px-xs-10 px-md-0">                        
                        <Icon icon-id="delivery" class="usp-icon mr-md-20 mb-xs-10 mb-md-0"></Icon>
                        <div><a href="">Free &amp; Safe Delivery</a></div>                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name: 'USPBlock',
     components: {  
        Icon    
    }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
   
   .usp-content {
       border-top: 1px solid #ddd;
       border-bottom : 1px solid #ddd;
       .usp-block {           
           @include media(md-up) {
            border-right: 1px solid #ddd;
           }
           .usp-icon {
               width: 28px;
               height: 28px;
           }
           a {
               color: #222;
               font-size: 12px;
               font-weight: bold;
               @include media(md-up) {
                    font-size: 14px;
                }
           }
       }
   }
   
</style>