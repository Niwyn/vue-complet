<template>
  <div>
    <div v-html="postTab.title.rendered" class="h4 title"></div>
    <div class="font-italic mb-2">Publié le {{formatDate(postTab.date)}}, il y a {{calcDate(postTab.date)}}</div>
    <div v-html="postTab.content.rendered.slice(0, 200)"></div>
  </div>
</template>

<script>
import Vue from 'vue'
import moment from 'moment'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)

export default {
  name: 'Post',
  props: ['postTab'],
  methods: {
    calcDate: function (date) {
      return moment(date, 'YYYYMMDD').fromNow()
    },
    formatDate: function (date) {
      return moment(date).format('h:mm, DD/MM/YYYY')
    }
  }
}

</script>

<style scoped>
  .title{
    color: #DAA588;
    font-weight: bold;
  }
</style>
