<template>
  <div>

    <navBar 
      @toggle-display="changeMain" 
      @toggle-log="hideAll"
      @logout="checkLogin" 
      :isLogin="isLogin">
    </navBar>
    
    <div id="front" v-if="!main && !hideLogReg">
      <imageDisplay 
        :srcUser="userImage" 
        :srcResult="resultImage"
        @dataCreate="fetchAllPostData"
        @goTimeline="changeMain"
        ></imageDisplay>
    </div>
    
    <div id="main" v-if="main && !hideLogReg">
      <listPost :posts="listPost" @fetch-data="fetchAllPostData"></listPost>
    </div>

    <login v-if="showLog && hideLogReg" @user-login="userIsLogin"></login>
    <register v-if="showReg && hideLogReg"></register>

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
  import containerForm from './components/containerForm'
  import axios from 'axios'
  import Swal from 'sweetalert2'
  

  export default {
    data() {
      return {
        main: true,
        hideLogReg: false,
        isLogin: false,
        showLog: false,
        showReg: false,
        baseUrl: 'http://localhost:3000',
        message: 'Hello world',
        userImage: 'https://picsum.photos/500',
        resultImage: 'https://picsum.photos/200/300',
        listPost: []
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
      },
      fetchAllPostData(){
        axios({
          url: `${this.baseUrl}/post`,
          method: 'GET'
        })
        .then(({data})=>{
          this.listPost = data
        })
        .catch(err => {
          Swal.fire({
              icon: 'error',
              title: 'Oops...',
              text: `${err.response.data.message}`
          })
        })
      }
    },
    created() {
        this.checkLogin()
        this.fetchAllPostData()
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