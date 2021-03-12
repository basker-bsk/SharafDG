<template>
  <div class="d-xs-flex flex-xs-column">
    <div
      class="px-xs-20 py-xs-15 d-xs-flex bg-cl-primary align-item-center"
      @click="$emit('resetSelected')"
    >
      <Icon
        class="list__arrow white w-xs-12 h-xs-10 mr-xs-10"
        icon-id="LeftArrow"
      />
      <span class="cl-white font-bold">{{ data.link.title }}</span>
    </div>
    <div class="d-xs-flex brdr-cl-secondary brdr-bottom-1 p-xs-20">
      <router-link
        :to="localizedRoute('/')"
        class="font-bold d-xs-flex align-item-center"
      >
        {{ $t(data.linkText) }}
      </router-link>
    </div>
    <div
      class="sharaf-experiences d-xs-flex flex-xs-column pb-xs-15 p-xs-15 overflow-xs-auto"
    >
      <div
        v-for="menu in data.experiences"
        :key="menu.id"
        class="d-xs-flex mb-xs-15"
      >
        <div class="col-xs-4">
          <img class="image" :src="menu.image" alt="" width="100">
        </div>
        <div class="col-xs-8">
          <p class="font-bold my-xs-0 mb-xs-5">
            {{ menu.title }}
          </p>
          <p class="my-xs-0 mb-xs-5">
            {{ menu.description }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
  name: 'SharafExperiences',
  data () {
    return {
      expList: []
    }
  },
  components: {
    Icon
  },
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>
<style lang="scss" scoped>
@import "~theme/css/variables/variables";
@import "~theme/css/helpers/functions/color";
.sharaf-experiences {
  height: calc(100vh - 125px);
  .image {
    border-radius: 5px;
  }
  .h-85vh {
    height: 85%;
  }
  .h-15 {
    height: 15%;
  }
}
</style>
