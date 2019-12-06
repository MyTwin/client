<template>
  <div class="nav">
      <ul>
          <li><a href="#" @click="toggleShow(true)">Timeline</a></li>
          <li><a href="#" @click="toggleShow(false)">Create</a></li>

          <li class="right-nav"><a href="#" v-if="isLogin" @click.prevent="logout">Logout</a></li>
          <li class="right-nav" v-if="!isLogin"><a href="#" @click.prevent="toggleLog(true)">Login</a></li>
          <li><a href="#" v-if="!isLogin" @click.prevent="toggleLog(false)">Register</a></li>
      </ul>
  </div>
</template>

<script>
export default {
    props: ['isLogin'],
    methods: {
        toggleShow(value) {
            this.$emit('toggle-display', value)
        },
        toggleLog(value) {
            this.$emit('toggle-log', value)
        },
        logout() {
            localStorage.clear()
            this.$emit('logout')
        }
    }
}
</script>

<style scoped> 
    .nav ul{
        width: 100%;
        height: 3rem;
        display: flex;
        list-style: none;
        background-color: #e04766;
        align-items: center;
    }
    ul li {
        margin-left: 1rem;
        height: 3rem;
    }
    li a {
        text-decoration: none;
        color: #fff;
        line-height: 3rem;
        display: block;
        padding: 0 1rem;
    }
    .right-nav {
        margin-right: 1rem;
        margin-left: auto;
    }
    li a:hover {
        background-color: #c51639;
        transition: 0.4s background-color;
    }
</style>