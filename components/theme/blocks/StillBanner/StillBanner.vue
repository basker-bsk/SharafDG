<template>
   <div class="still-banner-container">
      <div class="container center-xs">
         <section class="top-banner-section">
            <div class="banner-image-div" v-for="(name,index) in data" :key="index">
               <img
                  class="tile-image banner-image"
                  v-lazy="name.image">
               <div class="still-banner-css">
                  <span v-html="name.heading">{{ name.heading }}</span>     
                  <p v-html="name.desc">{{ name.desc }}</p>
                  <button href="" v-html="name.action">{{ name.action }}</button>
               </div>
            </div>
         </section>
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


.still-banner-container .tile {
	display: flex;
	overflow: hidden;
}

.still-banner-container .tile-image {
	width: 100%;
	height: 100%;
	border-radius: 5px;
}

.still-banner-container .still-banner-css {
	position: absolute;
	float: left;
	width: 100%;
	text-align: left;
	top: 0;
	padding: 20px;
}

.still-banner-container .still-banner-css span {
	font-size: 28px;
	width: 25%;
	margin: 15px 0;
	font-weight: normal;
	display: flex;
	color: #ffffff;
}

.still-banner-container .still-banner-css p {
	font-size: 13px;
	color: #ffffff;
}

.still-banner-container .still-banner-css button {
	margin-top: 15px;
	width: 20%;
	padding: 12px 0;
	border-radius: 5px;
	/* border-color: white; */
	border-width: inherit;
	border-style: none;
}

@media only screen and (max-width: 600px) {
	.still-banner-container {
		padding: 0;
	}
	.still-banner-container .tile-image {
		border-radius: 0px;
	}
	.still-banner-container .container {
		padding: 0;
	}
	.still-banner-container .still-banner-css {
		padding: 25px;
	}
	.still-banner-container .still-banner-css span {
		width: 65%;
	}
	.still-banner-container .still-banner-css p {
		font-size: 13px;
		width: 55%;
	}
	.still-banner-container .still-banner-css button {
		width: 55%;
	}
	.still-banner-container .banner-image {
		height: 100%!important;
		min-width: 230%!important;
	}
}

.still-banner-container .top-banner-section {
	display: grid;
	grid-template-columns: 1fr;
	grid-template-rows: 350px;
	grid-column-gap: 0px;
	grid-row-gap: 0px;
	align-content: center;
	justify-content: center;
}

.still-banner-container .banner-image-div {
	position: relative;
}

.still-banner-container .top-banner-section .banner-image-div {
	grid-area: 0.25;
}

.still-banner-container .top-banner-section .banner-overlay-div {
	grid-area: 0.25;
}

.still-banner-container .top-banner-section .banner-text-div {
	grid-area: 0.25;
}

.still-banner-container .banner-image {
	display: grid;
	min-width: 350px;
	width: 100%;
	}

</style>