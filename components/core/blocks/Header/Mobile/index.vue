<template>
    <nav class="d-xs-flex">
    <button
    type="button"
    class="bg-cl-transparent brdr-none inline-flex py0 pl0 pr15"
    @click="openMenu"
    :aria-label="$t('Open menu')"
    data-testid="menuButton"
  >
    <Icon class="white w-xs-20 h-xs-16" icon-id="hamburger" />
    </button>
    <transition name="slide-left">
        <div v-if="openSidebarMenu" class="mobilemenu_container z-xs-10 top-0 left-0 fixed h-100  bg-cl-sdg-lightgray w-80p">
            <div class="d-xs-flex flex-xs-column">
                <div class="signin_container bg-cl-sdg-darkblue uppercase cl-white px-xs-20 h-xs-50 h-md-auto d-xs-flex align-item-center"
                @click="login">
                    <div class="user_icon relative mr12">
                        <Icon class="white w-xs-24 h-xs-24 " icon-id="login" />
                        <span v-if="currentUser" class="logged-in absolute  bg-cl-sdg-orange"></span>
                    </div>
                    <a class="link-white" v-if="!currentUser" 
                    href="#" @click.prevent="closeMenu">Sign In</a>
                    <span v-if="currentUser" class="uppercase">{{currentUser.firstname}}</span>
                </div>
                <div class="menulinks_container font-bold">
                        <MobileMenu 
                        :shopallcategories="menuitems.categories.category" 
                        :brands="menuitems.brands.brand"
                        />
                    <div class="myaccountlinks_wrapper px-xs-20 py-xs-10 bg-cl-white" v-if="currentUser">
                        <MyAccountLinks @click="closeSidebarMenu"/>
                    </div>
                    <div class="px-xs-20 py-xs-10 " @click="closeSidebarMenu">
                        <MenuLinks />
                    </div>
                </div>
                <div class="logout_country_container bg-cl-white brdr-top-1 brdr-cl-secondary">
                    <div class="d-xs-flex justify-space-around w-100 align-item-center">
                        <div class=" p-xs-20">
                            <lang-icon class="icon d-xs-flex pointer " />
                        </div>
                        <a  v-if="currentUser" href="#" class="w-50 d-xs-flex justify-center brdr-left-1 brdr-cl-secondary  p-xs-20" @click.prevent="logout" >
                            {{ $t('Logout') }}
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </transition>
    <div v-if="openSidebarMenu" @click="closeSidebarMenu" class="overlay" />
  </nav>
</template>

<script>
import Icon from 'theme/components/custom/Global/Icon'
import { mapState } from 'vuex'
import MyAccountLinks from '../Shared/MyAccountLinks'
import MobileMenu from './MobileMenu'
import MenuLinks from './MenuLinks'
import LangIcon from '../Shared/LangIcon'
import i18n from '@vue-storefront/i18n'
import { disableBodyScroll, clearAllBodyScrollLocks } from 'body-scroll-lock'
export default {
    name:'MobileMenuContainer',
     components: {
        Icon,
        LangIcon,
        MyAccountLinks,
        MobileMenu,
        MenuLinks
    },
    data(){
        return{
            openSidebarMenu:false,
            componentLoaded: false,
            isCurrentMenuShowed:true
        }
    },
    props: {
       menuitems: {
        type: Object,
        required: true
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
            this.closeSidebarMenu();
        },
    },

}
</script>
<style lang="scss">
@import "~theme/css/animations/transitions";
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';

.signin_container{
    letter-spacing: 1px;
    .user_icon{
        .logged-in{
            border-radius: 50%;
            border:1px solid color(white);
            right: -2px;
            top:0;
            width: 8px;
            height: 8px;
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
.logout_country_container{
    position: absolute;
    bottom: 0;
    left: 0;
    letter-spacing: 1px;
    width: 100%;
    text-transform: uppercase;
}
.slide-left-enter-active,
.slide-left-leave-active{
  transition: transform .25s;
  left:0;
}

.slide-left-enter,
.slide-left-leave-to {
  transform: translateX(-100%);
}
</style>