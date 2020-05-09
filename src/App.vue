<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
//import storage from './storage'
export default {
  name: 'App',
  components: {
    
  },
  data(){
    return {

    }
  },
  mounted(){
    // storage.setItem('a',1);
    // storage.setItem('user',{a:1});
    // storage.setItem('abc',{a:1},'user');
    // storage.clear('a');
    //storage.clear('a','user');
    this.getUser();
    this.getCartCount();
  },
  methods:{
    getUser(){
      this.axios.get('/user').then((res={})=>{
        this.$store.dispatch('saveUserName',res.username);
      });
      console.log(this);
    },
    getCartCount(){
       this.axios.get('/carts/products/sum').then((res=0)=>{
         this.$store.dispatch('saveCartCount',res)
      })
    }
  }
}
</script>

<style lang="scss">
@import './assets/sass/reset.scss';
@import './assets/sass/config.scss';
@import './assets/sass/button.scss';
</style>
