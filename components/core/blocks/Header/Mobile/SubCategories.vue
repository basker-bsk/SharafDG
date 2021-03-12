<template>
  <div class="bg-cl-white z-xs-1 absolute h-100 w-100 top-0 left-0">
    <div class="d-xs-flex flex-xs-column">
      <div
        class="px-xs-20 py-xs-15 d-xs-flex bg-cl-primary align-item-center"
        @click="$emit('resetSubSelected')"
      >
        <Icon
          class="list__arrow white w-xs-12 h-xs-10 mr-xs-10"
          icon-id="LeftArrow"
        />
        <span class="cl-white font-bold">{{ title }}</span>
      </div>
      <div class="h-100vh overflow-xs-auto">
        <ul class="py-xs-10">
          <li
            class="px-xs-20 py-xs-10 relative"
            :class="{'active':(selectedSubCategory == subindex && openSubMenu)}"
            v-for="(submenu,subindex) in subcategories"
            :key="subindex"
          >
            <div
              class="d-xs-flex d-xs-flex w-100 justify-space-between align-item-center"
              @click="expandSubmenu(subindex)"
            >
              <router-link
                v-if="!submenu.subcategories"
                :to="localizedRoute(submenu.url)"
                :title="$t(submenu.name)"
                class="link-dark"
              >
                {{ submenu.name }}
              </router-link>
              <span v-if="submenu.subcategories">{{ submenu.name }}</span>
              <span v-if="submenu.subcategories">
                <Icon
                  v-if="(selectedSubCategory == subindex && openSubMenu)"
                  class="list__arrow dark w-xs-12 h-xs-10"
                  icon-id="downArrow"
                />
                <Icon
                  v-if="!(selectedSubCategory == subindex && openSubMenu)"
                  class="list__arrow dark w-xs-12 h-xs-10"
                  icon-id="RightArrow"
                />
              </span>
            </div>
            <transition name="slide-left">
              <ul class="pt-xs-10 acc-menu">
                <li
                  class="px-xs-10 py-xs-5 font-normal"
                  v-for="(submenu2,index) in submenu.subcategories"
                  :key="index"
                >
                  <router-link
                    :to="localizedRoute(submenu.url)"
                    class="link-dark"
                  >
                    {{ submenu2.name }}
                  </router-link>
                </li>
              </ul>
            </transition>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
export default {
  name: 'SubCategories',
  components: {
    Icon
  },
  data () {
    return {
      openSubMenu: false,
      selectedSubCategory: Number
    }
  },
  props: {
    subcategories: {
      type: Array,
      required: true
    },
    title: {
      type: String,
      required: true
    }
  },
  methods: {
    expandSubmenu (index) {
      this.selectedSubCategory = index;
      this.openSubMenu = !this.openSubMenu;
    }
  }
}
</script>
<style scoped lang="scss">
.acc-menu {
  display: none;
}
.active {
  .acc-menu {
    display: block;
  }
}
</style>
