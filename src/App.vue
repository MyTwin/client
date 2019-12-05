<template>
  <div>
    <div><a :href="shareFacebook" target="_blank"><span><i class="fab fa-facebook" style="margin-right: 5px;"></i></span></a></div>
    <imageDisplay :srcUser="userImage" :srcResult="resultImage"></imageDisplay>
    <!-- <listPost :posts="listPost"></listPost> -->
  </div>
</template>

<script>
import imageDisplay from './components/imageDisplay'
import listPost from './components/listPost'

export default {
  data() {
    return {
      message: 'Hello world',
      linkImage: 'https%3A%2F%2Fstorage.googleapis.com%2Fecommercebucket.danangbahari.com%2F1575580332867ayam.jpg',
      desc: 'ini adalah ayam yang enak sekali',
      userImage: 'https://icatcare.org/app/uploads/2018/07/Thinking-of-getting-a-cat.png',
      resultImage: 'https://i.dailymail.co.uk/1s/2019/10/29/14/20320992-7625529-Cara_a_five_year_old_125lb_Bengal_tiger_has_been_fitted_with_a_g-a-8_1572358357911.jpg',
      listPost: [
        {
          id:1,
          userImage: 'https://icatcare.org/app/uploads/2018/07/Thinking-of-getting-a-cat.png',
          resultImage: 'https://i.dailymail.co.uk/1s/2019/10/29/14/20320992-7625529-Cara_a_five_year_old_125lb_Bengal_tiger_has_been_fitted_with_a_g-a-8_1572358357911.jpg'
        },
        {
          id:2,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:3,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:4,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:5,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:6,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:7,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:8,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:9,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:10,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:11,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        },
        {
          id:12,
          userImage: 'https://picsum.photos/400/520',
          resultImage: 'https://picsum.photos/400/520'
        }
      ]
    };
  },
  components: {
    imageDisplay,
    listPost
  },
  computed:{
    shareFacebook(){
      return `https://www.facebook.com/sharer/sharer.php?u=${this.linkImage}&quote=${this.desc}`
    }
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  a{
    text-decoration: none;
  }
</style>