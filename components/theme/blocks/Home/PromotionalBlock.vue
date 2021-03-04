<template>

        <div class="promotional-block">
            <div class="container pr-xs-0 pr-xs-0 pr-md-10">
                <div class="row">
                    <div class="col-xs-12 col-lg-2 order-1 order-md-0">
                        <h3 class="fontWeight-400 mb-xs-12 d-none d-md-block">Your Favourite Categories</h3>
                        <p>View your favourite categories</p>
                        <div class="d-xs-flex mt-md-25 mb-xs-20 mb-md-0"><ButtonOutline color="primary" link="www.google.com" class="px40">sign in</ButtonOutline></div>
                    </div>
                    <div class="col-xs-12 col-lg-10 pr-xs-0 pr-md-10">
                        <h3 class="fontWeight-400 d-md-none">Your Favourite Categories</h3>
                        <div class="promotion-block pl-md-10 py-xs-12 py-md-0">
                            <ul class="pb-xs-20 pb-md-0">
                                <li>   
                                    <a href="">
                                        <div class="image-block">                                        
                                            <img src="https://www.searchpng.com/wp-content/uploads/2019/02/Vivo-Apex-PNG-Image.png" alt="" /> 
                                        </div>
                                   </a>
                                    <div class="text-block"><a href="">Mobiles & Tablets</a></div>
                                </li>
                                <li>   
                                    <a href="">
                                        <div class="image-block">                                        
                                            <img src="https://www.searchpng.com/wp-content/uploads/2019/02/Vivo-Apex-PNG-Image.png" alt="" /> 
                                        </div>
                                   </a>
                                    <div class="text-block"><a href="">Laptops & Gaming</a></div>
                                </li>
                                <li>   
                                    <a href="">
                                        <div class="image-block">                                        
                                            <img src="https://www.searchpng.com/wp-content/uploads/2019/02/Vivo-Apex-PNG-Image.png" alt="" /> 
                                        </div>
                                   </a>
                                    <div class="text-block"><a href="">TV & entertainment</a></div>
                                </li>
                                <li>   
                                    <a href="">
                                        <div class="image-block">                                        
                                            <img src="https://www.searchpng.com/wp-content/uploads/2019/02/Vivo-Apex-PNG-Image.png" alt="" /> 
                                        </div>
                                   </a>
                                    <div class="text-block"><a href="">Home & Kitchen</a></div>
                                </li>
                                <li>   
                                   <a href="">
                                        <div class="image-block">                                        
                                            <img src="https://www.searchpng.com/wp-content/uploads/2019/02/Vivo-Apex-PNG-Image.png" alt="" /> 
                                        </div>
                                   </a>
                                    <div class="text-block"><a href="">BEUATY</a></div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    
</template>

<script>
import ButtonOutline from 'theme/components/theme/ButtonOutline'
export default {
    name: 'PromotionalBlock',
    components: {  
        ButtonOutline    
    }
}
</script>


<style lang="scss" scoped>
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
    .promotion-block {
        ul {
            display: flex;            
            @include media(md-down) {
                overflow-x: auto;
            }
            @include media(md-up) {
                justify-content: center;
            }
            li { 
                flex-direction: column;
                justify-content: center;                
                text-align: center; 
                .image-block {   
                    margin: 10px 5px 0;
                    width: 95px;
                    height: 95px;
                    background-color: color(sdg-lightgray);
                    border-radius: 50%; 
                    padding: 15px;
                    @include media(sm-up) {
                        margin: 0 40px;
                    }
                    @include media(md-up) {
                        width: 120px;
                        height: 120px;                       
                        padding: 20px;                        
                    }               
                    &:hover {
                        box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
                    }                   
                }
                .text-block {
                    
                    font-weight: bold;                    
                    letter-spacing: 2px;
                    margin-top: 20px;
                    text-transform: uppercase;                    
                    a {
                        color: color(sdg-dark);
                        font-size: 10px;
                        @include media(md-up) {
                            font-size: 12px;
                        }
                    }
                }
            }
        }
    }
</style>