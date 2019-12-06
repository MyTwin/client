<template>
<div>
  <h1>{{ message }}</h1>
  <!-- <div class="fb-quote">Ini adalah quote</div> -->
  <div><a :href="shareFacebook" target="_blank"><span><i class="fab fa-facebook" style="margin-right: 5px;"></i></span></a></div>
</div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello world',
      linkImage: 'https%3A%2F%2Fstorage.googleapis.com%2Fecommercebucket.danangbahari.com%2F1575580332867ayam.jpg',
      desc: 'ini adalah ayam yang enak sekali'
    };
  },
  computed:{
    shareFacebook(){
      return `https://www.facebook.com/sharer/sharer.php?u=${this.linkImage}&quote=${this.desc}`
    }
  }
}
</script>

<style scoped>
a{
  text-decoration: none;
}
</style>