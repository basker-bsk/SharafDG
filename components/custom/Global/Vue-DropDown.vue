<template>
  <div
    class="dropdown d-xs-flex align-item-center justify-space-between pointer"
    @click="toggleRiskLevels" @mouseleave="isBottomSectionToggled = false"
    :style="[
      { '--options-height': optionsHeight + 'px' },
      { '--option-height': optionHeight + 'px' },
      { '--dropdown-width': width + '%' }
    ]"
  >
    <span class="label w-100 px-xs-15 d-xs-flex align-item-center">
      <span v-if="selectedText.flag" class="flag d-xs-flex">
        <img :src="selectedText.flag" class="w-xs-20 h-xs-20 mr-xs-10" />
      </span>
      <span>{{ (selectedText.value ? selectedText.value : config.placeholder) }}</span>
    </span>
    <Icon class="list__arrow w-xs-12 h-xs-10" :class="{'active':isBottomSectionToggled}" icon-id="downArrow" />
   
    <div v-if="isBottomSectionToggled"   class="options w-100 d-xs-flex flex-xs-column pt-xs-5">
      <div v-for="(option,index) in configOptions" :key="index" class="d-xs-flex align-item-center option px-xs-15"  @click="setCurrentSelectedOption(option);" >
        <span v-if="option.flag" class="flag d-xs-flex"><img :src="option.flag" class="w-xs-20 h-xs-20 mr-xs-10" /></span>
        <span>{{ option.value }}</span>
      </div>
    </div>
</div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import { Fragment } from 'vue-fragment'
export default {
  name: "dropdown",
  data() {
    return {
      isBottomSectionToggled: false,
      optionsHeight: 0,
      optionHeight: 35,
      width: "",
      configOptions: [],
      selectedText:"",
    };
  },
  components: {
    Icon,
    Fragment,
  },
  props: ["config"],
  computed: {},
  methods: {
    toggleRiskLevels() {
      this.isBottomSectionToggled = !this.isBottomSectionToggled;
    },
    setCurrentSelectedOption(option) {
      this.selectedText = option;
      this.$emit('clicked', option);
     // this.$emit("setSelectedOption", option);
    },
    setConfigData() {
      this.configOptions = this.config.options;
      this.width = this.config.width;
      this.placeholder = this.config.placeholder; 
    },
    setOptionsHeight() {
      this.optionsHeight = this.optionHeight * this.configOptions.length;     
    }
  },
  created() {
    this.setConfigData();
    this.setOptionsHeight();
    
  },
  beforeUdate() {
    // this.setOptionsHeight();
  },
  mounted() {
  }
};
</script>

<style lang="scss" scoped>
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';

.dropdown {  
  position: relative;  
  color: color(sdg-dark);
  user-select: none;
  text-transform: uppercase;
  font-weight: bold;
  font-size:12px;
  letter-spacing: 2px;
  .label{
    border: 1px solid color(sdg-clrgray);
    border-radius: 5px;
    width: var(--dropdown-width);
    height: var(--option-height);
    line-height: var(--option-height);
  }
  .flag{
    img{
      border-radius: 50%;
    }
  }
  .list__arrow{
    position: absolute;
    right: 10px;
  }
}
.dropdown:hover {
  transition: 0.7s all;
}

.options {
    margin-bottom: calc(-1 * var(--options-height) - 3px);
    position: absolute;
    left: 0;
    top: calc(var(--option-height) - 1px);
    z-index: 2;
    margin-top: -3px;
    border: 1px solid color(sdg-clrgray);
    border-top:0;
    background: color(white);;
    border-radius: 0 0 5px 5px;
    transition: 0.7s all;
    .option {      
      width: auto;
      height: var(--option-height);
      line-height: var(--option-height);
    }
}
</style>
