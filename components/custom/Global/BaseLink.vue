<template>
  <component
    :is="compontentType"
    :href="type === 'link' ? link : false"
    :to="type !== 'link' ? localizedRoute(link) : false"
    class="link"
    :class="{ 'link--icon': icon }"
  >
    <Icon
      v-if="icon && iconBefore"
      class="link__icon link__icon--before"
      :icon-id="icon"
    />
    <slot />
    <Icon v-if="icon && !iconBefore" :class="['link__icon', iconClass]" :icon-id="icon" />
  </component>
</template>

<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
  name: 'BaseLink',
  components: {
    Icon
  },
  props: {
    icon: {
      type: String,
      required: false,
      default: null
    },
    iconClass: {
      type: String,
      required: false,
      default: null
    },
    iconBefore: {
      type: Boolean,
      required: false,
      default: false
    },
    type: {
      type: String,
      required: false,
      default: null
    },
    link: {
      type: String,
      required: false,
      default: null
    }
  },
  computed: {
    compontentType () {
      return this.type === 'link' ? 'a' : 'router-link'
    }
  }
}
</script>
