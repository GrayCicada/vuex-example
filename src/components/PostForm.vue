<template lang="html">
  <form>
     <input type="text" placeholder="title" v-model="title">
     <input type="text" placeholder="body" v-model="body">
     <button type="submit" @click.prevent="submit">Create post</button>
  </form>
</template>

<script>
import {mapMutations} from 'vuex'
export default {
   data(){
      return{
         title: '',
         body: ''
      }
   },
   methods: {
      ...mapMutations(['createPost']),
      submit(){
         this.createPost({
            title: this.title,
            body: this.body,
            id: Date.now()
         });
         this.title = this.body = ''
      }
   }
}
</script>

<style lang="css" scoped>
input{
   display: block;
   width: 100%;
   border: 1px solid #ddd;
   border-radius: 4px;
    padding: 10px;
    margin-bottom: 10px;
}
button{
   background: green;
   color: #fff;
   border-radius: 4px;
   padding: 0.5rem 0.75rem;
   border: 1px solid green;
   font-size: 1rem;
}
</style>
