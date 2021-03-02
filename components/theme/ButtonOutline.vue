<template>
  <component
    :is="compontentType"
    :to="redirectionLink"
    class="button button-outline"
    :class="{      
      primary : color === 'primary', 'cl-sdg-lightblue primary-outline' : color === 'primary',
      secondary : color === 'secondary', 'cl-sdg-lightblue secondary-outline' : color === 'secondary',
      px20 : link ? true : false,
      px40 : link ? false : true
    }"
  >
    <slot>Button</slot>
  </component>
</template>

<script>
import focusClean from 'theme/components/theme/directives/focusClean'

export default {
  name: 'ButtonOutline',
  directives: { focusClean },
  props: {
    color: {
      type: String,
      required: true
    },
    link: {
      type: String,
      default: null,
      required: false
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
@import "~theme/css/variables/colors";
@import "~theme/css/helpers/functions/color";
$dark-border: color(secondary);
$white: color(white);
$black: color(black);
$lightblue: color(sdg-lightblue);
$darkblue: color(sdg-darkblue);

.button-outline {
  border: 1px solid;
  background-color: color(transparent);
  padding-top: 7px;
  padding-bottom: 7px;
  height: 30px;
  font-size: 7px;
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
  .button-outline {   
    padding-top: 11px;
    padding-bottom: 11px;
    height: 40px;
    font-size: 12px;
    letter-spacing: 2px;
  }
}
.primary-outline {
  border-radius: 4px;  
  border-color: $lightblue;
  color: $lightblue;
  &:hover,
  &:focus {
    color: $darkblue;
    border-color: $darkblue;
    text-decoration: none;
  }
}
.secondary-outline {
  &:hover,
  &:focus {
    color: $black;
    background: $white;
    border-color: $white;
    text-decoration: none;
  }
}
</style>
