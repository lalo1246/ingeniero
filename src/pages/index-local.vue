<template>
  <q-page>
    <!--<img alt="Quasar logo" src="~assets/quasar-logo-full.svg">-->

    <q-spinner
      v-if="loading"
      color="primary"
      size="3em"
    />    
    <q-list bordered>
      <q-item 
        clickable 
        v-ripple
        v-for="post in posts" 
        :key="post.id"  
        
      >
        <q-item-section avatar>
          <q-avatar size="70px">
            <img>
          </q-avatar>
        </q-item-section>
        <q-item-section>{{ post.nombre }}</q-item-section>
      </q-item>
    </q-list>
    <q-dialog full-width v-model="showImageDialog">
          <q-card>
            <q-card-section class="row items-center justify-between">
              <div class="text-h6">Image</div>
              <q-space />
              <q-btn icon="close" flat round dense v-close-popup />
            </q-card-section>
            <q-card-section>
              <q-img
  
              />
            </q-card-section>
          </q-card>
        </q-dialog>        
  </q-page>
</template>
<style>
</style>

<script>
import axios from 'axios'
export default {
  name: 'PageIndex',
  async created () {
      var url = 'http://192.168.1.12/ingeniero-backend/productos'
      var le = await axios.get(url)
      this.loading = false  
      try{
        
        //this.posts = le.data.data.children
        console.log(le.data)
        this.posts = le.data
      }
      catch(e){
        this.loading = false
      }
  },
  data() {
    return {
      showImageDialog: false,
      imageUrl: '',
      loading: false,
      posts:[]
    }
  },
  methods: {
    showImage (image) {
    this.showImageDialog = true
    this.imageUrl = image
    }
  }
}
</script>
