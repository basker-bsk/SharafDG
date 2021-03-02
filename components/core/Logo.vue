<template>
<div class="d-xs-flex middle-xs logo_container">
  <router-link :to="localizedRoute('/')" :title="$t('Home Page')" class="d-xs-none d-md-inline-flex no-underline ">
   <!-- <img
      :width="width"
      :height="height"
      src="/assets/logo.png"
      :alt="$t(defaultTitle)"
    >-->
    <Icon class="logo w-sm-170 h-sm-24" icon-id="sharaf-logo-long" />
  </router-link>
  <router-link :to="localizedRoute('/')" :title="$t('Home Page')" class="d-xs-inline-flex d-md-none no-underline ">
    <Icon class="logo w-xs-45 h-xs-24" icon-id="Sharaf-square" />
  </router-link>
  </div>
</template>

<script>
import config from 'config'
import { currentStoreView } from '@vue-storefront/core/lib/multistore'
import Icon from 'theme/components/custom/Global/Icon'

export default {
  data () {
    const storeView = currentStoreView()
    return {
      defaultTitle: storeView.seo.defaultTitle ? storeView.seo.defaultTitle : config.seo.defaultTitle
    }
  },
  components: {
    Icon
  },
  props: {
    width: {
      type: [String, Number],
      required: true
    },
    height: {
      type: [String, Number],
      required: true
    }
  }
}
</script>
<style scoped lang="scss">
.logo_container{
  .logo{
    fill: #fff;
  }
}
</style>