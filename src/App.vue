<template>
  <div id="app">
    <!-- <img :src="require('./assets/logo.png')"> -->
    <!-- <h1>{{ msg }}</h1>
    <h2 @click="changeText">Essential Links</h2> -->
    <TodoList/>
    <ul>
      <li><router-link to="/about">About</router-link></li>
      <li><router-link to="/product">Product</router-link></li>
    </ul>
    <div>
      <transition name="fade" mode="out-in">
        <router-view :key="+new Date()"></router-view>
      </transition>
    </div>
  </div>
</template>

<script>
import VueRouter from 'vue-router';
import TodoList from '@/components/TodoList';
import About from './components/About'
import Product from './components/Product'
import NotFound from './components/NotFound'

const Home = {
  template: `
    <div>
      Home
      <div @click="changeToAbout">change to about</div>
    </div>
  `,
  methods:{
    changeToAbout(){
      this.$router.push({
        path: `/about/${123}`,
      })
    }
  }
}

export default {
  name: 'app',
  router: new VueRouter({
    // mode: 'history',
    routes: [
      {path: '/', component: Home},
      {path: '/about/:id?', component: About},
      {path: '/product', component: Product},
      {path: '*', component: NotFound },
    ]
  }),
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components:{
    TodoList
  },
  methods:{
    changeText(){
      this.msg = 'clciked';
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}

/*
fade-enter-active / fade-leave-active
進入完成state / 正要離開state
fade-enter / fade-leave-to
進入前狀態 / 離開後狀態

順序 -> 
fade-enter -> fade-enter-active
fade-leave-active -> fade-leave-to

本質就是因為css 對沒有數值的屬性沒辦法做transition
所以vue 包裝好組件讓
我們能用transition特性 由 在<transition> 上下name屬性
即對應到class，然後讓元素能從狀態一過場到狀態二


*/
.fade-enter-active,.fade-leave-active {
  transition: transform .3s ease-in,opacity .3s ease-in;
  opacity: 1;
  transform: translateX(0px);
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.fade-enter{
  transform: translateX(50px);
}
.fade-leave-to{
  transform: translateX(-50px);
}
</style>
