<template>
    <modal name="modal-video" :width="800">
    <div class="close flex justify-flex-end pb-xs-20 pointer" @click.prevent="closeVideo">Close</div>
    <iframe width="100%" height="400" :src="currentVideoProps.influencerVideoUrl" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </modal>
</template>


<script>
import Modal from 'theme/components/core/Modal'
export default {
  name: 'VideoPopup',
  props: ["currentVideoProps"],
    components: {    
        Modal
    },

  methods: {   
    closeVideo() {
      this.$bus.$emit('modal-hide', 'modal-video')      
    }    
  }
};
</script>

<style scoped>
.modal .modal-container {
    padding: 20px;
}
</style>