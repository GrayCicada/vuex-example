<template>
<div id="app">
   <PostForm />
   <hr>
   <h4>Posts count: {{postsCount}}</h4>
   <div class="post" v-for="post in validPosts" :key="post.id">
      <h3>{{post.title}}</h3>
      <p>{{post.body}}</p>
   </div>
</div>
</template>

<script>
   import {mapGetters, mapActions} from 'vuex'
   import PostForm from './components/PostForm'
   export default {
      name: 'app',
      // computed: {
      //    allPosts(){
      //       return this.$store.getters.allPosts;
      //    }
      // },
      // Альтернативный способ
      computed: mapGetters(['validPosts', 'postsCount']),
      methods: mapActions(['fetchPosts']),
      async mounted() {
         // this.$store.dispatch('fetchPosts')
         this.fetchPosts(15)
      },
      components: {
         PostForm
      }
   }
</script>

<style>
#app {
   font-family: 'Avenir', Helvetica, Arial, sans-serif;
   -webkit-font-smoothing: antialiased;
   -moz-osx-font-smoothing: grayscale;
   text-align: center;
   color: #2c3e50;
   margin: 60px auto;
   width: 400px;
}
.post{
   text-align: left;
   border: 1px solid #eee;
   border-radius: 5px;
   margin-bottom: 1rem;
   padding: 1rem;
}
</style>
