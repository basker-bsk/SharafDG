<template>
    <ul class="menulinks_wrapper2">
        <li class="d-xs-flex align-item-center py-xs-10">
            <router-link @click="openSidebarMenu = false"  class="link no-underline block py10" :to="localizedRoute('/my-account')">
            Help
            </router-link>
        </li>
            <li class="d-xs-flex align-item-center py-xs-10">
            <router-link @click="openSidebarMenu = false"  class="link no-underline block py10" :to="localizedRoute('/my-account')">
            Store Locator
            </router-link>
        </li>                
    </ul>
</template>
<script>
export default {
    name:"MenuLinks",
}
</script>