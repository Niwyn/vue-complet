<template>
  <div class="container">
    <div v-if="posts && posts.length" class="row">
      <div v-for="post of posts" class="col-lg-6 post">
        <Post :postTab="post"/>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Post from '@/components/Post.vue'
import axios from 'axios'
import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)



export default {
  name: 'home',
  components: {
    Post
  },
  data () {
    return {
      posts: []
    }
  },
  created () {
    axios.get(`http://www.madeinblue.com/wp-json/wp/v2/posts`)
      .then(response => {
        // JSON responses are automatically parsed.
        this.posts = response.data
      })
      .catch(e => {
        this.errors.push(e)
      })
    axios.get(`http://www.madeinblue.com/wp-json/wp/v2/posts`)
      .then(response => {
        // JSON responses are automatically parsed.
        this.posts = response.data
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>

<style>
  .container{
    padding-top: 100px;
  }
</style>
