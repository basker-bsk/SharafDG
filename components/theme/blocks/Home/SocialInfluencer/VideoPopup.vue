<template>
    <modal name="modal-video" :width="800">
    <div class="close" @click.prevent="closeVideo">Close</div>
    <iframe width="100%" height="400" :src="currentVideoProps.name" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
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