<template>
<div class="myacc_links">
    <div class="py-xs-10 py-md-5" v-for="(page, index) in navigation" :key="index" @click="notify(page.title)">
        <router-link @click.native="showMenu = false" class="d-xs-flex align-item-center no-underline py-md-5" :to="localizedRoute(page.link)">
           <Icon class="w-xs-24 h-xs-24 mr-xs-10" :icon-id="page.id" />
           <span> {{ page.title }}</span>
        </router-link>             
    </div>
</div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"MyAccountLinks",
    components: {
        Icon,
    },
    data () {
        return {
        showMenu: false,
            navigation: [
                { title: this.$t('My Account'), link: '/my-account', id:'login' },
                { title: this.$t('Orders'), link: '/my-account/orders', id:'order' },
                { title: this.$t('Recomanded For You'), link: '/my-account/shipping-details', id:'foryou' },
                { title: this.$t('Inbox'), link: '/my-account/newsletter', id:'mail' },        
                { title: this.$t('Wishlist'), link: '#',id:'wishlist' },
            ]
        }
    },
    methods: {
    notify (title) {
      if (title === 'My loyalty card' || title === 'My product reviews') {
        this.$store.dispatch('notification/spawnNotification', {
          type: 'warning',
          message: this.$t('This feature is not implemented yet! Please take a look at https://github.com/DivanteLtd/vue-storefront/issues for our Roadmap!'),
          action1: { label: this.$t('OK') }
        })
      }
    }
  }
}
</script>
<style scoped lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.dropdown-content, .myacc_links{
    a{
        color: color(black);
        font-weight: bold;
        font-size: 14px;
      } 
}

</style>