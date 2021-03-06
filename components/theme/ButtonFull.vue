<template>
  <component
    :is="compontentType"
    :type="!link ? type : false"
    :to="redirectionLink"
    class="button full-button brdr-none"    
    :class="{ 
      'no-underline pointer align-center border-box': link, 
      'disabled': disabled, 
      'button-disabled': disabled,
      primary : color === 'primary', 'primary-full' : color === 'primary',
      secondary : color === 'secondary', 'secondary-full' : color === 'secondary',
      px20 : link ? true : false,
      px40 : link ? false : true
    }"
    data-testid="subscribeSubmit"
    :disabled="disabled"
  >
    <slot>
      Button
    </slot>
  </component>
</template>

<script>
import focusClean from 'theme/components/theme/directives/focusClean'
export default {
  name: 'ButtonFull',
  directives: { focusClean },
  props: {
    type: {
      type: String,
      required: false,
      default: 'button'
    },
    color: {
      type: String,
      required: false
    },
    link: {
      type: String,
      required: false,
      default: null
    },
    disabled: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  computed: {
    compontentType () {
      return this.link ? 'router-link' : 'button'
    },
    redirectionLink () {
      return this.link ? this.localizedRoute(this.link) : null
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
 
  .disabled {
    background-color: gray
  }
  .full-button {    
    padding-top: 7.5px;
    padding-bottom: 7.5px;
    height: 30px;
    font-size: 11px;
    border-radius: 4px;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 1px;
    transition: all .2s linear;
    &.w-full {
      width: 100%;
    }
    &.w-200 {
      min-width: 200px;
    }  
}

@media screen and (min-width: 900px) {
  .full-button {   
    padding-top: 12px;
    padding-bottom: 12px;
    height: 40px;
    font-size: 12px;
    letter-spacing: 2px;
  }
}
.primary-full {    
  background-color: color(sdg-blue);
  color: color(white);
  &:hover,
  &:focus {
    background-color: color(sdg-darkblue);
    text-decoration: none;
  }
}
.secondary-full {
  background-color: color(white);
  color: color(sdg-dark);
  &:hover,
  &:focus {
    color: color(sdg-lightblue);
    text-decoration: none;
  }
}
  
</style>
