<template>

  <div class="col-md-7 brdr-right-1 brdr-cl-secondary p-md-15 dropdown-center">
        <div v-for="(item, index) of subCategoryList1"
          :key="index" class="menulist"
        >
          <a class="list__link" href="" >
            <strong class="list__content ">
              {{ item.name }}
            </strong>
          </a>
          <ul v-if="item.subcategories">
            <li  v-for="(itemlist, index) of item.subcategories" :key="index">
               <a class="list__link" href="" > {{itemlist.name}} </a>
            </li>
          </ul>
        </div>     
    </div>
</template>

<script>

export default {
  name: 'SubCategory',
  props: {
    category: {
      type: Array,
      required: true
    }   
  },
  computed: {
    subCategoryList () {
      let subCategoryList = this.category || []
      return subCategoryList;
    },
    subCategoryList1 () {
      let subCategory = this.subCategoryList
      return subCategory.filter((category, index) => {
        return index <= 9
      })
    },

  },

}
</script>

<style lang="scss" >

</style>
