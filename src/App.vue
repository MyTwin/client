<template>
  <div>

    <navBar 
      @toggle-display="changeMain" 
      @toggle-log="hideAll"
      @logout="checkLogin" 
      :isLogin="isLogin">
    </navBar>
    
    <div id="front" v-if="!main && !hideLogReg">
      <imageDisplay :srcUser="userImage" :srcResult="resultImage"></imageDisplay>
    </div>
    
    <div id="main" v-if="main && !hideLogReg">
      <listPost :posts="listPost"></listPost>
    </div>

    <login v-if="showLog && hideLogReg" @user-login="userIsLogin"></login>
    <register v-if="showReg && hideLogReg"></register>

    <container-form></container-form>
    <!-- <div class="container">
      <upload-image></upload-image>
      <imageDisplay :srcUser="userImage" :srcResult="resultImage" v-if="resultDisplay"></imageDisplay>
    </div>
    <div>
      <a :href="shareFacebook" target="_blank"><span><i class="fab fa-facebook" style="margin-right: 5px;"></i></span></a>
    </div> -->
    <!-- <listPost :posts="listPost"></listPost> -->

  </div>
</template>

<script>

  import imageDisplay from './components/imageDisplay'
  import listPost from './components/listPost'
  import navBar from './components/navbar'
  import login from './components/login'
  import register from './components/register'
  

  export default {
    data() {
      return {
        main: true,
        hideLogReg: false,
        isLogin: false,
        showLog: false,
        showReg: false,
        message: 'Hello world',
        userImage: 'https://picsum.photos/500',
        resultImage: 'https://picsum.photos/200/300',
        listPost: [
          {
            id:1,
            userImage: 'https://icatcare.org/app/uploads/2018/07/Thinking-of-getting-a-cat.png',
            resultImage: 'https://i.dailymail.co.uk/1s/2019/10/29/14/20320992-7625529-Cara_a_five_year_old_125lb_Bengal_tiger_has_been_fitted_with_a_g-a-8_1572358357911.jpg',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:2,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 10
          },
          {
            id:3,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 2
          },
          {
            id:4,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 55
          },
          {
            id:5,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 1
          },
          {
            id:6,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:7,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:8,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:9,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:10,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:11,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          },
          {
            id:12,
            userImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            resultImage: 'https://picsum.photos/400/520',
            userAvatar: 'https:picsum.photos/200',
            caption: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Rem perferendis repellat hic. Quam laudantium molestias illo tempore officia, provident impedit velit dicta id, porro perferendis aut. Illum dicta at nemo?',
            likes: 0
          }
        ]
      };
    },
    methods: {
      changeMain(v) {
        this.main = v
        this.hideLogReg = false  
      },
      hideAll(v) {
        if (v === true) {
          this.showLog = true
          this.showReg = false
          this.hideLogReg = true
        } else {
          this.showReg = true
          this.showLog = false
          this.hideLogReg = true
        }
      },
      userIsLogin(v) {
          this.showLog = false
          this.showReg = false
          
          this.hideLogReg = false
          
          this.main = true
          this.isLogin = true
      },
      userIsLogout() {
          this.showLog = true
          this.showReg = true

          this.hideLogReg = false
          
          this.main = true
          this.isLogin = false
      },
      checkLogin() {
        if (localStorage.getItem('token')) {
          this.userIsLogin()
          } else {
            this.userIsLogout()
          }
      }
    },
    created() {
        this.checkLogin()
    },
    components: {
      imageDisplay,
      listPost,
      navBar,
      login,
      register
    }
  }

</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Lato&display=swap');
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Lato', sans-serif; 
  }
  body {
    background-image: radial-gradient( circle,  rgba(255,246,236,1) 39.5%, rgba(100,46,122,0.23) 100.2% );
  }
</style>