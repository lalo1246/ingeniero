<template>
  <q-page>
    <!--<img alt="Quasar logo" src="~assets/quasar-logo-full.svg">-->
    <q-spinner
      v-if="loading"
      color="primary"
      size="3em"
    />    
    <q-list v-else bordered>
      <q-item 
        clickable 
        v-ripple
        v-for="post in posts" 
        :key="post.data.id"  
      >
        <q-item-section avatar>
          <q-avatar size="70px">
            <img :src="post.data.thumbnail">
          </q-avatar>
        </q-item-section>
        <q-item-section>{{ post.data.title }}</q-item-section>
      </q-item>
    </q-list>    
  </q-page>
</template>
<style>
</style>

<script>
import axios from 'axios'
export default {
  name: 'PageIndex',
  async created () {
      var le = await axios.get('https://www.reddit.com/r/aww.json?raw_json=1')
      try{
        this.loading = false  
        this.posts = le.data.data.children
        console.log(le)
      }
      catch(e){
        this.loading = false
      }
  },
  data() {
    return {
      loading: true,
      posts:[]
    }
  }
}
</script>
