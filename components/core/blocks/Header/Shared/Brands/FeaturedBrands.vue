<template>
    <div class="col-xs-12 col-md-9 py-md-35 brand-slider">
        <p class="font-bold mt-xs-0 px-md-5">{{ $t(data.exclusiveBrandsTitle)}}</p>
         <div class="container">
             <div class="row  flex-md-wrap">
                <div class="col-xs-2 mb-xs-15" v-for="(brand,index) in data.exclusiveBrandDetails" :key="index" >
                    <img :src="brand.brandLogo" :alt="brand.brandLogo"  />
                </div>
             </div>
        </div>
    </div>
</template>
<script>

export default {
  name: 'FeaturedBrands',
    props: {        
        data:{
            type:Object,
            required:true
        }
    },
}
</script>
<style lang="scss">
.brand-slider{
    width: 400px;
    * {
    min-width: 0;
    min-height: 0;
    }
}
</style>
