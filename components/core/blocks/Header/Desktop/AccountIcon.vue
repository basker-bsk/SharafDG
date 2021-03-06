<template>
  <div
    class="relative dropdown"
    data-testid="accountButton"    
    tabindex="0"
    role="button"
    @mouseover="showMenu = true"
    @mouseout="showMenu = false"
    :aria-label="$t('Open my account')"
     @click.self="goToAccount()"
    @keyup.enter="goToAccount"
  >
    <button
      type="button"
      class="bg-cl-transparent brdr-none p0 align-item-center d-none d-xs-flex"
    >
      <div class="d-xs-flex align-item-center py-md-20 cl-white account">
        <div class="user_icon  mr12">
            <Icon class="icon login w-xs-24 h-xs-24" icon-id="login" />
            <span v-if="currentUser" class="logged-in"></span>
        </div>
          <span v-if="!currentUser">{{ $t('Sign In') }}</span>
          <span v-if="currentUser">{{currentUser.firstname}}</span>
          <Icon class="icon list__arrow cl-white w-xs-12 h-xs-10 ml10" :class="{'active':showMenu}" icon-id="downArrow" />
      </div>
    </button>
   
    <no-ssr>
      <div v-show="currentUser" >
        <div class="dropdown-content align-left lh20 px-md-20 py-md-10 bg-cl-white">
         <MyAccountLinks />
          <a href="#" class="no-underline  py-md-5 d-none d-xs-flex  align-item-center" @click.prevent="logout">
              <Icon class="w-xs-24 h-xs-24 mr-xs-15" icon-id="signout" />
              <span>{{ $t('Logout') }}</span>
            </a>
        </div> 
      </div>
    </no-ssr>
  </div>
</template>

<script>
import NoSSR from 'vue-no-ssr'
import { mapState } from 'vuex'
import Icon from 'theme/components/custom/Global/Icon'
import AccountIcon from '@vue-storefront/core/compatibility/components/blocks/Header/AccountIcon'
import MyAccountLinks from '../Shared/MyAccountLinks'

export default {
  mixins: [AccountIcon],
  data () {
    return {
      showMenu:false
    }
  },
  components: {
    'no-ssr': NoSSR,
    Icon,
    MyAccountLinks
  },
  computed:{
        ...mapState({
          isOpenLogin: state => state.ui.signUp,
          currentUser: state => state.user.current
        }),
    },
 methods: { 
  
    gotoAccount () {
      this.$bus.$emit('modal-toggle', 'modal-signup')
    },
 }
 
}
</script>

<style lang="scss" scoped>
@import '~theme/css/base/global_vars';
@import '~theme/css/variables/colors';
@import '~theme/css/helpers/functions/color';

$color-icon-hover: color(secondary, $colors-background);

.dropdown {
  outline: none;
  .account{
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 1.5px;
  }
  .icon{
    fill: #fff;
  }
  button {
    pointer-events: none;
  }
  @media (min-width: 768px) {
    .dropdown-content {
      display: none;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: 300px;
      top: 65px;
      z-index: 1;
      box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19); 
      -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
      -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.19);
      border-radius: 5px;  
      a{
          color: #000;
          font-size: 14px;
          font-weight: 600;
        }
    }
        
  }

  .user_icon{
      position: relative;
      .logged-in{
          position: absolute;
          width: 8px;
          height: 8px;
          border-radius: 50%;
          border:1px solid color(white);
          background: color(sdg-orange);
          right: -2px;
          top:0;
      }
  } 

  @media (min-width: 768px) {
    &:hover .dropdown-content:not(.dropdown-content__hidden),
    &:focus .dropdown-content:not(.dropdown-content__hidden) {
      display: block;
    }

    &:focus-within {
      background-color: $color-icon-hover;
      opacity: 1;
      .dropdown-content:not(.dropdown-content__hidden) {
        display: block;
      }
    }
  }

}

</style>
