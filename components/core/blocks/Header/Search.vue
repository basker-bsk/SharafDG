<template>
     <div class="header__search-wrapper px15 ">
              <div :class="['search-form search-form--fixed', { 'search-form__input-focus': isFocusVisible || isOverlay, 'search-form__input-result' : isOverlay }]">
                <div class="align-item-center d-xs-flex" :class="['input search-form__input-wrapper']"> 
                  <Icon class="search_icon w-xs-16 h-xs-16 mr15" icon-id="search" /> 
                  <input
                  ref="autocompletesearch"
                  name="search"
                  @input="searchKlevu"
                  @focus="isFocusVisible = true, isOverlay = true"
                  @blur="isFocusVisible = false"
                  @keydown.enter="redirectToSlp"
                  v-model="searchtext"
                  class="input__field search-form__input"
                  :placeholder="$t('Search Sharaf DG')"
                  type="text"
                  autocomplete="off"
                >
                <span class="close-btn " v-if="isOverlay" @click="isOverlay = false">
                    <Icon class="close_icon w-xs-16 h-xs-16 mr15" icon-id="search" /> 
                </span>
                </div>
                <div :class="['search-form__dropdown', {'search-form__dropdown--open': isOverlay }]">
                  <span>Search Results Items</span>
                </div>
                </div>
                <div v-if="isOverlay" @click="isOverlay = false" class="overlay" />
            </div> 
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
    name:"Search",
    data () {
        return {
            keywordSearch: '',
            isFocusVisible: false,
            isOverlay: false,
            searchtext: '',
            isSearchListing: false,
        }
    },
    components: {
        Icon
    },
    mounted () {
        this.$root.$on('focus-search', () => {
        this.isOverlay = !this.isOverlay
        this.isFocusVisible = !this.isFocusVisible
        });
        this.$root.$on('search-result', (data) => {
        this.isSearchListing = data
        });

    },
    methods:{
        searchKlevu (value) {
            this.autoCompleteData = [];
            this.isFocusVisible = true;
            this.isOverlay = true;
            if (value.srcElement.value.length < 2) {
                return;
            }
            this.$store.dispatch('klevu/search', value.srcElement.value);
        },
    },
}
</script>
<style  lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
// Search 
.header__search-wrapper{
    .search-form__input-wrapper{          
        background-color: #fff;
        border-radius: 5px;
        padding: 0 0 0 10px;        
        position: relative;
        @media (min-width: 768px) {
            padding: 0 15px;
            border-radius: 5px;
        }
    }
    input{
        width: 100%;    
        border: 0;    
        height: 30px;  
        box-sizing: border-box;
        @media (min-width: 768px) {
            width: 100%;
            height: 40px;
        }
        @media (max-width: 768px) {
            border-radius: 5px;
        }
    }
    input:focus{
        border:0;
        outline: 0;
    }
    .close-btn{
        display: none;
        position: absolute;
        left:100%;
        @media (max-width: 767px) {
            display: block;
            padding:5px 10px;
            float: right;
        }
    }
}
.search-form__input-result{
     .search-form__input-wrapper{
         @media (min-width: 767px) {
            border-bottom-left-radius:0;
            border-bottom-right-radius:0;
        }
     }  
}
.search-form{
    position: relative
}
.search-form__dropdown{   
    display: none;
    padding: 15px 20px;
    width: 100%;
    -ms-flex-pack: justify;
    justify-content: space-between;
    position: absolute;
    z-index: 10;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    box-shadow: unset;
    background-color: #fff;
    border-bottom-left-radius:5px;
    border-bottom-right-radius:5px;
}
.search-form__dropdown--open{
  display: block;
  @media (max-width: 767px) {
    background: #fff;
    width: 100%;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 60px;
   }
}
.search-form__input-result {
    z-index: 10;
    @media (max-width: 767px) {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      padding: 15px;
      background: color(sdg-blue);
      z-index: 10;
      .search-form__input-wrapper{
        width: 92%;
      }
    }
}

</style>