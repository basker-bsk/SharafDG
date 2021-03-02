<template>
<div class="container">
  <div class="row">
    <div
      class="col-sm-4 pb15"
      v-for="(tile, index) in social_tiles"
      :key="index"
    >
    <div class="wrap image-discover-css">
      <div class="tile middle-xs" >
        <img class="tile-image" v-lazy="tile.image">        
      </div>
      <div class="image-discover-parent">
      <span v-html="tile.heading">{{ tile.heading }}</span>     
      <p v-html="tile.desc">{{ tile.desc }}</p>
      <a href="" v-html="tile.link">{{ tile.link }}</a>
      </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'ImageDiscover',
  data () {
    return {
      social_tiles: [
        {
          image: '/assets/ig/ig01.jpg',
          name: 'Woman practicing on the beach',
          heading: 'Win Prizes!',
          desc: 'Spend more than AED 2,500 to qualify for our lucky draw, T&Cs apply.',
          link: 'Discover Now >'
        },
        {
          image: '/assets/ig/ig02.jpg',
          name: 'Man practicing on the beach',
          heading: 'Fresh start with Sharaf DG grocery',
          desc: 'Fresh goods and essentials delivered right to your home, quality is always assured.',
          link: 'Discover Now >'
        },
        {
          image: '/assets/ig/ig03.jpg',
          name: 'Woman drinks water form the bottle on the beach',
          heading: 'Smartphones bonanza',
          desc: 'Save up to 50% off selected smartphones! While stocks last. T&C apply.',
          link: 'Discover Now >'
        }
      ]
    }
  }
}
</script>

<style scoped lang="scss">
.tile {
  display: flex;
  overflow: hidden;
}

.tile-image {
  width: 100%;
  height: 100%;
  border-radius: 10px 10px 0 0;
}
.image-discover-parent {
    padding: 10px;
}
.image-discover-css span {
    font-size: 14px !important;
    font-weight: bold;
}
.image-discover-css p {
    font-size: 14px !important;
}
.image-discover-css a {
    color: #0072ff!important;
    font-size: 14px!important;
}
.v-text-left {
    text-align: left!important;
}
.wrap {
    background: #f7f7f7!important;
    border-radius: 0 0 10px 10px;
}
</style>
