<template>
  <div>
    <!-- <h1>{{ message }}</h1>
    <button-upload @asdasd="uploadImage" v-show="showButtonUpload"></button-upload>
    <BlockUI :message="blockUIData['msg']" :url="blockUIData['url']" v-if="blockUIData['display']"></BlockUI> -->
    <upload-image></upload-image>
  </div>
</template>

<script>

import Vue from 'vue'
import BlockUI from 'vue-blockui'
import loadingImage from './assets/logo-hacktiv8-animation.gif'
import buttonUpload from './components/buttonUpload'
import uploadImage from './components/uploadImage'

Vue.use(BlockUI)

export default {
  data() {
    return {
      showButtonUpload: true,
      blockUIData: {
        display: false,
        msg: 'Please Wait...',
        url: loadingImage
      }
    };
  },
  components: {
    buttonUpload,
    uploadImage
  },
  methods: {
   uploadImage: function(){
     this.showButtonUpload = !this.showButtonUpload
     this['blockUIData']['display'] = true
   }
  }
};
</script>

<style scoped>
</style>