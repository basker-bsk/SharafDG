<template>
    <svg class="icon" :[attrName]="attrValue">
      <use :xlink:href="'#'+updatedId" />
    </svg>
</template>
<script>
import i18n from '@vue-storefront/i18n'
export default {
  name: 'Icon',
  data () {
    return {
      locale: 'en-US'
    }
  },
  props: {
    iconId: {
      type: String,
      required: true
    },
    attrValue: {
      type: String,
      required: false,
      default: ''
    },
    attrName: {
      type: String,
      required: false,
      default: ''
    }
  },
  mounted () {
    this.locale = i18n.locale || 'en-US'
  },
  computed: {
    updatedId () {     
      if (this.locale === 'ar-SR' && (this.iconId === 'left_arrow' || this.iconId === 'right_arrow')) {         
        return this.iconId === 'left_arrow' ? 'right_arrow' : 'left_arrow'
      } else {
        return this.iconId;
      }
    }
  }
};
</script>
