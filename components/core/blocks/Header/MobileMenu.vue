<template>
    <nav class="d-xs-flex" :class="{'nav-open':openSidebarMenu}">
    <button
    type="button"
    class="bg-cl-transparent brdr-none inline-flex py0 pl0 pr15"
    @click="openMenu"
    :aria-label="$t('Open menu')"
    data-testid="menuButton"
  >
    <Icon class="icon w-xs-20 h-xs-16" icon-id="hamburger" />
  </button>
    <div class="mobilemenu_container bg-cl-white">
        <div class="signin_container bg-cl-sdg-darkblue cl-white px-xs-20 h-xs-50 h-md-auto d-xs-flex align-item-center"
        @click="login">
            <div class="user_icon  mr12">
                <Icon class="cl-white w-xs-24 h-xs-24 " icon-id="login" />
                <span v-if="currentUser" class="logged-in"></span>
            </div>
            <a class="link" v-if="!currentUser" 
            href="#" @click.prevent="closeMenu">Sign In</a>
            <span v-if="currentUser">{{currentUser.firstname}}</span>
        </div>
        <div class="menulinks_container">
            <div class="menulinks_wrapper" @click="closeSidebarMenu">
                <ul class="level-1" :class="{'active':openLevelOne}"> 
                    <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " @click="openLevelOne = true"
                    >
                        <span class="cl-white" href="">Shop All Products</span>
                        <Icon class="list__arrow cl-white w-xs-12 h-xs-10" icon-id="RightArrow" />
                    </li>
                    <li class="bg-cl-primary cl-white px20 py-xs-20  d-xs-flex align-item-center justify-space-between">
                        <router-link @click="openSidebarMenu = false"  class="no-underline block py10" :to="localizedRoute('/my-account')">Latest Arrivals</router-link>
                    </li>
                    
                </ul>
            </div>
            <div class="myaccountlinks_wrapper px-xs-20 py-xs-10 bg-cl-white" v-if="currentUser">
               <MyAccountLinks @click="closeSidebarMenu"/>
            </div>
            <div class="menulinks_wrapper2 px-xs-20 py-xs-10 " @click="closeSidebarMenu">
                <ul>
                    <li class="d-xs-flex align-item-center py-xs-10">
                        <router-link @click="openSidebarMenu = false"  class="no-underline block py10" :to="localizedRoute('/my-account')">
                        Help
                        </router-link>
                    </li>
                     <li class="d-xs-flex align-item-center py-xs-10">
                        <router-link @click="openSidebarMenu = false"  class="no-underline block py10" :to="localizedRoute('/my-account')">
                        Store Locator
                        </router-link>
                    </li>                
                </ul>
            </div>
        </div>
        <div class="logout_country_container bg-cl-white  brdr-top-1 brdr-cl-secondary w-100">
            <div class="d-xs-flex justify-space-around w-100 align-item-center">
                <div class=" p-xs-20"><lang-icon class="icon d-xs-flex pointer " /></div>
                <a  v-if="currentUser" href="#" class="w-50 d-xs-flex justify-center brdr-left-1 brdr-cl-secondary  p-xs-20" @click.prevent="logout" >
                    {{ $t('Logout') }}
                </a>
            </div>
        </div>
    </div>
      <div v-if="openSidebarMenu" @click="closeSidebarMenu" class="overlay" />
  </nav>
</template>

<script>
import Icon from 'theme/components/custom/Global/Icon'
import { mapState } from 'vuex'
import MyAccountLinks from './MyAccountLinks'
import LangIcon from 'theme/components/core/blocks/Header/LangIcon'
import AccountIcon from 'theme/components/core/blocks/Header/AccountIcon'
import i18n from '@vue-storefront/i18n'
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'
export default {
    name:'Mobile-Menu',
     components: {
        Icon,
        LangIcon,
        AccountIcon,
        MyAccountLinks
    },
    data(){
        return{
            openSidebarMenu:false,
            openLevelOne:false,
            componentLoaded: false,
            isCurrentMenuShowed:true
        }
    },
    computed:{
        ...mapState({
            currentUser: state => state.user.current
        }),        
    },
    mounted () {
        this.$nextTick(() => {
        this.componentLoaded = true;       
        })
        clearAllBodyScrollLocks()
    },

    methods: {
        openMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
            disableBodyScroll(this.$refs.container)
        },
        closeSidebarMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
            clearAllBodyScrollLocks()
        }, 
        login () {
            if (!this.currentUser) {
                this.$nextTick(() => {
                this.$store.commit('ui/setAuthElem', 'login')
                this.$bus.$emit('modal-show', 'modal-signup')
                this.$router.push({ name: 'my-account' })
                })
                this.openSidebarMenu = false;
            }
            
        },
        async logout () {
            await this.$store.dispatch('user/logout', {})
            this.$router.push(this.localizedRoute('/'))
            this.openSidebarMenu = false;  
            tihs.closeSidebarMenu();
        },
    },

}
</script>
<style scoped lang="scss">
@import "~theme/css/animations/transitions";
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.mobilemenu_container, .level-2{
    position: fixed;
    width: 80%;
    height: 100%;
    top:0;
    left: -100%;
    z-index: 10;
    overflow: auto;
    transition-duration: .25s;
}
.mobilemenu_container{
    background: color(sdg-lightgray);
    .signin_container .icon{
        fill: color(white);
    }
    .menulinks_wrapper a{
        color: color(white);
    }
    .myaccountlinks_wrapper a{
        color: color(black);
    }
    a.link{
        text-transform: uppercase;
        color: color(white);
        letter-spacing: 2px;
    }
}
nav{
    .icon{
      fill:color(white);
    }  
}
.nav-open{
    .mobilemenu_container{
        left: 0;
        transition-duration: .25s;
        .level-1{
            > li{
                border-bottom: 1px solid rgba(255, 255, 255, .3);                
            }                       
        }
        .level-1.active{
            .level-2{
                left: 0;
                transition-duration: .25s;  
            }
        } 
    }
}
.signin_container{
    text-transform: uppercase;
    letter-spacing: 1px;
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
}
.menulinks_container{
    overflow-y: auto;
    height: calc(100% - 122px);    
    span, a{
        font-size: 14px;
    }
}
.menulinks_wrapper{
    .icon{
        fill: color(white);
    }   
}
.myaccountlinks_wrapper, .menulinks_wrapper2{
    a{
        color: color(black);
    }
    .icon{
        fill: color(black);
    }
}
.logout_country_container{
    position: absolute;
    bottom: 0;
    left: 0;
    letter-spacing: 1px;
    text-transform: uppercase;
    a{
        color: color(black);
    }    
    .icon{
        fill: color(black);
    }
}
</style>