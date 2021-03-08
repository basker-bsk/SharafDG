<template>
    <div class="subnav-container z-xs-5 bg-white w-100 brdr-cl-secondary brdr-top-1">
        <div class="sharaf-experiences">
        <div class=" px-md-0 h-100 bg-white">
            <div class="container h-85 d-xs-flex pt-xs-35 flex-xs-column flex-xs-wrap">
                <div v-for="menu in categoryitems.experiences" :key="menu.id"
                class="d-xs-flex col-xs-12 col-md-4 px-xs-0">
                    <div class="container mb-xs-15 pr-xs-15">
                        <div class="row">
                            <div class="col-xs-3"><img class=" image" :src="menu.image" alt="" width="100" /></div>
                            <div class="col-xs-9">
                                <p class="font-bold my-xs-0 mb-xs-5">{{menu.title}}</p>
                                <p class="my-xs-0 mb-xs-5">{{menu.description}}</p>                         
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="h-15 d-xs-flex brdr-cl-secondary brdr-top-1 py-xs-20 align-item-center">
                <div class="container">
                    <router-link :to="localizedRoute('/')" class="font-bold d-xs-flex align-item-center">
                    <span>{{ $t(categoryitems.linkText) }}</span>
                    <Icon class="icon_arrow w-xs-12 h-xs-12 ml-xs-10" icon-id="RightArrow" />
                    </router-link>
                </div>
            </div>
        </div>
    </div>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"SharafExperiences",
     data () {
        return {
            expList:[],
        }
    },
    components:{
        Icon
    },
    props: {
        categoryitems: {
            type: Object,
            required: true
            },
        },
}
</script>
<style lang="scss" scoped>
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.sharaf-experiences{
    .image{
        border-radius: 5px;
    }
    .h-85{
        height: 85%;
    }
    .h-15{
        height: 15%;
    }
}
</style>