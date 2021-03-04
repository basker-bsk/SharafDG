<template>
  <div class="relative base-input">
    <div class="relative">
      <input
        class="
         py10 w-100 border-box brdr-round-5"
        :class="{pr30: type === 'password', empty: value === ''}"
        :type="type === 'password' ? passType : type"
        :name="name"
        :autocomplete="autocomplete"
        :value="value"
        :autofocus="autofocus"
        :ref="name"
        @input="$emit('input', $event.target.value)"
        @blur="$emit('blur')"
        @keyup.enter="$emit('keyup.enter', $event.target.value)"
        @keyup="$emit('keyup', $event)"        
      >
      <label>{{ placeholder }}</label>
    </div>
    <button
      v-if="iconActive"
      type="button"
      class="
        icon material-icons absolute brdr-none no-outline
        p0 bg-cl-transparent cl-brdr-secondary pointer
      "
      @click="togglePassType()"
      :aria-label="$t('Toggle password visibility')"
      :title="$t('Toggle password visibility')"
    >
      {{ icon }}
    </button>
    <ValidationMessages v-if="validations" :validations="validations" />
  </div>
</template>

<script>
import ValidationMessages from './ValidationMessages.vue'

export default {
  name: 'BaseInput',
  components: {
    ValidationMessages
  },
  data () {
    return {
      passType: 'password',
      iconActive: false,
      inputFocussed: false,
      icon: 'visibility_off'
    }
  },
  props: {
    type: {
      type: String,
      required: true
    },
    value: {
      type: [String, Number],
      default: ''
    },
    name: {
      type: String,
      required: false,
      default: ''
    },
    placeholder: {
      type: String,
      required: false,
      default: ''
    },
    autocomplete: {
      type: String,
      required: false,
      default: ''
    },
    focus: {
      type: Boolean,
      required: false,
      default: false
    },
    autofocus: {
      type: Boolean,
      required: false,
      default: false
    },
    validations: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    togglePassType () {
      if (this.passType === 'password') {
        this.passType = 'text'
        this.icon = 'visibility'
      } else {
        this.passType = 'password'
        this.icon = 'visibility_off'
      }
    },
    // setFocus sets focus on a field which has a value of 'ref' tag equal to fieldName
    setFocus (fieldName) {
      if (this.name === fieldName) {
        this.$refs[this.name].focus();        
      }
    },
    onFocusChange() {      
      if (this.value === "") {
        this.inputFocussed = true
        console.log('this.focus true',this.$refs)
      }else {
        this.inputFocussed = false
        console.log('this.focus false',this.$refs)
      }
    },
    onBlurr() {
      if (this.name === "") {
        setTimeout(this.inputFocussed = false, 100)
        console.log('this.value',this.$refs)
      }else{
        this.inputFocussed = true
        console.log('this.value',this.$refs)
      }
    }
  },
  created () {
    if (this.type === 'password') {
      this.iconActive = true
    }
  },
  mounted () {
    if (this.focus) {
      this.$refs[this.name].focus()
    }
  }
}
</script>

<style lang="scss">
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';

  $color-tertiary: color(tertiary);
  $color-black: color(black);
  $color-puerto-rico: color(puerto-rico);
  $color-hover: color(tertiary, $colors-background);

  .base-input {
    min-height: 4.5rem;
  

  input {
    background-color: color(white);
    border: 1px solid color(sdg-lightblack);
    padding: 5px 20px;
    @include media(sm-up){
      padding: 10px 20px;
    }
    font-family: 'Nunito Sans', serif;
    &:hover,
    &:focus {
      outline: none;
      border-color: color(sdg-lightblue);
    }

    &:disabled,
    &:disabled + label {
      opacity: 0.5;
      cursor: not-allowed;
      pointer-events: none;
    }
  }
  label {
    color:color(sdg-lightblack);
    background-color: color(white);
    padding: 1px 10px 2px;
    position:absolute;
    pointer-events:none;
    user-select: none;
    left: 10px;
    top: 5px;
    @include media(sm-up){
      top: 10px;
    }
    transition:0.2s ease all;
    -moz-transition:0.2s ease all;
    -webkit-transition:0.2s ease all;
  }
 input:focus ~ label, input:not(.empty) ~ label {
    top: -10px;
    font-size: 12px;
    color: color(sdg-lightblue);
  }

  .icon {
    right: 6px;
    top: 10px;
    &:hover,
    &:focus {
      color: $color-hover;
    }
  }
  }
</style>