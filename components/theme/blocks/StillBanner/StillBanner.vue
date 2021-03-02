<template>
<div class="container my-xs-25">
  <div class="row center-xs">    
    <div v-for="(name,index) in data" :key="index">
        <div class="tile middle-xs">
          <img
          class="tile-image"
          v-lazy="name.image">
          <div class="v-text-left px15 still-banner-css">

        <span v-html="name.heading">{{ name.heading }}</span>     
      <p v-html="name.desc">{{ name.desc }}</p>
      <button href="" v-html="name.action">{{ name.action }}</button>      
        </div>
        </div>
    </div>
  </div>
</div>
</template>

<script>
import states from "./data.json";
export default {
  name: "StillBanner",
  computed: {
    data () {
      return states.accounts.map((item) => {
        return (item);
      })
    }
  }
};
</script>

<style lang='scss' scoped>
@import '~theme/css/animations/transitions';

.tile {
  display: flex;
  overflow: hidden;
}

.tile-image {
  width: 100%;
  height: 100%;
  transition: transform 0.3s $motion-main;
}
.still-banner-css {
    position: absolute;
    float: left;
    width: 90%;
    text-align: left;
}
.still-banner-css span {
    font-size: 34px;
    width: 25%;
    margin: 15px 0;
    font-weight: normal;
    display: flex;
}
.still-banner-css p {
    font-size: 13px;
}
.still-banner-css button {
    margin-top: 15px;
    width: 20%;
    padding: 15px;
    border-radius: 5px;
    /* border-color: white; */
    border-width: inherit;
    border-style: none;
}
</style>
